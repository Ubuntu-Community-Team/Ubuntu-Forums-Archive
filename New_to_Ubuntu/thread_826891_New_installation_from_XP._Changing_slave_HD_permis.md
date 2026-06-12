---
title: "New installation from XP. Changing slave HD permissions and other starter quetsions"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by njigsaw on 2008-06-12
I operate a two disk computer with a smaller 40GB HD used for my system files and a larger 120GB for all my personal storage photos etc. The personal storage disk is something I want constant access to.

I have just eradicated Windows XP by installing Ubuntu onto the "system" disk. 

I cannot however access my personal disk without firstly having to sign on using my password.

If i gain access through using the password and then look at the permissions it comes up as root.

Could someone provide guidance please as to how to obtain constant non-password orientated access?

Also with the command /etc/fstab at what level inthe file hierachy do you use it?, desktop, home or media level?
Cant get it to work at all for me.

As an another aside my disk name has been transferred from windows as "bobs disk"
If I get into terminal and look at the media listings I can see my cd roms and disks etc and it labelled as "bobs\ disk", however I can not manage to get into it via the cd command. Is there some hang up about having spaces in linux file names????

Cheers in anticipation


njigsaw

---

### Post by ukripper on 2008-06-12
> **njigsaw said:**
> I operate a two disk computer with a smaller 40GB HD used for my system files and a larger 120GB for all my personal storage photos etc. The personal storage disk is something I want constant access to.

I have just eradicated Windows XP by installing Ubuntu onto the "system" disk. 

I cannot however access my personal disk without firstly having to sign on using my password.

If i gain access through using the password and then look at the permissions it comes up as root.

Could someone provide guidance please as to how to obtain constant non-password orientated access?

Also with the command /etc/fstab at what level inthe file hierachy do you use it?, desktop, home or media level?
Cant get it to work at all for me.

As an another aside my disk name has been transferred from windows as "bobs disk"
If I get into terminal and look at the media listings I can see my cd roms and disks etc and it labelled as "bobs\ disk", however I can not manage to get into it via the cd command. Is there some hang up about having spaces in linux file names????

Cheers in anticipation


njigsaw

Can you post output of the following command in terminal:
```
sudo fdisk -l
```

---

### Post by njigsaw on 2008-06-12
Right bare with me I think this will work, hopefully...



Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4905    39399381   83  Linux
/dev/hda2            4906        4998      747022+   5  Extended
/dev/hda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  42  SFS

---

### Post by ukripper on 2008-06-12
> **njigsaw said:**
> Right bare with me I think this will work, hopefully...



Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4905    39399381   83  Linux
/dev/hda2            4906        4998      747022+   5  Extended
/dev/hda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  42  SFS

can you post your output of fstab and mount:

```
gedit /etc/fstab
```

and for mount:
```
sudo mount
```

---

### Post by njigsaw on 2008-06-12
UKRIPPER, 


Results of gedit fstab thingy:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ea29a40f-c5b2-446f-acfd-175f584953e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e982ab18-18fd-4996-bafc-2b85db96d17d none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0




Results of sudo mount:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb1 on /media/Neals Disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sda1 on /media/N HAINES IP type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)


I take it that this all means something to you!?!?


Neal

---

### Post by ukripper on 2008-06-12
> **njigsaw said:**
> UKRIPPER, 


Results of gedit fstab thingy:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ea29a40f-c5b2-446f-acfd-175f584953e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e982ab18-18fd-4996-bafc-2b85db96d17d none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0




Results of sudo mount:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb1 on /media/Neals Disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sda1 on /media/N HAINES IP type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)


I take it that this all means something to you!?!?


Neal

install the package ntfs-3 if you dont have:
```
sudo apt-get install ntfs-3g
```


In terminal type this:
```
sudo mkdir /media/disk2
```

```
sudo chmod 755 -R /media/disk2
```

then
```
sudo gedit /etc/fstab
```

gedit will open up. Then

Add this to your fstab at the bottom of it:
```
/dev/hdb1 /media/disk2 ntfs-3g defaults,locale=en_GB.UTF-8 0 0
```

save, exit and then  reboot

---

### Post by hyper_ch on 2008-06-12
You think SFS works with ntfs-3g?

---

### Post by ukripper on 2008-06-12
> **hyper_ch said:**
> You think SFS works with ntfs-3g?

?:confused:

---

### Post by hyper_ch on 2008-06-12
Well, hdb1 is a SFS filesystem - not an ntfs one... can ntfs-3g handle that?

> **njigsaw said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  42  SFS

---

### Post by ukripper on 2008-06-12
> **hyper_ch said:**
> Well, hdb1 is a SFS filesystem - not an ntfs one... can ntfs-3g handle that?

unless I am missing  something, below is mount output:
> /dev/hdb1 on /media/Neals Disk type **ntfs** (rw,nosuid,nodev,umask=222,utf

---

### Post by ukripper on 2008-06-12
> **hyper_ch said:**
> Well, hdb1 is a SFS filesystem - not an ntfs one... can ntfs-3g handle that?

Thanks mate to point taht out i just checked the fdisk output i think I overlooked it. indeed it is SFS. I have no idea about this file system? How do you mount it then in ubuntu?

---

### Post by hyper_ch on 2008-06-12
no clue :) google said it's secure filesystem...  [http://www.cs.auckland.ac.nz/~pgut001/sfs/](http://www.cs.auckland.ac.nz/~pgut001/sfs/)

you might try with ntfs-3g.... but I have no clue if that works.

---

### Post by paulderol on 2008-06-12
[HTML]http://www.runtime.org/[/HTML]

have you been using this? the SFS links indicate that this software corrupts ntfs filesystems into SFS systems?

---

### Post by ukripper on 2008-06-12
found this post googling:
[http://ubuntuforums.org/archive/index.php/t-192275.html](http://ubuntuforums.org/archive/index.php/t-192275.html)

---

### Post by ukripper on 2008-06-12
> **hyper_ch said:**
> no clue :) google said it's secure filesystem...  [http://www.cs.auckland.ac.nz/~pgut001/sfs/](http://www.cs.auckland.ac.nz/~pgut001/sfs/)

you might try with ntfs-3g.... but I have no clue if that works.

in my opinion ntfs-3g should work for this as you see from mount command . mount for /dev/hdb1 is shown as ntfs whihc i guess user has mounted using root password.

---

### Post by njigsaw on 2008-06-12
WAsnt aware that Id used anything from [www.runtime.org](www.runtime.org).

Got as far in the process as doing the chmod but have come up with the following message: 


neal@neal-desktop:~$ sudo chmod -755 /media/disk2
chmod: invalid option -- 7
Try `chmod --help' for more information.

Apologies for being a numpty (give me gas turbines over computers anyday!) but is this just a typo problem or .......

Also reading on, wrt to this SFS malarky, if I save all my files from the HD onto DVD can I perform some sort of reformat that will bring the HD inline and eventually allow me to mount it!?

Thanks in advance

Thanks in ad

---

### Post by paulderol on 2008-06-12
i think the chmod message is a typo, but i believe that your second solution is also viable, and while more brute, makes the whole thing simpler. A formatting tool like gparted can wipe the disk for you to start over with, which has a livecd for that exact purpose [google will produce results, as my bookmarks folder suffered a critical failure last week]. The contents of the DVD can be then replaced in the clean directory, and chown/chmod-ed into compliance with your demands without outside complications.

---

### Post by ukripper on 2008-06-13
> **njigsaw said:**
> WAsnt aware that Id used anything from [www.runtime.org](www.runtime.org).

Got as far in the process as doing the chmod but have come up with the following message: 


neal@neal-desktop:~$ sudo chmod -755 /media/disk2
chmod: invalid option -- 7
Try `chmod --help' for more information.

Apologies for being a numpty (give me gas turbines over computers anyday!) but is this just a typo problem or .......

Also reading on, wrt to this SFS malarky, if I save all my files from the HD onto DVD can I perform some sort of reformat that will bring the HD inline and eventually allow me to mount it!?

Thanks in advance

Thanks in ad

Sorry it is ```
sudo chmod 755 -R /media/disk2
```

my typo.

---

### Post by hyper_ch on 2008-06-13
chmod on fat32/ntfs doesn't do anything ;)

---

### Post by ukripper on 2008-06-13
> **hyper_ch said:**
> chmod on fat32/ntfs doesn't do anything ;)

I agree, but I just wanted to make sure /media/disk2 folder is accessible. for user when fstab mounts it. I am just over cautious.:)

---

### Post by njigsaw on 2008-06-13
I tried the procedure through. 

At the last step where I add the line to the gedit output, save and then reboot I lose sight of the drive from my "places" 

I've removed that line, saved and rebooted and now I can re-see (sp/proper word?) the HD.

Unfortunately still appear to have the same issue of logging on to the drive to gain access.

Trying to understand all of the NTFS FAt32 etc, what is the ideal format for an Ubuntu/ linux HD, and can this be achieved easily via a reformat in Ubuntu or do I have to go back to Maxtor and download their format programs?

Ta

Neal

---

### Post by hyper_ch on 2008-06-13
do you have any data on that partition that you want to access? If not, then you could simple format it with another filesystem... ext3 for linux or ntfs if you want to have it shared with your windows installation.

---

### Post by njigsaw on 2008-06-13
Paulderol,

Sorry I missed your reply in there about the reformatting. Thanks for that.

---

### Post by ukripper on 2008-06-13
We can also go through sudoers route and disable sudo for the this drive access?

---

### Post by ukripper on 2008-06-13
> **hyper_ch said:**
> do you have any data on that partition that you want to access? If not, then you could simple format it with another filesystem... ext3 for linux or ntfs if you want to have it shared with your windows installation.

i fully agree with this. It will make your easier.:)

---

### Post by njigsaw on 2008-06-13
As the HD has all my personal data on it including photos and music I have to store it elsewhere first (ipod for that). 
I use my deskstop as the ultimate storage device and its now going to operate purely in Ubuntu/ Linux. 
I am looking to be able to also access the desktop HD with a dual boot laptop using windows/ ubuntu so that I can put music that was purchased through I-tunes onto my ipod without the hassle of having to get it ino some other recognisable form of coding. Think that the purchased files are AAC.

Therefore do I need to reformat as NTFS to allow both OSystems to see it?

---

### Post by njigsaw on 2008-06-13
Right then, replies are coming in faster than I can type a response. Reformatting it is.

---

### Post by ukripper on 2008-06-13
> **njigsaw said:**
> As the HD has all my personal data on it including photos and music I have to store it elsewhere first (ipod for that). 
I use my deskstop as the ultimate storage device and its now going to operate purely in Ubuntu/ Linux. 
I am looking to be able to also access the desktop HD with a dual boot laptop using windows/ ubuntu so that I can put music that was purchased through I-tunes onto my ipod without the hassle of having to get it ino some other recognisable form of coding. Think that the purchased files are AAC.

Therefore do I need to reformat as NTFS to allow both OSystems to see it?

If you need to access in dual boot environment with windows then yes you have to format either using fat32/ntfs I personally recommend ntfs.

---

### Post by njigsaw on 2008-06-13
One final set of questions then....

Once reformatted, how do I introduce the new drive to the computer and "mount" it etc to get the access I want?

Ta

---

### Post by ukripper on 2008-06-13
> **njigsaw said:**
> One final set of questions then....

Once reformatted, how do I introduce the new drive to the computer and "mount" it etc to get the access I want?

Ta

it will be mounted itself once you reboot in ubuntu as a read only.  
To make it writable from ubuntu you will need to install ntfs-3g using following command or through synaptic package manager:
```
sudo apt-get install ntfs-3g
```
and then go to Application-->system tools-->ntfs configuration (or something like that)

---

### Post by njigsaw on 2008-06-13
Thanks all for your time on this.

I'll go and have a play and let you know how I get on.

Neal


Im sure the days of pen paper were easier!

---

### Post by hyper_ch on 2008-06-13
> **ukripper said:**
> If you need to access in dual boot environment with windows then yes you have to format either using fat32/ntfs I personally recommend ntfs.

can also be ext3.... [http://www.fs-driver.org](http://www.fs-driver.org) --> makes it possible to access ext2/3 partitions from windows.

---

### Post by ukripper on 2008-06-13
> **hyper_ch said:**
> can also be ext3.... [http://www.fs-driver.org](http://www.fs-driver.org) --> makes it possible to access ext2/3 partitions from windows.

Won't recommend that, as ext3 (as a journaling FS) becomes more prone to corruption running from another OS using different filesystem.

NTFS-3g is reversed engineered and is very close to ntfs look alike which prevents that when used from ubuntu.

---

### Post by hyper_ch on 2008-06-13
> **ukripper said:**
> Won't recommend that, as ext3 (as a journaling FS) becomes more prone to corruption running from another OS using different filesystem.

Why? I'd say it's safer to use ext2/3 on windows than ntfs in linux ;)

---

### Post by ukripper on 2008-06-13
> **hyper_ch said:**
> Why? I'd say it's safer to use ext2/3 on windows than ntfs in linux ;)

ntfs-3g has wider community and developers which make constant updates available and fix security holes. The link above is more related to ext2 it may work with ext3 but i won't rely on that as i am not sure if any security updates will be released for that and possibilties of corruption. 

From my personal experience, I can rely on ntfs-3g as i have been using it since 1.5 years never experienced any corruption even using rsync on external ntfs drive attached to my ubuntu-backup server which handles 5 machines backup including ubuntu/fedora and windows through rsync, tar-based backup and unison. I haven't reformatted that ntfs drive since 1.5 years and is under constant load of syncing and backing up.

just a thought..:)

---

### Post by Bradtek on 2008-06-13
A couple of things don't look right here.
NTFS-3g is NOT needed in Hardy or Gutsy  (is OP using older version ?)
If so maybe time to update to hardy

Also OP said 
> I am looking to be able to also access the desktop HD with a dual boot laptop using windows/ ubuntu 

So why the debate over what file system .....  he only needs to setup **Samba shares** unless he actually intends to swap the laptop hard drive into the desktop every time he wants to transfer files ?

Main issue seems to be this SFS file system which the 
simplest answer is Format it as long as the OP can back up his data first.

---

### Post by ukripper on 2008-06-13
> **Bradtek said:**
> A couple of things don't look right here.
NTFS-3g is NOT needed in Hardy or Gutsy  (is OP using older version ?)
If so maybe time to update to hardy

Also OP said 


So why the debate over what file system .....  he only needs to setup **Samba shares** unless he actually intends to swap the laptop hard drive into the desktop every time he wants to transfer files ?

Main issue seems to be this SFS file system which the 
simplest answer is Format it as long as the OP can back up his data first.

It is needed in gutsy if you need to write to the ntfs drive. Hardy, i am not sure as i have upgraded to hardy not a fresh install and it was already there.

---

### Post by Bradtek on 2008-06-13
I should have been more specific.
NTFS-3g  does not need to be installed in 
Gutsy or Hardy as it is already integrated.

[http://www.ubuntu.com/getubuntu/releasenotes/710tour](http://www.ubuntu.com/getubuntu/releasenotes/710tour)
(near the bottom of page)

> NTFS writing

While previous Ubuntu releases only supported read access to Windows (NTFS) partitions, Gutsy Gibbon now fully supports reading and writing to them, by integrating the NTFS-3g project. This significantly eases file and document sharing with Windows. 

---

### Post by ukripper on 2008-06-13
i think you still need set configuration for writable access.
```
sudo apt-get install ntfs-config
``` should do for hardy.

---

### Post by hyper_ch on 2008-06-13
> **ukripper said:**
> ntfs-3g has wider community and developers which make constant updates available and fix security holes.
Still ntfs is closed source and it's backward engineered...

> **ukripper said:**
> The link above is more related to ext2 it may work with ext3 but i won't rely on that as i am not sure if any security updates will be released for that and possibilties of corruption.
Ext3 is nothing more but ext2 with file journaling. Completely backward compatible and as both ext2 and ext3 are opensource an adaption to windows will be, IMHO, more reliable than the backward engineering of ntfs-3g....

---

### Post by ukripper on 2008-06-13
> Still ntfs is closed source and it's backward engineered...

NTFS-3G is open source and still supported and updated regularly by large community and making life easier for people in dual booting mode.

> Ext3 is nothing more but ext2 with file journaling. Completely backward compatible and as both ext2 and ext3 are opensource an adaption to windows will be, IMHO, more reliable than the backward engineering of ntfs-3g....

As pointed out earlier, EXT3 is journaling FS and is more prone to corruption during writing from ntfs fs as opposed to writing from ext3 to ntfs-3g and is also open source [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/).

---

### Post by Bradtek on 2008-06-13
I'm writing this from Hardy and have previously used Gutsy.
I have never had to install or configure anything to be able 
to write to any of my 3 NTFS drives. (that I was aware of)
I just copy/paste a file from Home folder to 2 different 
NTFS drives and is totally seamless.

I am tempted now to reboot into Gutsy Live CD to double check this lol.

---

### Post by ukripper on 2008-06-13
> **Bradtek said:**
> I'm writing this from Hardy and have previously used Gutsy.
I have never had to install or configure anything to be able 
to write to any of my 3 NTFS drives. (that I was aware of)
I just copy/paste a file from Home folder to 2 different 
NTFS drives and is totally seamless.

I am tempted now to reboot into Gutsy Live CD to double check this lol.

interesting. i had to tinker with my edgy, feisty and gutsy to make ntfs-3g writable. May be i tinkered alot that it won't work without I play with it again.:lolflag:

---

### Post by hyper_ch on 2008-06-13
> **ukripper said:**
> NTFS-3G is open source and still supported and updated regularly by large community and making life easier for people in dual booting mode.
NTFS is not... > The exact file system specification is a trade secret, although (since NTFS v3.00) it can be licensed commercially from Microsoft through their Intellectual Property Licensing program.

> **ukripper said:**
> As pointed out earlier, EXT3 is journaling FS and is more prone to corruption during writing from ntfs fs as opposed to writing from ext3 to ntfs-3g.
Proof?

---

### Post by ukripper on 2008-06-13
> **hyper_ch said:**
> > NTFS is not... 

I never mentioned NTFS is open source

[QUOTE]Proof?
 
Proove ext3 won't get corrupt in the long run when used under ntfs?

And besides, it makes more sense using open source(ntfs-3g) with open source(ext3) rather than from closed source(ntfs) running open source drivers (ext3 drivers for windows)

---

### Post by Bradtek on 2008-06-13
I can confirm Gutsy Live CD allows me to Write to NTFS partition
copy/paste OK & edit file / save OK.
Only had to Mount Drive, which I don't have to do in Hardy

---

### Post by hyper_ch on 2008-06-13
> **ukripper said:**
> I never mentioned NTFS is open source
And hence it's backward engineered and hence there might still be unnoticed problems which could corrupt your whole partition...

> **ukripper said:**
> Proove ext3 won't get corrupt in the long run when used under ntfs?
Never seen any incident reported anywhere with fs-driver... au contraire to ntfs-3g

---

### Post by ukripper on 2008-06-13
same with ntfs-3g.:)

i guess it all boils down to matter of choice and opinions.

Nevermind, to OP could you let us know if your issues are resolved or you are still having problem?

---

### Post by ukripper on 2008-06-13
> **Bradtek said:**
> I can confirm Gutsy Live CD allows me to Write to NTFS partition
copy/paste OK & edit file / save OK.
Only had to Mount Drive, which I don't have to do in Hardy

Nice one! i am glad ubuntu package maintainers thought ntfs-3g as a viable and important option to be included in ubuntu out of the box.:)

---

### Post by njigsaw on 2008-06-13
Right then chaps,
For whatever reasonns the Gnome partioner editor wont allow me to do NTFS. 

Ive selected FAT32 as it was available and as I understand can be read by both Windows and Ubuntu.

having done this and rebooted my pc I still have the logon problem.

ANy guidance as to getting rid of the logon requirement gratefully accepted again.

Neal

See following logs
:
neal@neal-desktop:~$ sudo mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)


neal@neal-desktop:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4905    39399381   83  Linux
/dev/hda2            4906        4998      747022+   5  Extended
/dev/hda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+   b  W95 FAT32



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ea29a40f-c5b2-446f-acfd-175f584953e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e982ab18-18fd-4996-bafc-2b85db96d17d none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by ukripper on 2008-06-13
> **njigsaw said:**
> Right then chaps,
For whatever reasonns the Gnome partioner editor wont allow me to do NTFS. 

Ive selected FAT32 as it was available and as I understand can be read by both Windows and Ubuntu.

having done this and rebooted my pc I still have the logon problem.

ANy guidance as to getting rid of the logon requirement gratefully accepted again.

Neal

See following logs
:
neal@neal-desktop:~$ sudo mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)


neal@neal-desktop:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4905    39399381   83  Linux
/dev/hda2            4906        4998      747022+   5  Extended
/dev/hda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+   b  W95 FAT32



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ea29a40f-c5b2-446f-acfd-175f584953e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e982ab18-18fd-4996-bafc-2b85db96d17d none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

what kind of logon problems you are having? can post output of the following:
```
dmesg | tail
```

---

### Post by njigsaw on 2008-06-13
It goes back to the origianl issue of the drive being shown in my devices but  when I click on it for the first time I have to put in my master password to gain access.
As it is meant to be a slave drive I dont want to have this hassle.

I still cant write to it either as it tells me I dont have permissions to do this.Wont allow me to change the permissions either.

---

### Post by ukripper on 2008-06-13
> **njigsaw said:**
> It goes back to the origianl issue of the drive being shown in my devices but  when I click on it for the first time I have to put in my master password to gain access.
As it is meant to be a slave drive I dont want to have this hassle.

I still cant write to it either as it tells me I dont have permissions to do this.Wont allow me to change the permissions either.

i perosnally think you should stick to ext3/ntfs, fat32 has its own limitations.

Let me get this straight first. How exactly you want to use this drive? from dual boot or over the network?

---

### Post by njigsaw on 2008-06-13
It is now an Ubuntu only desktop.Was Windows only but that got binned. 
However the slave disk has all my windows files on it which I want to have access to by connecting directly with a cable to a dual boot laptop as well as add to using ubuntu.

As such I need a file system that Win and Ubuntu will happily read.

Having gone down the route of G partition edit that doesnt give me the option of NTFS format.

Looking at the NTFS-3g program it is only providing an option for external drives not internal ones.

WRT the mounting of the disk see attached screen shot for the latest message.

Myhard disk is now a blank piece of canvas to do whatever with since Ive backup up all relevent files.......

Neal

---

### Post by ukripper on 2008-06-13
remove that entry from fstab. 

1. if you want to access this drive using dual boot you can format to ntfs using windows.

2. if you wishing to access this drive using network from another windows machine then you dont need to format this in ntfs. you can format this in ext3 partition and then share your folders via samba and you can access from other windows machine without problem.

---

### Post by Bradtek on 2008-06-13
> I want to have access to by connecting directly with a cable to a dual boot laptop

What kind of cable ?
A network cable, USB, Serial, Parallel,  IDE cable ?

---

### Post by njigsaw on 2008-06-13
Bradtek.

Network cable I believe. Looks like a uk telephone cable connection only fatter!

---

### Post by Bradtek on 2008-06-13
Ok
Have you "connected these 2 computers before ?
If not you should be aware that to directly connect them
(network card to network card) you will need a "Crossover Cable"
and not a normal "Patch Lead"
[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

Now the question of what file system.
The windows Laptop will not care what file system the network uses
so you may aswell use a linux file system "ext3"

You will need to setup samba shares on your Ubuntu PC,
there are Tutorials on how to do that around here somewhere

HOWTO: Setup Samba peer-to-peer with Windows 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

As for this login problem, I probably would have done 
a fresh install of Hardy by now :confused:

---

### Post by njigsaw on 2008-06-13
It is a crossover cable I have and was using between the dsktop and laptop in the windows environment before.  And yes I'm geting close to loading the latest distrubution and starting again.

Im assuming that with going to the latest setup and starting afresh with a newly formatted ext3 slave HD the system will not give me these same issues as 7.04? I only put that on from a disk yesterday!?!

---

### Post by ukripper on 2008-06-13
> As for this login problem, I probably would have done 
a fresh install of Hardy by now

login problem in screenshot is just nothing major, just an /etc/fstab entry which needs to be deleted. delete the hdb1 entry and you are all good.

---

