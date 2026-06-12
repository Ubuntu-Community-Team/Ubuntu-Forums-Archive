---
title: "many version of ubuntu on the boot"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by mdysonr on 2008-04-26
I have installed on my computer windows xp and ubuntu 8.04,when i start the computer on the boot i have have more than 8 versions of ubuntu 8( including the versions of safe mode).
The problem is that the version ubuntu that is on default the sound don't work, on the others versions the sound is ok.
How can i erase or change the position the versions  on the boot

---

### Post by elmer_42 on 2008-04-26
First, I would reccomend backing up the file we are about to edit.
```
sudo cp /boot/grub/menu.lst ~/grub_menu.bak
```
Then, open up a terminal and run this:
```
sudo gedit /boot/grub/menu.lst
```
Then scroll down to where it says "## ## End Default Options ##". Simply copy and paste these options around as needed. If you really want to delete entries, you can delete them, but I have not personally tried that. Save the file and you are done!

---

### Post by nicedude on 2008-04-26
That's not 8 Ubuntu's that is multiple versions of the Linux kernel. You should post here whether the hardy kernel is working for your sound and such it will be one that says 2.6.24 I believe. Once you get the new version of the kernel running and working you can go into synaptic and remove older versions of the kernel if you want. Although only benifit is freeing a little HDD space ( maybe 70mb each ) and the old ones are a good fallback if something doesn't work.

---

### Post by mdysonr on 2008-04-26
ok it worked! thanks

---

