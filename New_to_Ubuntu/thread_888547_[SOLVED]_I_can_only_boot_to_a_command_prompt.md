---
title: "[SOLVED] I can only boot to a command prompt"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by one_iota on 2008-08-13
A few days ago I was in the middle of trying to install gnome-power-manager (Thread [here]("http://ubuntuforums.org/showthread.php?t=884864") in case relevant) when my internet connection went off and Ubuntu froze. I think I had to press the power button on my Laptop to restart. (Dell Inspiron 1525).

From that day forward I've been unable to boot to my Desktop. The command 'startx' did work initially but now even that fails, and just loads a blank, greyish screen with my mouse pointer in the middle.

Some of the code I see upon loading is:

```
usplash setting mode failed 1280x1024 failed
     "               "      1152x864  failed
kinit name_to_dev_t(/dev/disk/by-uuid/hex number)=sda5(8,5)
kinit trying to resume from    "      "
No resume image doing normal boot
```

It asks me for my username and password. I login and am greeted with the desktop command prompt. From there, I press Ctrl-Alt-F1 to get me to another screen, where the only error I can pick out seems to be:

```
(ww) intel: No matching Device section for instance (BusID PCI:0:2:1) found
```

from there I have to do Ctrl-Alt-Del to reboot which repeats everything above.

I've tried 'dpkg-reconfigure xserver-xorg' several times.

I've tried pressing 'esc' when loading, and tried the four options: loading my generic kernal 2.6.22-15; recovery mode; the other kernal 2.6.22-14; and its recovery mode)

I've tried 'sudo aptitude install ubuntu-desktop.' It finds packages that need installing but it can't complete because it wants to go online, which I don't know how to do from the command prompt.

Any help will be very gratefully received!

---

### Post by billgoldberg on 2008-08-13
> **one_iota said:**
> A few days ago I was in the middle of trying to install gnome-power-manager (Thread [here]("http://ubuntuforums.org/showthread.php?t=884864") in case relevant) when my internet connection went off and Ubuntu froze. I think I had to press the power button on my Laptop to restart. (Dell Inspiron 1525).

From that day forward I've been unable to boot to my Desktop. The command 'startx' did work initially but now even that fails, and just loads a blank, greyish screen with my mouse pointer in the middle.

Some of the code I see upon loading is:

```
usplash setting mode failed 1280x1024 failed
     "               "      1152x864  failed
kinit name_to_dev_t(/dev/disk/by-uuid/hex number)=sda5(8,5)
kinit trying to resume from    "      "
No resume image doing normal boot
```

It asks me for my username and password. I login and am greeted with the desktop command prompt. From there, I press Ctrl-Alt-F1 to get me to another screen, where the only error I can pick out seems to be:

```
(ww) intel: No matching Device section for instance (BusID PCI:0:2:1) found
```

from there I have to do Ctrl-Alt-Del to reboot which repeats everything above.

I've tried 'dpkg-reconfigure xserver-xorg' several times.

I've tried pressing 'esc' when loading, and tried the four options: loading my generic kernal 2.6.22-15; recovery mode; the other kernal 2.6.22-14; and its recovery mode)

I've tried 'sudo aptitude install ubuntu-desktop.' It finds packages that need installing but it can't complete because it wants to go online, which I don't know how to do from the command prompt.

Any help will be very gratefully received!

Install the ubuntu-desktop metapackage by putting the ubuntu cd in your computer.

ps: did you try

startx

?

---

### Post by one_iota on 2008-08-13
> Install the ubuntu-desktop metapackage by putting the ubuntu cd in your computer.

Thank you, I will give that a go!

Yup, I tried startx, it worked a few times then nothing.

---

### Post by one_iota on 2008-08-13
I've got the Ubuntu Live CD inserted and it has loaded the test installation of the Ubuntu Desktop. 

What would be the command to get ubuntu-desktop copied from the CD onto whichever directory it needs to go on my laptop? Would I need to do this from the terminal?

---

### Post by one_iota on 2008-08-15
I finally managed to get this resolved, so will post what worked for me in case it's of any help to anyone in the future. (including myself, knowing what I'm like!) :lol:

I had to plug an ethernet cable into my laptop (usually it's wireless). Laptop then booted to the command prompt. I typed 'sudo aptitude install ubuntu-desktop'.

Thankfully that worked, the ethernet cable had given me an automatic internet connection, and all the packages that I needed to restore my Desktop were installed. When it had finished installing, I typed 'sudo reboot' and was finally reunited with my Desktop again!

Sounds simple when you have the answers - but it took days of Googling, toil, sweat, trial and error and lots of this... :-k ](*,) #-o   :lol:

---

### Post by Crafty Kisses on 2008-08-15
Have you tried reconfiguring X? 
```
sudo dpkg-reconfigure xserver-xorg
```
See if that does it, that usually solves issues like these.

---

### Post by one_iota on 2008-08-15
Ooh we posted at almost the same time, Codename! :lol:

---

