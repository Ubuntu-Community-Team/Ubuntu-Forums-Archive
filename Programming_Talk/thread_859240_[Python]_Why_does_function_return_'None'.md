---
title: "[Python] Why does function return 'None'"
date: 2008-07-14
forum: Programming Talk
---

### Post by TreeFinger on 2008-07-14
[php]
def multipThreeFive(n, sum=0):
	""" Find if 'n' is a multiple of 3 or 5 """
	if n < 3:
		return sum
	if n % 5 == 0 or n % 3 == 0:
		sum += n
		multipThreeFive(n-1, sum)
	else:
		multipThreeFive(n-1, sum)

print multipThreeFive(10)
[/php]

---

### Post by Wybiral on 2008-07-14
Recursive calls are like normal function calls. How do you suspect the result of the recursive call makes it back to the original caller?

---

### Post by TreeFinger on 2008-07-14
> **Wybiral said:**
> Recursive calls are like normal function calls. How do you suspect the result of the recursive call makes it back to the original caller?

I'm confused by the output of this.

[php]
def multipThreeFive(n, sum=0):
	""" Find if 'n' is a multiple of 3 or 5 """
	if n % 5 == 0 or n % 3 == 0:
		sum += n
		if n == 3:
			print sum
			return sum
		multipThreeFive(n-1, sum)
	else:
		multipThreeFive(n-1, sum)

print multipThreeFive(10)
[/php]

```

33
None

```


ohhhh, I think I understand.. confusing though.

---

### Post by ghostdog74 on 2008-07-14
> **TreeFinger said:**
> I'm confused by the output of this.

[php]
def multipThreeFive(n, sum=0):
	""" Find if 'n' is a multiple of 3 or 5 """
	if n % 5 == 0 or n % 3 == 0:
		sum += n
		if n == 3:
			print sum
			return sum
		multipThreeFive(n-1, sum)
	else:
		multipThreeFive(n-1, sum)

print multipThreeFive(10)
[/php]

```

33
None

```


ohhhh, I think I understand.. confusing though.

how is it confusing? you forgot to return in your else: part, that's probably why you have None result.

---

### Post by Can+~ on 2008-07-14
A way of "understanding" recursions is taking the same function and putting it inside, for example:

[PHP]def myrecursion(x):
	x -= 1
	print "recursion:",x
	if x > 1:
		myrecursion(x)
	
	return x[/PHP]

This function will recursively subtract 1, but when calling with x=10, it will return 9, why?

[PHP]def myrecursion(10):
	x -= 1
	print "recursion:",x

	def myrecursion(9):
		x -= 1
		print "recursion:",x
		
		def myrecursion(8):
			#...
		return x
	
	return x[/PHP]

In pseudocode:

[PHP]Call function with 10
	Subtract 1
	Call function with 9
		Subtract 1
		Call function with 8
			Subtract 1
			Call function with 7
				...
			return 7
		return 8
	return 9[/PHP]

Each sub-return will return to the parent function, but that return goes unfetched, so you'll end up returning the value from the top of the recursion, and all the sub-returns are lost.

Mix that with the conditionals, and you got a major confusion.

---

### Post by TreeFinger on 2008-07-15
Should the problem I am solving even be done with recursion? When do you know whether to use recursion or not to use it?

[php]
def multipThreeFive(n, sum=0):
	""" Find if 'n' is a multiple of 3 or 5 """
	i, sum = 3, 0
	while i < n:
		if i % 3 == 0 or i % 5 == 0:
			sum += i
		i += 1
	return sum

print multipThreeFive(1000)
[/php]

---

### Post by CptPicard on 2008-07-15
> **TreeFinger said:**
> Should the problem I am solving even be done with recursion? When do you know whether to use recursion or not to use it?

Well, a loop is just a tail recursion, so for example in Scheme you *always* use recursion.

Recursion is a good candidate for divide-and-conquer situations where problem exhibits recursive substructure, that is, it "works the same way" in smaller sub-pieces as it works in the larger pieces.

That is, you have something a form of something like...

1. Handle simple termination case
2. do some preprocessing
3. divide instance into smaller pieces
4. handle sub-pieces in the same way
5. integrate answers
6. return

A tail recursion lacks step 5, therefore, it can be formulated as a loop as there is nothing to be done after recursing down.

---

