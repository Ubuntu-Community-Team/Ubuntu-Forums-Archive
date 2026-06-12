---
title: "Euler 3 code - doesn't work PYTHON"
date: 2009-04-09
forum: Programming Talk
---

### Post by tawfiqh on 2009-04-09
i couldn't get my code for project euler problem 3 to work:

so i got this code for finding a prime in python:

```

num = input('Enter the number which you wish to determine it is prime: ')

if num < 2:
	print "\nThe Number", num, " is not a prime!"
else:
	for div in range(2, (num/2)+1):
		if num%div==0:
			print "\nThe Number", num, " is not a prime!"
			break
	else:
		print "\nThe Number", num, " is a prime!"

```

I incorporated it into my program but it doesn't work

```
y=24
x=1
f=[]
pf=[]
while x<=y:
    if y%x==0:
        f.append(x)
        if x < 2:
            print "\nThe Number", x, " is not a prime!"
        elif x>2:

            for div in range(2, (x/2)+1):
                if x%div==0:
                    break
                else:
                   pf.append(x)


    x=x+1
        
print f
print pf

```

it just ouputs:
```

The Number 1  is not a prime!
[1, 2, 3, 4, 6, 8, 12, 24]
[]
```

why doesn't it work?

---

### Post by Arndt on 2009-04-09
> **tawfiqh said:**
> i couldn't get my code for project euler problem 3 to work:

so i got this code for finding a prime in python:

```

num = input('Enter the number which you wish to determine it is prime: ')

if num < 2:
	print "\nThe Number", num, " is not a prime!"
else:
	for div in range(2, (num/2)+1):
		if num%div==0:
			print "\nThe Number", num, " is not a prime!"
			break
	else:
		print "\nThe Number", num, " is a prime!"

```

I incorporated it into my program but it doesn't work

```
y=24
x=1
f=[]
pf=[]
while x<=y:
    if y%x==0:
        f.append(x)
        if x < 2:
            print "\nThe Number", x, " is not a prime!"
        elif x>2:

            for div in range(2, (x/2)+1):
                if x%div==0:
                    break
                else:
                   pf.append(x)


    x=x+1
        
print f
print pf

```

it just ouputs:
```

The Number 1  is not a prime!
[1, 2, 3, 4, 6, 8, 12, 24]
[]
```

why doesn't it work?

Because you have changed the indentation at one place when you included the first code into your program: the 'else' goes with the 'for', not with the 'if'. As you probably know, in python, indentation is significant for specifying the control structure.

---

### Post by benj1 on 2009-04-09
```
		if num%div==0:
			print "\nThe Number", num, " is not a prime!"
			break
```
get rid of the break it breaks out of the for loop

---

### Post by Arndt on 2009-04-09
> **benj1 said:**
> ```
		if num%div==0:
			print "\nThe Number", num, " is not a prime!"
			break
```
get rid of the break it breaks out of the for loop

Admittedly, the OP didn't say what the correct result should be.

---

### Post by tawfiqh on 2009-04-09
i got it to work a different way. (similar)

using 
```

def prime(num):
    if num < 2:
            f.append(x)
    else:
            for div in range(2, (num/2)+1):
                    if num%div==0:
                            print "\nThe Number", num, " is not a prime!"
                            break
            else:
                    print "\nThe Number", num, " is a prime!"
y=600851475143
x=1
f=[]
pf=[]
while x<=y:
    if y%x==0:
        prime(x)
    x=x+1

#print f
#print pf
print pf [-1]

```

it prints out a list of prime factors then starts printing a list of factors, the it lags to hell so i just take the last prime factor it lists
:p

---

