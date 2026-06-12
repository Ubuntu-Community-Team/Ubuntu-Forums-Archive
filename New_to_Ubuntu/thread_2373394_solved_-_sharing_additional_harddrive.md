---
title: "solved - sharing additional harddrive"
date: 2017-10-05
forum: New to Ubuntu
---

### Post by elron42 on 2017-10-05
Hello Everyone,

Appreciate any help with this.

Background
I've just installed ubuntu 17** on a machine. The purpose is to play movies / tv shows but also as a backup for house files. To this end it has a ssd (operating system) and two 4gig hdd for the backup purpose. The machines that will be backing up files to it are windows 10. I've fiddled and fiddle and can't get the drives to successfully share on my network.

It occurred to me that I am probably unclear on the steps I have to go through to succesfully share drives.

Steps so far:
1. Install samba
2. Check drives are automounting at startup
3. created a folder in the hd called "backups"
4. rightclick - local network share - tick all boxes - create share

Problems:

1. Windows 10 is refused connection when I try to access the drives
2. Share disappears when I reboot

What other steps do i need to insert into the proceedure? 

Appreciate any assistance,

E

---

### Post by Autodave on 2017-10-05
What format are the storage drives? Did you turn *fast boot *off in the bios?

---

### Post by elron42 on 2017-10-05
Hi Autodave,

They are formatted as NTFS and I do not have fast boot turned on

---

### Post by leunam12 on 2017-10-06
I always use the ip address to get to my shared directory, it has never failed.

In Windows open a window and type \\<ip_adress>\ on the address bar and press enter. It is a good idea to give your computer acting as the server a fixed ip address.

---

### Post by cariboo on 2017-10-06
As far as I'm concerned, your are taking a huge risk running NTFS drives on a linux server, if one of the drives gets corrupted, there are no guarantees that the drive can be repaired. I'd suggest formatting the drives to ext4 as Windows in this case won't care how the backup drives are formatted.

---

### Post by gordintoronto on 2017-10-06
Cariboo +1. Leunam12 +1.

Mount the drives in fstab, you use blkid to get a drive's id.

---

### Post by Morbius1 on 2017-10-06
>  2. Check drives are automounting at startup
Please post the output of the following command:
```
cat /etc/fstab
```
>  4. rightclick - local network share - tick all boxes - create share
Please post the output of this command so we can see how that share is configured:
```
net usershare info --long
```
Come to think of it post the output of this one as well so we can see how samba itself is set up:
```
testparm -s
```
>  2. Share disappears when I reboot
After a reboot run this command again:
```
net usershare info --long
```
If you still get an output that shows you how the share is configured then it didn't disappear. What may be happening is that the share emblem is missing from the folder. This happens from time to time depending on humidity levels, sun spot activity, and a lot of other things ....

If you mean the share disappears from Win10 after a reboot do yourself a favour:

** Either set this up with a static ip address and connect to it that way from Win10.

** Or use mDNS:

Run this command in Linux:
```
hostname
```
Let's say the output is **thisherepc**.

In Win10 open the file manager and enter this address:
```
\\thisherepc.local
```
Don't forget the ".local" at the end.

---

### Post by elron42 on 2017-10-07
Hi Nirbius1 and Others,

Thank you for the reply. I reinstalled as I think i stuffed it up with all my fiddling. Version is now 16.04 mate. All other factors are the same. I was able to logon from another linux machine but still not fro a windows 10 one. Here is the information as requested:

> **Morbius1 said:**
> Please post the output of the following command:
```
cat /etc/fstab
```


```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a4b021cd-ffb8-41dd-b03c-5cd268979735 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eb4ad0d5-06d1-4e17-81b1-d1dd9ee8d236 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
> Please post the output of this command so we can see how that share is congured:
```
net usershare info --long
```

```
info_fn: file /var/lib/samba/usershares/archive2 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/archive is not a well formed usershare file.
info_fn: Error was Path is not a directory.
```
> Come to think of it post the output of this one as well so we can see how samba itself is set up:
```
testparm -s
```
```
oad smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE


# Global parameters
[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb




[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No




[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
```
> After a reboot run this command again:
```
net usershare info --long
```
If you still get an output that shows you how the share is configured then it didn't disappear. What may be happening is that the share emblem is missing from the folder. This happens from time to time depending on humidity levels, sun spot activity, and a lot of other things ....
```
info_fn: file /var/lib/samba/usershares/archive2 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/archive is not a well formed usershare file.
info_fn: Error was Path is not a directory.
```
> If you mean the share disappears from Win10 after a reboot do yourself a favour:

** Either set this up with a static ip address and connect to it that way from Win10.

** Or use mDNS:

Run this command in Linux:
```
hostname
```
Let's say the output is **thisherepc**.

In Win10 open the file manager and enter this address:
```
\\thisherepc.local
```
Don't forget the ".local" at the end.


Got this:

[COLOR=#646464][FONT=&quot][h=1]Your file was not found[/h]It may have been moved or deleted.
ERR_FILE_NOT_FOUND



[/FONT][/COLOR]

---

### Post by Morbius1 on 2017-10-08
You've got nothing set up. The problem now is that it's been a day since you made that post and we have no idea what you have done since. All I can do is show you how I would have done this. 

I'm starting from a LiveDVD session of Ubuntu-Mate 16.04 so I'm doing all this without the OS even being installed:

[1] Install Samba:
```
sudo apt install samba
```
[2] Auto Mount an ntfs partition:

** Run this command to find the UUID number of my ntfs partition:
```
sudo blkid -c /dev/null
```
** Create a mount point for the partition to live:
```
sudo mkdir /media/Data
```
** Add this line to the end of /etc/fstab:
```
UUID=40F76A4E40B0C5CB /media/Data ntfs defaults,nls=utf8,uid=999,windows_names 0 0
```
** Ran this command to mount it:
```
sudo mount -a
```
** Created a subfolder archive:
```
sudo mkdir /media/Data/archive
```
[3] Edit /etc/samba/smb.conf and add this to the end of it:
```
[archive]
path = /media/Data/archive
read only = no
guest ok = yes
force user = ubuntu-mate
```
[4] Check to see what my host name was
```
hostname
```

Went to my Win10 machine

** Opened run ( WinKey + R ) and entered that address: \\ubuntu-mate.local

Add this is were I'm at now on Win10:
[ATTACH=CONFIG]277033[/ATTACH]

---

### Post by elron42 on 2017-10-12
[QUOTE=Morbius1;13695613]You've got nothing set up. The problem now is that it's been a day since you made that post and we have no idea what you have done since. All I can do is show you how I would have done this. 


Hi Morbius,

Sorry about the late reply. The reinstall setup was the outputs I posted above that you asked for. Apologies if i've made you job helping me harder. I'm a total noob at this but i like linux and want to improve my knowledge of it.
I've been away so have just sat down with the computer again.

Question: Cariboo posted above that I was taking a huge risk formatting to ntfs on a linux system. he suggested ext4 instead. Is this correct? If so, could you amend your instructions for drives formatted to ext4.

As always,

I apreciate any help you and the community have given me.

E

---

### Post by Morbius1 on 2017-10-12
> Question: Cariboo posted above that I was taking a huge risk formatting  to ntfs on a linux system. he suggested ext4 instead. Is this correct?  If so, could you amend your instructions for drives formatted to ext4.
I am not a penguinista so to me NTFS is just another file system. If you ask a senior System Administrator in a Fortune 500 company about ext4 he will tell you that he still considers it experimental so everything is relative.

Anyhoo, the way I created the share definition I anticipated that you might change your mind and move to a Linux filesystem since the "force user" is irrelevant when using an NTFS partition. The changes you would have to make to my previous post are:
> ** [COLOR=#0000cd]Add this line to the end of /etc/fstab:[/COLOR]
```
UUID=9a5e5f04-efae-4e10-a323-9bb8ffb1d179 /media/Data ext4 defaults,noatime 0 2
```
** Ran this command to mount it:
```
sudo mount -a
```
[COLOR=#0000cd]** Take possession of the mounted partition:[/COLOR]
```
sudo chown ubuntu-mate /media/Data
```
[I][COLOR=#0000cd]"ubuntu-mate" here would be replaced by your own user name.[/COLOR]
[/I]
[COLOR=#0000cd]** Created a subfolder archive:[/COLOR]
```
mkdir /media/Data/archive
```

---

### Post by elron42 on 2017-10-15
Hi Morbius 1

I followed the steps and I can see and browse to the directory. I can't write to it unfortunately. I know i have not set the permissions correctly somewhere. Here is a copy of what i did using your instructions:

[1] Install Samba:
Code:
sudo apt-get install samba

[2] Auto Mount an ext4 partition:
 
** Run this command to find the UUID number of my ntfs partition:
Code:
sudo blkid -c /dev/null
** Create a mount point for the partition to live:
Code:
sudo mkdir /media/Data
** Add this line to the end of
sudo pluma /etc/fstab
Code:
UUID=d809eaf8-b442-4885-9d1f-889251e30bd9 /media/Data ext4 defaults,noatime 0 2
 
** Ran this command to mount it:
Code:
sudo mount -a
sudo chown ian /media/Data
 
** Created a subfolder archive:
Code:
sudo mkdir /media/Data/archive
[3] Edit
sudo pluma /etc/samba/smb.conf
and add this to the end of it:
Code:
[archive]
path = /media/Data/archive
read only = no
guest ok = yes
force user = ian
[4] Check to see what my host name was
Code:
hostname

hostname is mozart

---

### Post by Morbius1 on 2017-10-16
You changed ownership of the mount point from root you ian:
> sudo chown ian /media/Data
But you created the subfolder as root which made the owner root:
> [COLOR=#0000cd]**sudo**[/COLOR] mkdir /media/Data/archive

In my last post I changed ownership of the mount point with sudo but created the subfolder as me which made the owner me:
> [COLOR=#0000cd]** Created a subfolder archive:[/COLOR]
```
mkdir /media/Data/archive 


```

Just change ownership of the subfolder to ian:
```
sudo chown ian /media/Data/archive
```

---

### Post by elron42 on 2017-10-19
Thank you so much Morbius1. That solved it. I really appreciate all the help you gave me. :)

---

