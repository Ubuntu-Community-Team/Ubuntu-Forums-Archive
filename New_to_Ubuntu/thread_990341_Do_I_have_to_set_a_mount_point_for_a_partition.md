---
title: "Do I have to set a mount point for a partition?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2008-11-22
I am currently installing Kubuntu 8.10 on a machine I intend to be a file server.  It has two HDDs, 160GB and 500GB.  I was partitioning the primary drive as:
2 GB swap
20 GB /
138 GB /home

I wanted to format the second drive and leave it open to be shared across a mixed windows/linux network, and storing music to be streamed, etc.  During the installation, Kubuntu is warning me that this drive "will not be used" if I don't set a mount point.

What are the ramifications of not setting a mount point?  Can't I just mount it later?

Thanks!

~Nix

---

### Post by taurus on 2008-11-22
You don't have to set a mount point for the second drive during the installing process if you don't want to.  You can still mount it later by adding an entry in /etc/fstab.

And for / and /home, you want to mount those during the installing.

---

### Post by m_duck on 2008-11-22
Yeah, when you're installing and choose not to use it, it just won't be mounted when you first start using Kubuntu. You can always set the mount point after you have installed by editing /etc/fstab.

---

### Post by Nixie Pixel on 2008-11-22
Ok, thank you very much - I have it installed and running now.

However I have a couple of issues.  First, how do I propery add the unmounted drive to /etc/fstab?

Second, I seem to be having trouble with the second drive.  It is missing about 70GB when I check its properties, it has something called Lost & Found on it (is this normal?), and I can't seem to copy any data over to it - it tells me that access is denied.  

Will those be solved if I get it properly located in the /etc/fstab file?

Thank you!

~Nix

---

### Post by Moop on 2008-11-22
I think this is what you're looking for. [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by m_duck on 2008-11-22
Was it a blank disk to start with or is it one you have been using before and just want mounted in kubuntu to access files? If there is nothing you want keeping on it, you could use gparted to repartition and format it which will hopefully sort out the missing space. Other than that I'm not sure with that issue.

As for mounting it, what file system is on it?

You'll need to make a folder to mount it in, (usually in /media or /mnt). E.g. from a terminal:```
sudo mkdir /media/foldername
```Then to edit fstab, type the following in konsole:
```
kdesu kate /etc/fstab
```This will bring up fstab in the kate text editor. Then you'll need to add a line to the bottom to mount your drive.

You can find the drive link by doing (in konsole):
```
sudo fdisk -l
```This will bring up details of the disks in your computer, along with their filesystem type. Find the "/dev/*something*" of the disk you want to mount so it can be added to fstab.

For example, my "media" partition is at /dev/sdc1 with filesystem of ntfs and I mount it in /media/Media, so the following line is in my /etc/fstab:
```
/dev/sdc1     /media/Media     ntfs-3g     defaults     0     0
```"Defaults" just sets the default permissions for the directory, which lets my username read/write etc from the disk. The two 0's do something that I'm not sure about, some sort of checks or something.

Then, save and exit kate, and type:```
sudo mount -a
``` into konsole, and with some luck that shud mount the disk to your mount point.

Hope that makes some sort of vague sense!

There's also a thread [here]("http://ubuntuforums.org/showthread.php?t=283131") with fstab related stuff.

---

### Post by Nixie Pixel on 2008-11-22
Hi, the disk was running NTFS, 500GB capacity, about 260GB full.  I copied the 260GB of data onto an external hard drive and during the Kubuntu install process deleted the partition and created a new one, formatted with ext3.  

I plan on using Samba to share it with the rest of my little network.

It probably won't let me copy data at the moment because the drive is not mounted, but I was able to see it in Dolphin (so I am not sure how to know positively one way or the other in this interface?).  I am concerned that I somehow lost 60-80GB of capacity.

I didn't think gparted was a part of KDE/Kubuntu?  I would be happy to use it, I am more comfortable working with a GUI than I am bash...

Using fdisk I see /dev/sb1, a 500.1 GB hard disk.  So its full capacity is recognized, but in Dolphin it isn't.  gparted would do the trick to tell what is what.

Thanks again!

~Nix

---

### Post by Nixie Pixel on 2008-11-22
So after installing and running gparted, it appears that my 500GB hard drive is showing up there as having a size of 465.76 GB, with 7.5 GB used.  Any ideas about why it lost 35 GB, and what might be taking up 7.5 GB of disk space, on a newly partitioned 500 GB hard drive?

(or should I be asking this elsewhere, like in Hardware?)

Thanks!

---

### Post by Moop on 2008-11-22
The 465gb sounds right for a 500gb hdd. It's all in the way bytes are calculated or something like that. I'm not sure about the 7.5gb used. Try showing hidden files (ctrl-h) and see if anything is there. Empty the trash?

---

### Post by apothecaryaaron on 2008-11-22
> **Moop said:**
> The 465gb sounds right for a 500gb hdd. It's all in the way bytes are calculated or something like that.
 
I think it goes like this:
1. Manufacturers use the conversion that 1 kb = 1000 bytes, 1 mb = 1000 kb, 1 gb = 1000 mb. 
2. Traditional (and technically more correct) methods work so that 1 kb = 1024 bytes, 1 mb = 1024 kb, 1gb = 1024 mb.
 
Gparted and the like use #2.  On a 500 Gb drive, that adds up.

---

### Post by crazyness003 on 2008-11-23
> **apothecaryaaron said:**
> I think it goes like this:
1. Manufacturers use the conversion that 1 kb = 1000 bytes, 1 mb = 1000 kb, 1 gb = 1000 mb. 
2. Traditional (and technically more correct) methods work so that 1 kb = 1024 bytes, 1 mb = 1024 kb, 1gb = 1024 mb.
 
Gparted and the like use #2.  On a 500 Gb drive, that adds up.
you have a point

"500 GBytes"[COLOR=Gray] [/COLOR][COLOR=Gray]*NOT EQUAL TO* [/COLOR]500,105,991,946 Bytes
465.76 GBytes[COLOR=Gray] *EQUALS* [/COLOR] 500,105,991,946 Bytes
(my drive is "500GB")
if you count by tens or 1 gb = 1,000,000,000 b
in binary 1 gb = 1,073,741,824 b

hence the 'lost' 35gb. 
Plus, its a marketing ploy. 500 sounds better than 465.76

---

### Post by Nixie Pixel on 2008-11-23
Hi, I successfully mounted the drive in /media/storage - thank you!

The only thing on this drive is something called "lost & found," nothing else hidden.  Unfortunately when I open up lost & found I am told that I don't have the permissions to view this folder.

I tried using chown as suggested in the tutorial posted above, but it didn't help.  Might I have done this incorrectly?  When I created /media/storage, wasn't I set as the owner?  If so, what was the point of doing these:

sudo chown -R nixie:nixie /media/storage

sudo chown -R 755 /media/storage

Thank you again!

---

### Post by crazyness003 on 2008-11-23
> **Nixie Pixel said:**
> Hi, I successfully mounted the drive in /media/storage - thank you!

The only thing on this drive is something called "lost & found," nothing else hidden.  Unfortunately when I open up lost & found I am told that I don't have the permissions to view this folder.

I tried using chown as suggested in the tutorial posted above, but it didn't help.  Might I have done this incorrectly?  When I created /media/storage, wasn't I set as the owner?  If so, what was the point of doing these:

sudo chown -R nixie:nixie /media/storage

sudo chown -R 755 /media/storage

Thank you again!
it may be that the 'lost $ found' folder is some sort of system file. Im not to sure about how ext3 handles stuff. But you may be able to view its contents by issuing this
```
kdesu *filemanager*
```
filemanager is whatever you use to view files (i use gnome, so mine is nautilus. i think kde uses konqueror or dolphin or somehting), then navigate to your mounted drive and check out whats in the folder. 
To be honest, i think you'll find nothing tho.
The important thing is that you can read/write to the drive, successfully.

Then start worrying about sharing with samba (which im having a problem as of yesterday :) )

---

### Post by Moop on 2008-11-23
Lost and found is the trash. Use gksudo nautilus to browse and empty the trash. It's probably left over trash that you don't have permission to delete. gksudo nautllus will give you the permission.

---

### Post by crazyness003 on 2008-11-23
> **Moop said:**
> Lost and found is the trash. Use gksudo nautilus to browse and empty the trash. It's probably left over trash that you don't have permission to delete. gksudo nautllus will give you the permission.
she's using KDE

kdesu 'whatever the dafault KDE WM' will do the trick

---

### Post by Nixie Pixel on 2008-11-23
Ok, thank you!

I cannot currently write to the drive - I tried copying a directory over and was told "you do not have permissions to create <foldername>."  

So my chown didn't work...did I not do chown correctly?

I want to be able to make/delete files/folders there at will, as well as give the network the ability to do this through samba.

---

### Post by lswb on 2008-11-23
The lost+found directory is created when an ext2 or ext3 filesystem is first created and by default is rwx for root only. You'll normally find one in the root of every ext2 or ext3 partition or filesystem. 

If there is a filesystem error, when fsck runs it will store any data it otherwise cannot handle in files in the lost+found directory. It is not related to the operation of .trash or .local/share/Trash.

---

### Post by crazyness003 on 2008-11-23
> **Nixie Pixel said:**
> Ok, thank you!

I cannot currently write to the drive - I tried copying a directory over and was told "you do not have permissions to create <foldername>."  

So my chown didn't work...did I not do chown correctly?

I want to be able to make/delete files/folders there at will, as well as give the network the ability to do this through samba.
can you copy over as root?

---

### Post by lswb on 2008-11-23
> **Nixie Pixel said:**
> 

sudo chown -R nixie:nixie /media/storage

sudo chown -R 755 /media/storage



That second command should be chmod, not chown. Issue both commands after the partition is mounted

---

### Post by Nixie Pixel on 2008-11-24
Thanks, the chmod error was the problem.  I wish there was a Linux/Ubuntu for Dummies (me) type web site out there, maybe I could avoid making newbie mistakes like this...

Now I am trying to configure Samba to allow anyone to connect to the drive.  I tried using the "Sharing Options" shell extension in (I believe) nautilis to create a share, and enable it for all users, but XP keeps whining that "windows is unable to log you on" when I attempt to connect to the share.  (It wants a username/password with domain name, i.e. ADAMO/Nixie even though I'm running a workgroup, not a domain, and if I enter nixie and then the password it still doesn't work).

So now I am stuck trying to work with smb.conf.  Why can't these darn Linux developers make nice GUIs with all the options so we don't have to work with configuration files??  =D

Any idea what options I need to change in smb.conf to get this working?  I had security = user commented (#) out, so that didn't help.  Perhaps it has to do with map guest = bad user?  Even though I am not trying to connect as a guest...(though in a perfect world I wouldn't have to authenticate at all, I could choose to share a particular directory/mount point without requiring additional authentication at any time)

Thank you yet again!

~Nix

---

### Post by crazyness003 on 2008-11-24
> **Nixie Pixel said:**
> Thanks, the chmod error was the problem.  I wish there was a Linux/Ubuntu for Dummies (me) type web site out there, maybe I could avoid making newbie mistakes like this...

Now I am trying to configure Samba to allow anyone to connect to the drive.  I tried using the "Sharing Options" shell extension in (I believe) nautilis to create a share, and enable it for all users, but XP keeps whining that "windows is unable to log you on" when I attempt to connect to the share.  (It wants a username/password with domain name, i.e. ADAMO/Nixie even though I'm running a workgroup, not a domain, and if I enter nixie and then the password it still doesn't work).

So now I am stuck trying to work with smb.conf.  Why can't these darn Linux developers make nice GUIs with all the options so we don't have to work with configuration files??  =D

Any idea what options I need to change in smb.conf to get this working?  I had security = user commented (#) out, so that didn't help.  Perhaps it has to do with map guest = bad user?  Even though I am not trying to connect as a guest...(though in a perfect world I wouldn't have to authenticate at all, I could choose to share a particular directory/mount point without requiring additional authentication at any time)

Thank you yet again!

~Nix
heres a nice gui for you (**very simple**)
"Samba Server Configuration Tool 1.2.63"
to get it, use synaptic, and search for "system-config-samba"
OR
type this in the terminal
```
sudo apt-get install system-config-samba
```Another one (**not so simple**; many, tweakable features) is the 'GADMIN-SAMBA' tool [COLOR=Red][DESIGNED FOR GTK+...gnome][/COLOR]
Synaptic, search for gadmin-samba. Once you find it, and try to install it, it will ask you to install the entire suite (GAMIN-TOOLS).
OR
in terminal
```
sudo apt-get install gadmin-tools
```This will install the whole suite, but all's you need it the SAMBA tool.

But if you're using KDE, im not sure if you'd have nautilus-share (im still assuming you're using KDE, since your OP stated Kubuntu)

Id try the simple one first. It basically has enough options to get you to do some file/printer sharing almost immediately.
Anyway, i hope this helped.

---

### Post by mngsailing on 2009-10-29
When moving to Prepare Disk Space, and 9.04 remix finds "This computer has Ubuntu 9.04 on it"
why is there no option to replace the existing 9.04 (which has become corrupted) with a new one 
in the same location?

Also, How is that little white slider supposed to work?   It is in sda3, and will not move to sda4.
When I select that option, (or anything other than having two Ubuntus), such as to specify manually, 
the white slider disappears!

---

