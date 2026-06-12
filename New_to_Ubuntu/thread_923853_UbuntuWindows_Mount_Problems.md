---
title: "Ubuntu/Windows Mount Problems"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-09-18
Hihi,
I'm running dual-boot at the moment with XP. However, recently, in windows I've started receiving an error message saying something about services.. After clicking 'Don't send' regarding the error report to microsoft, I get a RPC shutdown. If I abort it, it makes the machine run badly, if I don't it'll reset. Now I admit, I neglected to solve this problem, but everytime I wanted to shutdown the computer, I simply held the power button down to kill. And one day I turn on the laptop and when windows starts loading (the black screen with windows logo and load bar) I get a 0.5 second blue screen with some numericals and then it resets, and the cycle continues, unless I load Ubuntu <3
So I guess, firstly, just wondering if anyone has experienced this? And secondly, is it safe for me to mount the windows volume if it didn't shutdown properly? I know I'd have to force it, although not entirely sure how.. 
Thanks for consideration :D
Robin

---

### Post by jbrown96 on 2008-09-18
Not sure about the RPC problem. There shouldn't be any harm in mounting the directory. You would use ```
sudo mount -t auto /dev/sda2 /media/disk/
``` to mount it normally. Replace /dev/sda2 and /media/disk/ as needed. If it won't let you mount simply append ```
-o force
``` to the end of the last command

---

### Post by hungryOrb on 2008-09-18
> **jbrown96 said:**
> Not sure about the RPC problem. There shouldn't be any harm in mounting the directory. You would use ```
sudo mount -t auto /dev/sda2 /media/disk/
``` to mount it normally. Replace /dev/sda2 and /media/disk/ as needed. If it won't let you mount simply append ```
-o force
``` to the end of the last command

Thanks JBrown! :D
It doesn't find /media/disk/ though. Could you tell me how the drive is identified please? The windows installation is installed on G: and is NTFS.

---

### Post by nowshining on 2008-09-18
create the folder disk in /media/

sudo mkdir /media/disk or whatever u want to call it and rename disk/ in the command given to the name of the folder you chose..

---

### Post by hungryOrb on 2008-09-19
> **nowshining said:**
> create the folder disk in /media/

sudo mkdir /media/disk or whatever u want to call it and rename disk/ in the command given to the name of the folder you chose..

Thanks NS, not sure I understand though. Create a folder to mount? how does that folder gain the contents of the drive I want to mount? Arg. Not too techy minded sorry.

---

### Post by Elfy on 2008-09-19
Once the folder is created (with mkdir) the mount command mounts the drive into the folder you specify and the contents of the drive will be inside the folder.

For example /media/disk/windows/system32 - bearing in mind that spaces in windows folder names cause small changes.
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by hungryOrb on 2008-09-19
> **forestpixie said:**
> Once the folder is created (with mkdir) the mount command mounts the drive into the folder you specify and the contents of the drive will be inside the folder.

For example /media/disk/windows/system32 - bearing in mind that spaces in windows folder names cause small changes.
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Ahh thanks. But what about the drive? It it exclusively called with /dev/sda2/ ? Or is it possible it could be called something else?

---

### Post by Elfy on 2008-09-19
Oh yes - it could be called a number of things - asssuming you have mad the folder, run this command from a terminal

```
sudo fdisk -l
```

you will get a list of all your partitions - whichever one you want to mount - replace sda2 to with that. If you're unsure post the output here

---

### Post by hungryOrb on 2008-09-19
> **forestpixie said:**
> Oh yes - it could be called a number of things - asssuming you have mad the folder, run this command from a terminal

```
sudo fdisk -l
```

you will get a list of all your partitions - whichever one you want to mount - replace sda2 to with that. If you're unsure post the output here

Thanks thanks. So useful! :)

---

### Post by bumanie on 2008-09-19
Forestpixie is correct; post the output of > sudo fdisk -lYou need to put that into terminal and then hit enter, then put in your password and hit enter again. Cut and paste the output to the forum. The previous posters were guessing which partition windows is on. The output of sudo fdisk -l will provide us with that precise information, then someone can help. You get to terminal by going to Applications --> Accessories --> Terminal.

---

### Post by hungryOrb on 2008-09-24
> **bumanie said:**
> Forestpixie is correct; post the output of You need to put that into terminal and then hit enter, then put in your password and hit enter again. Cut and paste the output to the forum. The previous posters were guessing which partition windows is on. The output of sudo fdisk -l will provide us with that precise information, then someone can help. You get to terminal by going to Applications --> Accessories --> Terminal.

Thanks, was able to get the info. 
Another question, 'sudo fdisk -l' doesn't show the space used. Or at least, not in MB/GB. Is there a way to tell?
Am trying to re-install windows, but I can't identify the correct partition at which to overwrite the old.. HMM!

---

### Post by Elfy on 2008-09-24
```
df -h
``` will show you in humna readable format the space used/free on mounted drives

---

### Post by hungryOrb on 2008-09-24
> **forestpixie said:**
> ```
df -h
``` will show you in humna readable format the space used/free on mounted drives

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              47G   24G   21G  53% /
varrun                505M  232K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   64K  505M   1% /dev
devshm                505M  116K  505M   1% /dev/shm
lrm                   505M   38M  468M   8% /lib/modules/2.6.24-18-generic/volatile
/dev/sda5             464M   82M  358M  19% /boot
/dev/sda6             9.3G  7.4G  1.5G  84% /home
gvfs-fuse-daemon       47G   24G   21G  53% /home/gen/.gvfs
/dev/scd0             688M  688M     0 100% /media/cdrom0
/dev/sda3              75G   29G   47G  39% /media/disk-1


Thanks! Just wondering here, is /dev/sda1 and gffs-fuse-daemon the same partition? And in the winxp setup it recognises the partitions by drive letter. Is there a way to emulate the way drives are assessed to judge which partition is ok to rewrite in XP? I realise that size would be fine, in which case all I'd be looking for was a partition that is 75g.. but!
OK brb!

---

### Post by Elfy on 2008-09-24
I'm not really very sure about the gvfs - but suffice it to say for the moment that it is reporting your sda1

With a combination of sudo fdisk -l and df -h youi should be able to work out which is which.

It's likely that you could resize sda1 and have a partition availbale for xp, but it also depends to some extent on where on the disk partitions are physically positioned. Running gparted would give you that in all likelihood, you can install it on your buntu - but wouldn't be able to work from there though.

---

### Post by bab1 on 2008-09-24
> gvfs-fuse-daemon 47G 24G 21G 53% /home/gen/.gvfs

This is the Gnome virtual file system.  It is used to allow non Gnome aware apps to run in the Gnome userspace

---

