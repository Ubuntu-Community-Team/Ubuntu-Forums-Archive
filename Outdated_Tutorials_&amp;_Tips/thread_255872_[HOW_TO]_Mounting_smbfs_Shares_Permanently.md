---
title: "[HOW TO] Mounting smbfs Shares Permanently"
date: 2006-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by geco on 2006-09-12
I was wandering about mounting samba shares as non-root user and I found a good solution searching around the web.

You can find the **original** article on [JustLinux](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html).

So I paste and copy this how-to in ubuntuforums.

If I'm breaking any copyright :biggrin: I will not hesitate to delete this post.

[SIZE="3"]**Mounting smbfs Shares Permanently Help File**[/SIZE]

[SIZE="2"]By _Ray Cowan_[/SIZE]

This document provides help on mounting smbfs shares permanentantly. These can be shares on a Windows computer or on a Linux/UNIX server running Samba.

Throughout this document, I use the term Windows computer to indicate the server. It can be either a Windows computer or a Linux/UNIX server running Samba.

The Windows username and Windows password refer to the username and password on either the Windows computer or the Linux/UNIX server running Samba.
Mounting the Share

To mount an smbfs share from a Linux workstation at the command line, you can use either the smbmount command or use mount -t smbfs. Both command will work the same. When you use [COLOR="Red"]mount -t smbfs[/COLOR], the mount program actually passes the command over to [COLOR="Red"]smbmount[/COLOR] for execution. Throughout this document I'll use [COLOR="Red"]smbmount[/COLOR] instead of [COLOR="Red"]mount -t smbfs[/COLOR].

An example would look like this:
```

smbmount //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword

```
The mount equivalent is:
```

mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword

```
**//servername/sharename** refers to the name of the Windows computer and the name of the share.

**/mountdirectory** refers to the directory you use as the mount point on the Linux workstation. It can be any directory as long as the user executing the command has rights to it.

Whether you need to supply a username and password depends on what type of security you have on the Windows share. If you have a share created with no password on it, you shouldn't need to provide a username and password. If the share happens to be on a Windows NT server that is part of a domain, you would need to provide a domain login name and password.
Making the Mount Permanent

_smbmount does not make the mount permanent_. If the Linux workstation is rebooted, you will have to mount the share again. To make the mount occur each time you start the Linux workstation, you can put an entry in your **/etc/fstab** file. An example file would look like this:
```

LABEL=/ / ext3 defaults 1 1
LABEL=/boot /boot ext3 defaults 1 2
none /dev/pts devpts gid=5,mode=620 0 0
LABEL=/home /home ext3 defaults 1 2
none /proc proc defaults 0 0
none /dev/shm tmpfs defaults 0 0
/dev/hda3 swap swap defaults 0 0
/dev/cdrom /mnt/cdrom iso9660 noauto,owner,kudzu,ro 0 0
/dev/hdd4 /mnt/zip100.0 auto noauto,owner,kudzu 0 0
/dev/fd0 /mnt/floppy auto noauto,owner,kudzu 0 0
//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0

```
The last line in the file is the line that will mount the Windows share. You would add a line similar to that in your /etc/fstab file for each share you want to mount. Once again the username and password are only needed if the Windows share is set up to require them. If a username and password are not required, you may just replace them with the word defaults.

An important thing to remember is that _there is no space between the comma and the word password_. If you put a space there, it won't work.
Providing Security

The /etc/fstab is readable by everyone so it obviously wouldn't be a good idea to have your Windows password in it. The way to get around this is by using what is known as a _credentials file_. This is a file that contains just the username and password. The best place to put this file would be in your home directory. Here is how to do it.

Create a file in your home directory named .smbpasswd (the period at the start of the filename makes it a hidden file). Modifify the permissions on the file so only you have permission to read and write to it. The only thing in the file is your Windows username and password. Here's the commands you would enter to create the credentials file:
```

cd
echo username=mywindowsusername > .smbpasswd
echo password=mywindowspassword >> .smbpasswd
chmod 600 .smbpasswd

```
Substitute your Windows username and password in the commands. No one else except root would be able to read the contents of this file.

Once that is created, you would modify the line in the /etc/fstab file to look like this:
```

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpasswd 0 0

```
You can also use the credentials option in the smbmount command for security reasons. That command would look like this:
```

smbmount //servername/sharename /mountdirectory -o credentials=/home/myhomedirectory/.smbpasswd

```

[SIZE="3"]Providing Read/Write Access to the Share
[/SIZE]
Another problem with mounting the Windows share as shown in the /etc/fstab file above is that _only the root user would have read/write access to the share_. All other users would have read only access to it. If you wanted read/write access to it for yourself, _you need to specify your userid or groupid_. That would change the line in /etc/fstab to look like this:
```

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,uid=mylinuxusername,gid=mylinuxgroupname 0 0

```
Whatever user and or group you specified in the line would have read/write access to the mounted share. You can use either the user or group name or the user or group numerical ID. Either should work.

If you had several users you wanted to have read/write access to it, create a group and add those users to the group. Then specify just that groupid in the /etc/fstab file. You wouldn't need to specify a userid. The line in etc/fstab would look like this:
```

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,gid=sambausersgroup 0 0

```

_**You can see the man pages on smbmount, smbumount, mount, and fstab for more details.**_

[SIZE="3"]Troubleshooting[/SIZE]

If you have trouble mounting your Windows shares from /etc/fstab, here are some things to try.

The most important thing is to try to mount the share using the mount -t smbfs command from the command line. This is what will be executed when the the Linux workstation is booted up and the mounts in /etc/fstab are initialized. If you can't sucessfully mount the share with mount -t smbfs, it won't work in /etc/fstab. Work the bugs out with mount -t smbfs. Once it works, it should then work in /etc/fstab.

One of the most common problems with mount -t smbfs is a file not found error. The file not found is smbmnt, which is used by smbmount. It's usually a result of the smbmnt command not being in the path when the mount command executes. The mount command usually resides in the /bin directory and smbmnt resides in /usr/bin. To fix this problem, you need to create links to smbmnt in the /bin directory. To accomplish this, execute these commands as root:
```

ln -s /usr/bin/smbmnt /bin/smbmnt
ln -s /usr/bin/smbmount /bin/smbmount

```
Another problem occurs when a non-root user tries to mount a Windows share using smbmount. To allow them to do it you need to setuid root the smbmnt command. Since smbmnt usually resides in /usr/bin, you can accomplish it with this command as root:
```

chmod u+s /usr/bin/smbmnt

```
This will not work if you setuid the smbmount command. It is specifically written so that it won't execute if it is setuid root.

To allow non-root users to unmount the shares, you need to setuid the smbumount command. Execute this as root:
```

chmod u+s /usr/bin/smbumount

```

---

### Post by Bill_MI on 2006-09-18
Geco, be assured your HowTo has been used successfully.  Good jub!

I have an interesting result when using /etc/fstab: The HAL (hald) fails to come up cleanly *sometimes* (which makes me think network state is involved).  I've set it aside for now until I can find out how to get some clues - any appreciated.

---

### Post by vadar007 on 2006-09-18
Okay I had to use cifs vs smbfs. Everything works except for the implementation of the credentials file. Syslog says:

CIFS VFS: No username specified
CIFS VFS: cifs_mount failed w/ return code = -22

The file exists and contains the proper username and password, the owner <myusername> has R/W access, the line in fstab looks like:

//<servername>/photos /data/Photos cifs ro,credentials=/home/<myhomedirectory>/.smbpasswd 0 0

If I go with standard username and password in fstab it works fine.

What am I missing?

---

### Post by vadar007 on 2006-09-18
> **vadar007 said:**
> Okay I had to use cifs vs smbfs. Everything works except for the implementation of the credentials file. Syslog says:

CIFS VFS: No username specified
CIFS VFS: cifs_mount failed w/ return code = -22

The file exists and contains the proper username and password, the owner <myusername> has R/W access, the line in fstab looks like:

//<servername>/photos /data/Photos cifs ro,credentials=/home/<myhomedirectory>/.smbpasswd 0 0

If I go with standard username and password in fstab it works fine.

What am I missing?

Duh, needed to install smbfs (apt-get install smbfs)....

---

### Post by meyersjd on 2006-09-19
Anyone know how to mount a folder nested within a share on a windows computer?

In other words:
smbmount //server/share/folder mountpoint

Unfortunately this doesn't work for me. I want to only mount the folder within the share, not the whole share.

Suggestions?

---

### Post by jhaitas on 2006-09-20
I am unable to change the group permissions for folders within the samba share. i have tried

```
chmod 777 -R foldername
```

this does not work... what am i doing wrong?

---

### Post by bodhi.zazen on 2006-10-11
This how-to has been added to the ubuntu wiki:

[How to mount smbfs shares](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

---

### Post by utabintarbo on 2006-10-11
> **meyersjd said:**
> Anyone know how to mount a folder nested within a share on a windows computer?

In other words:
smbmount //server/share/folder mountpoint

Unfortunately this doesn't work for me. I want to only mount the folder within the share, not the whole share.

Suggestions?

While this is easy in Windows, it is not possible using smbmount. You can only mount actually shared resources. Sorry.:(

---

### Post by bigbadsi on 2006-10-18
I've only been using Ubuntu for a week so please bear with me...

I am unable to permanently mount a samba share.  I have samba running, I can access the share via network:/// and can mount the share manually using:
```
sudo mount -t smbfs //ugly/music /home/bigbadsi/mnt/ -o credentials=/root/.smbcredentials
```

Have have already set up /root/.smbcredentials and the contents of this file looks like this:
```
username=uglysamba
password=uglysamba
```

I have set up the user uglysamba on the remote windows box (as a limited user) and set the password to uglysamba.

The share won't mount automatically after a reboot.  This is my /etc/fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
//ugly/music /home/bigbadsi/mnt smbfs credentials=/root/.smbcredentials 0 0
```

I have tried changing the last line of /etc/fstab to read (as per [http://ubuntuguide.org/wiki/Dapper#How_to_permanently_mount_a_samba_share]("http://ubuntuguide.org/wiki/Dapper#How_to_permanently_mount_a_samba_share")):
```
//ugly/music /home/bigbadsi/mnt smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0
```

I have also tried changing the last line of fstab to:
```
//ugly/music /home/bigbadsi/mnt/ smbfs defaults 0 0
```

After reboot mount doesn't show my share.

Is this a permissions issue at startup, do I need to include other options in /etc/fstab or am I missing something else?  Also, is there a log I should have checked (I looked in /var/log/samba but didn't know what I was looking at)?

Thanks.

---

### Post by dmizer on 2006-10-22
> **meyersjd said:**
> Anyone know how to mount a folder nested within a share on a windows computer?

In other words:
smbmount //server/share/folder mountpoint

Unfortunately this doesn't work for me. I want to only mount the folder within the share, not the whole share.

Suggestions?

it should be smbmount //server/share\folder mountpoint

ie, reverse slash to specify the folder name.

---

### Post by DoomedTX on 2006-11-04
> **bigbadsi said:**
> After reboot mount doesn't show my share.

Is this a permissions issue at startup, do I need to include other options in /etc/fstab or am I missing something else?  Also, is there a log I should have checked (I looked in /var/log/samba but didn't know what I was looking at)?

Check your system log to see if you get this error:

smbfs: mount_data version 1684370019 is not supported

I've been troubleshooting that one tonight and unable to find any information other than it used to work in Breezy then stopped working in Dapper. I found a suggestion to add smbfs to /etc/modules but that has not worked for me. I'm still looking for an answer.

---

### Post by Rotlaus on 2006-11-14
> **DoomedTX said:**
> Check your system log to see if you get this error:

smbfs: mount_data version 1684370019 is not supported

I've been troubleshooting that one tonight and unable to find any information other than it used to work in Breezy then stopped working in Dapper. I found a suggestion to add smbfs to /etc/modules but that has not worked for me. I'm still looking for an answer.

I had the same error. After installing the smbfs package with
```
sudo apt-get install smbfs
```
the error went away.

cu,

Andre

---

### Post by DoomedTX on 2006-11-23
Unfortunately this does not fix the problem for me as smbfs was already installed. From what I've read, not having smbfs installed causes a similar error but that is not the case here. I've done a lot of searching on the 'net and so far the only advice I've found that wasn't "install smbfs" was to add smbfs to the modules loaded at startup. Again, this did not work for me. I could probably get around this by adding the mount commands to a script run towards the end of startup like .bashrc or something like that, but I'd rather have a real fix to this problem that appeared in the Breezy to Edgy upgrade.

---

### Post by total wormage on 2007-01-18
> **Bill_MI said:**
> Geco, be assured your HowTo has been used successfully.  Good jub!

I have an interesting result when using /etc/fstab: The HAL (hald) fails to come up cleanly *sometimes* (which makes me think network state is involved).  I've set it aside for now until I can find out how to get some clues - any appreciated.

i have the same problem, help will be appreciated :p

---

### Post by bib on 2007-02-13
Hi,

I have a FAT32 formated disk on a server running an old mandrake version (9), I normally mount this partition over the network on my ubuntu box. I have had no problem on Hoary for ages, but now that I have upgraded to 6.10 on an AMD64 box I get the weirdest problem.

I can create files save them the first time.
I cannot save an edited file, it blanks the old file and that's it (but I can save as a new file).

However there are variations:

if I use vi to edit an existing file, I get permission denied (cannot write file) and the original file is wiped when I quit without saving.
if I use gedit, I get a warning that it cannot backup the file and ask me to "save anyway" which, when I do, saves the file with the changes...
If I use Gimp to edit an existing file it gives me the same error as vi and blanks the image file.

I have looked everywhere for answers, copied my old fstab smbfs line from my previous box to my new one and even the smb.conf but it still doesn't solve the problem, I am at the end of my ideas. The only thing I saw was some posts that resembles my case and it is apparently a bug
[http://www.google.co.uk/search?q=samba+blanked](http://www.google.co.uk/search?q=samba+blanked)

so if someone has a better idea please let me know.

thank you very much

bib

---

### Post by Ares2 on 2007-02-16
Hey, im kind of new to linux/xubuntu and I'm having an hard time mounting my ntfs network drive.
I aint really sure of what to do but anyway, my windows workgroup is called Scott and my computer name is GABEY. The path I want to access is the whole C: drive on Gabey's computer.

Here's how I'm trying to access it,

sudo mount -t smbfs //GABEY/C /media/WINDOWS -o username=bleh,password=

I dont have a password on gabey's computer and this is what i'm getting: 


Anonymous login successful
7421: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


Can someone help me out?!?

---

### Post by geco on 2007-02-17
> **Ares2 said:**
> Hey, im kind of new to linux/xubuntu and I'm having an hard time mounting my ntfs network drive.
I aint really sure of what to do but anyway, my windows workgroup is called Scott and my computer name is GABEY. The path I want to access is the whole C: drive on Gabey's computer.

Here's how I'm trying to access it,

sudo mount -t smbfs //GABEY/C /media/WINDOWS -o username=bleh,password=

I dont have a password on gabey's computer and this is what i'm getting: 


Anonymous login successful
7421: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


Can someone help me out?!?

try 
```

sudo mount -t smbfs //GABEY/C /media/WINDOWS -o username=bleh,guest

```

---

### Post by RomanW on 2007-02-22
I followed this How To and it was useful and helpful to me. I can mount all shares flawlessly, I only have one problem: I can't mount shares that have a space in the directory name. e.g: the directory in this fstab line:

```
//Enigma-V2/Mijn Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

When I type **sudo mount -a** in the terminal, I get the following error:

```
[mntent]: line 12 in /etc/fstab is bad
```

Line 12 is the line I previously gave.

I tried all these variations of line 12:

```
"//Enigma-V2/Mijn Muziek" /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

```
//Enigma-V2/Mijn\ Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

```
'//Enigma-V2/Mijn Muziek' /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

They all give me the same error message as the original line.

With the combination ```
//Enigma-V2/Mijn\Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
``` I get this error message: 
```
12455: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
```

This is my entire fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda2
UUID=473804f9-e426-4057-92b3-43e86ae6fa4e  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=3d55a66d-1a14-487c-aaf0-f5e8bafb098a  none           swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/hdd                                   /media/cdrom1  udf,iso9660  user,noauto                 0  0  
//Enigma-V2/Downloads /home/blaatmeister/Desktop/Samba/Downloads smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
//Enigma-V2/Mijn\Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

Since the mount on line 11 works, there's nothing wrong with my .smbpasswd file.

I can also mount the share without a problem in the terminal using the command: 
[B]
sudo smbmount "//Enigma-V2/Mijn Muziek" /home/blaatmeister/Desktop/Samba/Muziek -o credentials=/home/blaatmeister/.smbpasswd[/B]

I'm hoping that someone here can tell me how I can mount the share using the fstab file. Thanks in advance. :)

---

### Post by Ares2 on 2007-02-26
> **geco said:**
> try 
```

sudo mount -t smbfs //GABEY/C /media/WINDOWS -o username=bleh,guest

```


I'm still getting that error, do you need any other info I can give to help me solve the problem?

---

### Post by geco on 2007-02-27
> **Ares2 said:**
> I'm still getting that error, do you need any other info I can give to help me solve the problem?
I read in smbmount manual:
> 
 password=<arg>
              specifies  the  SMB  password.  If this option is not given then the environment variable
              PASSWD is used. If it can find no passwordsmbmount will prompt for  a  passeword,  unless
              the guest option is given.

              Note  that  passwords  which  contain the argument delimiter character (i.e. a comma ’,’)
              will failed to be parsed correctly on the command line. However, the  same  password  de&#8208;
              fined  in  the PASSWD environment variable or a credentials file (see below) will be read
              correctly.


so if you have no password you should do:

> 
guest  Don’t prompt for a password


before using mount try 

```

smbmount //GABEY/C /media/WINDOWS -o username=bleh,guest

```

where **bleh** is your username, isn't it?

actually mount -t smbfs should call smbmount.

---

### Post by geco on 2007-02-27
> **RomanW said:**
> I followed this How To and it was useful and helpful to me. I can mount all shares flawlessly, I only have one problem: I can't mount shares that have a space in the directory name. e.g: the directory in this fstab line:

```
//Enigma-V2/Mijn Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

When I type **sudo mount -a** in the terminal, I get the following error:

```
[mntent]: line 12 in /etc/fstab is bad
```

Line 12 is the line I previously gave.

I tried all these variations of line 12:

```
"//Enigma-V2/Mijn Muziek" /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

```
//Enigma-V2/Mijn\ Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

```
'//Enigma-V2/Mijn Muziek' /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

They all give me the same error message as the original line.

With the combination ```
//Enigma-V2/Mijn\Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
``` I get this error message: 
```
12455: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
```

This is my entire fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda2
UUID=473804f9-e426-4057-92b3-43e86ae6fa4e  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=3d55a66d-1a14-487c-aaf0-f5e8bafb098a  none           swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/hdd                                   /media/cdrom1  udf,iso9660  user,noauto                 0  0  
//Enigma-V2/Downloads /home/blaatmeister/Desktop/Samba/Downloads smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
//Enigma-V2/Mijn\Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

Since the mount on line 11 works, there's nothing wrong with my .smbpasswd file.

I can also mount the share without a problem in the terminal using the command: 
[B]
sudo smbmount "//Enigma-V2/Mijn Muziek" /home/blaatmeister/Desktop/Samba/Muziek -o credentials=/home/blaatmeister/.smbpasswd[/B]

I'm hoping that someone here can tell me how I can mount the share using the fstab file. Thanks in advance. :)

don't know very well what you should do, actually you tried all the tricks I could suggest you.
As last resort you should rename your share with no **_spaces_** and see what happens.
;)

---

### Post by Ares2 on 2007-03-01
Both way are still giving me that weird error.

Anonymous login successful
4801: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

I tried mounting following another method and here is what im receiving:

//192.168.0.2/Scott /media/WINDOWS cifs auto,rw,username=bleh,guest,uid=blah 0 0

I tried changing the root folder, like, //192.168.0.2/GABEY or //192.168.0.2/C
either way, im still getting this error:

I run 
sudo mount /media/WINDOWS

mount error 113 = No route to host
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

---

### Post by RomanW on 2007-03-02
> **geco said:**
> don't know very well what you should do, actually you tried all the tricks I could suggest you.
As last resort you should rename your share with no **_spaces_** and see what happens.
;)

That's what I'm going to do now :). Should've done that earlier anyway, would've only cost me a few minutes. :D I was just wondering if it was possible to fix it, but apparently not. Thanks anyway.

---

### Post by robyoko on 2007-03-19
All,

Have read thread but am wondering, fstab is loaded at start up. What if I'm on a wireless network?

When I do following in a terminal  

sudo mount -t smbfs //share/share /home/robert/Desktop/Network -o username=XXX,password=XXX,uid=robyoko,gid=robyoko

share is mounted no problems

When I add it to fstab it isn't executed as there is no networkconnection at start up. How can I still add the share automatically?

Thanks!

---

### Post by dannyboy79 on 2007-03-21
please follow this guide and use cifs and not smbfs. [http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

---

### Post by asfaq on 2007-05-09
Tried the method in the first post but after entering ```
//myserver/thesharedfolder /media -o username=bleh,password=bleh1
``` i get this error.. ```
15571: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
```
Am running on Ubuntu for the first time since i want to go the open-source way.. any help is appreciated!

- Asfaq!

---

### Post by dannyboy79 on 2007-05-09
> **asfaq said:**
> Tried the method in the first post but after entering ```
//myserver/thesharedfolder /media -o username=bleh,password=bleh1
``` i get this error.. ```
15571: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
```
Am running on Ubuntu for the first time since i want to go the open-source way.. any help is appreciated!

- Asfaq!

this means that you don't have access to that server. can you please post the output after you enter the commands into a terminal session

smbtree
(NOTE: this will ask for a password, enter your password, should be same one when you use sudo)

this will return a list of available servers and what shares are available within each of the servers.

findsmb

this command should return a list of servers and whether they are local master browser or domain master browsers. (by the little * or the + symbol)

if you try this command

smbclient -L WHAATEVERTHESERVERNAMEISHERE

you should be prompted for a password, enter the password for that server. also, do the usernames and passwords match on ubuntu and whatever os is on the server? here is a good guide for debian which is what ubuntu is based on.

[http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)

---

### Post by pruss on 2007-06-04
Had problem with the credentials file at Ubuntu Fawn.
It could be fixed by deleting the line break after the password=<>

Old
```

username = <username>\n
password = <password>\n

```

became
```

username = <username>\n
password = <password>

```

This is a pretty ugly "Feature"....

Regs.

---

### Post by dannyboy79 on 2007-06-04
> **pruss said:**
> Had problem with the credentials file at Ubuntu Fawn.
It could be fixed by deleting the line break after the password=<>

Old
```

username = <username>\n
password = <password>\n

```

became
```

username = <username>\n
password = <password>

```

This is a pretty ugly "Feature"....

Regs.
I read somewhere that you should never use a gui text editor when creating files like these, not sure why, maybe because of the apps that read from then getting hung on this exact thing, use Vim or Nano. I didn't have this problem because I don't hit enter after the last line is entered, this is the same as /etc/fstab and many others I beleive

---

### Post by piagent on 2007-09-30
If you do a smbmount and the share goes down and comes back or just comes up late how can you set it up so the mount is sustainable?

I use the non-root method.  It works well and I want to stay with this.  Some web reading suggests a bug in smbfs which is doone better with cifs.  How do you do a non-root cifs mount?

---

### Post by dannyboy79 on 2007-10-03
not sure what you mean about being sustainable? If the machine that has the remote share being mounted locally goes down, there's not much you can do about this. just have to mount it again after it's back up. I suppose you could write some kind of cron job that checks whether the host is "UP" by pinging it, if a successful ping then use the mount command, if no successful ping, don't mount it.

The only reason you need to use sudo when using smbmount is because either the credentials isn't readable by the person issuing the mount command or that the folder you're trying to mount the remote share to isn't owned by the person issuing the mount command. otherwise, you don't have to use sudo.

---

### Post by ralvynl on 2007-10-03
What happens if the Windows COmputer dosnt have a password

---

### Post by piagent on 2007-10-04
> **dannyboy79 said:**
> not sure what you mean about being sustainable?  ...

The only reason you need to use sudo when using smbmount is ....

I think you understand, I just want the machine to heal itself,lol.  Gnome has some type of watchdog for it's Network-Browser feature.  It senses when a host goes away and comes back.  Gnome has a connect that puts a ghost link to the share, what I think I need is a Gnome mount (or map) that has some watchdog feature and works like the connect with features of autofs.  I'll work it out.  

I can use smbumount and smbmount as a non-root (chmod u+s) fixed that.  It's just hard to explain to the wife that when things don't work she has to go hands-on.  I don't see a Mac in my future, I like ubuntu, just "gotta" make it work.  

I seek to learn and get these machines to do what they were born to do ..... serve ME!

thanks, all input helps.

---

### Post by piagent on 2007-10-04
> **ralvynl said:**
> What happens if the Windows COmputer dosnt have a password

I ran into the same issues, I have an old machine with W98 running in the middle of  three ubuntus and one RH (soon to be retired and come back as ubuntu).  

I think you have two options:

1)turn on the windows client feature in your windows network settings (also file and print share if you plan to share out from that machine).  when you boot up you should be asked for a user name and password.  You can add this to your samba config .... i'm assuming your windows machine is subordinate. If your not asked you can go to your start and see a logon/logoff menu item.

2)Run your samba as "share" vs "user".  Very unpopular if your security minded.  I use this method on all my machines plus the force statements to make the  create and writes to be owned my the local user who shared out.  Once I did this my wife got very happy.  Both of us can share, add, delete, and modify at will. 

I'm not an expert in this area.

---

### Post by oh.mynameiscupid on 2007-11-15
> **RomanW said:**
> I followed this How To and it was useful and helpful to me. I can mount all shares flawlessly, I only have one problem: I can't mount shares that have a space in the directory name. e.g: the directory in this fstab line:

```
//Enigma-V2/Mijn Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

When I type **sudo mount -a** in the terminal, I get the following error:

```
[mntent]: line 12 in /etc/fstab is bad
```

Line 12 is the line I previously gave.

I tried all these variations of line 12:

```
"//Enigma-V2/Mijn Muziek" /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

```
//Enigma-V2/Mijn\ Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

```
'//Enigma-V2/Mijn Muziek' /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

They all give me the same error message as the original line.

With the combination ```
//Enigma-V2/Mijn\Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
``` I get this error message: 
```
12455: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
```

This is my entire fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda2
UUID=473804f9-e426-4057-92b3-43e86ae6fa4e  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=3d55a66d-1a14-487c-aaf0-f5e8bafb098a  none           swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/hdd                                   /media/cdrom1  udf,iso9660  user,noauto                 0  0  
//Enigma-V2/Downloads /home/blaatmeister/Desktop/Samba/Downloads smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
//Enigma-V2/Mijn\Muziek /home/blaatmeister/Desktop/Samba/Muziek smbfs credentials=/home/blaatmeister/.smbpasswd,uid=blaatmeister 0 0
```

Since the mount on line 11 works, there's nothing wrong with my .smbpasswd file.

I can also mount the share without a problem in the terminal using the command: 
[B]
sudo smbmount "//Enigma-V2/Mijn Muziek" /home/blaatmeister/Desktop/Samba/Muziek -o credentials=/home/blaatmeister/.smbpasswd[/B]

I'm hoping that someone here can tell me how I can mount the share using the fstab file. Thanks in advance. :)

Found the answer in another forum post:
[http://ubuntuforums.org/archive/index.php/t-27823.html]("http://ubuntuforums.org/archive/index.php/t-27823.html")
It turns out that you need to escape each space character with '\040', without the quotes.
Who would have guessed? :lolflag:
It totally works. Now my fstab looks like this:
> # /etc/fstab: static file system information.
## /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cefe7dc6-664a-41cf-a326-6eb61d19581f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4a6287a1-820f-4fad-bba1-f76bd10befeb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
//PBEARD/My\040Music    /home/madeline/My\040Music      smbfs   username=defaults,password=defaults     0       0
//PBEARD/SharedDocs     /home/madeline/SharedDocs       smbfs   username=defaults,password=defaults     0       0


---

### Post by pclark36 on 2007-12-08
Wow, in the GUI, I just tell it to connect to server, type in smb://IP address of computer with share/"share" or share folder name and it works like a champ

---

### Post by pssturges on 2007-12-22
Hi,

A bit of background... I have my main Mythbuntu box set up as a bit of a file server, with all the family's documents stored on it. Each family members documents are 'owned' by their username. I have also created a group called family, and given the group read/write permissions on all the documents. The folder containing all the documents is shared via samba.

I have other Ubuntu gutsy machines setup with the samba share mounted as described in this guide using my credentials. All family members can read/write to all the documents. All sounds good so far. 

Now the problem...

On the clients, all documents show as belonging to me in gnome. This in itself doesn't matter that much because of the group permission thing. The problem start when someone else tries to create a new file or folder and then edit it. It appears on the client machine as mine and given the default permission of drwxr-xr-x. This means the user who just created it, can't edit it!!!!

Interestingly, when I do an ls -l on the client machines, the ownership of the files show as the correct users.

I see two way around this:

1) is there a way to change the default permissions when creating a file/folder?

2) somehow getting the correct ownerships to appear


Any help much appreciated

Phil

---

### Post by josir on 2008-11-12
Hi folks, 

just to add two parameters that are useful on a daily use:

1) to those who have special characters on filename and directories, you can use:

iocharset=utf8

2) How to setup the mount be read/write to the group "plugdev" - use the gid= parameter.

Example that uses the 2 parameters:

mount -t smbfs //192.168.0.4/Aplicacao /mnt/Aplicacao -o credentials=/home/josir/.smbpasswd,gid=plugdev,iocharset=utf8

---

### Post by frankhdz on 2009-12-21
I can mount the shares fine but I cannot write to the shared folders, The sambashare group has my user name in the group but I am not able to write to the shared resource. What am I missing?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=19b5201a-39d3-4039-8444-d396683d05ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fe5a24f4-7ca9-4e4d-b3c0-34f8a3bc3416 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//galileoserver/us250 /home/frank/usb250 smbfs credentials=/home/frank/. smbpasswd,gid=sambashare 0 0

//galileoserver/us1tb /home/frank/usb1tb smbfs credentials=/home/frank/. smbpasswd,gid=sambashare 0 0
```

---

### Post by frankhdz on 2009-12-21
I found the problem. I forgot to add my username 
```
**uid=frank**,gid=sambashare
```

Now I can read and write to the shared folder.

---

### Post by jaya28inside on 2010-09-22
uh oh, now I'm in a dead mode.
Forgive me for bumping in.

Last time I tried to use the deprecated command (smbfs), but it works.

here via root account
> 
$> mount -t smbfs //mydestinatedIP/aDirectory /myPreferrablyDirectory -o username=Admin,password=Admin 


it works, the directory was mounted there.

and then, I try to add this line of code below to the **/etc/fstab**

> 
//mydestinatedIP/aDirectory /myPreferrablyDirectory -o username=Admin,password=Admin smbfs 0 0


but once I restarted my machine, it can not reach the given network. Gosh! Now I could not mount it. And the effect is now become worst. My Linux can't login, caused by the error given from fstab.

OOOOOooo... what should I do next?
My purpose is to enable the mount permanently,
but unfortunate things happened on it. Which part that I've forgotten anyway?

-- this line below is the updated one. after I go run over the google and his brother.

Thanks god, now I'm able to edit the /etc/fstab via Linux Live CD.
and then **apt-get lvm2**, execute **pvscan**, and then, **vgchange -a y**, and also **lvscan**,
and of course **mount **the device available. And gosh! edit the /etc/fstab there....

original source:
> [http://forums.virtualbox.org/viewtopic.php?f=3&t=32364](http://forums.virtualbox.org/viewtopic.php?f=3&t=32364)

... anyway, back to the topic. 
How to make it the mount permanent after machine restarted?

---

### Post by bodhi.zazen on 2010-09-22
Your fstab line is close, but the syntax is off a bit.

```
//mydestinatedIP/aDirectory /myPreferrablyDirectory cifs username=Admin,password=Admin 0 0
```You can add other options if needed, such as setting uid, gid, or permissions.

See:

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")  for details.

Last, rather then posting in an old thread (this one is 4 years old from the first post, one year from the last post) start a new thread.

A fair amount changes in 4 years. For example , why do you insist on using the depreciated smbfs ? You should use cifs, works fine, and one day smbfs will stop working altogether as it is depreciated, meaning no longer maintained and you should switch.

---

### Post by jaya28inside on 2010-09-22
really great!
case solved!

thanks.

---

### Post by jaeger2000 on 2010-11-02
NOTE: For remote directory.  When using the system name.  I could not  get the mount to work when editing the /etc/fstab unless I put the  appropriate details in /etc/hosts.
ie.

sudo gedit /etc/hosts


my_network_share     192.168.2.100



kind regards,
Ian Gregory, Sydney.
fyi: Ubuntu 10.10.

---

### Post by josir on 2010-11-03
Hi folks, 

I am just wandering.. In a single user machine, the fstab solution is fine. 

But if you have several users, each one with different shares needs, what is the best approach to automate the shares ?

Put on ~/.profile or what ?

---

### Post by chinaCat86 on 2011-02-14
> **josir said:**
> Hi folks, 

I am just wandering.. In a single user machine, the fstab solution is fine. 

But if you have several users, each one with different shares needs, what is the best approach to automate the shares ?

Put on ~/.profile or what ?

Hate to bump an old thread, but I too am interested in this. Looking around a lot of the guides suggest the fstab solution. But, I am trying to find a more secure solution to mount a samba share. Any suggestions?

Details of my situation
Mounting a centOs 5 share on an ubuntu 10.10 machine.

---

### Post by dmizer on 2011-02-14
> **chinaCat86 said:**
> Hate to bump an old thread, but I too am interested in this. Looking around a lot of the guides suggest the fstab solution. But, I am trying to find a more secure solution to mount a samba share. Any suggestions?

Details of my situation
Mounting a centOs 5 share on an ubuntu 10.10 machine.
A bit complicated but possible.

First of all, you need to make sure that each account on your clients also has an account on the server. That way you don't have to worry about adding credential files or exposing usernames and passwords in a clear text file.

If you have one client with multiple logins, then you can use autofs to automount on a per user basis. There's some information on wildcard mounting with autofs here: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

You'll also have to make sure that group permissions are configured correctly on the client so that files are readable and writable by the correct users. [https://help.ubuntu.com/community/MountWindowsSharesPermanently#Multiple%20Users](https://help.ubuntu.com/community/MountWindowsSharesPermanently#Multiple%20Users)

It may also help to rethink your server's /etc/samba/smb.conf file as well. It may be less complicated to configure your server for LDAP instead of using autofs: [https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)

Obviously this is only a rough outline as there are many variations and configuration possibilities.

---

