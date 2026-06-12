---
title: "Truecrypt permissions issue"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by arumiat on 2013-06-12
[FONT=arial][COLOR=#333333]So I've recently migrated from my MacOSX to Ubuntu.

However I'm having an issue with the permissions of the files I've brought across. [/COLOR]
[/FONT]
[LIST]
[*][FONT=arial]created a Truecrypt container on my MacOSX (a while ago).[/FONT]
[*][FONT=arial]works fine when moving this container and mounting it using Truecrypt on another MacOSX[/FONT]
[*][FONT=arial]mounting it via Truecrypt (using the GUI) on Ubuntu 12.04 gives me only read permissions.  I put in the correct Truecrypt password & my admin password to do this[/FONT]
[*][FONT=arial]right-clicking the file I want to modify and going into the permissions tab under Ubuntu shows the owner as [COLOR=#0000cd]501 - user #501[/COLOR]. Owner has read and write permissions[/FONT]
[*][FONT=arial]the group under this is [COLOR=#0000cd]dialout [/COLOR]and is read only[/FONT]
[*][FONT=arial]I obviously want write permissions on Ubuntu as well so I can modify the contents of my container ongoing[/FONT]
[*][FONT=arial]I've checked the volume properties in Truecrypt, - it was NOT created as a read-only volume. When I mount the volume in Truecrypt for each session the 'Mount as read-only' option is NOT ticked[/FONT]
[*][FONT=arial][/FONT]
[/LIST]
[FONT=arial][COLOR=#333333]Can anyone please enlighten me as to how to get write privileges with the mounted container? Want to offload my Mac asap but too worried to do so before I've got all my encrypted docs working.[/COLOR]
[COLOR=#333333]Thanks in advance[/COLOR][/FONT]

---

### Post by arumiat on 2013-06-14
So possible ways around this...
? use the chmod command to reset file permissions to read & write (either on linux or mac? [http://www.macinstruct.com/node/415](http://www.macinstruct.com/node/415))

Any thoughts really appreciated

---

### Post by cincinnatus13 on 2013-06-14
Yeah, sounds like you just need to chown it. 

I might get confirmation from someone else before you tried this (as I've only used chown a few times) but the syntax is
```
chown username:username nameoffile
```
assuming of course that you are root.

This is the basic layout. Knowing it's a TC volume, I would assume you don't need the -r since it is seen as only one file by itself. This will change it though to your username and group (1000 by default I believe.)
Either cd into the folder or type the full path- /location/of/file/nameoffile.tc

---

### Post by arumiat on 2013-06-17
Thanks Cincinnatus13

I've ended up using the info from this [article]("http://askubuntu.com/questions/150028/you-are-not-the-owner-message-when-trying-to-access-folder") to open up a gksu nautilus window (giving me root access) and I'm going to use that to hopefully change the file-permissions for the main directory and all the directories & files 'underneath' it. I'm still terrified of using the terminal window.

However if I try and change the Owner, Group or Others drop down menu to my user running as root (gksu nautilus) it gives an error that it is a 'read-only file system'. I imagine then even with terminal the same problem would apply. 

I'm wondering if there's a way to change the permissions on my Mac prior to transferring the files over to my Ubuntu system? Or whether it's the transfer of files via an external HDD that sets the permissions or something..

This is massively frustrating, any further help appreciated.

---

### Post by varunendra on 2013-06-17
> **arumiat said:**
> However if I try and change the Owner, Group or Others drop down menu to my user running as root (gksu nautilus) it gives an error that it is a '**[COLOR="#FF0000"]read-only file system[/COLOR]**'. I imagine then even with terminal the same problem would apply.

The highlighted part is the keyword here. What is the file system of the container?

Since you created it on MacOS, I think it may be HFS/HFS+. I'm not sure whether Ubuntu by default has write support for it or not. If not, you may just need to install hfsutils package.

If not sure, please show us the terminal (oh my.. ;)) output of -
```
mount
```
.. when the volume is mounted in truecrypt.

---

### Post by arumiat on 2013-06-17
I also tried transferring the Truecrypt file over using FAT32 on an external HDD, didn't make any difference.

---

### Post by varunendra on 2013-06-17
> **arumiat said:**
> I also tried transferring the Truecrypt file over using FAT32 on an external HDD, didn't make any difference.

Didn't get it. Do you mean you copied the encrypted files 'inside the container' over to a FAT partition and they were still read-only? If so, that is purely a mounting problem.

If it was the truecrypt container itself, then again, the filesystem of the container is what matters, not the filesystem of the partition on which the container resides as a file.

To be clear, the container file is treated as an independent drive/partition in itself by truecrypt. It has a filesystem of its own which is chosen at the time when you create a container.

---

### Post by arumiat on 2013-06-17
Hi Varun, sorry I only saw your initial message after posting mine about the FAT32 external HDD transfer..

As requested (using Terminal!)
xxxxxxx@xxxx-W35-37ET:~$ mount
/dev/sdb5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /boot type ext4 (rw)
/dev/sdb6 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/xxxxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxxx)
truecrypt on /tmp/.truecrypt_aux_mnt1 type fuse.truecrypt (rw,nosuid,nodev,allow_other)
/dev/mapper/truecrypt10 on /media/truecrypt10 type hfsplus (ro)

So looks like you were indeed right about the container being HFS+ (i.e. a MacOSX based file-system)

From what you said in your second response it sounds like I could copy all the files 'inside the Truecrypt container' mounted on my MacOSX over to my FAT32 external HDD. Then to Ubuntu & then create a new container inside Ubuntu using Truecrypt & re-encrypt them?

Thanks for your help, this is the last milestone from being able to sell my Mac!

---

### Post by cincinnatus13 on 2013-06-17
^ That'll work just fine.

---

### Post by varunendra on 2013-06-17
> **arumiat said:**
> From what you said in your second response it sounds like I could copy all the files 'inside the Truecrypt container' mounted on my MacOSX over to my FAT32 external HDD. Then to Ubuntu & then create a new container inside Ubuntu using Truecrypt & re-encrypt them?
That will be an easy (but lengthy) fix, like *cincinnatus13* already pointed out.

Also, based on this part of the mount command output -
```
/dev/mapper/truecrypt10 on /media/truecrypt10 type** hfsplus ([COLOR="#FF0000"]ro[/COLOR])**
```
.. I think you should be able to mount it with both read/write permissions by just installing "hfsutils" package -
```
sudo apt-get install hfsutils
```

From its description -
> Tools for reading and writing Macintosh volumes
 HFS is the native Macintosh filesystem format.
 .
 This package contains several command-line utilities for reading and
 writing Macintosh HFS-formatted media such as floppy disks, CD-ROMs,
 and hard disks.

Whatever suits you better. :)


**EDIT:**
If hfsutils alone doesn't help, try additionally installing hfsplus package also -
```
sudo apt-get install hfsplus
```
It is specifically meant to add support for hfs+, but doesn't mention explicitly if it can support write access to it.

---

### Post by cincinnatus13 on 2013-06-17
^^ Good point. I suppose it all depends what he has in it. I just imagine people encrypting small things like docs and stuff which wouldn't take that long to transfer and the aforementioned method would just be easier.
If he has a significant amount of files in there, then yes, I would totally recommend your procedure.

---

### Post by arumiat on 2013-06-17
Thanks Varun.

I installed both those packages but unfortunately the HFS+ Truecrypt container with all of its files is still mounting as read-only =(.

I ended up transferring the files over via a FAT32 USB (thanks Cincinnati) & I now have read and write access to them all.

HOWEVER frustratingly I created a new Truecrypt container within which to store said files securely in Ubuntu (I selected FAT file-system during creation) and after I've mounted it if I try and write anything to it it comes up with an error saying that I have read-only access to it?!

Thanks for all your help so far, at least I can access those critical files within Ubuntu now

---

### Post by varunendra on 2013-06-18
> **arumiat said:**
> HOWEVER frustratingly I created a new Truecrypt container within which to store said files securely in Ubuntu (I selected FAT file-system during creation) and after I've mounted it if I try and write anything to it it comes up with an error saying that I have read-only access to it?!

Please post the output of mount command again (only the relevant two lines will be enough).

Also, make sure the mount option is not set to "read-only" itself in TrueCrypt as shown in the attached image.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=243945&d=1371575647[/IMG]

---

### Post by grashdur on 2013-07-10
Hi All,

This problem goes beyond the importing of Truecrypt volumes from a Macintosh. I've been having problems with permissions on Truecrypt volumes' contents for years, and have tried various workarounds. Basically, the problem started after I switched from Windows to Ubuntu back in 2006, and has followed me onto every computer I use. The issue seems to be that the Linux version of Truecrypt insists on assigning ownership of files only to some other random user, not to the main user account in which I use Truecrypt. I think I read something on the Truecrypt site earlier explaining that in Linux, you're supposed to only be using Truecypt as root user ("for sercurity purposes") -- which makes absolutely no sense. Perhaps the designer of Truecrypt just doesn't use or understand Linux?

I've tried gksu nautilus to reassign ownership of files and folders, which used to work. Now that seems to work when I'm doing it, but when I go back to my normal file browser window, I see that that the permissions didn't really change. I'm using ext4 formatting.

Now I tried creating a new TC volume, to see if I can replace the old one -- but as it turns out, I don't have permission to write to my newly-created replacement file either. Since reinstalling my computer in May I was free of these problems, but now they just returned today, and none of my old workarounds help any more.

I've been struggling with this problem off and on for years -- there must be some solution to this problem. This is so frustrating. All I want is a way to protect my privacy.

---

### Post by grashdur on 2013-07-10
...okay, I just ran the Ubuntu updates for today, started up Truecrypt again, and now it's working fine. I don't understand what happened.

---

