---
title: "32bit/64bit"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Benbow on 2008-05-10
This may seem a dumb question but how do I tell whether my system is 32 or 64 bit?:confused:

---

### Post by Joeb454 on 2008-05-10
Open a terminal (Applications > Accessories > Terminal) and run ```
uname- a
```

And post the output in here :)

---

### Post by Benbow on 2008-05-10
Here goes :

benbow@benbow-desktop:~$ uname -a
Linux benbow-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

---

### Post by cool_penguin on 2008-05-10
when i type in that command on the terminal, i get the following:

harish@harish-laptop:~$ uname- a
bash: uname-: command not found
harish@harish-laptop:~$

---

### Post by PurposeOfReason on 2008-05-10
> **cool_penguin said:**
> when i type in that command on the terminal, i get the following:

harish@harish-laptop:~$ uname- a
bash: uname-: command not found
harish@harish-laptop:~$
Look where you put the -
:)

---

### Post by Joeb454 on 2008-05-10
> **Benbow said:**
> Here goes :

benbow@benbow-desktop:~$ uname -a
Linux benbow-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 **i686 GNU/Linux**

I made the bit you want to look at bold :) And you're running the 32 bit system. Hope that helps

> **cool_penguin said:**
> when i type in that command on the terminal, i get the following:

harish@harish-laptop:~$ uname- a
bash: uname-: command not found
harish@harish-laptop:~$

Make sure you include a space between 'uname' and the '-a'. If you want you can copy it from below ```
uname -a
```

---

### Post by Benbow on 2008-05-10
Thanks joeb for the info. What would it have said if I had been running a 64 bit system?

---

### Post by PurposeOfReason on 2008-05-10
> **Benbow said:**
> Thanks joeb for the info. What would it have said if I had been running a 64 bit system?
x86_64

---

### Post by Joeb454 on 2008-05-10
> **PurposeOfReason said:**
> x86_64

Indeed it would, I get ```
Linux dante 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```

---

### Post by Truefire on 2008-05-10
For more info on your system, install Sysinfo.

Add/Remove works, (with all availble applictions enabled)
but

 sudo apt-get install sysinfo

is faster :D

---

