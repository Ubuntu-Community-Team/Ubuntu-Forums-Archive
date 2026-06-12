---
title: "Terminal/adding codes help :)"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by edward1100 on 2013-05-28
Hi everyone, 

I've just installed ubuntu 12.04 on my lenovo laptop. This is the first time that I've ever used ubuntu so I'm still very much getting used to it. Once I installed ubuntu, I noticed that the brightness on my laptop doesn't changed when I try to change the brightness in the settings. I have found out how to fix this - 

I need to add the code:

acpi_backlight=vendor

to the code:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

This will sound like such a stupid question but I don't know what it means to add a code to another code :S

Something to do with the terminal??

Thanks in advance.

---

### Post by dino99 on 2013-05-28
hey, you know, every one has been lost the first time; no need to worry  :)

open the terminal, and run:
> sudo gedit /etc/default/grub
change the line to looks like : GRUB_CMDLINE_LINUX_DEFAULT=" acpi_backlight=vendor quiet splash"
then you need to save that file and exit
and finally update the boot loader:
> sudo update-grub

Thats it :D

---

### Post by edward1100 on 2013-05-29
Thanks a lot for your help, managed to do it! :)

---

### Post by Locus Kiesselbachi on 2013-05-29
Hwllo!
Just passing by.
Now, mark your thread as [**[SOLVED]**]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Regards.

---

