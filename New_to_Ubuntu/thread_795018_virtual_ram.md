---
title: "virtual ram"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by lex1 on 2008-05-15
I know how to set/create virtual RAM in windows hows it done in ubuntu?

lex1

---

### Post by lswest on 2008-05-15
"virtual RAM" is what the swap partition is used for that was set up when you install Ubuntu, you can however skip the partition and create a "swap file" afterwards, much like what Windows does.

---

### Post by exile on 2008-05-15
I linux it's called "swap" usually when you install Ubuntu you will be prompted to create some. It is not absolutely necessary depending on how much physical ram you have and what you are using the machine for but it is generally recommended to create swap at least as much as your physical.

To check to see if you already have swap setup goto
Applications -> Accessories -> Terminal 

type in the terminal
> swapon -s

if it returns something like /dev/hd* or /dev/sd* in the filename column then you have virtual ram setup.

You can check out: [http://ubuntuforums.org/showthread.php?t=89782]("http://ubuntuforums.org/showthread.php?t=89782") for some more discussion on adding swap.


I would advice to set the swap up at install time and then basically leave it as is. Only add more if you are maxing it out.

Good luck

---

