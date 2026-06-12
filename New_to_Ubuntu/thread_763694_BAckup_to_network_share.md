---
title: "BAckup to network share"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by EllisF on 2008-04-23
I am running Ubuntu linux on one of my machines on my network. On my network I also have a NAS drive and a Windows Home Server on my network. I have managed to map and create an icon on my desktop that gets me to these network devices. I used SMBA. Anyway what I would like to do and have not figured it out as of yet is to find a program or a script that will allow me to back up my linux machines automatically first as a complete backup then regular automatic differential or incrmental backups. I want to be able to direct this back up to either my Windows Home Server or my NAS. Any suggestions or instructions? Thanks.

---

### Post by mikeyphi on 2008-04-23
> **EllisF said:**
> I am running Ubuntu linux on one of my machines on my network. On my network I also have a NAS drive and a Windows Home Server on my network. I have managed to map and create an icon on my desktop that gets me to these network devices. I used SMBA. Anyway what I would like to do and have not figured it out as of yet is to find a program or a script that will allow me to back up my linux machines automatically first as a complete backup then regular automatic differential or incrmental backups. I want to be able to direct this back up to either my Windows Home Server or my NAS. Any suggestions or instructions? Thanks.

Hi there and welcome!
Have a look at Simple backup - available through Add/Remove
I use it to do exactly what you require.

---

### Post by EllisF on 2008-04-23
I beleive I am using that backup currently but letting it backup to its default location on the system hard drive. I have tried the option that allows for remote drive but I apparently have not been able to enter the path right or something right as when I test test it it does not pass the test. Maybe I am entering it wrong. I have entered it like samba://username:password@servername/folder. That is how I mapped the drive and it works but does not appear to work in simplebackup. Thanks.

---

### Post by mlentink on 2008-04-23
I had that problem as well. So what I did was mount the backup folder on the nas as a smb-mount (search for mount smbfs and you'll find out how) and use that. Works like a breeze, completely automagical.

---

### Post by EllisF on 2008-04-24
Well I enter terminal  then at the prompt I enter vi /etc/fstab and the file opens. I add this line:  //ntserver/docs /mnt/samba smbfs username=docsadm,password=D1Y4x9sw 0 0

I then enter :w and it comes back with add ! so I enter :w! and it will not overwrite the file. I am logged on as the only user account this computer has. I am guessing I need to log on as a super user or something but i have never been able to figure out how to log on to Ubuntu any other way. Thanks!

---

### Post by Paqman on 2008-04-24
Ubuntu uses the command sudo to temporarily take on super user rights.

Just prefix commands with it, for example "sudo vi /etc/fstab" would run vi to edit fstab as a super user.

---

### Post by EllisF on 2008-04-26
Ok I entered the vi editor as a super user and added the above line including the username= and pasword= but of course after the equal signs I used my user name for my Windows Home Server and my Window Hoem Server Passowrd. Also for the for the share I entered //my server name/the directory I wanted shared. I saved the new /etc/fstab file and rebooted. How do I verify it automounted as I see no signs that it did? Now getting back to simple back up do I select remote backup as destination and if so what do I put there? Thanks for the hand holding.

---

### Post by krisfrajer on 2008-04-26
if you type on the command prompt
df
you should see what units are currently mounted on your machine.
I am not an expert using sbackup but if you have your unit mounted already then on "backup destination" you just have to select the mounting point of your unit where you want to store your backup. Tha is the first thing I would try. It would be helpful to see your /etc/fstab file content... can you post it?
K.

---

### Post by EllisF on 2008-04-26
I hope this comes out okay I was not quite sure how to get it on the forum in a slightly edited format for privacy so I used vi to edit it then upload it to my server were I was able to open it in windows notepad and copy and paste to the forum. the * are for privacy in the last line. Thanks. By the way df did not list anything like the last line.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a3fb5d84-86aa-499b-9c6e-c639927b82ef /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=a85e6467-ce00-4add-b2ba-3176052b549a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
//C******/Public/mnt/samba smbfs username=E******,password=***** 0 0

---

