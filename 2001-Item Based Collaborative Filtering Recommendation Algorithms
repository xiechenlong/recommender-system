作者：Badrul Sarwar, George Karypis, Joseph Konstan, and John Riedl

引用次数：8000+，2019年10月

第一篇提出 item based CF 的论文。

## user based CF 的两个问题
1. 由于现实数据是稀疏的，所以有些用户查不到邻近用
2. 复杂度受用户数和商品数影响，导致大数据量下效率低下

## 商品相似度的三个模型
余弦相似度
$$ sim(i,j)=cos(\vec i, \vec j)=\frac{\vec i \cdot \vec j}{||\vec i||^2 * ||\vec j||^2}$$

皮卡尔相关性
$$sim(i,j) = \frac{\sum_{u \in U}{(R_{u,i}-\bar{R_i})(R_{u,j}-\bar{R_j})}}{\sqrt{ \sum_{u \in U}{(R_{u,i}-\bar{R_i})^2}}   \sqrt{\sum_{u \in U}{(R_{u,j}-\bar{R_j})^2}}}$$

优化后的余弦相似度
$$sim(i,j) = \frac{\sum_{u \in U}{(R_{u,i}-\bar{R_u})(R_{u,j}-\bar{R_u})}}{\sqrt{ \sum_{u \in U}{(R_{u,i}-\bar{R_u})^2}}   \sqrt{\sum_{u \in U}{(R_{u,j}-\bar{R_u})^2}}}$$

论文中指出优化后的余弦相似度效果最好，而余弦相似度的效果和皮卡尔相关性差不多。

从信息论的角度看，优化后的余弦相似度使用了更多的信息，既利用了$R_i$的数据，也用了$R_u$的数据，而其余两种方式都只用了$R_i$这一个维度的数据。

所以优化后的余弦相似度拥有了更大的信息量，效果就会更好些。

## 推荐模型
加权求和
$$P_{u,i} = \frac{ \sum_{all similar items, N}{ s_{i,N} * R_{u,N} } }{ \sum_{all similar items, N}{s_{i,N}} } $$

线性回归
$$ \bar{R_N^{'}} = \alpha R_i + \beta + \epsilon $$

论文中指出加权求和的效果更好。

## 数据集
943个用户，1682部电影，稀疏度$1-\frac{nonzero evtries}{total entries}$为0.9369.

## 评价指标: 平均绝对误差
$$ MAE=\frac{ \sum_{i=1}^{N}{|p_i-q_i|} }{N} $$

基线：user based CF
## 最优参数的确定方法
存储所有item的相似度会占用较大的硬件资源，为此只存储最相似的k个商品。通过对比不同k值下的MAE，得到最优值为30.

## 结论
item based CF效果比user based CF好。
