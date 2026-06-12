---
title: "Error loading splash screen - won't boot"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by Plex3000 on 2012-12-08
I'm not sure if I'm posting in the correct forum, but here's my problem. Please I need help.
I wanted to change my ubuntu 11.10 boot screen, so I downloaded Plymouth Manager. I was exploring the program because I downloaded a theme from gnome-look.org. However, I clicked the Edit button, and changed the part where it said /lib/plymouth/themes/ubuntu-logo, I changed ubuntu-logo for earth-sunrise, because that was the name of the folder, and also changed the next line where I had to write the .script file.
However, I rebooted and when it was turning off it said something like "failed to load Earth-sunrise.script", then when trying to boot, it appeared the purple screen, then turned black, and nothing. It won't boot. I installed ubuntu with Wubi. I was thinking about accessing the file that I edited from windows, so I could rewrite what was originally there, but I can't find a way to access the file. I tried ext2explore program, but the two white parts in the program are blank.
Please help!

UPDATE: Ok I got ext2explore to work, now I can see the files in my Ubuntu. I need to know the path of the file that I edited, it was the text displayed when I clicked the Edit button in Plymouth Manager. On the top of that screen, there was a file path, I need to know that, and also I need to know how to edit and save files in there from ext2explore; I can save files from Ubuntu to Windows but not Windows to Ubuntu, I need to know how to, THANKS IN ADVANCE!

P.S. Sorry for my bad english

---

### Post by bcbc on 2012-12-09
You have to boot an Ubuntu CD/USB and mount the root.disk in order to edit it. The only tool I know that can read the root.disk from Windows is read-only.

So you need to figure out which partition the root.disk is on but then it's like this (assume /dev/sda3 for the example):
```
sudo mkdir /media/win
sudo mount /dev/sda3 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```
Then you can edit anything on the wubi install. e.g. to browse:
```
nautilus /mnt
```

When you're done:
```
sudo umount /mnt
sudo umount /media/win
```

---

### Post by johnycsf on 2012-12-09
the beauty of ubuntu is that it is fully customizable but I also have messed with my boot options and splash screen and had nothing but problems. 
Word of advice is leave it alone and also upgrade your system!
:(

---

### Post by Plex3000 on 2012-12-09
> **bcbc said:**
> You have to boot an Ubuntu CD/USB and mount the root.disk in order to edit it. The only tool I know that can read the root.disk from Windows is read-only.

So you need to figure out which partition the root.disk is on but then it's like this (assume /dev/sda3 for the example):
```
sudo mkdir /media/win
sudo mount /dev/sda3 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```
Then you can edit anything on the wubi install. e.g. to browse:
```
nautilus /mnt
```

When you're done:
```
sudo umount /mnt
sudo umount /media/win
```

THANK YOU SO MUCH!! I was able to access and edit all of my files in my Ubuntu with this, I just had to change the procedure a bit: I just had to run the line
```

sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```
And nautilus opened automatically with my ubuntu files in it, Thank you very very very much. Now I just have to know the location of the file I changed.

Anyone with Plymouth Manager (or someone plz install it), click on the Edit button in the General tab, and there's a text there, please copy and paste what you have there here, so I have the original file, and tell me the path/location of that file (it appears in the top of the window). 
THANK YOU SO MUCH.

---

### Post by Plex3000 on 2012-12-10
OK I got it to work :D

I mounted my root.disk file from my bootable ubuntu usb, went to /lib/plymouth/themes and there was the file, just changed everything back to ubuntu-logo.

SOLVED
THANK YOU VERY MUCH, YOU REALLY HELPED ME.

---

### Post by bcbc on 2012-12-10
Great! 

I've never installed custom themes, but I have changed my plymouth theme to the solar flare. That's much better than the purple default (or the bright white edubuntu default).

To do it, go to the Software Centre and search on "plymouth-theme". Choose the solar theme and install it. Then from a command line, select it as the default:
```
sudo update-alternatives --config default.plymouth
```
That command presents a menu of options, you need to enter the number corresponding to the Solar Theme you just installed.

---

