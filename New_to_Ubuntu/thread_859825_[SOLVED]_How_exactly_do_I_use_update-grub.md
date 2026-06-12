---
title: "[SOLVED] How exactly do I use update-grub"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-07-14
Hi.  I need to know how it is that update-grub works, and how to use it.  I would like to know how in case I need to generate a new menu.lst in an "emergency."  However, I don't know if it makes any assumptions about root partitions, etc, because I have a really weird partition setup.(for instance, Ubuntu's root partition is \dev\sda5)

Thanks!

---

### Post by bodhi.zazen on 2008-07-14
update-grub /dev/sda

see also : 

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by S1xp4ck on 2008-07-14
[This "How To Doc"](https://help.ubuntu.com/community/GrubHowto) should help you with Grub.

---

### Post by cdtech on 2008-07-14
Looking through the menu.lst you can see the different options that update-grub reads during execution.

The options without a pound sign (#) will set on reboot without the update-grub command and with the (#) need to be set with the update-grub command.

I personally set my Pretty colours to:
# Pretty colours
# color cyan/blue white/blue
color light-blue/black light-cyan/blue

Which does not need the update-grub command (no #).

Hope this helps.......

**P.S.**
Always remember to save a backup of any file you modify until your sure it functions properly.

---

### Post by pi.boy.travis on 2008-07-15
Thanks!

---

