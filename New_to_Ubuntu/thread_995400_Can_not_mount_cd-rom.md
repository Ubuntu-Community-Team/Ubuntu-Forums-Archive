---
title: "Can not mount cd-rom"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by djax2 on 2008-11-27
I'm trying to install on a fujitsu LiteLine 366Mhz 128MB RAM. But I have trouble recognizing the CD-ROM. The error message reads: **Your installation cd-rom couldn't be mounted.**
Does anyone have an idea how to get the CD-Rom working?

---

### Post by cmnorton on 2008-11-28
You probably have to mount it manually.

1) Check to see that you have a mount directory for the cdrom:

ls -l /media/cdrom 

2) If the directory is not there, create it:

sudo mkdir /media/cdrom

3) Mount the volume:

sudo mount /dev/cdom /media/cdrom

---

### Post by Michael.Godawski on 2008-11-28
> I'm trying to install on a fujitsu LiteLine 366Mhz 128MB RAM.

That is very little Ram as for an Ubuntu installation.
> **Minimum requirements**

 
[LIST]
[*]166 MHz processor 
[*]64 MB of system memory (RAM) 
[*]At least 1.5 GB of disk space 
[*]VGA graphics card 
[/LIST]
 
**Recommended minimum requirements**

 
[LIST]
[*]300 MHz processor 
[*]256 MB of system memory (RAM) 
[*]8 GB of disk space 
[*]Graphics card capable of 800x600 resolution
[/LIST]


I would try using the alternate installer.

One question to clarify my comprehension: Are you able to launch the Live CD or the alternate installer in the first place, or does the installation stop with an error message?

---

### Post by darksideforge on 2008-11-28
> **cmnorton said:**
> You probably have to mount it manually.

1) Check to see that you have a mount directory for the cdrom:

ls -l /media/cdrom 

2) If the directory is not there, create it:

sudo mkdir /media/cdrom

3) Mount the volume:

sudo mount /dev/cdom /media/cdrom

Here are the responses when I typed the command(s) you gave (and there were some mistakes on my part because I'm not familiar with spacings between / and / yet):
```

name@name-laptop:~$ ls -1 /media/cdrom
name@name-laptop:~$ ls -1/media/cdrom
ls: invalid option -- '/'
Try `ls --help' for more information.
name@name-laptop:~$ sudo mkdir /media/cdrom
[sudo] password for name: 
mkdir: cannot create directory `/media/cdrom': File exists
name@name-laptop:~$ sudo mount /dev/cdrom/media/cdrom
mount: can't find /dev/cdrom/media/cdrom in /etc/fstab or /etc/mtab
name@name-laptop:~$ sudo mount /dev/cdrom /media/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Thank you for any assistance; at first it appears to tell me the directory is there, then it can't find it, then I can't create it, then I can't duplicate it because it IS there, then it's a wrong type.

My DVD-RW was working just fine two days ago...after an update it's suddenly not there anymore.  Suggestions?

---

### Post by darksideforge on 2008-11-28
In case it helps, here is the message I get when I insert a CD into my DVD-RW:

[IMG]http://i38.photobucket.com/albums/e129/diveclint/Screenshot-UntitledWindow.png[/IMG]

---

### Post by cmnorton on 2008-11-28
> **darksideforge said:**
> Here are the responses when I typed the command(s) you gave (and there were some mistakes on my part because I'm not familiar with spacings between / and / yet):
```

name@name-laptop:~$ ls -1 /media/cdrom
name@name-laptop:~$ ls -1/media/cdrom
ls: invalid option -- '/'
Try `ls --help' for more information.
name@name-laptop:~$ sudo mkdir /media/cdrom
[sudo] password for name: 
mkdir: cannot create directory `/media/cdrom': File exists
name@name-laptop:~$ sudo mount /dev/cdrom/media/cdrom
mount: can't find /dev/cdrom/media/cdrom in /etc/fstab or /etc/mtab
name@name-laptop:~$ sudo mount /dev/cdrom /media/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```Thank you for any assistance; at first it appears to tell me the directory is there, then it can't find it, then I can't create it, then I can't duplicate it because it IS there, then it's a wrong type.

My DVD-RW was working just fine two days ago...after an update it's suddenly not there anymore.  Suggestions?

You probably used a space for this command, right? Else there would only be one argument to the mount command. 

name@name-laptop:~$ sudo mount /dev/cdrom/media/cdrom

---

### Post by darksideforge on 2008-11-28
Here is the result when the only space is the space between "sudo" and "mount".


```
name@name-laptop:~$ sudo mount/dev/cdrom/media/cdrom
[sudo] password for name: 
sudo: mount/dev/cdrom/media/cdrom: command not found

```

---

### Post by cmnorton on 2008-11-29
Is your keyboard OK? Now you have no space between the mount command and the first parameter (the device).

---

### Post by darksideforge on 2008-11-29
> **cmnorton said:**
> Is your keyboard OK? Now you have no space between the mount command and the first parameter (the device).

It is very difficult to tell where you want me to put a space based on how your text is showing up on my computer. With some exaggerated spacing, here is the most recent command/response:

sudo  mount  /dev/cdrom/media/cdrom

Am I correct?  Below is a screenshot of the actual result (with correct spacing, of course. AND, I'm tired of hiding my screenname, so I didn't edit it out this time nor will I in the future):
```

darkside@darkside-laptop:~$ sudo mount dev/cdrom/media/cdrom
[sudo] password for darkside: 
mount: can't find dev/cdrom/media/cdrom in /etc/fstab or /etc/mtab
darkside@darkside-laptop:~$ 
```

BTW, thank you again for taking time to help me with this.

~darkside

---

### Post by darksideforge on 2008-11-29
Actually, apparently the board doesn't like my exaggerated spacing, so it's not your text but rather how the message board itself is interpreting my typing. Ubuntu should fix this!!  We might have to come up with another random symbol to indicate proper spacing such as:

sudo * mount * /dev/cdrom/media/cdrom

Also, I've been reading some posts where the command "force" is used after a command line...I'm assuming it's a last resort and not appropriate here?

~darkside

---

### Post by darksideforge on 2008-11-29
In accordance with instructions from Mc4man over on the Kubuntu board (please see: [http://ubuntuforums.org/showthread.php?p=6277559#post6277559]("http://ubuntuforums.org/showthread.php?p=6277559#post6277559") ) I followed his instructions regarding a regionset and it worked perfectly for me.

1. Bring up your terminal via Applications>Accessories>Terminal.
2. Type:
```
sudo apt-get install regionset
```
3. If your region is already set, do not change it.
4. Remove CD from player/bay/drive.
5. Perform normal restart.
6. After restart, reinsert CD and see if the drive reads it.
7. If this set of instructions works for you, PLEASE go to the link I listed above and thank Mc4man.

Best of luck,
~darksideforge

---

### Post by darksideforge on 2008-11-29
As an addendum, if your region is NOT set, go back to your terminal and type:
```
regionset
```

---

### Post by djax2 on 2009-08-12
ok I solved it by using another version of Xubuntu (8.04.1 Hardy version). Everything istalled just fine. Thx for everyones input.

---

