---
title: "Can't get back to Windows 7"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by PersonInNeed on 2013-02-20
Oh man, oh man I messed up. You'd think installing a nice free OS would be simple, reading the instructions sounded so simple yet, it was the exact opposite. 

I have been trying to get Ubuntu to work on my HP Pavilion dv6 laptop through USB and now I'm stumped.

right now I set my BIOS to boot from the Hard drive, I have nothing plugged into the laptop, and I get the message "Grub rescue"

I'v tried reinstalling ubuntu like 4 times already and the same thing happens every single time. I feel hopeless now.

I can't find any Windows 7 CD's anywhere's and the laptop is now useless. I go to System recovery and the same Grub message comes up.

Everything I try leads to "Reinstall" "Delete and reinstall" but no "Delete" option. I just want Windows back.

I wanted to run Ubuntu along side Windows initially in case you were wondering.

I need help and I need simple help. I don't understand all this command line stuff. I need an easy way to get back to Windows.

---

### Post by QIII on 2013-02-20
A forum member, YannBuntu, developed what is probably the very best tool for you to use.

Have a look at [this wiki](https://help.ubuntu.com/community/Boot-Repair).

I hope that helps.  Be sure to ask questions if you have trouble.

Best wishes!

---

### Post by Impavidus on 2013-02-20
What have you done exactly? Have you created free (that is: unallocated) space on your hard drive before installing? Did you choose "install alongside", "use whole disk" or "something else"?

Indeed, try the link QIII provided. You can create a BootInfo Summary and post the link here. It will tell us exactly what's wrong with your system. It won't damage your system more.

---

### Post by Mark Phelps on 2013-02-20
If boot-repair doesn't work, there is another option -- but it will cost you.  Win7 has a feature to create a free Repair CD, but you have to use the before you're in the situation you're in.

If you go to the site below, and pay the fee, you can download and burn an ISO file of a Windows Repair CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

When you have that CD made, boot from it and run Startup Repair three times -- that's right, three times.  It often takes all three passes to completely repair the boot loader.

---

### Post by edu4rd on 2013-02-20
Or you could use testdisk to recover all your data and then reinstall your OS again .

---

### Post by Mark Phelps on 2013-02-20
> **edu4rd said:**
> Or you could use testdisk to recover all your data and then reinstall your OS again .

Except ... the HP comes pre-installed which means they have no Disk to do a reinstall, and , even if they do reinstall, they will lose all their apps (no way to save them) and all their Windows Updates (no way to save them, either).

So, they're looking at HOURS of work to get a working machine back ... versus ... 15 minutes of running Startup Repair from a CD.

---

