---
title: "Ignore case"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-10-22
Over 300 people have viewed an old thread about how to set the terminal to ignore case. A staff member closed the thread a minute ago without a solution after I bumped it.

Does anyone know how to issue commands which ignore case or set the terminal to ignore case?

eg for this problem:
mirage kevin.JPG
mirage kevin.jpg

---

### Post by mardybear on 2012-10-23
Hi Kevin...

I'm no expert but was always under the impression that Linux and Ubuntu are case sensitive for anything related to terminal commands. I'm not sure there's a solution to your query. Maybe someone else out there would know better...

mardybear

---

### Post by critin on 2012-10-23
> **mardybear said:**
> Hi Kevin...

I'm no expert but was always under the impression that Linux and Ubuntu are case sensitive for anything related to terminal commands. I'm not sure there's a solution to your query. Maybe someone else out there would know better...

mardybear

I'm under the same impression, commands must be exact.

---

### Post by NikTh on 2012-10-23
I don't know if this serve your needs , but you can ignore-case with bash completion . 

Bash completion is the program that makes your "terminal life" easiest with the [Tab] key = auto-fill.

You can set this to ignore case with the following way 

```
touch .inputrc 
gedit .inputrc
```Place inside this line 
```
set completion-ignore-case On
```save the file , close the terminal and open a new. 

When you [Tab] now , you will see that is not case sensitive anymore. 

Thanks

---

### Post by vasa1 on 2012-10-23
> **Kevin McCready said:**
> Over 300 people have viewed an old thread about how to set the terminal to ignore case. A staff member closed the thread a minute ago without a solution after I bumped it.

Does anyone know how to issue commands which ignore case or set the terminal to ignore case?

eg for this problem:
mirage kevin.JPG
mirage kevin.jpg
1. Your images don't seem to be attached properly.
2. *They* prefer to close old threads because much of the information *may* be outdated. There's absolutely nothing wrong in starting a new thread with a link to an old thread for context.

Edit: did you see this: [http://askubuntu.com/questions/87061/can-i-make-tab-auto-completion-case-insensitive-in-the-terminal](http://askubuntu.com/questions/87061/can-i-make-tab-auto-completion-case-insensitive-in-the-terminal) ?

---

### Post by ~LoKe on 2012-10-23
Linux is a case-sensitive OS.  image.jpg and image.JPG are two different files.  If you made the terminal case-insensitive, you're bound to run into issues.

---

