---
title: "[SOLVED] Simple python script will work in IDLE yet not in terminal.."
date: 2008-11-07
forum: Programming Talk
---

### Post by MrJoeyUK on 2008-11-07
Ok, so I've made a simple program which asks for input and if input is true it runs a program (that has been defined..)

so.. the code is as follows, for the 'retrieval' program.

[B]choice = input ('What do you require?');
if (choice == test) : test()
[/B]

And the code for the program it is trying to retrieve is as follows..
[B]
def test():
    print 'This is a test..';[/B]

    
Like said in the thread title it will run in IDLE without fault but when I try to run it in terminal, which is what I would be using it in if I wanted to retrieve something, after I type the true answer, in this case 'test', I get..
[B]
NameError: name 'test' is not defined
[/B]

Am I doing something wrong here? Bare in mind I'm new to python so if it's a simple answer go easy. :)

Thanks for any help in advance.

---

### Post by ad_267 on 2008-11-07
You need to define your test function before you call it and before you set what choice is. Eg:

```
#!/usr/bin/env python

def test():
    print "This is a test..\n"

choice = input ("What do you require?")

if (choice == test):
    test()

```

You don't need to end your lines with a semicolon either.

---

### Post by MrJoeyUK on 2008-11-07
> **ad_267 said:**
> You probably need to define your test function before you call it.

But I thought I already done that with def test(): right? That file is saved.

EDIT: I see what you mean.. I didn't try incorporating it into one file.Hang on, i'll try this.

---

### Post by ad_267 on 2008-11-07
> **MrJoeyUK said:**
> But I thought I already done that with def test(): right? That file is saved.

I've edited my previous post to make it a bit more clear. You need to put the definition first in your file. Python doesn't read the file in advance, it reads it through from start to end.

---

### Post by MrJoeyUK on 2008-11-07
That worked perfectly, thanks. Still not sure what I did wrong as the code is practically the same.. 

Thanks buddy!

---

### Post by unutbu on 2008-11-07
[PHP]#!/usr/bin/env python
def test():
    print "This is a test..\n"

choice=raw_input("What do you require? ")
if choice=='test':
    test()
[/PHP]
Use raw_input instead of input.
input evaluates the response as python code. This makes it very dangerous in the wrong hands.

When you use raw_input, the user's response is stored in a string. Since choice is now a string, 
the if test clause changes to 
```

choice=='test'
```

Regarding the error -- When running IDLE, test got defined as a function before running 

```
if (choice == test):
    test()
```

When running it as a script, you have to define all variables before you use them. The Python interpreter reads the script from top to bottom and you can think of it as executing the lines in that order. So it has to be fed the definition of test before you use it in "choice == test".

---

### Post by MrJoeyUK on 2008-11-07
> **unutbu said:**
> 

Regarding the error -- When running IDLE, test got defined as a function before running 

```
if (choice == test):
    test()
```

When running it as a script, you have to define all variables before you use them. The Python interpreter reads the script from top to bottom and you can think of it as executing the lines in that order. So it has to be fed the definition of test before you use it in "choice == test".

Thanks for the explanation, I can see what you mean now. I was under the impression I would have to create a different file and call the file, I guess I was wrong. Still, having the information I want to retrieve within the retrieval script is even better!

---

