---
title: "Program in Java"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by kshsj777 on 2008-06-27
If a program is written in Java does that mean it will run in Linux either natively or under Wine?  

I'm still a novice when it comes to computers and I still don't really understand WHY windows programs don't work in linux and vice versa and why Wine can only run some programs.

---

### Post by wrtpeeps on 2008-06-27
You can write java programs for linux. However, if a program has been written to perform tasks on windows, it might not work if you run it on linux.

For example if a program intends to interact with the Windows registry, I don't know how it would behave if run on linux, probably just error out. 

That's my take on it anyway.

---

### Post by Inxsible on 2008-06-27
Java is multi-platform. Write Once, Run anywhere. This means that Java code written in Windows will run in Linux or Unix or Macs and vice-versa.

There is a catch though. It has to be a pure Java code, as in you cannot have any bindings from Java to COM/DCOM and the code should not use any native dlls for Windows.



With respect to why Windows programs do not run in Linux is because they are using Windows specific code.

---

### Post by wrtpeeps on 2008-06-27
> **Inxsible said:**
> Java is multi-platform. Write Once, Run anywhere. This means that Java code written in Windows will run in Linux or Unix or Macs and vice-versa.

There is a catch though. It has to be a pure Java code, as in you cannot have any bindings from Java to COM/DCOM and the code should not use any native dlls for Windows.



With respect to why Windows programs do not run in Linux is because they are using Windows specific code.

This is what I was trying to say, just much better worded. :)

---

### Post by kshsj777 on 2008-06-27
Wow!  Thanks, that was fast.  That helps a lot.

---

