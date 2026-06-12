---
title: "Appending to lists?"
date: 2007-07-24
forum: Programming Talk
---

### Post by flummoxed on 2007-07-24
```
threeSum = 0
threeMul= 3
threeList = []

while threeMul < 1000:
    threeList = threeList.append(threeMul)
    threeMul += 3 
```

The python interpreter keeps telling me that the 'NoneType' object has no attribute 'append'. It's talking about me trying to append to the threeList. I thought that declaring a variable with empty brackets meant that you're making a blank list. Why can't I append to it? I tried making it global to see if that was the problem, but no dice.

---

### Post by jeremytaylor on 2007-07-24
Hi there, 
I'm a beginner with python but I think it goes like this...

.append is a method for lists and adds it's argument to the end of the list and then returns None.

So all you need is

```
threeSum = 0
threeMul= 3
threeList = []

while threeMul < 1000:
    threeList.append(threeMul)
    threeMul += 3


```


hope that works/makes sense
Jeremy

---

### Post by jeremytaylor on 2007-07-24
Oh yes and to explain the error message. What happens is the first time you go through the loop you set your variable equal to None so the next time it goes through it raises an exception as None is obviously not a list and doesn't have the .append() method

Jeremy

---

### Post by flummoxed on 2007-07-24
Ohh right, I forgot that I didn't need to put the assignment operator for threeList while appending to it. The error message confused me too. Thanks!

---

### Post by smartbei on 2007-07-25
You can also do this:
```

threeSum = 0
threeMul= 3
threeList = []

while threeMul < 1000:
    threeList += [threeMul]
    threeMul += 3

```
lastly, a much simpler (and faster) way to do this is:
```

threeList=range(3,1000,3)
threeSum=sum(threeList)

```

---

