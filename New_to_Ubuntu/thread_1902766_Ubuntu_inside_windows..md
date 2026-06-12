---
title: "Ubuntu inside windows."
date: 2011-12-31
forum: New to Ubuntu
---

### Post by ElanCompaq on 2011-12-31
If you choose for ubuntu to run as an application inside windows but put it on a separate partition, and have a dual boot, will windows still be running in the background?

---

### Post by Karlchen on 2011-12-31
Hello, ElanCompaq.
> If you choose for ubuntu to run as an application inside windows but put  it on a separate partition, and have a dual boot, will windows still be  running in the background?I am afraid that there is a slight misunderstanding on your side.

_(1) Ubuntu inside a virtual machine which is run by Windows_
The only way of running Ubuntu inside Windows is by
+ creating a virtual machine
+ install Ubuntu in this virtual machine
+ launch the virtual machine thus running Ubuntu
In this case, Windows will be running while Ubuntu is. Yet, Ubuntu will not have a partition of its own. Instead the virtual machine will use a large disk file as its virtual disk, and Ubuntu will see this disk owned by the virtual machine and use it.
In this case, Ubuntu runs inside Windows - hm, sort of - yet, it does not have its own partition. Nor is this a dual boot system.

_(2) Ubuntu and Windows in their own partition(s) - real dual boot system_
If you create a separate partition for Ubuntu and install it on its own dedicated partition, you may choose on each boot whether to run Windows or Ubuntu. But they will never be up and running at the same time.
In this case, you have a real dual boot system. Both, Ubuntu and Windows, have their own dedicated partition(s). At any point in time, only one of the two operating systems is up an running, either Windows or Ubuntu, never both.

_(3) Ubuntu on the Windows partition - Wubi Installation_
Last there is - what you may have in mind - the Wubi installation. You start the Ubuntu installation by launching the file wubi.exe while Windows is running. Wubi will start the Ubuntu installation. It will create two pseudo disks on (one of) the Windows partition(s): swap.disk and root.disk. Both pseudo disks are actually just large files. swap.disk will later on be used by Ubuntu as its memory swap space. root.disk is the pseudo disk where Wubi will create the Ubuntu file system and install the Ubuntu system. 
By performing a Wubi installation, you will have a dual boot system, too. You can either boot Windows or Ubuntu. Again, either Windows will be up and running or Ubuntu, never both at the same time.

Kind regards,
Karl

---

### Post by ElanCompaq on 2011-12-31
Ok, what I did is number 2, thanks Karlchen for your response!:)

---

### Post by Mark Phelps on 2012-01-01
OK ... then please use the Thread Tools at the top of your thread, to mark this as SOLVED.  thanks

---

