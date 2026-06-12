---
title: "Grub (Yep good ol Grub ^^)"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by x-r4y on 2008-06-23
Hy, well at first I wanted to say that I am happy using Ubuntu, it's easy to use and perfect for beginners.

Well here is my problem, I usually worked with Windows, but then I got kinda pissed of and decided to use Linux, and everybody told me to use the Ubuntu, which really was a good choice, I installed Ubuntu while I was in Windows, and needless to say Ubuntu works without a problem. But now I wanted to install Fedora 9, becaus of the funtionality and because it uses KDE (Ubuntu I only run with GNOME). But the problem is I go through the installation without a problem, I make all the partitions (SWAP, /Boot, / and even a seperate /home) when the installation is done I reboot the pc and I want to startup Fedora, but the only thing I get is Grub2read Error.
I looked almost everywhere, and I saw something where the ppl said that it was because Grub doesn't have the drivers to read sda, sdb... but why does my Ubuntu work? Ubuntu uses as far as I know the Grub Bootloader.

Can someone help me resolve the problem? Thank you guys for any reply I get :)

p.s here is a link where a picture is that I draw xD Makes it visually easier to understand ^^

[http://rapidshare.com/files/124514616/Problem_with_installing.JPG.html](http://rapidshare.com/files/124514616/Problem_with_installing.JPG.html)

---

### Post by Duck2006 on 2008-06-23
If you want KDE in ubuntu, this link may help.

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

for the fix for grub, from the terminal run,

sudo fdisk 

and post the out put.

---

### Post by x-r4y on 2008-06-23
Now I seem to have a real problem -.- Always when I try to run Ubuntu I hangs on startup, so I use the save mode and after a while I get this message:

[80.131926] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[80.132064] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Done.
Begin: Mounting root file system... ...
Begin: Running /script/local-top...
Done.
Begin: Waiting for root file system... ...
Done.
Alert!!! /dev/disk/by-uuid/0CD6-OCD7 does not exist. Dropping to a shell! Check you root=boot argument (cat /proc/cmdline)
Check for missing modules (cat /proc/modules), or Device Files (ls /dev)
(initramfs)

So I started:

(initramfs)cat /proc/cmdline ---> root=UUID=0CD6-0CD7 loop=/ubuntu/disks/root.disk ro single

(initramfs)cat /proc/modules ---> thermal 16796 0_Live 0xf884b00
           processor 36872 1 thermal, Live 0xf8858000
           fan 56360 -Live 0xf8833000
           fbcon 42912 0-Live 0xf883f000
           tileblit 3456 1 fbcon, Live 0xf8831000
           font 9472 1 fbcon, Live 0xf882d000
           bitblit 67841 fbcon, Live 0xf8824000
           softcursor 3072 1 bitblit, Live 0xf8827000

(initframfs)ls /dev ---> /bin/sh: ls: not found
-----------------------------------------------------------------

What does all that mean? :-/ I just started with Ubuntu, and only no merely basics.

---

### Post by Duck2006 on 2008-06-23
From the live ubuntu cd reinstall grub.

sudo grub

find /boot/grub/stage1  " it will can back with )hd0,1) or some thing like that use in next step)
root (hdx,y)
setup (hd0)
exit

Once you have ubuntu running edit the menu.lst in there to load fedora. I install fedora core 6 yesterday the gurd.conf looked like this.

> title Fedora Core (2.6.18-1.2798.fc6xen)
	root (hd0,0)
	kernel /boot/xen.gz-2.6.18-1.2798.fc6 
	module /boot/vmlinuz-2.6.18-1.2798.fc6xen ro root=LABEL=/ rhgb quiet
	module /boot/initrd-2.6.18-1.2798.fc6xen.img

You will have to change the kernel to fit fedora core 9

---

### Post by Troll_the_Great on 2008-06-24
I am a beginner just like you so I can tell you anything about the grub problem, but if you want KDE (although I like gnome much better) is easy to install.Gnome and KDE are just desktop managers, you can install any of them,or both if you want.There are many other desktop managers, like X-Face for example.You can install any (or all of them and then choose you session when you log in).
To get KDE you have 2 options:
1.Download and install Kubuntu, which is Ubuntu but with the K desktop environment (KDE)
2.Keep Ubuntu, open a terminal and type:

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

See this link for more information:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
Hope this helps
Cheers!

---

### Post by x-r4y on 2008-06-24
Biiiiiiiiiiiig Thanx for the great help, everything is working now. I am gratefull (or however u write it ^^). Keep going ;)

And thanx again

Duck2006
Troll_the_Great

---

### Post by x-r4y on 2008-06-25
Everything is working fine ;)
There is just another question I have, the moment I'm usiing Grub, on the Internet I found Lilo and it's a rpm package, is it possible to install it in Fedora? And how would that work? Does it delete Grub and rewrites a new Boot for all my OS or would I have to rewrite it manually? :) Thx beforehand for the Information ;)

Erm... by the Way What does Hardy mean? ^^ :P

---

