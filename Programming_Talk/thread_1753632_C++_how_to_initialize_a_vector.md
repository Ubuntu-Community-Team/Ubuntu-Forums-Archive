---
title: "C++ how to initialize a vector"
date: 2011-05-09
forum: Programming Talk
---

### Post by erotavlas on 2011-05-09
Hi,

I have a simple question. How can I initialize the following vector?
```

std::vector<std::vector<std::pair<std::vector<std::pair<std::string, int> >, double> > > myVector;

```I would like to have 5 elements (for example) inside of myVector. i.e. the outer vector of myVector should be of size 5.
I think that the following way is not the only one.
```

std::vector<std::pair<std::vector<std::pair<std::string, int> >, double> > tempVector(0);
for (int i = 0; i < 5; ++i)
{
myVector.push_back(tempVector);
}

```What are the other ways?

Thank you

---

### Post by ziekfiguur on 2011-05-09
You could use the constructor: std::vector(size_type n, const T& value= T(), const Allocator& = Allocator());
It initializes the vector with its content set to a repetition, n times, of copies of value.

Just one remark though, i think it would be better to define a class than to use std::vector<std::pair<std::vector<std::pair<std::string, int> >, double> > as a datatype. It would certainly make your code a lot more readable and easier to understand. If you don't want to do that, you could also define a typedef for it so you don't have to repeat the whole thing every time in your code.

---

### Post by erotavlas on 2011-05-09
> **ziekfiguur said:**
> You could use the constructor: std::vector(size_type n, const T& value= T(), const Allocator& = Allocator());
It initializes the vector with its content set to a repetition, n times, of copies of value.

Just one remark though, i think it would be better to define a class than to use std::vector<std::pair<std::vector<std::pair<std::string, int> >, double> > as a datatype. It would certainly make your code a lot more readable and easier to understand. If you don't want to do that, you could also define a typedef for it so you don't have to repeat the whole thing every time in your code.

Thank you for your fast answer. Can you tell me how I can do your solution?

Can I use my code without using the tempVector?
```

std::vector<std::pair<std::vector<std::pair<std::string, int> >, double> > tempVector(0);
for (int i = 0; i < 5; ++i)
{
myVector.push_back(tempVector); // myVector.push_back(0) ????
}

```

---

### Post by ziekfiguur on 2011-05-09
since that constructor uses T() as a default argument i think you should just be able to use:
```
std::vector<std::vector<std::pair<std::vector<std::pair<std::string, int> >, double> > > myVector(5);
```
i haven't tested it though, maybe you would have to use
```
..blahblah... myVector(5, tempVector);
```

---

### Post by dwhitney67 on 2011-05-09
Is this not easier to digest, that is, clearer to read?
```

struct Data
{
   std::string str;
   int         val;
}; 

struct Data2
{
   std::vector<Data> data;
   double            dbl;
}; 

std::vector<Data2> myVector;

```
If you want to initialize the 'myVector' to have 5 elements:
```

std::vector<Data2> myVector(5);

```

---

### Post by nvteighen on 2011-05-09
dwhitney67's solution points to a general approach you should always take in account when programming: *repeated code is usually a symptom of insufficient/incorrect abstraction*. This is valid in all programming languages, no matter what paradigm; of course the solutions may vary from one language to another, but the general idea is always the same: avoid repetitions by creating new concepts that allow further simplification of your code.

---

