---
title: "The usual dual boot issues"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by 52vincent on 2008-07-17
Anyway hi all, new here. i have the same problem as many others.No dual boot option. Installed Ubuntu and I did not partition prior, I think I chose the use all disk space option when I should not have. I have searched these forums for hours and it looks like Iam hosed. I thought of trying testdisk and have downloaded it but when i try to install it, terminal cant find it.Iam staring at it on the desktop. Following is my fdisk readout.


Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ddf88b8

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13995 112414806 83 Linux
/dev/sda2 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris

here is my readout of sudo gedit

brian@molerat:~$ sudo gedit/boot/grub/menu.lst
sudo: gedit/boot/grub/menu.lst: command not found

not sure what happened there.

Any help would be great in attempting to recover Vista. should I try testdisk if so how do i install?
I know this topic has been covered Ad Nauseum, and I have followed link after link to other threads on this forum but they wind up on a tangent going somewhere that does'nt help me.

If there is any other info I can provide i will.
Thanks a bunch in advance.

Thanks again

---

### Post by Troll_the_Great on 2008-07-17
Let me see if I got it right.You had Vista installed, and then you installed Ubuntu over it?From what you posted,I can see your entire hard disk is partitioned for linux.You want your Vista back?In what way?Did you had some important files or you mean OS Vista?Because when you installed Ubuntu you erased it.Sorry...
If you want dual boot here is what you should do.First back up all your important data on another hard drive.Format all the partitions.Install Vista on one partition and then create a partition for Ubuntu (15 GB should be enough).Install Ubuntu on that partition and your done.Just remember is important to install Vista first and then Ubuntu, or you will have GRUB problems.
Hope this helps.
Cheers!

---

### Post by phantomjoker on 2008-07-17
ok - i used to triple boot - so three partitions, I had a slightly similar problem and I used BARTpe you can download it as a ISO file - burn it to a disk, insert and reboot, it acts as a live partition checker and management system - it works as a windows system - but since its live you can have any OS, give this a shot - works well for me 

I think this is what your needing - repost if i didn't understand your question correctly

a link to BARTpe - [http://www.nu2.nu/download.php?sFile=pebuilder3110a.exe]("http://www.nu2.nu/download.php?sFile=pebuilder3110a.exe")

hope i helped

---

### Post by philinux on 2008-07-17
If you've got one hard drive 120gig, you've now got ubuntu on it and during the install it formatted the drive.

You chose whole disk.

Hope you got backups of anything important.

The command should be

sudo gedit /boot/grub/menu.lst

With a space between gedit and the /

---

### Post by diffuze on 2008-07-17
> **52vincent said:**
> Device Boot Start End Blocks Id System
/dev/sda1 * 1 13995 112414806 83 Linux
/dev/sda2 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris

Windows is gone. Sorry..

> **52vincent said:**
> here is my readout of sudo gedit

brian@molerat:~$ sudo gedit/boot/grub/menu.lst
sudo: gedit/boot/grub/menu.lst: command not found

not sure what happened there.
You are typing it wrong. The correct way is:
sudo gedit /boot/grub/menu.lst

---

### Post by 52vincent on 2008-07-17
I was afraid of that, looks like I will be learning a new OS. I just wanted the dual boot option. I don't even have a recover disk, did not come with comp. guess I will call HP and have them send one.
On another topic why can't i get testdisk to work?

---

### Post by Inxsible on 2008-07-17
> **diffuze said:**
> Windows is gone. Sorry..


You are typing it wrong. The correct way is:
sudo gedit /boot/grub/menu.lst Notice the space between gedit and the /boot

Also using gksudo instead of sudo would be a better option because gedit is a graphical application

---

### Post by diffuze on 2008-07-18
> **Inxsible said:**
> Notice the space between gedit and the /boot

Also using gksudo instead of sudo would be a better option because gedit is a graphical application

Yes, correct. Good catch. :)

---

### Post by bumanie on 2008-07-18
I have not tried test disk from ubuntu, but it is > sudo apt-get install testdiskto download from the repository and get the program running > sudo testdiskin terminal. It is fairly easy to understand its menu's. The other option you have is to use ntfs undelete which is part of ntfsprogs - I think if you use that you have to save it to another partition. Saving it to the partition you are recovering, may overwrite some of the information you want to recover. Another program is photorec ( a stable-mate of testdisk). Despite its name, it recovers much more than photos. Check out their documentation [here]("http://www.cgsecurity.org/wiki/TestDisk") Photorec is in the "Data Recovery" box under test disk on the top left.

---

