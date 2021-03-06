# 机器学习相关的数学知识积累

1. 协方差矩阵（在 Ch13-PCA 里运用到）
2. SVD（在 Ch14-SVD 里运用到）
3. 奇异矩阵、多重共线性。（[对于普通最小二乘的系数估计问题，其依赖于模型各项的相互独立性。当各项是相关的，且设计矩阵 X 的各列近似线性相关，那么，设计矩阵会趋向于奇异矩阵，这会导致最小二乘估计对于随机误差非常敏感，产生很大的方差。例如，在没有实验设计的情况下收集到的数据，这种多重共线性（multicollinearity）的情况可能真的会出现。](http://sklearn.apachecn.org/#/docs/2)）

## 2. SVD 

[奇异值分解(SVD)原理与在降维中的应用](https://www.cnblogs.com/pinard/p/6251584.html)

## 评价指标

- **L2 范数**：求两个向量之差的平方和的根（如RMSE），标记为 $||\cdot||_2$
- **L1 范数**：求两个向量之差的绝对值之和（如MAE），标记为 $||\cdot||_1$
- 范数的指数越高，就越关注大的值而忽略小的值。

## 1. 均方根误差（RMSE）

> 参考：[《Sklearn 与 TensorFlow 机器学习实用指南》](https://hand2st.apachecn.org/#/docs/2.%E4%B8%80%E4%B8%AA%E5%AE%8C%E6%95%B4%E7%9A%84%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0%E9%A1%B9%E7%9B%AE?id=%E9%80%89%E6%8B%A9%E6%80%A7%E8%83%BD%E6%8C%87%E6%A0%87)

均方根误差测量的是系统预测误差的标准差。例如，RMSE 等于 50000，意味着，68% 的系统预测值位于实际值的 50000 美元以内，95% 的预测值位于实际值的 100000 美元以内（一个特征通常都符合高斯分布，即满足 “68-95-99.7”规则：大约 68% 的值落在 1σ 内，95% 的值落在 2σ 内，99.7% 的值落在 3σ 内，这里的 σ 等于 50000）。RMSE 计算公式：

$$RMSE = \sqrt{\frac{1}{m}\sum_{i=1}^{m}(h(x^{(i)})-y^{(i)})^2}$$

### 2. 平均绝对误差（也称作平均绝对偏差,Mean Absolute Error，MAE）

$$MAE = \frac{1}{m}\sum_{i=1}^{m}|h(x^{(i)})-y^{(i)}|$$

MAE 用的是 L1 范数，而 RMSE 用的是 L2 范数。因为 「范数的指数越高，就越关注大的值而忽略小的值」，所以 RMSE 比 MAE 对异常值更敏感
