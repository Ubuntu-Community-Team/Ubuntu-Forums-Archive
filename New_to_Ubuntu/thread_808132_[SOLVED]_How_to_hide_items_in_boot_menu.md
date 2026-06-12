---
title: "[SOLVED] How to hide items in boot menu?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-05-26
Following todays kernel update in Hardy I notice that I have two new menu options in my boot menu. No big deal on two of my computers (both just dual-boots) but the third is set up specifically to satisfy the curiosity of friends who want to know the differences between Ubuntu, and it's derivatives.

So I already have a long menu list with Ubuntu, Kubuntu, Xubuntu, and Win 98 (just for some old seldom used proprietary software). So adding the six new  kernel items makes for a really clunky, cluttered boot menu.

So the question is: can I safely "hide" the old kernel 2.6.24-16 entries (and if so how do I do it)? I really don't think it wise, nor would I want to remove them altogether but thought there might be some way to edit the menu lst to "hide" them. OTOH I really don't want to break everything .......... again. Breakage on that machine is common because I let everyone and anyone play with it.

---

### Post by shifty_powers on 2008-05-26
```
sudo apt-get install startup-manager
```

then system>admin>startup manager

---

### Post by Inxsible on 2008-05-26
When a new kernel gets installed it automatically makes entries in the menu.lst file.

Now you can either hide it in the menu.lst or simply search for it in Synaptic and Mark for complete removal.

If you are confident that the new kernel is not giving you any problems, then you can safely remove the kernels.

If not, you can hide them in /boot/grub/menu.lst by using this command ```
gksudo gedit /boot/grub/menu.lst
```Remove or comment the corresponding lines and they wont show up.

Word of caution here:  You can really screw up your ubuntu login if you dont know what you are doing. So be careful.

---

### Post by Norm24 on 2008-05-26
Click on System then Administration and finally on synaptics package manager.In the Search box type "linux-image".You can remove the older Kernals which in turn removes them from the boot list.

I can't take credit for that as I read this in another thread,I just can't remember which.

Inxsible beat me to it.

---

### Post by bumanie on 2008-05-26
Put a # in front of the lines you don't want to show up.

---

### Post by Norm24 on 2008-05-26
> **shifty_powers said:**
> ```
sudo apt-get install startup-manager
```

then system>admin>startup manager

There's no - between startup and manager.Just startupmanager.It can be installed though Synaptics also which might be easier for some who are still a little new at this,like me.

---

### Post by shifty_powers on 2008-05-26
so it is.

slip of the finger obviously ;)

---

### Post by kansasnoob on 2008-05-26
Thank you all very much. I love the options provided by Ubuntu in general. On the aforementioned quad boot I chose to edit menu lst by commenting out all unnecessary lines, which provided a superior cleanup and allowed me to also drop the rec. mode and mem test lines for Kubuntu and Xubuntu while retaining those for Ubuntu.

I used the advanced tab in Startup-Manager in my other two dual-boots to eliminate the older kernel lines in those boot menus, and all three machines now have really snazzy looking boot screens!

Awesome!

---

