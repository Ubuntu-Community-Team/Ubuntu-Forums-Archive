---
title: "Updates Hosed Grub ... Help!"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by oxsyn on 2008-05-28
Preface:  My system was a triple boot setup - Windows XP Pro / Ubuntu 8.04 / Backtrack 3.  I had to do some manual editing of the grub file to get it to work - but it worked, beautifully - for about two weeks.

Today, Ubuntu told me there were updates to install.  I let it run.  Just got home from work, it was rebooted.  Sitting at a grub> prompt.  It still has the custom grub background I set in my configuration file, but all I get is the grub> prompt, not my menu that lets me select which OS to load.

Zomg, help please!

---

### Post by Oldsoldier2003 on 2008-05-28
> **F4RR4R said:**
> Preface:  My system was a triple boot setup - Windows XP Pro / Ubuntu 8.04 / Backtrack 3.  I had to do some manual editing of the grub file to get it to work - but it worked, beautifully - for about two weeks.

Today, Ubuntu told me there were updates to install.  I let it run.  Just got home from work, it was rebooted.  Sitting at a grub> prompt.  It still has the custom grub background I set in my configuration file, but all I get is the grub> prompt, not my menu that lets me select which OS to load.

Zomg, help please!

from a live cd 
```
sudo fdisk -l
```
then we can get grub up and running based on that information. once you get grub working recovering the settings for your other oses should be trivial.

---

### Post by oxsyn on 2008-05-28
/dev/sda1 is windows xp pro
/dev/sda5 is ubuntu 8.04
/dev/sda7 is backtrack 3
/dev/sda6 is swap

---

### Post by stchman on 2008-05-28
> **F4RR4R said:**
> Preface:  My system was a triple boot setup - Windows XP Pro / Ubuntu 8.04 / Backtrack 3.  I had to do some manual editing of the grub file to get it to work - but it worked, beautifully - for about two weeks.

Today, Ubuntu told me there were updates to install.  I let it run.  Just got home from work, it was rebooted.  Sitting at a grub> prompt.  It still has the custom grub background I set in my configuration file, but all I get is the grub> prompt, not my menu that lets me select which OS to load.

Zomg, help please!

I don't recommend you manually edit your menu.lst file.  The latest updates included a new kernel and therefore it placed the new kernel at the top of menu.lst file.  A lot of people I see put XP boot at the top and that is a no no.

Chances are you placed something at the top of menu.lst and the new kernel update over wrote it.  The best way to do GRUB duties is to use StartUpManager.  It can set defaults and such.

---

### Post by Oldsoldier2003 on 2008-05-28
> **F4RR4R said:**
> /dev/sda1 is windows xp pro
/dev/sda5 is ubuntu 8.04
/dev/sda7 is backtrack 3
/dev/sda6 is swap

```
sudo grub
setup (hd0)
root (hd0,4)
exit
```

that will set up grub to boot ubuntu. you should be able to do```
sudo update-grub
```
to get grub to add the windows OS. From there you should be able to remember how to add the third OS :)

---

### Post by oxsyn on 2008-05-28
> **Oldsoldier2003 said:**
> ```
sudo grub
setup (hd0)
root (hd0,4)
exit
```

that will set up grub to boot ubuntu. you should be able to do```
sudo update-grub
```
to get grub to add the windows OS. From there you should be able to remember how to add the third OS :)

When I'm at the grub> prompt (which is where I go as soon as I boot), the "sudo grub" command isn't recognized (nor does it seem like it makes sense).

setup (hd0) completes with success
root (hd0,4) completes with success

exit is not a recognized command from the grub> prompt.

Rebooting brings me back to the same grub> prompt, nothing has changed (as far as I can tell).

---

### Post by Oldsoldier2003 on 2008-05-28
> **F4RR4R said:**
> When I'm at the grub> prompt (which is where I go as soon as I boot), the "sudo grub" command isn't recognized (nor does it seem like it makes sense).

setup (hd0) completes with success
root (hd0,4) completes with success

exit is not a recognized command from the grub> prompt.

Rebooting brings me back to the same grub> prompt, nothing has changed (as far as I can tell).

boot from a live cd and run the commands

---

### Post by meierfra. on 2008-05-28
It looks  like grub is installed correctly, but  there is some kind of problem with menu.lst

So boot from the LiveCD and post your "menu.lst":

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda5 /ubuntu
gksudo gedit /ubuntu/boot/grub/menu.lst

```

---

