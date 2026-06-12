---
title: "[SOLVED] Grub error 17"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Sunfist on 2008-08-24
I had to reinstall windows and I figured it would be no problem to reinstall grub after. Well I was wrong. I used the auto Super Grub on my first attempt and while it did give me back the grub boot menu, when I choose any of the Linux items I get an error 17. I can, however boot into windows just fine. So I figured I would boot into Linux with a live cd and do it manually, the grub find command says hd0,3 and when I type root (hd0,3) and then setup (hd0), the command seems to work, all the operations are succesfull, but when I try to boot it again I still get the same error 17. Any ideas?

---

### Post by ambar_N on 2008-08-24
HI there...

try to launch your live CD and reinstall the grub.
When get installation process in disk partition section, choose manual on it. Mount your HDD ("/" and "SWAP") without format it. Follow the installation until finish. 

Good luck....

---

### Post by kjohansen on 2008-08-24
are you running the grub command with sudo?

here is the site I worked from, it has screen shots to go with it.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6)

---

### Post by caljohnsmith on 2008-08-24
Sunfist, it sounds like your problem is with your Linux entries in Grub's menu.lst. Please boot a Live CD, and do the following from a terminal:
```
sudo fdisk -lu
```
Find your Linux partition that has Grub (sda4 maybe?), and mount it:
```
sudo mount /dev/sdaX /mnt
```
Where "X" is the Linux partition number. Then post the output of:
```
cat /mnt/boot/grub/menu.lst
```
Please post the output of all commands above.

---

### Post by Sunfist on 2008-08-24
Well I dont know exactly how to do a screen capture in linux, but this is the main items I saw that I think you are looking for and I think I see the problem, just dont know exactly how to fix it. When I run fdisk -lu I get a list similar to the following.
/dev/sda1  *  HPFS/NTFS
/dev/sda2     W95/FAT16
/dev/sda3     Extended
/dev/sda4     Linux
/dev/sda5     Linux Swap

Which obviously shows Linux is on sda4, the only thing I find curious about this is the sda3, as I dont know what that is or where it came from as I havnt made any extended partitions on this hd, but I'll deal with that later.

Second, the ouput of menu.lst shows the following
title Ubuntu 8.04.1 Kernal ect.
root (hd0,2) <--- Shouldnt this be hd0,3 ??

Oh and all the Linux entrys in menu.lst have the same root value (hd0,2)

---

### Post by Elfy on 2008-08-24
Yes they should be (hd0,3), edit the file and change them.

```
gksudo gedit /mnt/boot/grub/menu.lst
```

If you followed the above post

sda3 was made by ubuntu to house sda4 and sda5 when you instyalled, I guess with a guided option

---

### Post by Sunfist on 2008-08-24
I have it working now, it was the hd0,2 entry that needed to be changed to hd0,3. Still trying to figure out where that new partition came from, it had to have been created when I reinstalled windows, why and how I dont know but I am going to delete it if I cant find any good reason to keep it, the weird thing is, its the exact same size as my swap partition...very strange. The other thing I didnt know but found out the hard way is that editing the menu from within the menu doesnt seem to work, when you get the grub menu there is an option to edit the lines, I did that but apparently the changes dont actually get saved to the file. So I had to go in with gedit and do it that way. Also menu.lst isnt where the books and stuff say it is if you are acessing it via the live cd, I will go back and retrace my steps, might help someone else someday.

---

### Post by sandysandy on 2008-08-24
if sda3 is the same size as ur swap, its likely ur SWAP is a logical partition of ur extended partition sda3.

can u post a screen shot from gparted (available on live CD)

regards

---

### Post by caljohnsmith on 2008-08-24
Sunfist, you don't want to delete your sda3 partition, or you'll delete Ubuntu with it. sda3 is an "extended" partition, meaning it is like a container or shell around a bunch of "logical" partitions that you can create inside it. The reason for an extended partition is that your HDD normally only allows four partitions, known as "primary" partitions". So they figured out a way around that limitation by letting one primary partition be converted into an extended partition, and within that extended partition you can create almost as many logical partitions as you want.

If you look closely at your fdisk output, you'll see that sda4 and sda5 together use the disk space allocated to sda3. Also, if you pull up Ubuntu's partition editor (gparted) it will graphically show that sda4 and sda5 are inside sda3.

And to make changes to your Grub's menu permanent, you have to modify your /boot/grub/menu.lst. Any changes you make on startup using Grub's edit feature are not permanently saved. :)

---

