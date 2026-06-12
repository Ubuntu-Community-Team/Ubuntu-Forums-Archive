---
title: "Small snag setting up my first ubuntu server NAS box."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by CrabFu on 2008-11-26
Hello all. I've been a casual ubuntu user for the past year or so. Only using it for home computing. Tunderbird, Openoffice, Gimp and so on.

I've been in the need for some extra storage at home and in my small office at work. Using work as my Guinna pig of course. 

Currently the system stands as such.
Asus M2N-SE motherboard
generic network card
1x 80GB IDE disk (holding the OS on it
2x 1TB SATA Toshiba disks (Aiming for a Mirrored raid)

Since most walk-through guides either just showed you how to install ubuntu onto a raid durring OS install. (Which for some reason my live CD did not give me that partition option at install) I've been using two guides to lead my way.

[http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)
&
[http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

Now my setback comes as such. 

Following the guide to setup the software raid. I have gotten to the point of 
$ watch cat /proc/mdstat 
The disks are synced but they are not formated.
$ mkfs -t reiserfs /dev/md0
works but when I fdisk -l I'm greeted with
" Disk /dev/sdb doesn't contain a valid partition table" 
The same for the 2nd 1tb drive in the raid.

I DO have Gnome installed, under my "Computer - File Browser" it does show 1000.2 GB media but it will not let me mount it. I'm assuming this is because of the missing partition table? 

None of my utilitys list my raid "md0" for partitioning/formatting. Am I just missing the proper tool?

I'm sure I haven't provided enough information. I'll be keeping a sharp watch on this thread. Any help is highly appreciated. And I will reply with any information you need in a timely fashion. Thank you all for your time.

---

### Post by cozmicharlie on 2008-11-26
Your close.  Sounds like you have not created your partitions.  Is there a particular reason you are using reiserfs?  Also,what version of ubuntu are you using?  The easiest way to partition disks (I say easy because most people find graphical interface easier than command line) is to use the partition editor - menu>system>>administration>partition editor.  Create the partitions and format the disks in partition editor.  Under manage flags use Raid.  You will need to unmount the disks first.  Then once you have them partitioned correctly, mount them and continue with setting up software raid under mdadm.  If you get stuck post back.

---

### Post by CrabFu on 2008-11-26
Thanks for your quick reply. For version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

I don't have a partition editor in any of my system tabs. Is there an apt-get command to add the utility? 

Only reason I was using reiserfs is because I don't know many Linux tools yet and it was in the tutorial. I have no loyalty to it lol. I was doing most of the work through PuTTY on another pc in my network. Now I have it setup and I'm working through Terminal and the GUI.

---

### Post by cozmicharlie on 2008-11-26
Go into synaptic and install partition editor.  Reiser is OK but the developer is actually in jail (a long story) and I am not sure if he is maintaining it anymore.  The standard file system in Ubuntu is ext3 so I would recommend that.

---

### Post by cozmicharlie on 2008-11-26
Also, I would recommend Tunnelier ([http://www.bitvise.com/tunnelier](http://www.bitvise.com/tunnelier)) or winscp ([http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)) over Putty - much easier.  But, if you have putty set up you may want to stick with it.  Don't fix what isn't broke is my motto.

---

### Post by CrabFu on 2008-11-26
thanks again, I should have checked synaptic first lol.

I knew the standard format is ext3, but this file storage will be holding mostly auto cad files for use between 2-3  pc's on a windows network.  Both XP boxes. 

Will there be a problem with them accessing files on that type or should I consider NTFS?

Edit: I installed GParted, it gave me 6 results for "Partition Editor" It shows both of my drives independantly, not as one raid pool, Should I partition them independently? will I have to re sync the disks?

---

### Post by cozmicharlie on 2008-11-26
OK - reiser is supposed to be better for large files.  Do you need to have direct access in Windows?  Or, will you be accessing the Raid files via Putty or Samba.  If you are accessing through Samba or Putty it does not matter - if you need direct access from Windows then you will need a Windows compatible file system (NTFS).  There is a work around to get ext3 on Windows by using a virtual disk but I do not remember the name of the program that does this - google should help.

---

### Post by CrabFu on 2008-12-02
ok I'm sorry to bump this back to the top again but I keep running into setbacks every time I try to salvage this.

Having stated the process i've gone through I'm not sure of the command lines to go back and delete my RAID so I can start over again.

G-partition shows each disc individually and will not let me format them. 

Can someone point me in the direction of what I'm looking for or tell me how to just erase what I've done already so I can start from scratch. Most of my problem is that I just don't know what administration utilitys exist for ubuntu, which are good and which are a hastle. 

Thank you for your time.

---

### Post by cozmicharlie on 2008-12-02
If you want to reformat then the easiest way to do it is use gparted. It shows them, but won't let you format because they are mounted.  Follow these steps.

[LIST=1]
[*]Unmount the disks (just right click on the disks and unmount)
[*]Go to gparted and reformat the disks.  
[*]Reformat to ext3 (or whatever format you want).  Also, set them up as primary partitions.  They do not need to be bootable unless you are putting an operating system on them.
[*]After you have the disks partitioned then use mdadm to set up raid.  It is command line but it is fairly easy
[/LIST].

If you need help with mdadm post back.

---

