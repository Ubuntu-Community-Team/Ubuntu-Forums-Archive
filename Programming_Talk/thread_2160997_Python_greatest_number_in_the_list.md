---
title: "Python greatest number in the list"
date: 2013-07-09
forum: Programming Talk
---

### Post by mishumishu on 2013-07-09
solved!

---

### Post by ofnuts on 2013-07-09
Well, we are all very happy for you but what was the question?

---

### Post by alan9800 on 2013-07-09
> **ofnuts said:**
> Well, we are all very happy for you but what was the question?let's try to guess the question and the answer:[INDENT]**the question:**> given a list of numbers, how can I find the greatest of them in Python?
[/INDENT]
[INDENT]**the answer:**> use```
max(your_list_of_numbers)
```
[/INDENT]

---

### Post by ofnuts on 2013-07-09
Besides the one good answer, there are several not-so-good ones (like sorted(list)[-1])

---

### Post by alan9800 on 2013-07-09
> **ofnuts said:**
> ```
sorted(list)[-1]
```this is a sample of a slightly obfuscated code, isn't it? Indeed, at least for me, the purpose of a code like this isn't at all easy to understand.

---

### Post by trent.josephsen on 2013-07-10
Seems perfectly clear to me: take the last element of a sorted list.

---

### Post by ofnuts on 2013-07-10
Next time I'll use 'reduce(lambda x,y : x if x >y  else y,list)' :)

---

### Post by alan9800 on 2013-07-10
what I meant to say in my previous post is: "sorting a list hasn't always the purpose of finding its maximum value; why should I use sorted(list[-1]) when it's much more understandable max(list)?"

---

### Post by ofnuts on 2013-07-10
My original question was really wether the OP found the right solution (max(list)), or stumbled on something else that does the job but isn't 100% correct (like the ones I mentioned). Since he didn't tell us, we don't know.

---

### Post by epicoder on 2013-07-13
This is why knowing the correct answer to questions like this is important:
```

l = list(range(1000)); random.shuffle(l)
max(l): 0.105857849121 milliseconds
sorted(l)[-1]: 0.613212585449 milliseconds
reduce(lambda x, y : x if x > y else y, l): 1.07598304749 milliseconds

```
Time differences like these stack up very quickly in business applications that handle hundreds or even thousands of queries per second. It is important to know the fastest way to handle trivial operations like this so you don't drive yourself nuts when trying to optimize your code later.

---

