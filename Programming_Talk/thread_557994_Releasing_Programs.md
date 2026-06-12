---
title: "Releasing Programs"
date: 2007-09-23
forum: Programming Talk
---

### Post by azan00 on 2007-09-23
Hello, first of all let me say that I come from windows (moving over slowly to Linux yay). When I write a program I am used to making an exe and distributing that.

But Linux seems different, from my experiences of installing other peoples programs it appears that there are many different ways of distributing programs.

So, what should I do? I have made a simple little dice roller using gtk, I compiled it on my laptop (linux) then I tried moving over the executable onto my desktop (linux) but the program wouldn't execute.

Do I have to set it to some special release mode? Or do I distribute the code then use a makefile to have the user compile it?

Any explanation would be appreciated. :)

---

### Post by ssam on 2007-09-23
the most generic way to release your program is in source form. you could also make packages, but these are usually specific to a distribution and platform. to package for ubuntu/debian you need to make .deb packages.

if you program is super cool, then distros will make the packages them selves. this is much easier than learning how to do 5 different package formats.

---

### Post by azan00 on 2007-09-23
Ok, so if my program has other libraries (such as Gtkmm) I would need the user to get those? Should I then write an install script to get all the required dependencies?

In this case, my program is very very simple. It seems like too much trouble, is there a really easy way to just distribute the compiled program?

Also I have been compiling my code command line, do any IDEs like Anjuta automate this process?

---

### Post by gnusci on 2007-09-23
if you want release binary, then use [COLOR="Red"]static[/COLOR] compilation.

---

### Post by azan00 on 2007-09-23
Ok, I'll look into it.

Thanks much everyone. :)

---

### Post by Steveway on 2007-09-23
Don't forget. If you use code that is licensed under the GPL then you have to release your code under the GPL, too.
Easiest way would be to distribute the source and make proper configure and make scripts.

---

### Post by azan00 on 2007-09-23
Ahh, right...

I think I will try to get Anjuta working as I had heard that it automates much of this process for you. Am I correct? I am basically looking for the easiest way to do this.

---

