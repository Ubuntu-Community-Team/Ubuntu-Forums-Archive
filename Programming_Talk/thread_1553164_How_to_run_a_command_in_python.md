---
title: "How to run a command in python?"
date: 2010-08-14
forum: Programming Talk
---

### Post by afroman10496 on 2010-08-14
Hey all It's my first week of Python and I think im getting the hold of it but I cant find how to run a command in python such as...

```
firefox http://www.google.com/
```
or
```
uname -r
```
or
```
rm -rf /home
```
**(scratch that last one!!) :D**

So what's the command for executing commands and how do you incorpriate those into normal python commands like
```
print "Your system will rm -rf itself in 3... 2... 1...
```
? 

Thanks!:P:P:P

---

### Post by Bachstelze on 2010-08-14
Look at the os and subprocess modules.

---

### Post by afroman10496 on 2010-08-14
> **Bachstelze said:**
> Look at the os and subprocess modules.

so what does that mean?

---

### Post by Bachstelze on 2010-08-14
Means that the functions you want are documented [here]("http://docs.python.org/library/os.html") and [here]("http://docs.python.org/library/subprocess.html").

---

### Post by afroman10496 on 2010-08-14
Oh cool. Sorry I'm still sort of new to this programming thing.

Thanks :)

---

### Post by ghostdog74 on 2010-08-14
Stop if you are doing that. You are making your code non portable. Use Python's own modules and functions to remove files and do system commands, unless REALLY NECESSARY (like you are calling a command that doesn't have API for Python etc) .

Otherwise, you might just as well learn to write a shell script.

---

### Post by ApocalypeX on 2010-08-14
> **ghostdog74 said:**
> Stop if you are doing that. You are making your code non portable. Use Python's own modules and functions to remove files and do system commands, unless REALLY NECESSARY (like you are calling a command that doesn't have API for Python etc) .

Otherwise, you might just as well learn to write a shell script.

This. You want your work to be portable to other OSs, its a nightmare rewritting a program just so you can port it to windows for example.

---

### Post by ssam on 2010-08-15
if you do need to start a web browser you could use

```

xdg-open http://example.com

```

which would lauch the users default web browser, and should work on any recent linux.

---

