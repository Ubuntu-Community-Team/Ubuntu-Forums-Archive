---
title: "problem dual boot windows 7"
date: 2017-10-11
forum: New to Ubuntu
---

### Post by stamos19 on 2017-10-11
Hello everyone,As I am a new ubuntu user and I am trying to figure out a few things, I would like to ask for your valuable contribution.

I  installed ubuntu 16.04 lts in my current desktop running windows7. At  the start up the menu for choosing the OS, although ubuntu  runs smoothly after choosing it, windows 7 do not boot and a purple screen appears and  nothing happens. Windows 7 can be manually booted from BIOS menu, but I would prefer to select it without entering BIOS (everytime I want to boot in windows 7).
I ran the boot-repair program but the problem persists. I attach the summary report.

[paste.ubuntu.com/25706588]("http://paste.ubuntu.com/25706588")

I would greatly appreciate your help!

Stam

---

### Post by wildmanne39 on 2017-10-11
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by oldfred on 2017-10-11
Report says Secure Boot may be on? Is it?

I do not believe they have fixed grub to boot Windows in UEFI Secure Boot mode. There is a loss of the chain of trust, so it cannot be Secure boot mode.
Turn off UEFI Secure boot and see if then grub boots Windows.

Most with similar issue have left Windows fast start up on, as then grub also does not boot hibernated Windows.

       Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

