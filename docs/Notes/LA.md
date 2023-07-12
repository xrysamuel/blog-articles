# 线性代数笔记

*Time: 2022/11/20*

*Note Author: XrySamuel*

## 符号、定义与声明

零矩阵（$ \mathbf{O} $）、对角矩阵（$ diag $）、单位矩阵（$ \mathbf{E} $）、对称矩阵、反对称矩阵、线性方程组、解、解集、系数矩阵（$ \mathbf{A} $）、增广矩阵（$ \widetilde{\mathbf{A}} $）、（行/列）初等变换（$ret/cet$）、初等矩阵、（简化）阶梯形矩阵（$ (R)REM $）、子式（$ M $）、余子式（$ M' $）、代数余子式（$ A $）、逆序数（$ \tau $）

- 如无特殊说明，向量均指的是列向量
- 若 $ \sum $ 省略下标，则是对求和式中的重复指标求和；若省略上标，则是对指标能取到的所有值进行求和
-  $ a_{ij} $ 指的是矩阵 $ \mathbf{A} $ 在第 i 行第 j 列上的元素，对 $ b_{ij} $、$ c_{ij} $ 等同理
- $ r_{i} $ 指的是矩阵或行列式的第 i 行
- $ c_{j} $ 指的是矩阵或行列式的第 j 列
- $ (F(i,j)) $ 指的是在第 i 行第 j 列上的元素为 $ F(i,j) $ 的矩阵
- 如无特殊说明，$m$ 和 $n$ 指的是矩阵的行数和列数


## 大纲
- A 矩阵代数
    - A1 矩阵的运算
        - 运算
            - 矩阵加减
            - 矩阵数乘
            - 矩阵乘法
            - 矩阵的逆
                - 伴随矩阵法
                - 初等变换法
            - 矩阵的迹
            - 矩阵的转置
            - 伴随矩阵
            - 行列式
                - 定义式
                - 按行（列）展开
                - 按多行（列）展开
            - 矩阵的秩
                - 定义
                - 初等变换法
        - 运算性质
        - 分块矩阵的运算
    - A2 特征值和特征向量
        - 特征值
        - 特征向量
        - 特征值和特征向量的求法
        - 特征值的性质
        - 特征向量的性质
    - A3 二次型
        - 二次型
        - 标准二次型
        - 规范二次型
        - 正定二次型
- B1 解线性方程组
    - 解出解
        - n 个未知数 n 个方程：Cramer 法则
        - n 个未知数 m 个方程：Gauss-Jordan 算法
    - 解的情况
        - n 个未知数 n 个方程：系数矩阵行列式
        - n 个未知数 m 个方程：矩阵的秩
            - 齐次线性方程组
            - 非齐次线性方程组
- B2 向量空间
    - 子空间
        - 零空间
        - 特征子空间
    - 极大无关组
    - 基
    - 向量组的秩
- C 矩阵关系
    - C1 等价关系
        - 等价关系
        - 等价标准形
    - C2 相似关系
        - 相似关系
        - Jordan 标准形
    - C3 合同关系
        - 合同关系
        - 合同标准形

## A1 矩阵的运算

研究对象：矩阵及其运算

*本章将引入矩阵代数工具，其中矩阵的基本运算及其基本性质将会贯穿整个线性代数的体系。*

**矩阵的运算**
- 矩阵加减：$ \mathbf{A}+\mathbf{B} := (a_{ij} + b_{ij})$
- 矩阵数乘：$ k\mathbf{A} := (ka_{ij})$
- 矩阵乘法：$ \mathbf{A}\mathbf{B} := (\sum a_{ik}b_{kj}) $
- 方阵的逆：$ \mathbf{A}^{-1} : \mathbf{A}^{-1}\mathbf{A}=\mathbf{A} \mathbf{A}^{-1}=E$
    - 伴随矩阵法：$ \mathbf{A}^{-1} = \frac{1}{|\mathbf{A}|}\mathbf{A}^{*} $
    - 初等变换法：$ (\mathbf{A}\ \mathbf{E}) \xrightarrow{ret}\cdots\xrightarrow{ret}(\mathbf{E}\ \mathbf{A}^{-1}) $
- 方阵的迹：$ tr(\mathbf{A}) := \sum a_{ii}$
- 矩阵的转置：$ \mathbf{A}^{T} := (a_{ji})$
- 伴随矩阵：$ \mathbf{A}^{*} := (A_{ji})$
- 方阵的行列式：$ D=|\mathbf{A}| $
    - 定义式：$ |\mathbf{A}| = \sum_{j_{1}j_{2}\cdots j_{n}}(-1)^{\tau(j_{1}j_{2}\cdots j_{n})}a_{1j_{1}}a_{2j_{2}}\cdots a_{nj_{n}}$
    - 按行（列）展开：$ |\mathbf{A}| = \sum_{j} a_{ij}A_{ij} $
    - 按多行（列）展开：$ |\mathbf{A}| = \sum_{q} M_{q}A_{q} $
- 矩阵的秩：$ r=r(\mathbf{A}) $
    - 定义：有一个 $ r $ 阶子式不为 0，高于 $ r $ 阶子式都为 0
    - 初等变换法：$ \mathbf{A} \xrightarrow{ret/cet}\cdots\xrightarrow{ret/cet} REM$

**矩阵的运算性质**（显然的性质略）
- 线性运算性质
- 矩阵转置的性质
    - $ (\mathbf{A}+\mathbf{B})^T=\mathbf{A}^T+\mathbf{B}^T $
    - $ k \mathbf{A}^{T}=(\mathbf{kA})^T $
- 矩阵乘法的性质（注意无交换律、消去律）
    - $ (\mathbf{A}\mathbf{B})^T = \mathbf{B}^T \mathbf{A}^T $
- 方阵的迹的性质
    - $ tr(\mathbf{A}\mathbf{B}) = tr(\mathbf{B}\mathbf{A}) $
- 行列式的性质
    - $ D=D^{T} $
    - 倍乘：$ k|r_{1}, r_{2},\cdots,r_{n}|= |r_{1}, r_{2},\cdots,kr_{p},\cdots,r_{n}| $，$ r $ 换成 $c $ 也成立，下同
    - 拆分：$ |r_{1}, r_{2},\cdots,r^{(1)}_{p},\cdots,r_{n}| + |r_{1}, r_{2},\cdots,r^{(2)}_{p},\cdots,r_{n}| = |r_{1}, r_{2},\cdots,r^{(1)}_{p} + r^{(2)}_{p},\cdots,r_{n}| $
    - 对换：$ |r_{1}, r_{2},\cdots,r_{p},\cdots,r_{q},\cdots,r_{n}|= - |r_{1}, r_{2},\cdots,r_{q},\cdots,r_{p},\cdots,r_{n}| $
    - 倍乘：$ |r_{1}, r_{2},\cdots,r_{p},\cdots,r_{q},\cdots,r_{n}|= |r_{1}, r_{2},\cdots,r_{p},\cdots,kr_{p}+r_{q},\cdots,r_{n}| $
    - $ |\mathbf{A}\mathbf{B}|=|\mathbf{A}||\mathbf{B}| $
        - 证明：令 $ \mathbf{D} = \begin{vmatrix}
            A &  O \\
            -E &  B \\
        \end{vmatrix} $
- 伴随矩阵的性质
    - $ \mathbf{A}\mathbf{A}^*=|\mathbf{A}|\mathbf{E} $
    - $ |\mathbf{A}^*|=|\mathbf{A}|^{(n-1)} $
- 可逆矩阵的性质
    - $ \exists \mathbf{A}^{-1} \iff |\mathbf{A}| \neq 0 $
    - $ (\mathbf{A}^T)^{-1}=(\mathbf{A}^{-1})^T $
    - $ (\mathbf{A}\mathbf{B})^{-1} = \mathbf{B}^{-1} \mathbf{A}^{-1} $
    - $ |\mathbf{A}^{-1}| = |\mathbf{A}|^{-1} $
- 秩的性质
    - $ 0 \leqslant r(\mathbf{A}) \leqslant min\left\{ m,n \right\}  $
    - $ r(\mathbf{A})=r(\mathbf{A}^T) = r(A^{T}A)=r(A A^{T})$
    - 行阶梯形矩阵的秩是它的非零行数
    - 矩阵乘以可逆矩阵，秩不变（矩阵初等变换后秩不变）
    - $ r(\mathbf{A} \pm \mathbf{B})\leqslant r(\mathbf{A})+r(\mathbf{B}) $
    - $ r(\mathbf{A})+r(\mathbf{B})-n\leqslant r(\mathbf{A}\mathbf{B})\leqslant min\left\{ r(\mathbf{A}),r(\mathbf{B}) \right\} $（$ \mathbf{A},\mathbf{B} $ 分别是 $ m \times n,n\times l $ 矩阵）
    - $ max\left\{ r(\mathbf{A}),r(\mathbf{B}) \right\} \leqslant r(\mathbf{A}\quad \mathbf{B})=r(\mathbf{B}\quad \mathbf{A}) \leqslant r(\mathbf{A}) + r(\mathbf{B}) $
    - $ r(\mathbf{A}^*)= \begin{cases}n,\ r(\mathbf{A})=n \\ 1,\ r(\mathbf{A})=n-1 \\ 0,\ r(\mathbf{A})<n-1 \\ \end{cases}$
    - $ \displaystyle r\begin{bmatrix}\mathbf{A} &  \mathbf{O} \\ \mathbf{O}& \mathbf{B}  \\\end{bmatrix} =r(\mathbf{A})+r(\mathbf{B})$
    - $ \displaystyle r\begin{bmatrix}\mathbf{A} &  \mathbf{O} \\ \mathbf{C}& \mathbf{B}  \\\end{bmatrix} \geqslant r(\mathbf{A})+r(\mathbf{B})$

**分块矩阵的运算**

- 分块矩阵加减：$ \mathbf{A}+\mathbf{B} = (A_{ij} + B_{ij})$
- 分块矩阵数乘：$ k\mathbf{A} = (kA_{ij})$
- 分块矩阵乘法：$ \mathbf{A}\mathbf{B} = (\sum A_{ik}B_{kj}) $
- 分块矩阵的转置：$ \mathbf{A}^{T} = (A^{T}_{ji})$
- 分块对角矩阵的逆：$diag(A_{1},A_{2},\cdots,A_{s})^{-1}=diag(A^{-1}_{1},A^{-1}_{2},\cdots,A^{-1}_{s})$
- 分块对角矩阵的行列式：$|diag(A_{1},A_{2},\cdots,A_{s})|=|A_1||A_2|\cdots|A_{s}|$
- 特殊分块矩阵的伴随矩阵：$ \begin{bmatrix}A &  O \\O &  B \\ \end{bmatrix}^* = \begin{bmatrix}|B|A^{*} &  O \\O &  |A|B^{*} \\ \end{bmatrix}$

## B1 解线性方程组

研究对象：线性方程组 $ \mathbf{A}x=\beta $，以及特殊情况——齐次线性方程组 $ \mathbf{A}x=0 $，以及作为推广的矩阵方程 $ \mathbf{A}\mathbf{X}=\mathbf{B} $

*解线性方程组是线性代数的核心问题。解线性方程组的方法以及对线性方程组解的情况（相容性、唯一性、解的结构）的探讨建立在上一章“A1 矩阵的运算”所介绍的矩阵代数工具之上；而为了进一步研究解的情况，研究解的结构，引入下一章“B2 向量空间”。*

**Cramer 法则** （n 个未知数 n 个方程）

$$\begin{cases}
x_{1}=D_{1}/D \\
x_{2}=D_{2}/D \\
\ \vdots \\
x_{n}=D_{n}/D \\
\end{cases}\\$$

其中

$$D_{j}=\begin{vmatrix}
    a_{11} & \cdots& a_{1(j-1)} & b_{1} & a_{1(j+1)} &\cdots & a_{1n} \\
    a_{21} & \cdots& a_{2(j-1)} & b_{2} & a_{2(j+1)} &\cdots & a_{2n} \\
    \vdots &  & \vdots & \vdots & \vdots &  & \vdots \\
    a_{n1} & \cdots& a_{n(j-1)} & b_{n} & a_{n(j+1)} &\cdots & a_{nn}
    \end{vmatrix}
$$

本质就是矩阵求逆

**Cramer 法则** （系数矩阵为方阵的矩阵方程）

$ (\mathbf{A}\quad \mathbf{B}) \xrightarrow{ret}\cdots\xrightarrow{ret}(\mathbf{E}\quad \mathbf{A}^{-1}\mathbf{B}) $，$ \mathbf{A}^{-1}\mathbf{B} $ 就是矩阵方程的解

**Gauss-Jordan 算法** （n 个未知数 m 个方程）

$ \widetilde{\mathbf{A}} \xrightarrow{ret}\cdots\xrightarrow{ret} RREM $，对增广矩阵进行行变换对应方程的解不变，故 $ RREM $ 对应的方程的解就是原方程的解

**解的情况**（相容性、唯一性、解的结构）

对于 n 个未知数 n 个方程

- 唯一解：$ |\mathbf{A}|=0 $

对于 $ \mathbf{A}x=\beta $

- 有解：$ r(\mathbf{A}) = r(\widetilde{\mathbf{A}}) $
    - 唯一解：$ r(\mathbf{A}) = r(\widetilde{\mathbf{A}}) = n $
    - 无穷多解：$ r(\mathbf{A}) = r(\widetilde{\mathbf{A}}) < n$
- 无解：$ r(\mathbf{A}) +1= r(\widetilde{\mathbf{A}}) $

对于 $ \mathbf{A}x=0 $

- 只有 0 解：$ r(\mathbf{A}) = n $
- 有无穷多解（非零解）：$ r(\mathbf{A}) < n $

对于 $ \mathbf{A}\mathbf{X}=\mathbf{B} $

- 有解：$ r(\mathbf{A}) = r(\mathbf{A}\quad \mathbf{B}) $

解的结构：
- $ \mathbf{A}x=0 $：它的解集 $ Nul \mathbf{A} $ 是 $ K^{n} $ 的 $ n-r(\mathbf{A}) $ 维子空间，$ Nul \mathbf{A} $ 的一组基称为该齐次方程的基础解系
- $ \mathbf{A}x=\beta $：它的解集是 $ \left\{ \gamma = \gamma_{0}+\sum k_{j}\eta_{j}|k_{j}\in K \right\} $，其中 $ \eta_{1},\cdots,\eta_{n-r(\mathbf{A})} $ 是 $ Nul \mathbf{A} $ 的一组基

## B2 向量空间

研究对象：向量空间及向量组

*向量空间是在研究线性方程组解的结构时抽象出的更深刻的结构。*

**n 维向量空间**：$ K^{n} $ 关于向量加法和纯量乘法

**线性子空间**
- 零空间：$ Nul \mathbf{A}=\left\{ \alpha\in K^{n}|\mathbf{A}\alpha=0 \right\}  $
- 生成子空间：$ L(\alpha_{1}\cdots\alpha_{s})=\left\{\sum k_{i}\alpha_{i}|k_{i}\in K\right\} $
- 特征子空间：$ V_{\lambda_{i}}=\left\{ \alpha\in K^{n}|(\lambda_{i}\mathbf{E}-\mathbf{A})\alpha=0 \right\}  $

**线性表示** $ \beta \leftarrow \alpha_{1}\cdots\alpha_{s} $：$ \beta = \sum k_{i}\alpha_{i}$
- 方程视角：$ \mathbf{A}x=\beta $ 有解，$ \mathbf{A}=(\alpha_{1}\cdots\alpha_{s}) $
- 线性子空间视角：$ \beta \in L(\alpha_{1}\cdots\alpha_{s}) $

**线性表示** $ \beta_{1}\cdots\beta_{s}\leftarrow \alpha_{1}\cdots\alpha_{s} $：$ \forall \beta_{i}\leftarrow \alpha_{1}\cdots\alpha_{s} $
- 方程视角：$ \mathbf{A}\mathbf{X}=\mathbf{B} $ 有解，$ \mathbf{A}=(\alpha_{1}\cdots\alpha_{s}) $，$ \mathbf{B}= (\beta_{1}\cdots\beta_{s})$（解 $ \mathbf{X} $ 被称为表示矩阵）
- 线性子空间视角：$ L(\beta_{1}\cdots\beta_{s}) \subset L(\alpha_{1}\cdots\alpha_{s}) $

**向量组等价** $ \beta_{1}\cdots\beta_{s}\leftrightarrow \alpha_{1}\cdots\alpha_{s} $
- 线性子空间视角：$ L(\beta_{1}\cdots\beta_{s}) = L(\alpha_{1}\cdots\alpha_{s}) $
- 表示矩阵视角：表示矩阵可逆

$ \alpha_{1}\cdots\alpha_{s} $ **线性相关**：$ 0 = \sum k_{i}\alpha_{i}$，其中 $ k_{1}\cdots k_{s} $ 不全为 0
- 线性表出视角：$ \exists \alpha_{i} $ 被其余向量线性表示
- 方程视角：$ \mathbf{A}x=0 $ 有非零解，$ \mathbf{A}=(\alpha_{1}\cdots\alpha_{s}) $

$ \alpha_{1}\cdots\alpha_{s} $ **线性无关**：
- 线性表出视角：$ \forall  \alpha_{i} $ 不能被其余向量线性表示
- 方程视角：$ \mathbf{A}x=0 $ 只有零解，$ \mathbf{A}=(\alpha_{1}\cdots\alpha_{s}) $

**定理**：
- 某一向量组被少于其向量个数的向量组线性表出，则该向量组必线性相关（证明：利用表示矩阵）
- n 维向量空间中任意多于 n 个向量组成的向量组必线性相关（证明：利用第一条定理）
- 两组线性无关的向量组等价，则向量个数相同（证明：利用第一条定理）
- 一组线性无关的向量和某向量组成新的向量组，新的向量组线性相关，等价于该向量被该向量组线性表出（证明：按定义）

下面三个定义紧密相关：

- **极大线性无关组**
- **基**
- **向量组的秩**

**极大线性无关组** = **向量组生成的子空间的基**

**极大线性无关组的个数** = **向量组生成的子空间的维数** = **向量组生成的子空间的基的个数** = **向量组的秩**

**矩阵的行秩** = **矩阵的列秩** = **矩阵的秩**

## C1 等价关系

研究对象：一种矩阵关系——等价关系

**矩阵等价**

$ \mathbf{A} \cong \mathbf{B} \iff \mathbf{P}\mathbf{A}\mathbf{Q}=\mathbf{B}$，其中 $ \mathbf{P} $，$ \mathbf{Q} $ 可逆

$ \mathbf{A} \cong \mathbf{B} \iff r(\mathbf{A}) = r(\mathbf{B}) $

$ \mathbf{A} \cong \mathbf{B} \iff \mathbf{A} \xrightarrow{ret/cet}\cdots\xrightarrow{ret/cet} \mathbf{B} $

$ \mathbf{A} \cong \mathbf{B} \iff \mathbf{P}_s\mathbf{P}_{s-1}\cdots\mathbf{P}_1\mathbf{A}\mathbf{Q}_1\mathbf{Q}_2\cdots\mathbf{Q}_t=\mathbf{B}$，其中 $ \mathbf{P}_i $，$ \mathbf{Q}_i $ 为初等矩阵

任何矩阵都等价于等价标准形

等价标准形

$ \begin{bmatrix}
    \mathbf{E}_r &  \mathbf{O} \\
    \mathbf{O} &  \mathbf{O} \\
\end{bmatrix} $

## A2 特征值和特征向量

研究对象：矩阵的特征值和特征向量

**核心概念**：

n 阶方阵 $ \mathbf{A} $ 的 **特征值** $ \lambda $ ，属于 $ \lambda $ 的 **特征向量** $ \alpha $：
$ \alpha $ 非零，$ \mathbf{A}\alpha= \lambda \alpha $

**矩阵相似** $ \mathbf{A} \sim \mathbf{B}:\  \mathbf{P}\mathbf{A}\mathbf{P}^{-1}=\mathbf{B}$ （见 C 矩阵关系）

**特征值和特征向量的求法**：
- 计算特征多项式 $ f(\lambda)=|\lambda \mathbf{E} - \mathbf{A}| $
- 解一元 n 次方程 $ f(\lambda)=0 $，求出特征值，考虑重根：$ \lambda_{1},\lambda_{2},\cdots,\lambda_{n} $；对于某个 $ \lambda_{0} $，含有它的因式的指数称为它的代数重数
- 对每个特征值 $ \lambda_{i} $，求出齐次线性方程组 $ (\lambda_{i}\mathbf{E} - \mathbf{A})x=0 $ 的一个基础解系 $ \alpha_{1}, \alpha_{2},\cdots,\alpha_{r}$，此基础解系的所有非零线性组合 $ \alpha = k_{1} \alpha _1+k_{2} \alpha_{2} + \cdots + k_{g_{i}} \alpha_{g_{i}} $ 就是所有属于 $ \lambda_{i} $ 的特征向量，$ g_{i} $ 称为几何重数，几何重数不大于 $ \lambda $ 的代数重数

**特征值的性质**：
- $ \sum_{j} \lambda_{j}=\sum a_{ii} = tr(\mathbf{A})$
- $ \prod_{j}\lambda_{j}=|\mathbf{A}| $
- $ (\lambda_{1},\lambda_{2},\cdots,\lambda_{n})(\mathbf{A}) \Longrightarrow (\lambda_{1},\lambda_{2},\cdots,\lambda_{n})(\mathbf{A}^T) $
- $ (\lambda_{1},\lambda_{2},\cdots,\lambda_{n})(\mathbf{A}) \Longrightarrow (\lambda_{1}^{-1},\lambda_{2}^{-1},\cdots,\lambda_{n}^{-1})(\mathbf{A}^{-1}) $，
且 $ (\lambda_{i}:\alpha)(\mathbf{A}) \Longrightarrow  (\lambda_{i}^{-1}:\alpha)(\mathbf{A}^{-1})$
- $ (\lambda_{1},\lambda_{2},\cdots,\lambda_{n})(\mathbf{A}) \Longrightarrow (|\mathbf{A}|\lambda_{1}^{-1},|\mathbf{A}|\lambda_{2}^{-1},\cdots,|\mathbf{A}|\lambda_{n}^{-1})(\mathbf{A}^*) $，
且 $ (\lambda_{i}:\alpha)(\mathbf{A}) \Longrightarrow  (|\mathbf{A}| \lambda_{i}^{-1}:\alpha)(\mathbf{A}^{*})$
- $ (\lambda_{1},\lambda_{2},\cdots,\lambda_{n})(\mathbf{A}) \Longrightarrow (P(\lambda_{1}),P(\lambda_{2}),\cdots,P(\lambda_{n}))(P(\mathbf{A})) $，
且 $ (\lambda_{i}:\alpha)(\mathbf{A}) \Longrightarrow (P(\lambda_{i}):\alpha)(P(\mathbf{A}))$

**特征向量的性质**：
- 属于不同特征值的 特征向量 所组成的向量组 线性无关
    - 证明：Vandermonde 行列式
- 属于不同特征值的 线性无关的特征向量组 所组成的向量组 线性无关



## C2 相似关系

研究对象：一种矩阵关系——相似关系

**方阵相似**

$ \mathbf{A} \sim \mathbf{B} \iff \mathbf{P}\mathbf{A}\mathbf{P}^{-1}=\mathbf{B}$

$ \mathbf{A} \sim \mathbf{B} \iff \mathbf{A},\mathbf{B}$ 具有完全相同的特征值 $ \iff \mathbf{A},\mathbf{B}$ 具有相同的特征多项式

$ \mathbf{A} \sim \mathbf{B} \Longrightarrow r(\mathbf{A}) = r(\mathbf{B}),\ tr(\mathbf{A})=tr(\mathbf{B}),\ |\mathbf{A}|=|\mathbf{B}|$

$ \mathbf{A} \sim \mathbf{B} \Longrightarrow P(\mathbf{A}) \sim P(\mathbf{B})$，$ P(x) $ 是多项式

$ \mathbf{A} \sim \mathbf{B} \Longrightarrow \mathbf{A}^{-1} \sim \mathbf{B}^{-1}$，$ \mathbf{A} , \mathbf{B} $ 可逆

任何方阵都相似于 Jordan 标准形

Jordan 标准形

$ \begin{bmatrix}
    J_{1} &  &  &   \\
     & J_{2} &  &   \\
     &  & \ddots &   \\
     &  &  &  J_{n} \\
\end{bmatrix} $

其中 $ J_{i}=\begin{bmatrix}
    \lambda_i &  &  &   \\
    1 & \lambda_i &  &   \\
     & \ddots & \ddots &   \\
     &  & 1 &  \lambda_i \\
\end{bmatrix}_{m \times m} $

n 阶方阵相似于对角矩阵 $\iff$
- 有 n 个线性无关的特征向量
- 各特征值的代数重数等于几何重数
- 最小多项式无重根

## A3 二次型

研究对象：实二次型、实对称矩阵

**核心概念**：

n 元**实二次型** $f$ 的矩阵 $ \mathbf{A} $：$ f(x_{1},x_{2,}\cdots,x_{n}) = \sum a_{ij}x_{i}x_{j} = x^{T}\mathbf{A}x $，$ a_{ij}=a_{ji} \in \mathbb{R} $

**矩阵合同**：$ \mathbf{A}  \simeq \mathbf{B}:\  \mathbf{P}^T\mathbf{A}\mathbf{P}=\mathbf{B}$，其中 $ \mathbf{P} $ 可逆

**标准二次型**：$ f = \sum a_{ii}x_{i}^2 $（$ \mathbf{A} $ 为实对角矩阵）

**规范二次型**：$ f= x_{1}^2+x_{2}^2+\cdots+x_{p}^2-x_{p+1}^2-\cdots-x_{r}^2 $（$ \mathbf{A} $ 为合同标准形）

存在非奇异线性变换 $ x = \mathbf{C}y $ 将 $ f $ 化为标准二次型（任何实方阵都合同于合同标准形）

且各标准二次型正项项数相同（惯性定理）

**正定二次型**：$ \forall \alpha \neq0 $，$ \alpha^{T}\mathbf{A} \alpha>0$，$ \mathbf{A} $ 称为正定矩阵
- $ f $ 是 n 阶正定二次型 $ \iff $ $ p=r=n $
- $ f $ 是 n 阶正定二次型 $ \iff $ $ f $ 的规范二次型为 $ z_{1}^2 + z_{2}^2+\cdots+z_{n}^2 $
- $ f $ 是 n 阶正定二次型 $ \iff $ $ \mathbf{A} $ 合同于 $ \mathbf{E}_n $
- $ f $ 是正定二次型 $ \iff $ $ \exists $ 可逆矩阵 $ \mathbf{C} $，使得 $ \mathbf{A}=\mathbf{C}^T \mathbf{C} $
- $ f $ 是 n 阶正定二次型 $ \iff $ $ f $ 的各阶顺序主子式都大于零
- $ f $ 是 n 阶正定二次型 $ \iff $ $ \mathbf{A} $ 的特征值大于 0

类似地定义负定二次型、半正定二次型、半负定二次型、不定二次型

## C3 合同关系

研究对象：一种矩阵关系——合同关系

**实方阵合同**

$ \mathbf{A}  \simeq \mathbf{B} \iff \mathbf{P}^T\mathbf{A}\mathbf{P}=\mathbf{B}$，其中 $ \mathbf{P} $ 可逆

$ \mathbf{A} \simeq \mathbf{B} \iff r(\mathbf{A})=r(\mathbf{B}) $ 且 $ p(\mathbf{A})=p(\mathbf{B}) $

任何实方阵都合同于合同标准形

$ \begin{bmatrix}
    \mathbf{E}_p & \mathbf{O} &  \mathbf{O} \\
    \mathbf{O} & -\mathbf{E}_q &  \mathbf{O} \\
    \mathbf{O} & \mathbf{O} &  \mathbf{O} \\
\end{bmatrix} $

## D 特殊矩阵

**秩一矩阵**
- $ r(\mathbf{H})=1 $
- $ \mathbf{H}=\beta \alpha^{T} $，$ \beta,\alpha $ 非零
- 行成比例、列成比例
- $tr(\mathbf{H})=\alpha^{T}\beta $
- $ \mathbf{H}^{m}=tr(\mathbf{H})^{m-1}\mathbf{H} $
- 特征多项式 $ f(x)=x^{n-1}(x-tr(\mathbf{H})) $，最小多项式 $ m(x)=x(x-tr(\mathbf{H})) $
- $ tr(\mathbf{H})\neq 0 $，即 $ \alpha,\beta $ 不正交
    - $ tr(H):\beta $
    - $ 0: $ $ \alpha^{T}x=0 $ 的基础解系
    - 可以对角化
- $ tr(\mathbf{H})= 0 $，即 $ \alpha,\beta $ 正交
    - $ 0: $ $ \alpha^{T}x=0 $ 的基础解系
    - 不可以对角化

> 上述性质可以推导另一类矩阵 $ \mathbf{G}=\mathbf{E}-k \beta \alpha^{T} $ 的性质

$\mathbf{A}\mathbf{B}=\mathbf{O}$

- $ \mathbf{B} $ 的列都是 $ \mathbf{A}x=0 $ 的解
- $ r(\mathbf{A}_{m\times n})+r(\mathbf{B}_{n\times k})\leqslant n $（$ \mathbf{A},\mathbf{B} $ 分别是 $ m \times n,n\times l $ 矩阵）

**幂零矩阵**

**幂等矩阵**

**对合矩阵**

**循环矩阵**

**可交换矩阵**

**各行元素之和为 $ a $ 的矩阵**
- 行列式
- 有特征值 $ a $，对应的一个特征向量 $ (1,1,\cdots,1)^T $
