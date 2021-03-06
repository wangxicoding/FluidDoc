.. _cn_api_fluid_layers_expand:

expand
-------------------------------

.. py:function:: paddle.fluid.layers.expand(x, expand_times, name=None)

expand运算会按给定的次数对输入各维度进行复制（tile）运算。 您应该通过提供属性 ``expand_times`` 来为每个维度设置次数。 X的秩应该在[1,6]中。请注意， ``expand_times`` 的大小必须与X的秩相同。以下是一个用例：

::

        输入(X) 是一个形状为[2, 3, 1]的三维张量（Tensor）:

                [
                   [[1], [2], [3]],
                   [[4], [5], [6]]
                ]

        属性(expand_times):  [1, 2, 2]

        输出(Out) 是一个形状为[2, 6, 2]的三维张量（Tensor）:

                [
                    [[1, 1], [2, 2], [3, 3], [1, 1], [2, 2], [3, 3]],
                    [[4, 4], [5, 5], [6, 6], [4, 4], [5, 5], [6, 6]]
                ]

参数:
        - **x** (Variable)- 一个秩在[1, 6]范围中的张量（Tensor）.
        - **expand_times** (list|tuple|Variable) - 每一个维度要扩展的次数。

返回：     expand变量是LoDTensor。expand运算后，输出（Out）的每个维度的大小等于输入（X）的相应维度的大小乘以 ``expand_times`` 给出的相应值。

返回类型：   变量（Variable）

**代码示例**

..  code-block:: python

        import paddle.fluid as fluid

        # example 1:
        data_1 = fluid.layers.fill_constant(shape=[2, 3, 1], dtype='int32', value=0)
        expanded_1 = fluid.layers.expand(data_1, expand_times=[1, 2, 2])
        # the shape of expanded_1 is [2, 6, 2].

        # example 2:
        data_2 = fluid.layers.fill_constant(shape=[12, 14], dtype="int32", value=3)
        expand_times = fluid.layers.fill_constant(shape=[2], dtype="int32", value=4)
        expanded_2 = fluid.layers.expand(data_2, expand_times=expand_times)
        # the shape of expanded_2 is [48, 56].








