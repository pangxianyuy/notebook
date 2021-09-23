
# pandas



```python
# 如何输出每行的值
for index,row in df.iterrows():
    print(index)

# 如何对dataframe做多个条件的过滤，两种写法：
    # 1、普通的写法
    data[(data.a > 2)&(data.a<3)]
    # 2、query的写法（如果数据量很多、且处于介值的化比较方便）
    ## 比较pythonic
    data.query(2<a<3>)

# 对数据进行groupby 和 降序展示
df.groupby('serial_id').count().sort_values('pass',ascending=False).head(10)

# 关于解析json文件
'''
1、对json格式的数据使用json.loads;这种办法不会处理json内部的嵌套格式；
2、嵌套格式使用pd.json_normalize，返回的是一个DataFrame的格式；
3、展开后的数据列名称为：a.b.c
'''
L,F = [],[]
for data in t:
    time, elements = data.split('c.c.b.f.engine.service.OrderService - ')
    try:
        elements = json.loads(elements[1:-2])
        L.append(elements)    
    except:
        F.append(elements)
df = pd.json_normalize(L)

# 针对多列的逻辑计算
# 重点是：axis=1
data_all['lapass'] = data_all.apply(lambda x: x['islast']*x['pass'],axis=1)

# pandas一次新增多列：
t69['x'],t69['y'] = xt[:,0],xt[:,1]

# pandas全文筛选满足条件的数据
np.where((a.values>1)&(a.values<10)) #返回的是dataFrame格式的数据
# 也可以使用numpy进行满足条件的数据处理
np.where((a>3)&(a<5)) # 返回的是ndarry

# 计算相关性，并取上三角矩阵；
relation = relation.corr()
upper_triangle = np.triu(relation, 0)

# 淦，pandas还能直接绘图？？
bdata['ind_h7DVlH4Y6g'].plot(kind='hist') 

# 逐行遍历的一种写法
for index, row in df.iterrows():
    print(index) # 输出每行的索引值


# 对于使用pandas的qcut 的结果，是一种interval的数据类型，需要特别的处理
b['sort'] = b['unique_values'].apply(lambda x: x.right)
b.sort_values(by='sort',ascending=True,inplace=True)
b.plot(x='unique_values',y=['counts','counts2'],kind='bar')

# 把value_counts 转 dataframe 的写法：
b1 = p1.value_counts('bins').rename_axis('unique_values').reset_index(name='counts')

# 设置某一列为index
df.set_index(["Column"], inplace=True)

#排序
indices = np.argsort(importances)[::-1]
include = []
for f in range(15):
    include.append(feat_labels[indices[f]])

```

# 待办事项

- [ ] [在使用pandas进行切片的时候,出现一个警示,让选用.loc](https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy)
- [ ] [apply 和 map 的区别](https://blog.csdn.net/u010569893/article/details/103733319)

## 参考文章
[关于如何按行输出每一行的值：](https://blog.csdn.net/sinat_29675423/article/details/87972498)

[pandas的去重方法，包括保留第一个值、保留最后一个值](https://www.yisu.com/zixun/150970.html#:~:text=pandas%E4%B8%AD%E7%9A%84%E6%95%B0%E6%8D%AE%E5%8E%BB%E9%87%8D%E5%A4%84%E7%90%86%E7%9A%84%E5%AE%9E%E7%8E%B0%E6%96%B9%E6%B3%95.%20%E6%95%B0%E6%8D%AE%E5%8E%BB%E9%87%8D%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8duplicated%20%28%29%E5%92%8Cdrop_duplicates%20%28%29%E4%B8%A4%E4%B8%AA%E6%96%B9%E6%B3%95%E3%80%82.%20DataFrame.duplicated%EF%BC%88subset%20%3D,None%EF%BC%8Ckeep%20%3D%E2%80%98first%27%20%EF%BC%89%E8%BF%94%E5%9B%9Eboolean%20Series%E8%A1%A8%E7%A4%BA%E9%87%8D%E5%A4%8D%E8%A1%8C.%20first%EF%BC%9A%E6%A0%87%E8%AE%B0%E9%87%8D%E5%A4%8D%EF%BC%8CTrue%E9%99%A4%E4%BA%86%E7%AC%AC%E4%B8%80%E6%AC%A1%E5%87%BA%E7%8E%B0%E3%80%82.%20last%EF%BC%9A%E6%A0%87%E8%AE%B0%E9%87%8D%E5%A4%8D%EF%BC%8CTrue%E9%99%A4%E4%BA%86%E6%9C%80%E5%90%8E%E4%B8%80%E6%AC%A1%E5%87%BA%E7%8E%B0%E3%80%82.)

[关于pandas的链接操作，主要注意反人类的写法](https://www.jianshu.com/p/2358d4013067)

[pandas的全文筛选操作](https://www.gairuo.com/p/pandas-selecting-data)

[pandas interval的数据处理](https://pandas.pydata.org/pandas-docs/version/0.23.4/generated/pandas.Interval.html)

[python 的深拷贝与浅拷贝：list、dict和dataframe](https://zhuanlan.zhihu.com/p/25221086)
    dataframe的copy() 和 切片都默认为深拷贝的（改变后者不会更改原来数据的值）。

[应该形成如何的代码规范？建议书籍code clean](https://www.zhihu.com/question/26721180)
