# 简单的开始
## 基本操作
pytorch 中基本数据抽像为一个Tensor对象，它与numpy中ndarray很相近,pytorch 创建张量的方式有很多种，很像numpy
如下：
```
import torch
uninitilaized = torch.Tensor(3, 2) #一个未被初始化的Tensor
rand_initialized = torch.rand(3 ,2) #矩阵大小确定但数值随机
matrix_with_ones = torch.ones(3 ,2)
matrix_with_zeros = torch.zeros(3, 2)
```
其返回结果为
```
tensor([[1.1547e+19, 4.1988e+07],
        [3.0357e+32, 1.1547e+19],
        [6.4069e+02, 4.3066e+21]])
tensor([[0.6317, 0.7521],
        [0.0189, 0.5954],
        [0.0438, 0.3352]])
tensor([[1., 1.],
        [1., 1.],
        [1., 1.]])
tensor([[0., 0.],
        [0., 0.],
        [0., 0.]])
```
我们也可用list初始化，pytorch支持的数据类型具体可见(pytorch的官网)[http://pytorch.org/docs/master/tensors.html]
这些数据类型都可作为类别将使用list初始化。
```
list_1 = [1, 2, 3]
list_initialized = torch.FloatTensor(list_1)

output：
tensor([1., 2., 3.])
```
pytorch也可使用shape属性获得张量形状(size()方法同样可得)
```
size = rand_initialized.size()
shape = rand_initialized.shape
print(size == shape)

output:
True
```
shape对象从python元组中继承，因此元组操作同样适用于shape对象,但是元组是不可变的，shape亦如此
```
torch.Size([3, 2])
```
那么
```
print(shape[0])
print(sahpe[1])

output:
3
2
```
张量的许多运算与numpy相近
```
#张量标量操作
y = matrix_with_ones + 2 # y每个元素＋2
print(y)

z = torch.ones(2, 1)
print(z)
h = matrix_with_ones * y @ z #变量matrix_with_ones和y为3 * 2阶张量，与numpy一样,*实现了二者对应元素相乘,@是矩阵乘法
print(h)
#张量间的加法

k1 = matrix_with_ones.add(y) # + 或者 add实现了相同张量相加，a.add(b)不会对a,b有任何更改，而a.add_(b)会更改a为求和结果,in-palce 运算符遵循后缀下划线约定
print(k1)
k2 = matrix_with_ones.add_(y) #in-place的加法
print(k2)
k3 = matrix_with_ones.matmul(z) #矩阵乘法，还可以用@和mm实现
print(k3)

output:
tensor([[3., 3.],
        [3., 3.],
        [3., 3.]])
tensor([[1.],
        [1.]])
tensor([[6.],
        [6.],
        [6.]])
tensor([[4., 4.],
        [4., 4.],
        [4., 4.]])
tensor([[4., 4.],
        [4., 4.],
        [4., 4.]])
tensor([[8.],
        [8.],
        [8.]])
```


