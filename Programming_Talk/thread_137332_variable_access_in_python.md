---
title: "variable access in python"
date: 2006-02-27
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-27
I have two files first.py and second.py

```

## filename: first.py
from second import y
x = 10
print 'y = ', y

```


```

## filename: second.py
from first import x
y = 20
print 'x = ', x

```

When I try to run either of the .py files here, it gives an error. Doesn't python allow this kind of variable sharing.

Can you please explain.

---

### Post by GazaM on 2006-02-27
I'm extremely tired at the moment, so I won't be able to spend my time looking up all the info you're looking for right now. I will however tell you this... when you say 'from second import y' what you're telling python is that you want to import the function or class y from the file second, NOT that you want the variable y.

I'm not fully sure of how (or even how possible it is) to purely share a single variable in two Python files, but if no one has answered this by the time i wake up (which I highly doubt) then I'll take some more time to look it up for you.

---

### Post by jstrube on 2006-02-27
The problem is that as soon as python encounters "from first import x" it goes to first.py, where it says "from second import y". But you _are_ in second and python didn't get to y, yet, i.e. y doesn't exist.
It is not a problem to share classes, functions or variables. The problem is the recursive import.
Get rid of one of the import statements and then execute the file that still has the import.

---

### Post by wylfing on 2006-02-27
**jstrube** explained correctly. It is perfectly legitimate to import global variables from another module. (Import works on "objects" and functions and variables are both objects, so it's all fair game.) But when you start getting into cross-importing, you can run into unexpected problems, of which this is one.

As was pointed out, by the time you get to the second import statement, the first variable hasn't been defined yet. So, one way to handle this is to simply define the variables above the import statements. You have another problem too, however, which is that whenever you execute an import, any "naked" code is going to be executed at that time. What I mean by that is the print statements in your examples -- they aren't enclosed in anything, so they get executed as soon as the file is loaded (or reloaded). So in this case you're going to execute things multiple times: first.py will run, then it will load second.py, which in turn loads first.py *again* and runs it, so in fact the "hidden" instance of first.py is what is run first, then second.py, then the *first* incarnation of first.py finishes.

So, in all, yes you can do what you are asking, i.e., sharing variables and other code, but you need to be aware of what you are actually asking python to do.

---

### Post by krypto_wizard on 2006-02-27
The reason why I am doing this is because in my little project I have four files.

In the main.py(first file) I read the input file which contain lots of variables. There are three other .py files which sometimes need access to these variables and thats why i import those varaibles.

Also, the main.py instantiates one another class and thats why it imports it.

My bigger project demanded the above mentioned thing.

Is it against the programming ethics or my design is bad ??

Can you suggest something ??

thanks for your time

 

[QUOTE=wylfing]**jstrube** explained correctly. It is perfectly legitimate to import global variables from another module. (Import works on "objects" and functions and variables are both objects, so it's all fair game.) But when you start getting into cross-importing, you can run into unexpected problems, of which this is one.

As was pointed out, by the time you get to the second import statement, the first variable hasn't been defined yet. So, one way to handle this is to simply define the variables above the import statements. You have another problem too, however, which is that whenever you execute an import, any "naked" code is going to be executed at that time. What I mean by that is the print statements in your examples -- they aren't enclosed in anything, so they get executed as soon as the file is loaded (or reloaded). So in this case you're going to execute things multiple times: first.py will run, then it will load second.py, which in turn loads first.py *again* and runs it, so in fact the "hidden" instance of first.py is what is run first, then second.py, then the *first* incarnation of first.py finishes.

So, in all, yes you can do what you are asking, i.e., sharing variables and other code, but you need to be aware of what you are actually asking python to do.[/QUOTE]

---

### Post by wylfing on 2006-02-28
Eh, "ethics" in programming is a sharply limited subject. ;) 

I really can't tell whether what you are doing is good design or not. It is usually best to avoid too much incestuous cross-importing among modules, because, as I said before, it can lead to unexpected behaviors. What I think is more worrisome about what you've said is that you seem to be relying on a lot of global variables and (as I called it) "naked" code, neither of which are especially good ideas.

Why not encapsulate your data in some class instances and pass those around instead? It will probably make your life easier.

---

### Post by jerome bettis on 2006-02-28
yeah i'm not really sure what you're doing (much less why) but have you thought about just writing a getXXX() function that just returns the variable you want?

better yet rethink this and design it better with classes so it's not just "getting a variable from a file" but rather calling a method on an object.

---

### Post by thumper on 2006-02-28
When I first started with python I tended to put different classes in different files.  Probably just because of my background in C++.  However this just complicated the matter most of the time.

There is no reason not to define multiple classes and functions in a single python script, and it often makes things much easier to deal with.  Since your classes and functions rely on each other, why not just have them all in the same module?

---

### Post by krypto_wizard on 2006-02-28
Thanks for yor comments, I will try to improve upon on my code and keep you posted.

---

