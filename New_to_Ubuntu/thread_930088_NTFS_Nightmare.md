---
title: "NTFS Nightmare"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by jacobroecker on 2008-09-25
I knew I had to get rid of vista and I love the speed of ubuntu.  I've got all my files on an external hard disk that's NTFS.  I've read about 6 tutorials on what to do (tried to follow them as well) and it seems nothings working for mounting this drive.  

My most recent attemp too me to the NTFS-3G website where I modified the suggested file based according to instructions:

/dev/sda1 /mnt/windows ntfs-3g defaults 0 0

is what I added.  

The referenced URL is [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

Please help.  I don't know much yet.  But those files that end in .deb make everything work smooth.  Is there one of those to make this HDD work?

---

### Post by Paqman on 2008-09-25
NTFS-3G is included in Ubuntu by default these days, so you shouldn't need to fiddle about with that. To get your drive mounted there's a good tool called [ntfs-config](apt:ntfs-config).

---

### Post by kansasnoob on 2008-09-25
If ntfs-config doesn't quite get-r-done you can install ntfsprogs. Both are in synaptic.

Some info on ntfs-config:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

And ntfsprogs:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by jacobroecker on 2008-09-26
Ok one of the problems I had was looking in the Add/Remove software.  I didn't realize to change it so it looked at all the repositories.  Since then I was able to find the app and run it properly.

Now all I've got to do is read through the greek on how to get my ipod working--  :-)

Thanks folks.  Sorry for sounding like such a greenie.  It used to be that linux folks wouldn't help you out unless you had a technical clue.  I'm glad this forum seems to be moving away from that.  I like my computer running fast.  No more windows.

-Jacob

---

### Post by muteXe on 2008-09-26
Have you checked out banshee mate?
[http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/)

Not used it myself, but i've heard good things about it.

Tom

---

### Post by Sycron on 2008-09-26
I don't know but here, NTFS work like a charm in all the newest linux version. Are you sure that you didn't messed some configs ?

hava a look at ```
/etc/fstab
``` file .

---

### Post by vanadium on 2008-09-26
A common reason why an ntfs disk does not automount is that it is "unclean". this means that it has not been properly closed after use (drive was removed without unmounting first, drive was removed from a windows system without using the : Safely remove hardware icon, etc...). Before messing up your Ubuntu system, first have the drive itself checked. Unfortunately, because it is an ntfs disk, you need Windows for that.

It is somethimes sufficient just to connect the drive to a Win system, then use the tray icon to disconnect it again. Else, you can use the Windows checking tools to check and eventually repair the drive.

---

### Post by WitchCraft on 2008-09-26
open a terminal:

sudo apt-get update
sudo apt-get install ntgs-3g
sudo apt-get upgrade
sudo apt-get dist-upgrade

to mount:
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force


to transfer files:
sudo mkdir ~/windows
sudo cp -R /media/windows/* ~/windows


to unmount:
umount /media/windows

---

### Post by jacobroecker on 2008-10-16
It's not so much that it 'didn't work' It's that I'm not familiar enough with the menus to find the application.

Where is it?

---

### Post by earthpigg on 2008-10-16
what application? your earlier post makes it sound like you solved everything ok...

---

### Post by jacobroecker on 2008-10-16
To Clarify:

I did solve the problem.  But I went about it a rather difficult way.

I reinstalled ubuntu with the drive connected--everything worked just fine.

Not the best way to solve it, but I was running the 386 version when I've got a 64 bit processor.  So it made sense to match hardware and software.

I had the same problem arise this evening when I plugged in an external hdd.

This time I was unwilling to re-install.  I forgot where the NTFS app was on the menu's  Applications-->System Tools and vented my frustration again on this thread.

So, now I'm up and running on this machine and trying to build the hdd that I plugged in tonight as a boot disk to install ubuntu on my eee pc.

Thanks for caring enough to reply to my confusion.  I like this community--I think I'll stick around.

---

