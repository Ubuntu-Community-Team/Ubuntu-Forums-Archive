---
title: "Adding a hard drive"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2013-05-20
Hi guys
I have a ubuntu server 12.04 running minecraft
I added a plugin that saves backups and now my hard drive is full.

My backups are in /var/www/minecraft/backups

I want to add a hard drive to store the backups separately. I have added a second drive using the virtual media manager.

I'm not sure how to partition the drive though without the partitioning wizard that runs in the installer.

How do I partition the drive and mount it correctly.

I want the backups on one drive and everything else on the other.

---

### Post by Albury_Boy on 2013-05-20
[FONT=arial]Hi [/FONT]**[COLOR=#000000][bigmonmulgrew]("http://ubuntuforums.org/member.php?u=375356"),[/COLOR]**[SIZE=2][FONT=arial]

Is there a special reason for using the virtual media manager? It sounds like you're making it extra hard on yourself. Masochistic much? ;-)[/FONT][/SIZE]

---

### Post by bigmonmulgrew on 2013-05-20
Basically I'm running it on virtual box
I gave it 20GB of space which was plenty.

Now There are backups its filled up almost completely.

I thought it would be easier to create a second hard drive than to reinstall the server on a bigger virtual disc.
Also the virtual HDD is on my SSD and I thought it would be better to put the virtual drive for the backup on my storage drive.

Then I realised I don't know how to partition and mount the drive :(

I'm happy to hear alternate suggestions

---

### Post by Albury_Boy on 2013-05-20
Sorry man :(. I'm not a virtualization expert, I run my server native on 12.04 LTS. Lean and mean. Adding extra drives is 'reasonably' simple for me. Fit it, format it, find the UUID, mount with fstab, fill it up.

I'm guessing (and only guessing) that you are running Oracle Virtual Box within Windows/OSX?? You checked the VM wiki? [https://www.virtualbox.org/manual/ch03.html#settings-storage](https://www.virtualbox.org/manual/ch03.html#settings-storage)

---

### Post by Albury_Boy on 2013-05-20
[FONT=arial][SIZE=2]PS. You might want to re-post this in the [COLOR=#000000]Virtualisation forum instead of the Absolute Beginners . You might get some better help over there.[/COLOR][/SIZE][/FONT]

---

### Post by bigmonmulgrew on 2013-05-20
Well its not a virtualisation question.

I have added the hard drive in the virtual PC settings. As far as the rest of the process goes it should be the same as if I had a real server and added a physical hard drive

Yes I'm using oracle on Windows

---

### Post by Albury_Boy on 2013-05-20
Ok. If it truly works the same as a native install, then this may help. Docs are at [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I run my server head-less from Windows with PuTTY, but I have the gui installed for convenience. When I want a GUI I use Xming to redirect X to my laptop.

gparted is the partition manager I prefer to use in Ubuntu. It's a gui package. It's very intuitive. I haven't broken anything with it yet.
fdisk is the command line only version. I got butterfly's when I've used it in the past.

The docs show how to set partitions, set ownership, and mount at boot. I prefer to mount using UUID rather than by location. After formatting, find the UUID with [FONT=courier new]sudo blkid[FONT=arial] and append it to [FONT=courier new]/etc/fstab[/FONT][/FONT][/FONT][FONT=courier new][FONT=arial]
[/FONT][/FONT]
Good luck.

---

### Post by supremedalek on 2013-05-20
If dmesg or fdisk -l can see the new drive, you are in business. (g)parted or fdisk would be the next tool to use. gparted is convenient since it is a gui and will do the partioning and formatting for you.

---

### Post by bigmonmulgrew on 2013-05-22
ok I installed the xubuntu desktop as I'm familiar with gparted thought it would be best to use a gui

I partitioned the drive using gparted
I then followed the link above on how to mount.

I have now moved my backups to the new drive and now the backups are going onto the new drive.

I then decided to remove the gui. 

tried sudo apt-get remove
xubuntu-desktop
xubuntu*
xcde*
xorg*

but im still getting the logon screen How do i restore the old gui

---

### Post by bigmonmulgrew on 2013-05-22
or rather how do i restore the old cli

---

### Post by Albury_Boy on 2013-05-24
[SIZE=2][FONT=arial][COLOR=#333333]Try this. It looks about right: 

> 
xfce4 itself is a meta-package that will install a default configured xfce desktop environment.[/COLOR] [COLOR=#333333]In most cases the base files that comes with xfce4 are:[/COLOR]
[FONT=courier new][COLOR=#333333]xfconf, xfce4-utils, xfwm4, xfce4-session, thunar, xfdesktop4, exo-utils[/COLOR][/FONT]
[COLOR=#333333]
So you can do[/COLOR]
[FONT=courier new][COLOR=#333333]sudo apt-get purge xfconf xfce4-utils xfwm4 xfce4-session thunar xfdesktop4 exo-utils xfce4-panel xfce4-terminal[/COLOR][/FONT]
[COLOR=#333333]
Then most of the package that were associated with these package become autoremovable so you can run[/COLOR]
[FONT=courier new][COLOR=#333333]sudo apt-get autoremove[/COLOR][/FONT]
[COLOR=#333333]OR[/COLOR]
[COLOR=#333333]Almost all xfce4 package depend upon[FONT=courier new] libxfce4util-common[/FONT]. Just purge that one and you remove everything related to xfce
[/COLOR][COLOR=#333333]

REPOST from [http://askubuntu.com/questions/59640/how-can-i-completely-remove-xfce4-when-apt-get-remove-purge-doesnt-work](http://askubuntu.com/questions/59640/how-can-i-completely-remove-xfce4-when-apt-get-remove-purge-doesnt-work)[/COLOR][/FONT][/SIZE]

---

### Post by lethall1 on 2013-05-24
Hm, as I understood, you have Windows as main os, and Linux as guest os. It's very simple to add disk to guest Linux. You have to download guestos pack from Oracle web site, add to your virtual box, install guest os pack in Linux, add path to your new hdd in preference of virtual machine, and mount it as vboxsf file system. You may add mount command in /etc/init.d/rc.local to mount it automatically. If you have any questions, I will be happy to help. I use vbox on Windows too, because my wife hates Linux :-)

---

