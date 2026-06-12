---
title: "Really n00bish python question"
date: 2005-04-23
forum: Programming Talk
---

### Post by Gnobody on 2005-04-23
I was reading some Dive into Python for the first time and I was wondering why my simple name/string program doesn't work: 


print "Welcome"
print
name = raw_input("Please enter in your name: ")
	if name == "Jason" then 
	print "Hello Jason!"
else 
print "Go away!"

---

### Post by sas on 2005-04-23
[QUOTE=Gnobody]I was reading some Dive into Python for the first time and I was wondering why my simple name/string program doesn't work: 
[/QUOTE]
Your problem is missing ":" after if and else, also next isn't a keyword in python (iirc)
 your code should look more like this:```
print "Welcome"
print
name = raw_input("Please enter in your name: ")
if name == "Jason":
	print "Hello Jason!"
else:
	print "Go away!"
```

---

### Post by Gnobody on 2005-04-24
[QUOTE=sas]Your problem is missing ":" after if and else, also next isn't a keyword in python (iirc)
 your code should look more like this:```
print "Welcome"
print
name = raw_input("Please enter in your name: ")
if name == "Jason":
	print "Hello Jason!"
else:
	print "Go away!"
```[/QUOTE]
 Wow, Python and Gedit pwn me.  Now to learn PyGTK...

---

