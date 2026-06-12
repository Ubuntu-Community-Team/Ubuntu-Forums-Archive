---
title: "Ubuntu 8.04 and 8.10 installed"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by dax029 on 2008-11-27
Hi

I have a Dell laptop with Vista Home Edition installed.  I also have Ubuntu 8.04 installed.
After speaking with a friend I decided to install 8.10 and was advised to just install it from the CD.  After doing so I now have Vista, 8.04 and 8.10 installed in separate partitions.

Could someone advise the best way to remove 8.04 and then merge the partitions of both Ubuntu versions.

Thanks in advance for your help

Cheers
Dax

---

### Post by Michael.Godawski on 2008-11-27
I would use the Gparted Live CD:


[LIST]
[*][http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
[*]Manual for Gparted: [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
[/LIST]

---

### Post by jakupl on 2008-11-27
yes. Use gparted. If you dont have it installed allready than do:

```
sudo apt-get install gparted
```

to install it. You will find it under System---> Administration --> Partition Editor.

I would just erase the partition with 8.04, then resize the 8.10 partition to full and thats it.

You will probably want to edit /boot/grub/menu.lst also, to remove the 8.04 appearance.

EDIT: oh yeah, forgot that to resize the 8.10 partition, it can't be mounted. So you will have to do this on a live cd.

---

### Post by bhadotia on 2008-11-27
For the below solution to be successful you have to have the two ubuntu partitions side by side on the hard disk.
In Ubuntu 8.10 install Gparted:
```
sudo apt-get install gparted
```
Then using System>Administration>Partition Editor delete the ubuntu 8.04 partition after removing the data that is valuable to you from that partition.

Then boot into a live CD and as above install gparted (if it is not already present in the menu) and launch it. Then merge the deleted Ubuntu 8.04 partition (which is now actually a free space on the HDD) and the Ubuntu 8.10 Partition. This operation may take a very long time and should not be interrupted otherwise you will loose your ubuntu 8.10 installation.

If the two ubuntu partitions are not adjacent on the HDD, then, I suggest you just delete the ubuntu 8.04 partition and merge the resultant free space with any other partition (next to it), if you don't need the extra space for your ubuntu 8.10 partition. For manipulating ntfs partitions through gparted you need to install ntfsprogs:
```
sudo apt-get install ntfsprogs
```

Otherwise (if the two ubuntu partitions are not adjacent on the HDD and you need to merge them for whatever reason) you will have to manually move the free space (generated after deleting ubuntu 8.04 partition) next to the ubuntu and then merge it using the live environment (Live CD).
Good Luck!:popcorn:

EDIT: 
For removing the appearance of the ubuntu 8.04 option from the boot menu edit  the /boot/grub/menu.list file using the following command:
```
gksudo gedit /boot/grub/menu.list
```
The at the end of that file remove the appearances of the ubuntu 8.04 options. [Here]("http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/")is the info needed to edit that file.
Cheers!

---

### Post by dax029 on 2008-11-29
Thanks Michael I ahve Gparted so will check out
Cheers

Dax

---

### Post by dax029 on 2008-11-29
Thanks jakupl

Yes I already removed the entries in my grub file. That was the easy part.
I'm still having a problem trying to delete the partition, basically it' saying that I need to unmount any logical partitions higher then a 5. I'm trying to unmount sda5 which is the partition where 8.04 is installed.  I have tried to unmount the other partition (sda7) but I get the message that it couldn't unmount from the following mainpoints /

So now I'm completely lost.

I have attached some screen shot which hopefully can help you to assist me.

Thanks again in advance

Dax

---

### Post by dax029 on 2008-11-29
Hi bhadotia

Thanks for your detailed response however as in my response to jakupl I'm still having problems.  Hopefully one of you can assist
Thanks again
Cheers
Dax

---

### Post by jakupl on 2008-11-29
> **dax029 said:**
> Thanks jakupl

Yes I already removed the entries in my grub file. That was the easy part.
I'm still having a problem trying to delete the partition, basically it' saying that I need to unmount any logical partitions higher then a 5. I'm trying to unmount sda5 which is the partition where 8.04 is installed.  I have tried to unmount the other partition (sda7) but I get the message that it couldn't unmount from the following mainpoints /

So now I'm completely lost.

I have attached some screen shot which hopefully can help you to assist me.

Thanks again in advance

Dax

Just to be sure, you are using your live cd. Right?

---

### Post by bhadotia on 2008-11-29
> **dax029 said:**
> Hi bhadotia

Thanks for your detailed response however as in my response to jakupl I'm still having problems.  Hopefully one of you can assist
Thanks again
Cheers
Dax

You would have had no problem if you would have read my post carefully.:)
First delete the swap at /dev/sda8 (after unmounting it), delete /dev/sda5 and edit /etc/fstab to use /dev/sda6 as the swap partition. 
Then, boot into a live CD and merge the freed space into /dev/sda7.This process will take a lot of time (possibly evn 8-10 hrs) as you will use live CD, So remain patient and don't even think about touch the ongoing process before its done otherwise you will loose everything.:popcorn:

---

### Post by dax029 on 2008-11-29
Thanks jakupl

I'll give that a try

Cheers
Dax

---

### Post by dax029 on 2008-11-29
Thanks for your response bhadotia, however without offending you can I just say that I was disappointed with your first line in your response "You would have had no problem if you would have read my post carefully."

I DID read your post several times. However as I'm relatively new at Ubuntu am still having some difficulty with some of the terminology used. Don't get me wrong I really do appreciate yours and everyone else's assistance I just don't believe  the tone of your response was warranted.

Having said that I'd still like to thanks you for your assistance and hopefully I can get it all soreted out

Cheers

Dax

---

### Post by Duck2006 on 2008-11-29
[http://wiki.partedmagic.com/index.php/Using_GParted](http://wiki.partedmagic.com/index.php/Using_GParted)

---

### Post by dax029 on 2008-11-29
Hi Duck

Thanks for the quick response and link.  Very formative information

Cheers
Dax

---

### Post by bhadotia on 2008-11-30
> **dax029 said:**
> Thanks for your response bhadotia, however without offending you can I just say that I was disappointed with your first line in your response "You would have had no problem if you would have read my post carefully."

I DID read your post several times. However as I'm relatively new at Ubuntu am still having some difficulty with some of the terminology used. Don't get me wrong I really do appreciate yours and everyone else's assistance I just don't believe  the tone of your response was warranted.

Having said that I'd still like to thanks you for your assistance and hopefully I can get it all soreted out

Cheers

Dax

I used this :) at the end of the first line, meaning I was in a joking mood. You again did not read my post carefully:popcorn:

---

### Post by ugm6hr on 2008-11-30
> **dax029 said:**
> I have attached some screen shot which hopefully can help you to assist me.

I can see that sda7 is mounted as / (root) in your screenshot.

I would strongly advise you to do any partition editing using the Ubuntu LiveCD (which has GParted / Partition Editor pre-installed) rather than your Ubuntu installation on HD.  You should then not get the errors that are causing your problems.

However, I would offer one more point: you may find that your Grub menu is broken following all this partition shuffling.  Be prepared for that - if you do not have another computer to access the internet with, or a LiveCD that allows a connection, you may be on your own with an installation that doesn't boot.

There are ways to resolve that issue, but you may not know how by yourself.

---

### Post by dax029 on 2008-11-30
Thanks for the added information ugm6hr.

Yes I am now using the Live CD. Part of my problem I think was that I was using the 8.40 CD but since have used the 8.10 version and the deleting, resizing of the partitions worked fine.

Yes I have had to go into the Grub menu and change the boot number but I had a backup so that saved any heartache.

I have only been using Ubuntu for a couple of months on my desktop PC which had XP installed so setting it up on the laptop with Vista Home was a real learning experience, but thanks to everyone who has responded it has made the change easier.  I am well and truly a Ubuntu convert......farewell Windoze

Cheers and thanks again

Dax

---

