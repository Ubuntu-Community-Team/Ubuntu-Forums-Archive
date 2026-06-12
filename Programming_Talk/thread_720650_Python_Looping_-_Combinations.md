---
title: "Python Looping - Combinations"
date: 2008-03-10
forum: Programming Talk
---

### Post by Siph0n on 2008-03-10
I have a list of a list of integers:
```

[[[7, 5], [6, 1], [6, 4], [5, 3], [4, 6]], [[11, 8], [9, 6], [6, 7], [5, 2], [3, 0]], [[15, 4], [10, 9], [8, 5], [7, 1], [2, 7]], [[7, 5], [7, 6], [6, 0], [5, 2], [3, 3]], [[11, 8], [9, 2], [6, 5], [4, 4], [3, 0]], [[9, 5], [7, 3], [6, 7], [5, 6], [4, 4]], [[11, 9], [8, 5], [7, 1], [6, 2], [5, 0]], [[9, 4], [9, 6], [6, 5], [4, 0], [4, 9]], [[13, 4], [11, 5], [8, 7], [4, 1], [3, 3]], [[9, 7], [5, 0], [5, 1], [4, 3], [3, 5]], [[6, 0], [6, 2], [5, 1], [5, 5], [5, 6]], [[10, 2], [8, 1], [6, 4], [4, 6], [3, 5]], [[12, 8], [9, 6], [8, 4], [4, 0], [4, 7]], [[9, 5], [8, 2], [7, 3], [5, 0], [3, 4]], [[8, 5], [8, 6], [7, 8], [4, 9], [3, 3]], [[11, 7], [9, 3], [5, 8], [5, 9], [4, 6]]]

```

Each inner list:
```

[[7, 5], [6, 1], [6, 4], [5, 3], [4, 6]]
[[11, 8], [9, 6], [6, 7], [5, 2], [3, 0]]
[[15, 4], [10, 9], [8, 5], [7, 1], [2, 7]]
[[7, 5], [7, 6], [6, 0], [5, 2], [3, 3]]
[[11, 8], [9, 2], [6, 5], [4, 4], [3, 0]]
[[9, 5], [7, 3], [6, 7], [5, 6], [4, 4]]
[[11, 9], [8, 5], [7, 1], [6, 2], [5, 0]]
[[9, 4], [9, 6], [6, 5], [4, 0], [4, 9]]
[[13, 4], [11, 5], [8, 7], [4, 1], [3, 3]]
[[9, 7], [5, 0], [5, 1], [4, 3], [3, 5]]
[[6, 0], [6, 2], [5, 1], [5, 5], [5, 6]]
[[10, 2], [8, 1], [6, 4], [4, 6], [3, 5]]
[[12, 8], [9, 6], [8, 4], [4, 0], [4, 7]]
[[9, 5], [8, 2], [7, 3], [5, 0], [3, 4]]
[[8, 5], [8, 6], [7, 8], [4, 9], [3, 3]]
[[11, 7], [9, 3], [5, 8], [5, 9], [4, 6]]

```

I only care about the 2nd number in the list, the first number was there so i can sort it. I am trying to get all the different permutations, but am having trouble. 

```

   for ii in range(0,5):
        check = ""
        for i in range(0,len(numbers[0][0])):
            temp = reduced_Maxes[i][ii]
            check += str(temp[1:][0])
        CheckNum(check)

```

len(numbers[0][0]) == 16 ... That is the length of each number

So it returns:
5845859447028557
1696235650216263
4750571571144388
3212462013560099
6073040935657436

Any ideas how I can get it to produce ALL the different permutations? I tried adding another for loop on the outside of the two i already have, and have it go from 0-16, but cant figure out how i should encorporate that in the inner for loops.... Any help would be greatly appreciated! Thanks

---

### Post by Siph0n on 2008-03-11
I figured it out... but only by using 16 for loops.... Does any one have a DIFFERENT way? ;)

---

### Post by CptPicard on 2008-03-11
```



l = [1, 2, 3, 4, 5]


def permutations(li):
	if li == []:
		yield li
	for i in range(0, len(li)):
		for p in permutations(li[0:i] + li[i+1:len(li)]):
			yield ([li[i]] + p)
		

			
for x in permutations(l):
	print x


```

Use list comprehensions to extract the series of numbers you want to feed into the generator function.

---

### Post by Wybiral on 2008-03-11
Wait... You need the permutations of the second number of the most inner lists (the pairs)? That sounds like too much info to me, why don't you just extract them into a list of their own and use a normal permutation function?

---

