# zero-shot Text-to-Image Generation

该论文主要是一篇可以zero-shot的文本生成图像的模型，主要是通过训练一个基于image、text的多模态transformer。

## 方法论

直接使用image作为token会占用大量内存，很不划算，所以，使用两阶段训练过程。

1. 使用 变分之编码器对图像进行编码，对其进行压缩成32x32的图像token，并且每个元素都仅有8192个可能的数值。大大减少了transfomer的压力。
2. 第二个阶段就是将文本token和图像token进行连接形成一个新的向量送入transformer。

### Stage one: learing the visual codebook
