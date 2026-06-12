---
title: "Issues connecting to USB storage on Wireless Router"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by bookabooka on 2013-07-19
Hi

Please can i ask for advice on my issue?

I have a WD N900 Central Wireless Router, this comes with 2tb internal HDD and also has a USB port for connecting storage. 

My issue is that upon setting up the Storage on the router it gives me options for Share(Samba) DLNA, FTP and iTunes to select as attributes, however no matter which one of these I select the storage does not appear in my 'browse network' area, unless i choose an option for afp server. If I select the afp server it will appear in the list to select, ask me for credentials and try connecting. It will however only open up the public folder contained with kaffeine.

I can access it via firefox with [ftp://192.168.1.1/blahblahblah](ftp://192.168.1.1/blahblahblah)...

What am I doing wrong?

---

### Post by TheFu on 2013-07-19
I would expect that access would only be available using the IP address, not by browsing.  I have a WD HD TV Live that shares USB drives on the network. No password needed, only FAT32 (or maybe NTFS) formatted disks work.

That means if you select samba, then you'd access it with \\192.168.1.1\ and browse from there from MS-Windows.  In a Linux world, smb://192.168.1.1/ is what I'd expect. Of course, if your DNS or /etc/hosts file has an IP/hostname cross-ref, then you CAN use the hostname instead of the IP.

I am able to mount the WDTV on Linux with this:
```
mkdir ~/wdtv
sudo mount -t cifs //wdtv/usb-drive /home/thefu/wdtv  -o rw,uid=thefu
```
Clear as mud?

Of course, I don't have the same device that you do, so this stuff might not apply at all. Hopefully the examples will be useful to someone, if not you.

---

### Post by bookabooka on 2013-07-19
Cheers mate, will try that code tomorrow see if it works. Is there a gui for samba mounting?

---

### Post by TheFu on 2013-07-20
> **bookabooka said:**
> Cheers mate, will try that code tomorrow see if it works. Is there a gui for samba mounting?

Don't know. I've never used a GUI for this.  GUIs are just another layer of things to break and hide some of the more powerful options.  Don't fear the CLI/shell.

---

### Post by bookabooka on 2013-07-20
Hi Tried the code but something went awry...

Please see what terminal gave me in return. :)

:~$ sudo mount -t cifs //192.168.1.1/Hitachi_HDS721010DLE630_69/  -o rw,uid=films 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
bookabooka@bookabooka:~$ sudo mount -t cifs //192.168.1.1/Hitachi_HDS721010DLE630_69/  -o rw,uid=films
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by TheFu on 2013-07-20
Looks to me like you didn't tell it where to mount.  It appears only the source dir is listed above - the target is missing.
The trailing / looks funny on the source directory too.   Or did I miss a space somewhere?  The target directory **should** be empty - otherwise all the files unside and under it will be hidden by the mount.

When something like this happens, always check the man page - **man mount** to ensure the command works on your system like it works on other peoples'.  Sometimes commands have differences between versions/distros.

There is also a tool called **smbtree** that will show all the samba/NT shares on a LAN. It is handy to verify that a specific file system is actually being shared. I often forget to share on my Windows laptop - it isn't always powered on, isn't always sharing certain areas that need manual sharing setup after every reboot.  I miss rc.local on windows.

---

### Post by dannyboy79 on 2013-07-20
open nautilus and click on the "Go" menu item, in the drop down choose Location, then type in the IP of your WD drive like this
```
smb://192.168.0.38/
```
and it should appear. let's check that first before we actually mount it locally

---

### Post by bookabooka on 2013-07-20
I knew where nautilus was on 10.10 bit on 12.10 I am having difficulty finding anything. I'm not that happy with 12.10...:(

---

### Post by dannyboy79 on 2013-07-20
if you're using the default Unity, then just simply type in the word Nautilus in the dash.

---

### Post by bookabooka on 2013-07-20
Cheers dannyboy, doing it that way worked a treat. I am confused though why it works that way and not the conventional way. 

How would I go about mounting these or maybe even map them as a network drive much like windows (blasphemy) does? f

---

### Post by bookabooka on 2013-08-06
Update...

I can get into the file system of the hdd via nautilus and open folders and click on files, however when I try to open one up it fails to load on my machine.

Is this because the drive is not mounted? How can I mount the drive using the ip address?

Please let me know as its annoying me now.

---

### Post by TheFu on 2013-08-06
> **bookabooka said:**
> Update...

I can get into the file system of the hdd via nautilus and open folders and click on files, however when I try to open one up it fails to load on my machine.

Is this because the drive is not mounted? How can I mount the drive using the ip address?

Please let me know as its annoying me now.

See post #2. Be certain to get all the arguments correct - I vaguely recall you tried this previously, but left off some options/arguments.

---

### Post by kurt18947 on 2013-08-06
I recently got a WD N600.  I'm brand new to many aspects of networking.  I did find Filezilla works perfectly for FTP access.  I tried two different configurations.  One was to turn off DHCP on the WD and reassign the I.P. address to 192.168.1.x  where x= something other than 1.  The WD was connected LAN port to LAN port to an Actiontec router which is upstream from the WD and handles DHCP chores.  One flaw with this configuration is the WD router doesn't recognize that it has an internet connection so time synchronization doesn't work, can't upgrade firmware via the network connection etc.  When I try to connect via Nautilus (I'm running 13.10 on this machine) I  can see the USB flash drive in the WD router's USB port.  When I click on the USB drive though,  I get the following message:

**The link &#8220;SanDisk_Cruzer_Blade_30&#8221; is broken. Move it to Trash?**

This link cannot be used because its target &#8220;/var/tmp/storage/SanDisk_Cruzer_Blade_30&#8221; doesn't exist.

I also tried making the WD router 192.168.x.1 and activating DHCP.  I moved the cable from the Actiontec from the LAN port to the WAN port of the WD router.  The WD router then recognized it had an internet connection and for whatever reason the FTP server was recognized by and worked with Nautilus.  I think this configuration is double NAT, I was having problems printing to a networked printer on the other subnet for instance.  Within the same subnet things worked very well though.  The error message above does not appear using Nautilus, I can see files and move them between machines.  Why Nautilus works perfectly in the 'double NAT' configuration but not in the all-on-one-subnet configuration is a question.  

Short version, you're not alone with navigating via Nautilus on a WD router.  I tried accessing via smb://etc. etc. very briefly but the networked drive wasn't even recognized and I only spent a couple minutes on that.  Still curious that one probably unwise configuration Nautilus worked but doesn't behave when all devices are on one subnet. (Apologies if my terminology is incorrect)

---

