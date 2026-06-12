---
title: "[SOLVED] help with python basics"
date: 2008-08-20
forum: Programming Talk
---

### Post by dwalker0044 on 2008-08-20
Hi everyone,

I'm having problems with a few of the basics - how to translate a few concepts from C/C# into python. Also please free to correct any terminology that I have use in-correctly. 

To begin with I notice that python doesn't need a main function to work, but is it good practice to have one? 

Then, what is good practice to close functions/modules. I noticed that when main *is* included it is ended with 

```
if __name__ == '__main__': main()
```

But I have no idea what this means, can someone give an explanation please?

Then finally, if I have a module and I want to access a few different variables which I have incorporated into a class - how can I link the two? The only way I have found to do this so far is to define my class and then access the variables (or is the correct term attribute?) using code that is not apart of *any* module. Im thinking along the lines of a namespace equivalent like that used in c#

I look forward to any replies!

---

### Post by pmasiar on 2008-08-20
Explained by Guido himself:

[http://www.artima.com/weblogs/viewpost.jsp?thread=4829](http://www.artima.com/weblogs/viewpost.jsp?thread=4829)

Doing this allows you to have some code (in main) if you run this as 'main' module (ir from commandline - not imported), and not to run it if module is imported into other module as library. All gain with no pain.

---

### Post by days_of_ruin on 2008-08-20
> **dwalker0044 said:**
> Hi everyone,

I'm having problems with a few of the basics - how to translate a few concepts from C/C# into python. Also please free to correct any terminology that I have use in-correctly. 

To begin with I notice that python doesn't need a main function to work, but is it good practice to have one? 

Then, what is good practice to close functions/modules. I noticed that when main *is* included it is ended with 

```
if __name__ == '__main__': main()
```

But I have no idea what this means, can someone give an explanation please?


Then finally, if I have a module and I want to access a few different variables which I have incorporated into a class - how can I link the two? The only way I have found to do this so far is to define my class and then access the variables (or is the correct term attribute?) using code that is not apart of *any* module. Im thinking along the lines of a namespace equivalent like that used in c#

I look forward to any replies!

Are you reading a python book/tutorial?You'll get a better answer if you do.

---

### Post by dwalker0044 on 2008-08-20
I'm not reading the official hand book, but I've been looking at other reading materials. I will check it out, but I've found that my main problem is pulling it together - which doesn't seem to be covered so well. As I said, I can use classes and write modules, but when comes to using a class within a module I can't! 

Is there a section on common practices and also, what is the equivalent to a name space, or perhaps you can suggest a chapter to read. It would really help me as I've seem to have hit a bit of a brick wall. Perhaps what I will do is give an example of what exactly I want to do tomorrow (it's late here!)

Thanks everyone for your replies!

---

### Post by pmasiar on 2008-08-20
Try following links from my wiki (see sig) for Python beginners

---

### Post by dwalker0044 on 2008-08-24
Hi again,

With the help of the comments posted I was able to solve my problems. So thanks again I am now marking this thread as solved

Regards

---

