---
title: "Python: Sort List Specifically"
date: 2010-04-01
forum: Programming Talk
---

### Post by tdrusk on 2010-04-01
Lets say I have a 2 lists
string = ['O','B','C','A','L']
key   = ['C','O','B', 'A', 'L']


Now what I want to do is sort string by the indexes of key. For example, after I sort string, I want it to be ['C','O','B', 'A', 'L'].

How can I do this?

---

### Post by geirha on 2010-04-01
Would be easier if you gave each character a weight. E.g. using a dict:
```
weight={ 'C':0, 'O':1, 'B':2, 'A':3, 'L':4 }
```

Then you can use the weight as the key to sort by
```
string = ['O','B','C','A','L']
string.sort(key=lambda x: weight[x])

```

You can generate the weight from your current key list of course.
```

key = ['C','O','B', 'A', 'L']
weight = dict((y,x) for x,y in enumerate(key))

```

---

### Post by tdrusk on 2010-04-01
> **geirha said:**
> Would be easier if you gave each character a weight. E.g. using a dict:
```
weight={ 'C':0, 'O':1, 'B':2, 'A':3, 'L':4 }
```Then you can use the weight as the key to sort by
```
string = ['O','B','C','A','L']
string.sort(key=lambda x: weight[x])

```You can generate the weight from your current key list of course.
```

key = ['C','O','B', 'A', 'L']
weight = dict((y,x) for x,y in enumerate(key))

```
Oh thank you :)
I saw something similar in the Python Tutorial, but I didn't quite understand it.

---

### Post by diesch on 2010-04-02
You can do it without a dict:
```
string.sort(key=lambda x: key.index(x))
```
but that's much less efficient.

---

### Post by tdrusk on 2010-04-06
Okay, now that I am working on this more I have one more question.
Consider I have 2 lists
```
string = ['O','B','C','A','L']
rank   = [ 1 , 5 , 7,  4 ,  3] 
```
How can I sort string by the numbers in rank? For example, the output would be
```
string = ['O', 'L', 'A', 'B', 'C']
```Thanks for all the help so far. You guys are great.

---

### Post by delfick on 2010-04-06
> **tdrusk said:**
> Okay, now that I am working on this more I have one more question.
Consider I have 2 lists
```
string = ['O','B','C','A','L']
rank   = [ 1 , 5 , 7,  4 ,  3] 
```
How can I sort string by the numbers in rank? For example, the output would be
```
string = ['O', 'L', 'A', 'B', 'C']
```Thanks for all the help so far. You guys are great.

some pseudo code for you

```

for each letter:
   while that letter has the wrong index:
      look at that letter's rank
      if the rank is different than the letter's index:
          swap the letter with where's it's supposed to go

```

However, this does depend on the ranks being equivalent to the index of each letter in the array.

If however the ranks is more of a weighting and doesn't necessarily equate to a sequence of numbers, then you can go through and normalize the ranking first.....

(for example, if ranking is [9, 20, 1, 5, 5], then normalized ranking would be [3, 4, 0, 1, 2])

:D

*returns to studies*

---

### Post by diesch on 2010-04-06
Create a list containing (rank, letter) tuples, sort that list, and get the letters:
```
[i[1] for i in sorted(zip(rank, string))]
```

---

