---
title: "beginning python syntax error"
date: 2015-01-31
forum: Programming Talk
---

### Post by Drone4four on 2015-01-31
Check out this sample code:

```

def changeLetters(myString, origLtr, repLtr):
	newString = ""
	for i in myString:
		if i == origLtr:
			newString = newString + repLtr
		else:
			newString = newString + i
		return newString

string1="Hellen, today is a great and terrible day."

x = changeLetters(string1,"a","z")
print(x)

```

According to the free Udemy tutorial where I got this sample code from, it's supposed to replace all the instances of  “a” in Hellen's string with “z”.  But when I run my script in my shell, it prints the first initial of the string.  I figure I made a syntax error when copying it over from the video but I am too daft to see it.  I made a number of other syntax errors which I was able to spot on my own, but not this one.

---

### Post by steeldriver on 2015-01-31
the over-indentation of `return newString` is causing it to return on the first loop iteration,  I think

---

### Post by teaddict on 2015-02-02
try it now (:
you have problem with "return newString".
```

def changeLetters(myString, origLtr, repLtr):
    newString = ""
    for i in myString:
        if i == origLtr:
            newString = newString + repLtr
        else:
            newString = newString + i
    return newString


string1="Hellen, today is a great and terrible day."


x = changeLetters(string1,"a","z")
print(x)

```

---

### Post by Drone4four on 2015-02-06
Thank-you teaddict and steeldriver: By reducing the indenetation by one block, my script runs perfectly.  

However I have since modified the script slightly to prompt the user for the variables.  I am trying to make it interactive.  Here is my script now:
```

def changeLetters(myString, origLtr, repLtr):
	newString = ""
	for i in myString:
		if i == origLtr:
			newString = newString + repLtr
		else:
			newString = newString + i
	return newString

string1=raw_input("Enter your string:	")
a = raw_input("Now enter the character you would like to replace:	")
b = raw_input("Now enter the character that you want me to replace it with:		")
x = changeLetters(string1,a,b)
z = raw_input("Are you ready?  If you're ready, press Y if not, press N"
if z == Y:
	print(x)
if z == N:
	print "Thank-you for choosing Direct Energy. You have yourself a good day!"
	break

```
My terminal is spitting it back at me with another syntax error:
```

$ python functions_and_strings.py 
  File "functions_and_strings.py", line 15
    if z == 1:
             ^
SyntaxError: invalid syntax
$ 

``` 
I also tried 'if z = Y' I tried using 'if z == 1' 
No dice.

What exactly is wrong with my syntax at that line?

---

### Post by steeldriver on 2015-02-06
check your parentheses in the previous line

---

### Post by Drone4four on 2015-02-09
There was a missing parenthesis at line 14.  I overlooked that.  Thank-you, steeldriver.  

The scripts executes successfully and gets past the original error how it still chokes later at the same line.  Here is the input/output of my script now:

```
$ python functions_and_strings.py 
Enter your string:	Finding Inspiration From Within is the Name of the Game
Now enter the character you would like to replace:	i
Now enter the character that you want me to replace it with:		z
Are you ready?  If you're ready, press Y if not, press NY
Traceback (most recent call last):
  File "functions_and_strings.py", line 15, in <module>
    if z == Y:
NameError: name 'Y' is not defined
 $ python functions_and_strings.py 
  File "functions_and_strings.py", line 15
    if z == Y:
             ^
SyntaxError: invalid syntax
$
```

I know what's wrong.  I didn't define my Y variable or at least didn't reference it properly at the line which reads: if z == Y .  I know this line is wrong but I am not sure why or how to write that line properly.  Any guidance?

---

### Post by steeldriver on 2015-02-09
Is  Y a variable? or is  it a string literal against which you wish to compare the value of variable z?

```

if z  == 'Y':

```

---

### Post by Drone4four on 2015-02-18
That worked.  Thanks, **steeldriver**.

---

