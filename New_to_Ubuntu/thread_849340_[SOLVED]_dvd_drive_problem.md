---
title: "[SOLVED] dvd drive problem"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by irishy on 2008-07-04
Help please I have seen a solution similar to the one that I need in the forum but it was not right for my problem.In Hardy Heron my dvd drive shows up in computer but when I click on it the message I get is unable to mount location
can anyone help please

---

### Post by ChameleonDave on 2008-07-04
Please go to a command-line terminal and enter the following command:

```

cat /etc/fstab

```

---

### Post by irishy on 2008-07-05
thanks I did as you instructed I think typed in what you said
this is what came up
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=87741fe3-7af7-40f1-ac6e-23cfca387c15 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b5351bcc-50f9-43a8-837f-554a1496872a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
tony@tony-desktop:~$ 
Is there something else to do the dvd drive remains unmounted
thanks

---

### Post by ChameleonDave on 2008-07-06
> **irishy said:**
> 
Is there something else to do the dvd drive remains unmounted
thanks

Yes, that was just to collect information.

Now try this:

```

ls -l /dev/cd*  /dev/scd*  /dev/dvd*

```

That should give me the last bit of info I need to see what needs to be fixed.

---

### Post by irishy on 2008-07-07
Thanks again this is what showed up
lrwxrwxrwx  1 root root      4 2008-07-07 13:23 /dev/cdrom -> scd0
lrwxrwxrwx  1 root root      4 2008-07-07 13:23 /dev/cdrw -> scd0
lrwxrwxrwx  1 root root      4 2008-07-07 13:23 /dev/dvd -> scd0
lrwxrwxrwx  1 root root      4 2008-07-07 13:23 /dev/dvdrw -> scd0
brw-rw----+ 1 root cdrom 11, 0 2008-07-07 14:23 /dev/scd0
thanks

---

### Post by mc4man on 2008-07-07
Why don't you put some media in the drive and then run ```
sudo lshw -C disk
```
Ck. here for what should be displayed for type of media inserted
[http://ubuntuforums.org/showthread.php?p=5333436#post5333436](http://ubuntuforums.org/showthread.php?p=5333436#post5333436)
post your complete ...lshw

---

### Post by ChameleonDave on 2008-07-08
What happens when you try this command?

```

**sudo mount -v /media/cdrom0**
ls -l /media/cdrom0

```

---

### Post by irishy on 2008-07-08
thanks for advice I have tried a dvd in the drive and it couldn't play it I tried with cd but same result the cd drive does not show up until I insert the cd
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
hope it makes sense

---

### Post by irishy on 2008-07-08
I am not to sure about all this I have just installed amarok I have copied a cd to the library and now that is playing sorry if this just confusing it is to me

---

### Post by irishy on 2008-07-08
thanks mc4man the result of your instruction was as follows I hope it means something (certainly not to me)
 *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7170A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 1.04
       serial: [Optiarc DVD RW AD-7170A 1.04 Jun21,2007
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-disk
       description: ATA Disk
       product: MAXTOR STM325082
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 9ND0CK2F
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=47954794
thanks in anticipation

---

### Post by ChameleonDave on 2008-07-08
> **irishy said:**
> thanks for advice I have tried a dvd in the drive and it couldn't play it I tried with cd but same result the cd drive does not show up until I insert the cd
 mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts

...


It is not immediately clear what that is the output of.  It appears to be the help message from "sudo mount --help".  Perhaps you could be more specific.

When posting commands or output on this forum, select the text and then click on the "#" button in the editing window.  This will format it as quoted code.  It makes it much much easier to read.

---

### Post by ChameleonDave on 2008-07-08
> **irishy said:**
> I am not to sure about all this I have just installed amarok I have copied a cd to the library and now that is playing sorry if this just confusing it is to me

So, in other words, you are able to mount an audio CD and use a program to access its audio data.

Now try a CD-ROM such as the Ubuntu installation CD.  Are you able to mount it and display its contents in the file manager?

---

### Post by irishy on 2008-07-08
Thanks for the advice I have used the isntallation disc as you have suggested and the cdrom browser shows all the contents and I am able to open them this was done without any input from me and I am able to open the files If this is not what you are asking can you tell me how to open file manager and its location I am not to sure
thanks again

---

### Post by ChameleonDave on 2008-07-08
> **irishy said:**
> Thanks for the advice I have used the isntallation disc as you have suggested and the cdrom browser shows all the contents and I am able to open them this was done without any input from me and I am able to open the files If this is not what you are asking can you tell me how to open file manager and its location I am not to sure
thanks again

The window that the files show up in is called a "file manager".  More specifically, the default Ubuntu/GNOME file manager is called "Nautilus", and the default Kubuntu/KDE file manager is "Konqueror" or "Dolphin".  By way of comparison, on Windows it's called "Windows Explorer".

OK, it looks like your drive is working perfectly for audio CDs and CD-ROMs.  

Is there anything actually not working correctly?  Do DVD-ROMs fail to mount?

---

### Post by irishy on 2008-07-09
Thanks for your reply I put a dvd in the drive and it was identified but when I clicked on it the message "Could not mount could not read from resource" came up I hope this means something
thanks again

---

### Post by ChameleonDave on 2008-07-09
> **irishy said:**
> Thanks for your reply I put a dvd in the drive and it was identified but when I clicked on it the message "Could not mount could not read from resource" came up I hope this means something
thanks again

So CDs work but not DVDs?

Is it a DVD burnt on Windows Vista?

If you insert the DVD and then enter "*sudo mount -v /media/cdrom0*" on the command line, what exactly is the output?  (Quote it using the "#" button in the post editor when you write your reply.)

---

### Post by irishy on 2008-07-09
"sudo mount -v /media/cdromO"
bash: sudo mount -v /media/cdromO: No such file or directory
I am losing it here  I don't know how to post it  with the hash key the dvd I am using is a bought pre recorded one please advise
thanks

---

### Post by ChameleonDave on 2008-07-09
> **irishy said:**
> "sudo mount -v /media/cdromO"
bash: sudo mount -v /media/cdromO: No such file or directory
I am losing it here  I don't know how to post it  with the hash key the dvd I am using is a bought pre recorded one please advise
thanks

I can see there that you have put a letter O instead of a zero.  That is why it fails.  It would be much better if you copied and pasted instead of typing stuff out.  That would avoid typing errors.

When you write a reply to this, look at the box you're editing in.  See how there is a sort of bar at the top where you can choose fonts and suchlike?  There is a button with a hash sign on it there.  To mark a bit of text as being code, select the text and then click on that button.

---

### Post by irishy on 2008-07-10
```
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
```
This is the result I hope this is right and means something
thanks

---

### Post by ChameleonDave on 2008-07-10
> **irishy said:**
> ```
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
```
This is the result I hope this is right and means something
thanks

Well, it means what it says!  :-)

It means that the drive identified as "/dev/scd0" is currently mounted (i.e. you can access its files) at "/media/cdrom0".

If it tells you that, then the disc should be working fine.  You should be able to type "ls /media/cdrom0" and get a listing of the contents of the drive.  You should be able to open the drive in your file manager with "konqueror /media/cdrom0" or "nautilus /media/cdrom0".

---

### Post by irishy on 2008-07-10
I thank you for all your patience but I just don't know what is meant in your instruction, how do I access nautilus is it requiring installing and what you are telling has it to be done every time I want to access a dvd thanks and sorry for not understanding

---

### Post by ChameleonDave on 2008-07-10
> **irishy said:**
> I thank you for all your patience but I just don't know what is meant in your instruction, how do I access nautilus is it requiring installing and what you are telling has it to be done every time I want to access a dvd thanks and sorry for not understanding

You access it by typing what I wrote.  Those were commands to type into the terminal.  You didn't really have to understand them, just enter them into the terminal.  If the one with "nautilus" doesn't work, try "konqueror" instead.

I'm trying to see if we can successfully mount everything you want to mount.  Once we've done that, we'll see about having it happen automatically.

---

### Post by irishy on 2008-07-10
Thanks again there was no response from the commands you gave me I had copied and pasted as you previously suggested unless again I am missing the point
thanks

---

### Post by ChameleonDave on 2008-07-10
> **irishy said:**
> Thanks again there was no response from the commands you gave me I had copied and pasted as you previously suggested unless again I am missing the point
thanks

Surely that's not possible.

You're telling me that when you use the "mount" command, it tells you that it is already mounted at "/media/cdrom0", and that when you then do "konqueror /media/cdrom0" the terminal responds with absolutely nothing at all?

Even if the Konqueror program were somehow missing from your Kubuntu installation, there would be a message telling you so.  There is no way that it would just say nothing.  I won't believe that without a screenshot proving it!

---

### Post by irishy on 2008-07-11
thanks  the result was that when I entered both commands separately there was no result unless I am doing something wrong but I copied and pasted both commands 
thanks

---

### Post by ChameleonDave on 2008-07-11
> **irishy said:**
> thanks  the result was that when I entered both commands separately there was no result unless I am doing something wrong but I copied and pasted both commands 
thanks

No result at all?

OK, let's check that we're on the same wavelength here.

I want you to type these into a command-line terminal.  Now, I believe that you are running Kubuntu (i.e. the KDE version of Ubuntu).  That means that your terminal program is called "Konsole".  Open Konsole.  Type some commands, pressing Enter after each one.

For example, try "df".  It should display a report on how much disk space you have left.  Does that work?

Now enter "mount".  It should display a report of all your mounted stuff.  Does that work?

Now enter "sudo mount -v /media/cdrom0".  It should either mount it or tell you it's already mounted.

If that works, do "ls -l /media/cdrom0".  It should display a list of the contents of the drive (if the drive is mounted).

Is there really no response at all?

---

### Post by irishy on 2008-07-11
Thanks again I am using Hardy Heron, this is the result of your instructions
```
:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            205846148   3564620 191907156   2% /
varrun                  485024       100    484924   1% /var/run
varlock                 485024         0    485024   0% /var/lock
udev                    485024        48    484976   1% /dev
devshm                  485024        12    485012   1% /dev/shm
lrm                     485024     38684    446340   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon     205846148   3564620 191907156   2% /home/tony/.gvfs
:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/tony/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tony)
tony@tony-desktop:~$ sudo mount -v /media/cdrom0ls -l /media/cdrom0
[sudo] password for tony: 
mount: you didn't specify a filesystem type for /media/cdrom0ls
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying fuseblk
mount: special device /media/cdrom0ls does not exist
:~$ 


```I am never on the same wavelength as anyone else
thanks again

---

### Post by ChameleonDave on 2008-07-11
> **irishy said:**
> 
tony@tony-desktop:~$ sudo mount -v /media/cdrom0ls -l /media/cdrom0


Just look what you did there!

---

### Post by irishy on 2008-07-11
Sorry about that this is what I have just done. I hope that's better tony@tony-desktop:```
~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            205846148   3565280 191906496   2% /
varrun                  485024       100    484924   1% /var/run
varlock                 485024         0    485024   0% /var/lock
udev                    485024        48    484976   1% /dev
devshm                  485024        12    485012   1% /dev/shm
lrm                     485024     38684    446340   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon     205846148   3565280 191906496   2% /home/tony/.gvfs
tony@tony-desktop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/tony/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tony)
tony@tony-desktop:~$ sudo mount -v /media/cdrom0
[sudo] password for tony: 
mount: No medium found
```
Thanks

---

### Post by ChameleonDave on 2008-07-11
> **irishy said:**
> 
mount: No medium found

To me, that says that there is no disc in the drive.  There is a disc in there, right?

---

### Post by irishy on 2008-07-11
Even sorrier this is the next attempt 
```
 df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            205846148   3585932 191885844   2% /
varrun                  485024       100    484924   1% /var/run
varlock                 485024         0    485024   0% /var/lock
udev                    485024        56    484968   1% /dev
devshm                  485024        12    485012   1% /dev/shm
gvfs-fuse-daemon     205846148   3585932 191885844   2% /home/tony/.gvfs
tmpfs                   485024     39760    445264   9% /lib/modules/2.6.24-19-generic/volatile
/dev/scd0              3568808   3568808         0 100% /media/cdrom0
tony@tony-desktop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/tony/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tony)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=tony)
tony@tony-desktop:~$ sudo mount -v /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
tony@tony-desktop:~$ ls -l /media/cdrom0
total 4
dr-xr-xr-x 2 4294967295 4294967295  40 2036-02-07 01:58 AUDIO_TS
dr-xr-xr-x 2 4294967295 4294967295 560 2036-02-07 01:58 VIDEO_TS
tony@tony-desktop:~$ 


```
thanks for persevering

---

### Post by ChameleonDave on 2008-07-11
> **irishy said:**
> Even sorrier this is the next attempt 
```

tony@tony-desktop:~$ ls -l /media/cdrom0
total 4
dr-xr-xr-x 2 4294967295 4294967295  40 2036-02-07 01:58 AUDIO_TS
dr-xr-xr-x 2 4294967295 4294967295 560 2036-02-07 01:58 VIDEO_TS
tony@tony-desktop:~$ 


```
That is the contents of the DVD.  You have successfully mounted it.  Indeed, the output from the mount command indicated that it was already mounted.  It seems that your system is now successfully automounting stuff that you insert.  All you have to do is go to the correct directory for it.

If you (without taking the disc out or anything) type "konqueror /media/cdrom0", it should open the DVD in Konqueror.  You can also open Konqueror from the application menu and then type the "/media/cdrom0" location into its address bar.

The next thing you might want to do is watch the DVD in a player.  To do that you will probably have to install software that decodes encrypted DVDs (DVDs are usually encrypted to stop people copying them).  I can tell you how to do that too.

---

### Post by irishy on 2008-07-11
Thanks, the cd/dvd drive now shows up in my computer, when I typed in the konqueror command it was not installed but gave me the code to install I think I have done it correctly and regarding the software decode installation I would be very grateful if you could help 
thanks

---

### Post by ChameleonDave on 2008-07-12
> **irishy said:**
> Thanks, the cd/dvd drive now shows up in my computer, when I typed in the konqueror command it was not installed but gave me the code to install I think I have done it correctly and regarding the software decode installation I would be very grateful if you could help 
thanks
Konqueror wasn't installed?  Hmm, that makes me think that you don't have Kubuntu.

You put "Kubuntu" in the name of this thread, but maybe you made a mistake.  Perhaps you have the default Ubuntu with GNOME.

If you have Kubuntu with KDE 3, the file manager is "konqueror".
If you have Kubuntu with KDE 4, the file manager is "dolphin".
If you have Ubuntu with GNOME, the file manager is "nautilus".
If you have Xubuntu with Xfce, the file manager is "thunar".

Which one did you install?

Anyway, this is how you install stuff for watching DVDs.

First you have to open up your list of software repositories.  Do this with **one** of the following two commands.  (I'm giving two commands because one is right for KDE and the other is right for GNOME.)

```

kdesudo kwrite /etc/apt/sources.list
gksudo gedit /etc/apt/sources.list

```Add the following line to the file (copy and paste)"

```

deb http://packages.medibuntu.org/ hardy free non-free

```Save and close.

Now go back to the terminal, and do this command:

```

sudo apt-get update && sudo apt-get install vlc libdvdcss2 non-free-codecs

```Then log out and log back in again, just in case.

You should now be able to play different types of media.

One good media player is VLC.  Open it from the application menu, or just type "vlc" on the command line.  You can use it to play DVDs, or any media files you have.

---

### Post by irishy on 2008-07-12
Thanks again I think that it is ubuntu it was the second command that worked although I don't know how to prove which version I have, the vlc player you mention I  downloaded and installed it previously this is the result of the commands
 ```
gksudo gedit /etc/apt/sources.listdeb http://packages.medibuntu.org/ hardy free non-free
:~$ sudo apt-get update && sudo apt-get install vlc libdvdcss2 non-free-codecs
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://im.archive.ubuntu.com hardy Release.gpg
Ign http://im.archive.ubuntu.com hardy/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://im.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://im.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://im.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://im.archive.ubuntu.com hardy-updates Release.gpg
Ign http://im.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://im.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://im.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://im.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://im.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://im.archive.ubuntu.com hardy-updates Release              
Hit http://security.ubuntu.com hardy-security/restricted Packages   
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://im.archive.ubuntu.com hardy/main Packages
Hit http://im.archive.ubuntu.com hardy/restricted Packages
Hit http://im.archive.ubuntu.com hardy/main Sources
Hit http://im.archive.ubuntu.com hardy/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://im.archive.ubuntu.com hardy/universe Packages
Hit http://im.archive.ubuntu.com hardy/universe Sources
Hit http://im.archive.ubuntu.com hardy/multiverse Packages
Hit http://im.archive.ubuntu.com hardy/multiverse Sources
Hit http://im.archive.ubuntu.com hardy-updates/main Packages
Hit http://im.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://im.archive.ubuntu.com hardy-updates/main Sources
Hit http://im.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://im.archive.ubuntu.com hardy-updates/universe Packages
Hit http://im.archive.ubuntu.com hardy-updates/universe Sources
Hit http://im.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://im.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate



```
I hope it means something to you I have not progressed any yet
thanks

---

### Post by ChameleonDave on 2008-07-12
> **irishy said:**
> Thanks again I think that it is ubuntu it was the second command that worked although I don't know how to prove which version I have, the vlc player you mention I  downloaded and installed it previously this is the result of the commands
 ```
gksudo gedit /etc/apt/sources.listdeb http://packages.medibuntu.org/ hardy free non-free

```
Again, you didn't look at what you were doing.  Look at that command above.

I told you to do "*gksudo gedit /etc/apt/sources.list*" at the terminal, and then to add the line "*[noparse]deb http://packages.medibuntu.org/ hardy free non-free[/noparse]*" to the file that came up.  You just smooshed it all together.

---

### Post by irishy on 2008-07-12
Thanks again for being there I struggled a bit with this and this is the result if I have got it right
```
gksudo gedit /etc/apt/sources.list
tony@tony-desktop:~$ deb http://packages.medibuntu.org/ hardy free non-free
bash: deb: command not found

```

---

### Post by ChameleonDave on 2008-07-12
> **irishy said:**
> Thanks again for being there I struggled a bit with this and this is the result if I have got it right
```
gksudo gedit /etc/apt/sources.list
tony@tony-desktop:~$ deb http://packages.medibuntu.org/ hardy free non-free
bash: deb: command not found

```
Well, we're getting there.  You managed to separate the two things.  But it's still not right.  You need to put the first one into the terminal and press enter.

That will open up a new window asking you for your password, and then when you've done that, it'll open up another window with an editing program.  You'll see a file with lots of lines beginning with the word "deb".  Right?

At that point, paste the second thing I gave you into the file.  Just put it on its own line right at the end, all by itself.  Then click to save the file and close the editing program.

It's not too hard, is it?  Please, my forehead is bleeding from banging it against the brick wall here... :(

---

### Post by irishy on 2008-07-12
Thanks again 
I did not think anything had happened as a result of your last instruction what I have done is tried to play several dvd's one of which did play, the others all came up with the the same message, An error occurred could not read from resource 
ps thanks and I think I did it right this time

---

### Post by ChameleonDave on 2008-07-12
> **irishy said:**
> Thanks again 
I did not think anything had happened as a result of your last instruction what I have done is tried to play several dvd's one of which did play, the others all came up with the the same message, An error occurred could not read from resource 
ps thanks and I think I did it right this time
No, I doubt it's really sorted out.

Try again.  It's not too hard.

Do the following command in the terminal:

```
gksudo gedit /etc/apt/sources.list
```

It will open a new window.  If it doesn't, then you did something wrong.

Next, paste the following line into the window that opened:

```
deb http://packages.medibuntu.org/ hardy free non-free
```

Click on the "Save" button, then close the window.

You have now given your computer access to new software.

Next, let's install the software:

Go back to the terminal, and enter the following line:

```
sudo apt-get update && sudo apt-get install -y libdvdcss2 non-free-codecs
```

Only then will you be able to play all discs and files.

---

### Post by irishy on 2008-07-13
Thanks for the info I have now tried several times to use your instructions and I am copying and pasting so that should eliminate any mistake this is what shows up
 ```
sudo apt-get update && sudo apt-get install -y libdvdcss2 non-free-codecs
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://im.archive.ubuntu.com hardy Release.gpg                   
Ign http://im.archive.ubuntu.com hardy/main Translation-en_US        
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://im.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://im.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://im.archive.ubuntu.com hardy/multiverse Translation-en_US  
Hit http://im.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://im.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://im.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://im.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://im.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://im.archive.ubuntu.com hardy Release
Hit http://im.archive.ubuntu.com hardy-updates Release                         
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://im.archive.ubuntu.com hardy/main Packages                           
Hit http://im.archive.ubuntu.com hardy/restricted Packages           
Hit http://im.archive.ubuntu.com hardy/main Sources                  
Hit http://im.archive.ubuntu.com hardy/restricted Sources            
Hit http://im.archive.ubuntu.com hardy/universe Packages             
Hit http://im.archive.ubuntu.com hardy/universe Sources              
Hit http://im.archive.ubuntu.com hardy/multiverse Packages           
Hit http://im.archive.ubuntu.com hardy/multiverse Sources            
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://im.archive.ubuntu.com hardy-updates/main Packages         
Hit http://im.archive.ubuntu.com hardy-updates/restricted Packages   
Hit http://im.archive.ubuntu.com hardy-updates/main Sources          
Hit http://im.archive.ubuntu.com hardy-updates/restricted Sources    
Hit http://im.archive.ubuntu.com hardy-updates/universe Packages     
Hit http://im.archive.ubuntu.com hardy-updates/universe Sources      
Hit http://security.ubuntu.com hardy-security/universe Packages      
Hit http://security.ubuntu.com hardy-security/universe Sources       
Hit http://security.ubuntu.com hardy-security/multiverse Packages    
Hit http://im.archive.ubuntu.com hardy-updates/multiverse Packages   
Hit http://im.archive.ubuntu.com hardy-updates/multiverse Sources
Get:1 http://packages.medibuntu.org hardy Release.gpg [189B]
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Get:2 http://packages.medibuntu.org hardy Release [9335B]
Ign http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 190B in 16s (12B/s)
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```
In media player I still get the same error message up 
thanks again

---

### Post by ChameleonDave on 2008-07-13
I think you somehow made a mistake when you pasted the line into the file.

Post the contents of the file here.  You can get the contents of the file by doing "cat /etc/apt/sources.list" on the terminal.

Then I'll be able to see what you did.

---

### Post by irishy on 2008-07-13
Thanks again this is the result
 ```
cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://im.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://im.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://im.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://im.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://im.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://im.archive.ubuntu.com/ubuntu/ hardy universe
deb http://im.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://im.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://im.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://im.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://im.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://im.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://im.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://im.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiversedeb 
deb http://packages.medibuntu.org/ hardy free non-free

 


```

---

### Post by ChameleonDave on 2008-07-13
> **irishy said:**
> Thanks again this is the result
 ```

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse**deb** 
deb http://packages.medibuntu.org/ hardy free non-free

```
There is the problem.  See the extra word "deb" stuck on the end of the line there?  You somehow managed to stick that in there.

Here are some commands to automatically fix that.  Input them exactly.  Really check what you are putting.

```

sudo -s
cd /etc/apt/
cp sources.list  sources.list.backup
cat sources.list.backup | sed s/multiversedeb/multiverse/g > sources.list
apt-get -y install medibuntu-keyring non-free-codecs libdvdcss2
exit

```

---

### Post by irishy on 2008-07-13
Thanks is there just one command or six separate ones

---

### Post by ChameleonDave on 2008-07-13
> **irishy said:**
> Thanks is there just one command or six separate ones
As you can see, they are on six separate lines.  You must, as always, press Enter after each one.

Here is what each command does:

[LIST]
[*]Gives you admin powers;
[*]Put you in the right directory;
[*]Makes a copy of the list of software sources;
[*]Runs through that file looking for the mistake you made, and outputs a corrected version over the top of the list of software sources;
[*]Installs some software;
[*]Gives up the admin powers.
[/LIST]

---

### Post by irishy on 2008-07-13
Thanks again I have either got it wrong again and if I have, I am at  loss to know why, or perhaps one of the commands is wrong this is what is displayed
```
:~# cd /etc/apt/
root@tony-desktop:/etc/apt# cp sources.list  sources.list.backup
root@tony-desktop:/etc/apt# cat sources.list.backup | sed s/multiversedeb/multiverse/g > sources.list
root@tony-desktop:/etc/apt# 
root@tony-desktop:/etc/apt# apt-get -y install medibuntu-keyring non-free-codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gcc-3.3-base libstdc++5 w32codecs
Suggested packages:
  regionset gstreamer0.10-pitfdll mplayer
The following NEW packages will be installed:
  gcc-3.3-base libdvdcss2 libstdc++5 medibuntu-keyring non-free-codecs
  w32codecs
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.8MB of archives.
After this operation, 35.7MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring libdvdcss2 w32codecs non-free-codecs
E: There are problems and -y was used without --force-yes
root@tony-desktop:/etc/apt# 


```
thanks

---

### Post by ChameleonDave on 2008-07-13
> **irishy said:**
> 
E: There are problems and -y was used without --force-yes
root@tony-desktop:/etc/apt# 
We are nearly there!

I put "-y" in there so that it wouldn't ask you any questions, but apparently that wasn't enough.

Just try once again, and we should be finished.

Do this at the terminal.  Don't bother copying the output.

```

sudo apt-get --force-yes update

```

Then do this.  Give me the output.

```

sudo apt-get --force-yes install medibuntu-keyring regionset gcc-3.3-base libstdc++5 w32codecs libdvdcss2

```

Make sure the command is absolutely correct!

---

### Post by irishy on 2008-07-14
Thanks this is what happened~$ sudo apt-get --force-yes update
[sudo] password for: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy Release
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/main Sources                  
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/universe Sources              
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
  510 Not Extended [IP: 87.98.242.10 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
  510 Not Extended [IP: 87.98.242.10 80]
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  510 Not Extended [IP: 87.98.242.10 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  510 Not Extended [IP: 87.98.242.10 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
tony@tony-desktop:~$ sudo apt-get --force-yes install medibuntu-keyring regionset gcc-3.3-base libstdc++5 w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gstreamer0.10-pitfdll mplayer
The following NEW packages will be installed:
  gcc-3.3-base libdvdcss2 libstdc++5 medibuntu-keyring regionset w32codecs
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.8MB of archives.
After this operation, 35.8MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring libdvdcss2 w32codecs
Install these packages without verification [y/N]?  
I left it at this position
thanks again

---

### Post by ChameleonDave on 2008-07-14
> **irishy said:**
> 
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring libdvdcss2 w32codecs
 Install these packages without verification [y/N]?  
I left it at this position
thanks again
Say yes, say yes, say yes!!

I could have sworn that "--force-yes" would make it just install without asking you.  But never mind.  Just tell it yes.

If you have said no, then go back and do the last command again.  Just the last command.

(The reason why it says they can't be authenticated is that we haven't installed the "medibuntu-keyring" yet.  I'm trying to install that, so that the warning goes away.)

---

### Post by irishy on 2008-07-14
Thanks that has done it I appreciate your patience and I will understand if you avoid my posts in future
thanks 
Tony

---

### Post by ChameleonDave on 2008-07-14
> **irishy said:**
> Thanks that has done it I appreciate your patience and I will understand if you avoid my posts in future
thanks 
Tony
Hahah, well, it has been quite an exercise in patience, but a challenge is fun too!  Don't hesitate to alert me to any future problems you have.

Have you actually managed to watch a DVD yet?

If you're feeling up to it, use the menu marked "Thread Tools" (it near the top of this page) to mark this thread as "SOLVED".

---

### Post by irishy on 2008-07-14
Thanks again I done as you have asked and I have a dvd on at the moment
thanks
Tony

---

