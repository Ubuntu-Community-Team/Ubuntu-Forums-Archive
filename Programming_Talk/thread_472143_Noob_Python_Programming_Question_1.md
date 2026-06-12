---
title: "Noob Python Programming Question 1"
date: 2007-06-12
forum: Programming Talk
---

### Post by Sethalos on 2007-06-12
I'm working through the tutorials to learn Python, and I've come across something I'm not sure about, was hoping someone could explain it to me.

Here's the program:

name = raw_input("What is your UserName: ")
 password = raw_input("What is your Password: ")
 print "To lock your computer type lock."
 command = "Bob"
 input1 = "Fill"
 input2 = "Gorge"
 while command != "lock":
     command = raw_input("What is your command: ")
 while input1 != name:
     input1 = raw_input("What is your username: ")
 while input2 != password:
     input2 = raw_input("What is your password: ")
 print "Welcome back to your system!"

My question is why do you have to place a string variable in Input1 and input2 and command?

Thanks.

Seth

---

### Post by LaRoza on 2007-06-12
> **Sethalos said:**
> I'm working through the tutorials to learn Python, and I've come across something I'm not sure about, was hoping someone could explain it to me.

Here's the program:

name = raw_input("What is your UserName: ")
 password = raw_input("What is your Password: ")
 print "To lock your computer type lock."
 command = "Bob"
 input1 = "Fill"
 input2 = "Gorge"
 while command != "lock":
     command = raw_input("What is your command: ")
 while input1 != name:
     input1 = raw_input("What is your username: ")
 while input2 != password:
     input2 = raw_input("What is your password: ")
 print "Welcome back to your system!"

My question is why do you have to place a string variable in Input1 and input2 and command?

Thanks.

Seth

```
name=raw_input("Prompt: ")
```
Takes user input, while displaying the word "Prompt: " and assigns that value to the variable name. You do not need to put any information in the parentheses of the rawa_input, but nothing will be displayed before the input line.

When putting code on the forum display it between the [?code] Code Here [/code] tags, without the ? to make it easier to read.

---

### Post by pointone on 2007-06-12
It's because you're attempting to reference variables before defining them. When you say:

```
while command != "lock":
```

Python tries looks to see if command is currently equal to "lock"; but command doesn't exist unless you've defined it elsewhere. The better solution to this problem is to assign command, input1, and input2 the value:

```
None
```

Yes, the capital N is important.

Think of it this way: if I just randomly meet you on the street and demand you answer the question: "Is x greater than 3?" Can you answer? No! You have no idea what "x" is! If I instead say: "x is equal to 5. Is x greater than 3?" then you can answer.

Using None is simply a cleaner way of initializing variables than defining random numbers or strings. Other programmers will recognize what you're trying to do, whereas defining command = "Bob" is actually quite confusing.

---

### Post by HackingYodel on 2007-06-12
> **Sethalos said:**
> My question is why do you have to place a string variable in Input1 and input2 and command?

Thanks.

Seth

If I understand you question correctly.

*input1*, *input2* and *command* need string variable because the **raw_input()** function returns a string.

When you compare *input1*, *input2*, *command*, and *name* with the** !=** they have to be of string types.

For this example you could have used an empty string "" or garbage string "eoaohe" just as well as the strings "Bob", "Fill", etc.

Is that what you were asking?

---

### Post by Sethalos on 2007-06-12
That's it...thanks very much I understand it now. Seems silly I didn't figure that out before this, lol.

Thanks again.

---

### Post by pointone on 2007-06-13
> **HackingYodel said:**
> When you compare *input1*, *input2*, *command*, and *name* with the** !=** they have to be of string types.

Sorry, but this is incorrect. From some interactive Pythoning:

```
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> x = "This is a string"
>>> y = 5 # This is a number
>>> x == y
False
>>> x != y
True
>>> x > y
True
>>> y > x
False
>>> "String" == 5
False
>>> "String" == None
False
>>> import sys
>>> "String" == sys
False
>>>
```

In Python, you can compare any object to any other object. Strings, integers, functions, modules, whatever! Python figures out if things are equal in it's own way.

---

### Post by HackingYodel on 2007-06-13
Sorry Sethalos, I was completely incorrect.

The other post in this thread have the proper advice, please disregard my confusion.

Now, excuse me while I go and wipe some statically typed egg off my face.

---

### Post by Sethalos on 2007-06-14
Ok...I have it now. thanks.

I appreciate the clarification.  The hardest part of this is the problem solving aspect, lol.  Given a task, and then trying to figure out how to actually compose the programming to accomplishment seems to be the hardest part of all this for me.

Seth

---

