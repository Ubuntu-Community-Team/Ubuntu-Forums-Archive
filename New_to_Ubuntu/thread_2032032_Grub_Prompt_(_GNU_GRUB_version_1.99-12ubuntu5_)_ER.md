---
title: "Grub Prompt ( GNU GRUB version 1.99-12ubuntu5 ) ERROR"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by RipShade41 on 2012-07-23
[CENTER]GNU GRUB version 1.99-12ubuntu5[/CENTER]

[B]Minimal BASH-like line editing is supported. For the first word, TAB
 lists possible command completions. Anywhere else TAB
 lists possible device or file completions.

grub>_[/B]

---------------------------------------------------------------------------------------------------------------------------

Hey guys i really have a problem trying to boot linux/ubuntu on my netbook. I have had it
 for while and i know some about linux but not enough to fix this problem. I have searched
 to find a solution for this and people have said to type 'sudo' or 'apt-get'. A lot of the commands
 that people have told others wont work on my netbook and it doesn't have a CD drive to use
 the right programs to fix this problem.

I have heard that i can fix it with a usb but i have no idea where to find a program to fix this. I have 
ubuntu 11.04 and i randomly turned off my computer and this grub prompt came up. I really don't
 want to have to re-install ubuntu and lose all my files. can anyone plz help.

---

### Post by barrykgerdes on 2012-07-24
I have the same problem but no one seems to know how to fix it

Barry

---

### Post by SirWhy on 2012-07-24
Let's get you back into Ubuntu first.

At the grub prompt type
```
ls
```

This will list all the drives and partitions.
You want to find the partition your root is on.
So use ```
ls (hdX,Y) (don't actually type X or Y, substitute with one of the drives listed when you used ls)
```

After finding your root partition post back. Sorry If I'm unclear or anything

---

