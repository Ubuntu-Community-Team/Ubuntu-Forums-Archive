---
title: "A way to randomize numbers in simple number game?"
date: 2006-07-23
forum: Programming Talk
---

### Post by GStubbs43 on 2006-07-23
Hi, I am just starting to learn python and I made a simple number game that you guess a number, right now I have that number set to 43 but is there a way I can either
a) randomize the number automatically [within a range like 1-100]
b) set 5-10 numbers for it to randomize through

?

Here is the code:
```
print "Welcome to the number game"
print ' '
print ' '
print ' '
print 'To play, just guess a number, any number. Please enter your first guess below.' 
print ' '
number =  43
running = True

while running:
	guess = int(raw_input('Your guess : '))
	
	
	if guess == number:
		print 'Good job!!! You got it!. Yay!'
		running = False
	elif guess < number:
		print 'Good try, but it is a little higher than that... Enter your next guess below : '
	else:
		print 'Good try, but it is a little lower than that... Enter your next guess below : '
else:
	print 'The number game is over.'	
	
print 'Goodbye.'

```

This was taken from [here]("http://it.metr.ou.edu/byteofpython/while-statement.html").

Thanks! I'm new to programming and a lot of people said python is a good language to start with, I'm not planning on doing anything big just doing this for fun. :D  But I still wanna know how to do this, if possible. :-k :-D

---

### Post by GStubbs43 on 2006-07-23
Okay, I got it thanks to CrazyMYKL in the #python irc channel, to get a random number, `import random` then `random.randint(1,100)`

Thanks anyway for looking, I hope someone else can get help from this!

---

