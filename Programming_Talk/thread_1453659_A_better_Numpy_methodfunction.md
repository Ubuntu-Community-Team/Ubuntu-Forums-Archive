---
title: "A better Numpy method/function?"
date: 2010-04-13
forum: Programming Talk
---

### Post by eckeroo on 2010-04-13
Hello all,

I do not know how to use Numpy for creating sequences like in the following example:

[A,B,C,D]

=>

A*A, A*B, A*C, A*D, B*A, B*B, B*C, B*D, C*A....

So far, I can only think of using for loops:

[PHP]from scipy import array, zeros

Equation = [2, 3, 4, 5]
index = range(len(Equation))

MyMatrix=zeros((len(Equation)**2,1))

x=0

for coefficient1 in index:
    for coefficient2 in index:
        MyMatrix[x]=Equation[coefficient1]*Equation[coefficient2]
        x+=1

print MyMatrix[/PHP]

Can Numpy do this better without loops?

I want to improve the coding of my last program: [http://bit.ly/9IMRV3](http://bit.ly/9IMRV3)

---

### Post by avidday on 2010-04-13
> **eckeroo said:**
> Hello all,

I do not know how to use Numpy for creating sequences like in the following example:

[A,B,C,D]

=>

A*A, A*B, A*C, A*D, B*A, B*B, B*C, B*D, C*A....


In matrix theory, that type of sequence is known as a type of Kronecker product (see [http://en.wikipedia.org/wiki/Kronecker_product](http://en.wikipedia.org/wiki/Kronecker_product)). In numpy you can calculate it like this:

```

In [10]: A=np.arange(1,5)

In [11]: print A
-------> print(A)
[1 2 3 4]

In [12]: print kron(A,A)
-------> print(kron(A,A))
[ 1  2  3  4  2  4  6  8  3  6  9 12  4  8 12 16]

```

---

