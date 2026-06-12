---
title: "[SOLVED] Editing GRUB in KDE"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by gingerj on 2008-09-10
Hi All,

I am trying to edit GRUB in Kubuntu, first I tried the old command that I used in Ubuntu:

sudo gedit /boot/grub/menu.lst

Then that failed not realising gedit was exclusive to gnome (although thinking about it the "g" was the give away).

So I searched my application for a text editor and found kate so I typed the following:

sudo kate /boot/grub/menu.lst

Which outputs the following message: 
sudo: kate: command not found

**So how do I edit grub?**

---

### Post by gingerj on 2008-09-10
I have also used kdesu kwrite /boot/grub/menu.lst

This brings up an alert saying "command not found!"

---

### Post by Shazaam on 2008-09-10
kdesu kate or kdesudo kate might work.

---

### Post by SuperSonic4 on 2008-09-10
have you tried ```
kdesu kate /boot/grub/menu.lst
```. kdesu is the KDE equivalent of gksudo and used for running GUI apps. The only other thing I can think of is to replace kate with kwrite or to open kate/kwrite as root and open /boot/grub/menu.lst

---

### Post by aysiu on 2008-09-10
You should never use ```
sudo kate
``` ever.

*kdesu* is the way to go for graphical applications. Are you running Kubuntu with KDE 4, by chance? For some reason, the paths to certain applications (like Kate) isn't added for the root user in KDE 4.

---

### Post by caljohnsmith on 2008-09-10
Check if you have kate:
```
which kate
```
If that shows "/usr/bin/kate" you've got it (at least that's where it is in KDE 3.5, not sure if it is in the same location in KDE4). If you don't, you can install it with:
```
sudo apt-get install kate
```
And if for some reason kate is not in your root user's path, you can always run it with:
```
kdesu /path/to/kate /boot/grub/menu.lst
```
Where "/path/to/kate" is what you got from the "which kate" command.

---

### Post by aysiu on 2008-09-10
This link may help you out:
[How to use Konqueror or Kate as sudo in Kubuntu KDE 4 Remix](http://www.psychocats.net/ubuntucat/how-to-use-konqueror-or-kate-as-sudo-in-kubuntu-kde-4-remix/)

---

### Post by frklin on 2008-09-10
[http://kde-apps.org/content/show.php/KGRUBEditor?content=75442](http://kde-apps.org/content/show.php/KGRUBEditor?content=75442) :idea:

---

### Post by gingerj on 2008-09-11
Many thanks all, I have resolved my issue with editing GRUB.

The trick was using the "which" command as the file path was different, once I manually put the file path into the kdesu cmd it worked first time.

Cheers again! (mods can close)

---

