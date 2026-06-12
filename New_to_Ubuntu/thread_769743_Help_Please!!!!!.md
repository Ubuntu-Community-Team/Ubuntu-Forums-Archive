---
title: "Help Please!!!!!"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by runnerdi7 on 2008-04-26
So I have Ubuntu installed which worked fine, and XP installed on a 2gig partition ( I only use XP for one program i use rarely).  My problem is when i boot my computer, it automatically goes into XP and i can't figure out how to get into my Ubunutu.  I poked around my bios but couldn't find anything obvious.  I was under the impression i would get a startup screen when i boot up but apparently not? Help Please!

If it helps I installed Ubuntu first on a clean install, then installed Xp afterwards on a small 2 gig partition that was already there.

---

### Post by miwaypet on 2008-04-26
You have to install XP first. It will not recognize the Linux partition. When you install ubuntu after XP, it (XP) will show up as an option on the boot screen in ubuntu.

Hope this helps.

---

### Post by dangerpl on 2008-04-26
That's the problem. You should have installed XP first. You will have to reconfigure GRUB. Search the forums for GRUB configuration as I am not an expert on that, however I am sure this topic has come up before.

---

### Post by scragar on 2008-04-26
you need to restore grub, so boot into a liveCD if you have one(should be able to use small amounts of RAM since you have a swap partition), and use Gparted first(system>Administration>Partition Editor)to remove the boot flag from your XP partiton and add it back to ubuntu.
next you need to start grub manager, so open a terminal and type:
```
sudo grub
```
then, check your partition no:
```
find /boot/grub/stage1
```
once your done with that copy the line back as show:
```
root **(hd0,1)**
```
then finaly reinstall grub:
```
setup (hd0)
```

which should fix grub, however before you leave you will want to mount your ubuntu partiton, and edit the fstab:
```
sudo mkdir /media/disk && sudo mount /dev/**hda1** /media/disk
```
where hda1 is your partiton name(check against```
cat /proc/partitions
```), then launch gedit and edit the file:```
sudo gedit /media/disk/etc/fstab
```
and adjust like so:

FROM:```
**#**/dev/sda1
**UUID=ht834h8-3th283-r2h38-r32j9** / auto...
```
TO```
/dev/sda1 / auto ...
```once your done with that, save and reboot.


Sorry about the size of the post, but it is far easier to install windows first, luckily I just did all this a couple of days ago, so it's fresh in my memory :P

---

### Post by Moop on 2008-04-26
How did you ever fit XP on a 2gb partition? 

You can recover grub to get back into ubuntu. 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jimrz on 2008-04-26
When you installed XP it overwrote your mbr. You will need to reinstall grub to get back to ubuntu. There are several good HowTo's on these forums on doing this or, probaly better, you can download the [[COLOR="Sienna"]***_SuperGrub_***[/COLOR]]("http://www.supergrubdisk.org/") disk and use it.

---

### Post by runnerdi7 on 2008-04-26
so i followed scragar's instructions (which worked beautifully thank you!), now upon boot i go right into ubuntu. I still didnt get a boot screen, How do i get it so i can choose, do i have to just flag both partitions with boot status?

---

### Post by scragar on 2008-04-26
you will just have to add the option to GRUB:
```
gksudo gedit /boot/grub/menu.lst
```
towards the top you'll find:
```
timeout		5
```this is how long grub waits, set it long enough for you to pick windows when you want to boot, but not so large as to leave you waiting ages.
then also, make sure that "hiddenmenu" is commented out```
#hiddenmenu
```
then scroll right down, towards the end, and add:
```
title		Other operating systems:
root

title                 Windows XP
rootnoverify (hd0,1)
chainloader +1
```

save and exit, now that wasn't so hard was it?

---

### Post by runnerdi7 on 2008-04-26
i typed in the first line of code, but when gedit opened it was empty?


i lied, it worked

---

### Post by scragar on 2008-04-26
huh? then where did you install grub if it's not there...?

copy and paste instead of typing it, highlight, then middle click to paste out :P

---

### Post by natrixgli on 2008-04-26
ah you got it working, nevermind!


-n8

---

### Post by runnerdi7 on 2008-04-26
thanks for everything, works perfectly

---

