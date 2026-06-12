---
title: "Using python interpreter to learn python by my self"
date: 2008-06-12
forum: Programming Talk
---

### Post by MongooseCage on 2008-06-12
I am a very noob programmer.I just want to try some programming because I like computers and wish to make some day a free software for everyone.Besides I dont have much to do in the summer holidays so I rather train my stupid brain. I have been using the Python Interpreter in Konsole and [http://docs.python.org/tut/]("http://docs.python.org/tut/") to learn the python basics.

So I decided to make a little text program to calculate The Pythagoras' Theorem. Which would show working and errors.

But for some reason I keep on getting errors now. I copy paste it into the Python Interpreter and it gives me an error that I don't seem to understand. Though it was mentioned on the tutorials about 'modules' but I can't import it as a module it gives me errors that it can't find my file whatsoever.

```

def py(a, b, c):
	print "This is a program designed to calclate the Pythagoras' theorem.2008."
	print ""
	if c == 0:
		if b > 0:
			if a > 0:
				print "a**2 + b**2 = c**2"
				print a, "**2", "+", b,"**2", "=","c**2"
				print a**2, "+", b**2, "=", "c**2"
				print a**2 + b**2 , "=", "c**2"
				print (a**2 + b**2)**0.5, "=", "c", "<=="
				print ""
	if c == 0:
		if a <= 0:
			print "Variable a is less than 0."
			print "This program is designed to calculate positive numbers."
		if b <= 0:
			print "Variable b is less than 0."
			print "This program is designed to calculate positive numbers."
	if a == 0:
		if b > 0:
			if c > 0:
				print "a**2 + b**2 = c**2"
				print "a**2", "+", b,"**2", "=", c,"**2"
				print "a**2", "=", c,"**2", "-", b,"**2"
				print "a**2", "=", c**2, "-", b**2
				print "a**2", "=", c**2 - b**2
				print "a", "=", (c**2 - b**2)**0.5, "<=="
				print ""
	if a == 0:
		if b <= 0:
			print "Variable b is less than 0."
			print "This program is designed to calculate positive numbers."
		if c <= 0:
			print "Variable c is less than 0."
			print "This program is designed to calculate positive numbers."
	if b == 0:
		if a > 0:
			if c > 0:
				print "a**2 + b**2 = c**2"
				print a, "**2", "+", "b**2", "=", c, "**2"
				print "b**2", "=", c, "**2", "-", a, "**2"
				print "b**2", "=", c**2, "+", a**2
				print "b**2", "=", c**2 + a**2
				print "b", "=", (c**2 - a**2)**0.5, "<=="
				print ""
				
	if b == 0:
		if a <= 0:
			print "Variable a is less than 0."
			print "This program is designed to calculate positive numbers."
		if c <= 0:
			print "Variable c is less than 0."
			print "This program is designed to calculate positive numbers."

	if (c**2 - a**2)**0.5 == b:
		print "True"

```

I get:

```

>>> def py(a, b, c):
...     print "This is a program designed to calclate the Pythagoras' theorem.2008."
...     print ""
...     if c == 0:
...             if b > 0:
...                     if a > 0:
...                             print "a**2 + b**2 = c**2"
...                             print a, "**2", "+", b,"**2", "=","c**2"
...                             print a**2, "+", b**2, "=", "c**2"
...                             print a**2 + b**2 , "=", "c**2"
...                             print (a**2 + b**2)**0.5, "=", "c", "<=="
...                             print ""
...     if c == 0:
...             if a <= 0:
...                     print "Variable a is less than 0."
...                     print "This program is designed to calculate positive numbers."
...             if b <= 0:
...                     print "Variable b is less than 0."
...                     print "This program is designed to calculate positive numbers."
...     if a == 0:
...             if b > 0:
...                     if c > 0:
...                             print "a**2 + b**2 = c**2"
...                             print "a**2", "+", b,"**2", "=", c,"**2"
...                             print "a**2", "=", c,"**2", "-", b,"**2"
...                             print "a**2", "=", c**2, "-", b**2
...                             print "a**2", "=", c**2 - b**2
...                             print "a", "=", (c**2 - b**2)**0.5, "<=="
...                             print ""
...     if a == 0:
...             if b <= 0:
...                     print "Variable b is less than 0."
...                     print "This program is designed to calculate positive numbers."
...             if c <= 0:
...                     print "Variable c is less than 0."
...                     print "This program is designed to calculate positive numbers."
...     if b == 0:
...             if a > 0:
...                     if c > 0:
...                             print "a**2 + b**2 = c**2"
...                             print a, "**2", "+", "b**2", "=", c, "**2"
...                             print "b**2", "=", c, "**2", "-", a, "**2"
...                             print "b**2", "=", c**2, "+", a**2
...                             print "b**2", "=", c**2 + a**2
...                             print "b", "=", (c**2 - a**2)**0.5, "<=="
...                             print ""
...
...     if b == 0:
...             if a <= 0:
...                     print "Variable a is less than 0."
...                     print "This program is designed to calculate positive numbers."
...             if c <= 0:
...                     print "Variable c is less than 0."
...                     print "This program is designed to calculate positive numbers."
...
>>>     if (c**2 - a**2)**0.5 == b:
  File "<stdin>", line 1
    if (c**2 - a**2)**0.5 == b:
    ^
IndentationError: unexpected indent
>>>             print "True"  

```

Could you please help me on this I have been stuck on this for weeks avoiding python because I have no clue what to do about this. 

P.S. I am not very smart so help me follow.

---

### Post by LaRoza on 2008-06-12
You can run Python from a file, which is the normal method.

[http://ubuntuforums.org/showthread.php?t=692720](http://ubuntuforums.org/showthread.php?t=692720)

If you have any problems, don't hesitate to post.

---

### Post by Can+~ on 2008-06-12
The interactive shell is for typing things directly, usually for start learning the syntax, or for a beefed-up scientific calculator.

Write a file called myfile.py, and go to the console, go into the folder and type:

```
python myfile.py
```

That will run it.

---

### Post by MongooseCage on 2008-06-12
> **Can+~ said:**
> The interactive shell is for typing things directly, usually for start learning the syntax, or for a beefed-up scientific calculator.

Write a file called myfile.py, and go to the console, go into the folder and type:

```
python myfile.py
```

That will run it.

I tried that but it doesnt do anything.

```

mongoose@The-Heron:~/Desktop$ python Pytha.py
mongoose@The-Heron:~/Desktop$

```

Am I doing something wrong here?

BTW, really quick post. I was expecting reply a day later or something lol.

---

### Post by CptPicard on 2008-06-12
Seems to be it's because you only have "defs" (definitions) in there. They do not actually do anything on their own yet, they just set up your functions in the module namespace.

You need to call your function at the end of the file... so if you have "def foo(x)" you need to do a "foo(5)" or somesuch to actually run the function.

---

### Post by geirha on 2008-06-12
```

...                     print "This program is designed to calculate positive numbers."
...
>>>     if (c**2 - a**2)**0.5 == b:

```

It's because you have an empty line between that print-line and the if-line, which causes python to close the function. You can see that it closes the function definition by the change in prompt from ... to >>>. If you make sure you have the correct indentation on the empty-line, it should work, but usually, when working this way, it's easier to either remove all empty lines (temporarily), or copy/paste smaller sections at a time (that's what I usually do).

---

### Post by pmasiar on 2008-06-12
see wiki in my sig for link, including "a day of IDLE toying".

Shell is used to try snippets of code, max couple lines at a time. For anything above 3-5 lines, edit the code in file and run it. You will have errors, and file edit is simpler than retyping the code.

---

### Post by shadylookin on 2008-06-12
> **MongooseCage said:**
> I tried that but it doesnt do anything.

```

mongoose@The-Heron:~/Desktop$ python Pytha.py
mongoose@The-Heron:~/Desktop$

```

Am I doing something wrong here?

BTW, really quick post. I was expecting reply a day later or something lol.

by the looks of it all you have is a function you need something at the end that isn't in the function like

```

py(3,4,5)

```

otherwise you've just declared the function but never told the program to do anything.

---

### Post by schauerlich on 2008-06-13
I would add this to the end of your script.

```

# Ask the user for input:

a = input("What is a?: ")
b = input("What is b?: ")
c = input("What is c?: ")


# And then call the function you defined earlier.

py(a,b,c)

```

Also, you might want to put

```

#! /usr/bin/python

```

So that bash will run it through python.

---

### Post by roelpeeters on 2008-06-13
In case you go for the solution of EDavidBurg don't forget to do a 
```

mongoose@The-Heron:~/Desktop$ chmod +x Pytha.py

```
So that the file becomes an executable script for bash.

---

### Post by dmm1285 on 2008-06-13
Here are some things to think about:

1) Try breaking your one big function into multiple smaller ones. For example, your three "areas" displaying your output are almost exactly the same, you could make a display_output function.

2) You don't need to nest your if statements like you did. This:
```

if c == 0:
		if b > 0:
			if a > 0:

```

is equivalent to:
```

if ((c == 0) and (b > 0) and (a>0))

```

3) Mixing your program's algorithms with the display code is a big no-no. If you want to learn more about why you shouldn't, check out MVC model on wikipedia.

4) "This is a program designed to calculate the Pythagoras' theorem.2008." This should be a docstring. Check out the python site if you don't know what these are.

5)Don't use zero for the unknown letter. It would be much clearer if you used a string/character instead. This is the beauty of a dynamically typed language.

If these points are overwelming to you, just concentrate on points 1
and 2 for now. Here is roughly the same program in Scheme:
```

(define pythag-theorem
 (lambda (a b c)
  (cond
   ( (not (number? a)) (find-root c - b))
   ( (not (number? b)) (find-root c - a))
   ( (not (number? c)) (find-root a + b))
)))

(define square 
 (lambda (x)
  (* x x)
))

(define find-root
 (lambda (x operator y)
  (sqrt (operator (square x) (square y)) )
))

;start here
(display (pythag-theorem 3 "b" 5))

```

Try walking through this code and figure out how it works (start
under the line marked start here). If you really get stuck, one of
the pytonistas could whip out the Python equivalent.

---

### Post by MongooseCage on 2008-06-13
> **geirha said:**
> ```

...                     print "This program is designed to calculate positive numbers."
...
>>>     if (c**2 - a**2)**0.5 == b:

```

It's because you have an empty line between that print-line and the if-line, which causes python to close the function. You can see that it closes the function definition by the change in prompt from ... to >>>. If you make sure you have the correct indentation on the empty-line, it should work, but usually, when working this way, it's easier to either remove all empty lines (temporarily), or copy/paste smaller sections at a time (that's what I usually do).

Aw man, yeap you are correct! No wonder it was giving me that. I thought python limited the lines that you can copy and paste into it or something.

---

### Post by MongooseCage on 2008-06-13
> **dmm1285 said:**
> Here are some things to think about:

1) Try breaking your one big function into multiple smaller ones. For example, your three "areas" displaying your output are almost exactly the same, you could make a display_output function.

2) You don't need to nest your if statements like you did. This:
```

if c == 0:
		if b > 0:
			if a > 0:

```

is equivalent to:
```

if ((c == 0) and (b > 0) and (a>0))

```

3) Mixing your program's algorithms with the display code is a big no-no. If you want to learn more about why you shouldn't, check out MVC model on wikipedia.

4) "This is a program designed to calculate the Pythagoras' theorem.2008." This should be a docstring. Check out the python site if you don't know what these are.

5)Don't use zero for the unknown letter. It would be much clearer if you used a string/character instead. This is the beauty of a dynamically typed language.

If these points are overwelming to you, just concentrate on points 1
and 2 for now. Here is roughly the same program in Scheme:
```

(define pythag-theorem
 (lambda (a b c)
  (cond
   ( (not (number? a)) (find-root c - b))
   ( (not (number? b)) (find-root c - a))
   ( (not (number? c)) (find-root a + b))
)))

(define square 
 (lambda (x)
  (* x x)
))

(define find-root
 (lambda (x operator y)
  (sqrt (operator (square x) (square y)) )
))

;start here
(display (pythag-theorem 3 "b" 5))

```

Try walking through this code and figure out how it works (start
under the line marked start here). If you really get stuck, one of
the pytonistas could whip out the Python equivalent.

Why do I need it as a docstring compared to just printing it? There was a little lesson about docstrings but I didnt really get into that bit because it seemed rather complex. Wouldn't  a simple 'print' do it?

It will take me  some time to digest the rest. I have done 2) but how do I make all my functions smaller? can python do algebra or something? like find the variables in some way?

---

### Post by MongooseCage on 2008-06-13
> 3) Mixing your program's algorithms with the display code is a big no-no. If you want to learn more about why you shouldn't, check out MVC model on wikipedia.

I read the MVC but the purpose of my function is to show working and solve the problem so that when the user has to explain how he got the answer he could look at the solution. However, I was wondering how I can make it that when they are about to enter the variable as in

```

	Please enter the variable a(leg):(They enter in "3")
	Please enter the variable b(leg):(They enter in "4")
	Please enter the variable c(hypotenuse):(They don't enter anything)

```

That the function would assume that it has to find the variable c

---

