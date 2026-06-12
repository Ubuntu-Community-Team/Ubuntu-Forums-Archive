---
title: "System doesn't boot"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by Keshav2050 on 2013-01-22
When I switch on my PC I get 

[CENTER]**GNU GRUB **version 2.00-7ubuntu11

[LEFT]Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>_


Where the last '_' is the prompt like thing, or I sometimes get boot failure when I type 'exit' or sometimes directly when I switch on PC. Initially I thought the hard disk wasn't working, but I don't understand how the latest grub in ubuntu loaded. I also got 'no device found' when I opened partition editor, but now again I can see all partitions and view data in those partitions or file systems. Can anyone please help me.
[/LEFT]
[/CENTER]

---

### Post by audiomick on 2013-01-22
I think your best bet might be to go here
```
https://help.ubuntu.com/community/Boot-Repair
```

THe boot repair function might fix your problem, or you could generate a boot info summary as described there and post it here so people can have a look and maybe see what is going on.

---

### Post by Keshav2050 on 2013-01-22
I don't know why but now the system is working fine, and thanks for the suggestion. Actually I have a CD of ubuntu 9.04 though I use 12.10 (actually I lost CD of 12.04). which doesn't contain boot repair. So if I couldn't open ubuntu I can't use boot-repair.

---

### Post by grahammechanical on 2013-01-22
For those who do not know, Grub is a boot loader. It is installed into the Master Boot Record of the hard disk when we install Ubuntu. If Ubuntu is the only OS on the machine we will not see a Grub boot menu but it is there non-the-less. If there is more than one OS on the machine then we get a Grub Boot menu so we can select an OS to boot.

The message that is appearing here is the Grub program's way of saying that it cannot find an OS to boot. So, it puts us at a Grub prompt so that we can run Grub commands that might direct it to the OS to boot it.

Before any one can help you need to give much more information. We need information about your hardware; the operating systems on the machine and what you were doing lately that might explain why this has happened. What has changed recently?

You have GNU GRUB version 2.00-7ubuntu11. That tells me that you must be running Ubuntu 12.10 for Grub 1.99 is on Ubuntu 12.04 at least until the second week in February when 12.04 will be updated with Grub 2.0.

But that is as far as I can go.

---

### Post by audiomick on 2013-01-22
If you look at that page, you will find instructions on how to make a bootable usb or CD with boot repair on it, and you can run it from there.

If it is working now, though, just watch it and see how it behaves. It is possible that the machine had a problem finding the hard drive. If it is a desktop, you might want to open it up and make sure all the cables are properly seated.

---

