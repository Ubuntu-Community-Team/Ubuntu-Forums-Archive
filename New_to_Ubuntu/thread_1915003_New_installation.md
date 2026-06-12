---
title: "New installation"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by KatyWood on 2012-01-25
Hello everyone
I have a PC with four hard drives, one has Windows Vista installed, another has Windows 7 and the other two are empty. I want to install Ubuntu on one of the empty drives but I do not know how to do this.
Can anyone help please?
Thanks

---

### Post by sanderd17 on 2012-01-25
You go to here: [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Download the Ubuntu iso (CD image) and follow the steps mentioned

when something is not clear, just ask.

Do test Ubuntu with your hardware before you install it.

---

### Post by raja.genupula on 2012-01-25
Hi Sander , Hope you're doing good . 

+1 to above post and look at this link .It have installation process with Images .I hope it will gives idea regarding installation .

[http://blog.sudobits.com/2011/09/11/how-to-install-ubuntu-11-10-from-usb-drive-or-cd/](http://blog.sudobits.com/2011/09/11/how-to-install-ubuntu-11-10-from-usb-drive-or-cd/)

All the best.

---

### Post by KatyWood on 2012-01-25
Thanks for that.
I'm still confused, does Ubuntu have to create a new partition even if I want to use the whole of the harddrive? I don't understand all the options when I click on Something Else during installation.

---

### Post by oldfred on 2012-01-25
With multiple drives, I always suggest a complete stand alone install. That means the grub2 boot loader will also be on the same drive and that drive can boot without all others. Some suggest disconnecting all the other drives and that is the absolute safest way. The other alternative is to use manual install. All the auto install options will install the grub2 boot loader to sda which is not usually what you want. You can reinstall boot loader(s) afterward if necessary.

Also if drives are large you want a smaller / (root) partition and let /home be the larger partition.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by KatyWood on 2012-01-25
Thank you for all your help.
Another question please, my processor is 64bit compatible, yet the download options recommend 32bit Ubuntu. Why is this?

---

### Post by oldfred on 2012-01-25
There must now be a 1000 threads with this question in recurring discussions, if interested do a search for any of them. 

Use 64 bit if hardware is 64 bit. Recommendation primarily is for those who do not know and then they may have 32 bit hardware.

---

