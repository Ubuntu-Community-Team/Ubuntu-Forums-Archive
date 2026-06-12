---
title: "Geany Problem"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by jjblackfox on 2008-06-01
I recently intalled Geany for Ubuntu Hardy Heron and I tried to run the project and it gave me a permission denied error. Has anyone else had the same problem, and how do I fix it?

[edit]
New Problem:
My computer completely messed up because I had a bad hard disk and I had to reinstall Ubuntu. I installed Geany again and it compiles fine, but it won't let me execute any programs.


I keep getting a "failed to execute the terminal program" error.

---

### Post by Monicker on 2008-06-01
You tried to open a project and got that error?  What exactly were you doing when you got the error?

I've never run into that problem myself.  Perhaps you were trying to open a file to which your normal user account does not have access.

---

### Post by jjblackfox on 2008-06-01
> **Monicker said:**
> You tried to open a project and got that error?  What exactly were you doing when you got the error?

I've never run into that problem myself.  Perhaps you were trying to open a file to which your normal user account does not have access.

Hi, I have an admin account so that shouldn't be the problem. What I did was save a project to my desktop, compile it, then I tried to Execute it. 

To install Geany, I typed: sudo apt-get install geany
Do I have to enable any other repositories?

---

### Post by jjblackfox on 2008-06-01
bump

---

### Post by iaculallad on 2008-06-01
> **jjblackfox said:**
> I recently intalled Geany for Ubuntu Hardy Heron and I tried to run the project and it gave me a permission denied error. Has anyone else had the same problem, and how do I fix it?

Try relating with the thread link below on installing Geany.

[http://ubuntuforums.org/showthread.php?t=470169](http://ubuntuforums.org/showthread.php?t=470169)

---

### Post by amingv on 2008-06-01
Did you build (link) the project after you compiled it or are you trying to run the <name_of_program>.o file?
The .o file is not executable and will give you this error, you need to link the object file in order to be able to run it (F9 in geany IIRC).

---

### Post by jjblackfox on 2008-06-02
> **iaculallad said:**
> Try relating with the thread link below on installing Geany.

[http://ubuntuforums.org/showthread.php?t=470169](http://ubuntuforums.org/showthread.php?t=470169)
Thanks, I followed the guide and it works now.
What does it mean when it says sh: PAUSE: not found?

---

### Post by jjblackfox on 2008-06-04
My computer completely messed up because I had a bad hard disk and I had to reinstall Ubuntu. I installed Geany again and it compiles fine, but it won't let me execute any programs.

 
I keep getting a "failed to execute the terminal program" error.

---

### Post by jjblackfox on 2008-06-04
The problem is not just with geany, I tried using Dev-c++ with wine and it lets me compile, but it doesn't build.

---

### Post by jjblackfox on 2008-06-04
> **jjblackfox said:**
> The problem is not just with geany, I tried using Dev-c++ with wine and it lets me compile, but it doesn't build.

bump

---

### Post by iaculallad on 2008-06-04
Open up your terminal:

```
sudo apt-get install build-essential
```

Then do the re-compile you're mentioning.

---

### Post by parakeets11 on 2008-09-06
What I found out was the problem for me when it said that it "failed to execute the terminal program" was that I never built it in the first place.  You have to compile, then build after compiling.  Then it would execute for me.

---

