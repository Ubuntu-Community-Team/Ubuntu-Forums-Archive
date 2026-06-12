---
title: "lots of problems with Kubuntu"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by nynoah on 2008-11-26
I don't know if anyone else has been having as many problems with Kubuntu as I have.  I wish that Ubuntu had all the nice programs of Kubuntu.  I would give anything for Ubuntu just to have the Kubuntu programs.  I know I can download them.  But they just do not integrate perfectly like they should.  

I am trying to use Kubuntu more but I have some of the following problems

I can not mount my spare hard drives.  I go to the area to mount but I keep on getting errors.  > Return code from mount was 32.
"mount failure"

I can not change the icons individually.  I have changed them on batch.  But I can not change individual icons.  It days I do not have the permission.  Example - am trying to change firefox3 to a different one because the icon batch I have does not have a new one for firefox3

For some reason I can not get more than one desk top.  I have right clicked on it and added 4 but it always defaults back to 1.  

Also another annoying thing.  If I move my mouse off Kopete it does not let me type there.  My spell check does not work under Kopete either.

Amarok will not inventory my music collection.

The System tray seems to be broken.  my icons that are supposed to be stock in there like volume does not appear.  I had to add the other icon from the applet choices but that one is WAY too complicated.  I just want the simple volume one back.

I added another menu bar at the top to try to make it more like Ubuntu.  But I can not do as much with it.  For one I can not change its size it is one default size and that is WAY too small.


There is more.  But I will just leave it like this.  I do have compiz effects working.  But it is nowhere near as nice as Ubuntus.  Does anyone have any advice or can point me to a more expert tutorial site.  Because I am not an expert but I am not a newbie by a long shot.

Thanks everyone.

---

### Post by taurus on 2008-11-26
Can you at least mount your spare harddrive from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by nynoah on 2008-11-26
I was never great at the command line mounting for hard disks.  That was one of the things I was so great full for that Ubuntu fixed.  Here is what I get from those commands.

> 
[sudo] password for noah:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000586e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60049   482343561   83  Linux
/dev/sda2           60050       60801     6040440    5  Extended
/dev/sda5           60050       60801     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe084e084

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24863058

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       35729   286993161   83  Linux
/dev/sdc2           35730       36481     6040440    5  Extended
/dev/sdc5           35730       36481     6040408+  82  Linux swap / Solaris
noah@noah-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=31f7755c-6f64-4370-893a-10e29c96185a / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=39c86878-1fb3-469d-b1b9-f3da186972b7 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
<device> <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/sdb4 <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/sdb1 <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/sdc1 <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
noah@noah-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             457G  325G  109G  75% /
varrun                998M  192K  998M   1% /var/run
varlock               998M     0  998M   0% /var/lock
udev                  998M   84K  998M   1% /dev
devshm                998M     0  998M   0% /dev/shm
lrm                   998M   45M  954M   5% /lib/modules/2.6.24-21-rt/volatile
noah@noah-desktop:~$
                             

---

### Post by nynoah on 2008-11-26
Ok one thing that may look confusing.  I have another hard drive with a broke Ubuntu install on there.  That one is like 350 gig.  My primary ubuntu/kubuntu install is 500gig.

---

### Post by nynoah on 2008-11-26
Do I have to somehow go under the Gui as Root?

---

### Post by nynoah on 2008-11-26
Is this because I have KDE4 installed also?

---

### Post by taurus on 2008-11-26
I suppose you want to mount /dev/sdb1 & /dev/sdc1 since /dev/sdc5 is another swap partition.

```
sudo mkdir /media/sdb1 /media/sdc1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo mount -t ext3 /dev/sdc1 /media/sdc1
sudo swapon /dev/sdc5  <-- This would mount that extra swap partition on the spare harddrive.
df -h
free -m
```

Not sure how you modified your /etc/fstab but it was a mess, especially about this part.

```

<device> <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/sdb4 <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/sdb1 <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/sdc1 <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0

```

---

### Post by nynoah on 2008-11-26
yeah not sure how that got to be such a mess.  I think it has to do with me trying to mount things with the KDE3 gui interface.  I am on KDE4 now.  It is no better.  I wonder what is causing all these bugs.  Should I switch over to Ubuntu to do a permanent CHRAM mod?

---

### Post by nynoah on 2008-11-26
How can I get in there to manually delete some of those ones that are obviously dead?

> <device> <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0


---

### Post by taurus on 2008-11-26
You can edit /etc/fstab and remove those lines with

```
sudo nano -Bw /etc/fstab
```
Once you are done, you can save it and exit with <Ctrl>x and Y for the question.

---

### Post by nynoah on 2008-11-26
Ok I am back under Gnome now.  Here is what it looks like now

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=31f7755c-6f64-4370-893a-10e29c96185a / ext3 nouser,relatime,errors=remount-ro,a$
# /dev/sda5
UUID=39c86878-1fb3-469d-b1b9-f3da186972b7 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb4 <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/scd0 <mount\040point> auto users,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0



---

### Post by taurus on 2008-11-26
You should also remote the last two lines in /etc/fstab as well.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

```

/dev/sdb4 <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/scd0 <mount\040point> auto users,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0

```

And if you want to mount those two Linux partions and that extra swap partition, you can add those three lines at the end of /etc/fstab.

```

/dev/sdc5   none          swap   sw         0   0
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
/dev/sdc1   /media/sdc1   ext3   defaults   0   1

```
Save it and then reboot.  Everything should be in order now.

---

### Post by nynoah on 2008-11-26
Ok I just want the one to be mounted perm.  The other is a lost linux hard drive that I am going to repair someday after I get the money to buy a spare to mirror it first.  That one is called "/dev/sdb1"  that is a straight ext3 only hard drive that has music files and movies stored on it.  Whats to commands for that one alone?

Thanks for your help too

should i just disconect the other drive and redo the commands so you can see it less cluttered?

---

### Post by taurus on 2008-11-26
If you only want to mount the second harddrive, /dev/sdb1, then just add this line to the end of /etc/fstab so it will be mounted automatically each time you boot, making your movies & music available whenever you want.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
Once you have add that entry in /etc/fstab.  Save it and exit gedit editing window.  Then, mount /dev/sdb1 with

```
sudo mount -a
df -h  <-- You should see /dev/sdb1 is now mounted to /media/sdb1 from the output.
```

And if you want to be able to write to /media/sdb1 without root privilege, you can change the ownership of /dev/sdb1 from root to your login name.  Assuming your login name is noah, you would do something like

```
sudo chown -R noah:noah /media/sdb1
ls -la /media
```

---

### Post by nynoah on 2008-11-26
Ok sorry if I am making your work harder.  I went in and disconected the other hard drive and moved the port ribbon to be in the same plug area as my primary hard drive.  I reran the code and I am pasting the new code into here.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=31f7755c-6f64-4370-893a-10e29c96185a / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=39c86878-1fb3-469d-b1b9-f3da186972b7 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb4 <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/scd0 <mount\040point> auto users,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0

---

### Post by taurus on 2008-11-26
Instead of using /dev/sdb1, let's find out the UUID for the second harddrive.  It's better that way.  what's the output of this command from a terminal?

```
sudo blkid
```

---

### Post by nynoah on 2008-11-26
This is what I get

> noah@noah-desktop:~$ sudo blkid
/dev/sda1: UUID="31f7755c-6f64-4370-893a-10e29c96185a" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="39c86878-1fb3-469d-b1b9-f3da186972b7" 
/dev/sdb1: UUID="80d687b1-fd1b-4c10-abea-52e91f14dc57" TYPE="ext3" 
noah@noah-desktop:~$ 


---

### Post by taurus on 2008-11-26
I guess you are still using Gnome.  Edit /etc/fstab from a terminal

```
gksudo gedit /etc/fstab
```
and remove the last two lines from it.

```

/dev/sdb4 <mount\040point> auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
/dev/scd0 <mount\040point> auto users,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0 

```
Now, add this line to the end of /etc/fstab to have your second harddrive mounted automatically each time you boot Ubuntu.

```
UUID=80d687b1-fd1b-4c10-abea-52e91f14dc57   /media/sdb1   ext3   defaults   0   2
```
Save it and close down gedit editing window.  Now, mount your second harddrive with

```
sudo mount -a
df -h
```
Again, if you want to have write permission to /media/sdb1, you can change the ownership of /media/sdb1 from root to your login name, noah.

```
sudo chown -R noah:noah /media/sdb1
ls -la /media
```

---

### Post by nynoah on 2008-11-26
Ok I did almost all the things you asked but I got an error.  

> noah@noah-desktop:~$ sudo mount -a
mount: mount point /media/sdb1 does not exist
noah@noah-desktop:~$ 

Closed out terminal and redid the command again and got this.

> noah@noah-desktop:~$ noah@noah-desktop:~$ sudo mount -a
bash: noah@noah-desktop:~$: command not found
noah@noah-desktop:~$ mount: mount point /media/sdb1 does not exist
bash: mount:: command not found
noah@noah-desktop:~$ noah@noah-desktop:~$ 
bash: noah@noah-desktop:~$: command not found
noah@noah-desktop:~$ 
noah@noah-desktop:~$ 
noah@noah-desktop:~$ 
noah@noah-desktop:~$ 

Yes I am in Gnome now too.

---

### Post by nynoah on 2008-11-26
should I unmount this hard drive while I do this stuff.  Is that making a difference?

ok edit..... I unmounted it using partition editor and reran the command still got this.

> noah@noah-desktop:~$ sudo mount -a
mount: mount point /media/sdb1 does not exist
noah@noah-desktop:~$ 


---

### Post by taurus on 2008-11-26
I thought we have already created that mount point.  You just need to create the mount point, /media/sdb1, before you can mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by nynoah on 2008-11-26
Thanks Taurus.  Here is what I get now after the commands.  I am assuming I need to go back and the Chrma commands.

> noah@noah-desktop:~$ sudo mkdir /media/sdb1
[sudo] password for noah: 
noah@noah-desktop:~$ sudo mount -a
noah@noah-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             457G  326G  108G  76% /
varrun                998M  192K  998M   1% /var/run
varlock               998M     0  998M   0% /var/lock
udev                  998M   68K  998M   1% /dev
devshm                998M   12K  998M   1% /dev/shm
lrm                   998M   45M  954M   5% /lib/modules/2.6.24-21-rt/volatile
gvfs-fuse-daemon      457G  326G  108G  76% /home/noah/.gvfs
/dev/sdb1             294G  233G   47G  84% /media/sdb1
noah@noah-desktop:~$ 



---

### Post by nynoah on 2008-11-26
Ok I went back and did the other commands you had from before.  Just picked up where it left off.

I think I did it twice by accident.  Hope that does not confuse of cause a problem


> noah@noah-desktop:~$ sudo mkdir /media/sdb1
[sudo] password for noah: 
noah@noah-desktop:~$ sudo mount -a
noah@noah-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             457G  326G  108G  76% /
varrun                998M  192K  998M   1% /var/run
varlock               998M     0  998M   0% /var/lock
udev                  998M   68K  998M   1% /dev
devshm                998M   12K  998M   1% /dev/shm
lrm                   998M   45M  954M   5% /lib/modules/2.6.24-21-rt/volatile
gvfs-fuse-daemon      457G  326G  108G  76% /home/noah/.gvfs
/dev/sdb1             294G  233G   47G  84% /media/sdb1
noah@noah-desktop:~$ sudo chown -R noah:noah /media/sdb1

ls -la /media
noah@noah-desktop:~$ 
noah@noah-desktop:~$ ls -la /media
total 28
drwxr-xr-x  7 root root 4096 2008-11-26 14:25 .
drwxr-xr-x 23 root root 4096 2008-10-16 20:40 ..
lrwxrwxrwx  1 root root    6 2008-05-02 20:33 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-05-02 20:33 cdrom0
lrwxrwxrwx  1 root root   45 2008-11-01 21:08 .directory -> /etc/kubuntu-default-settings/directory-media
drwx------  2 root root 4096 2008-11-11 15:18 EOS_DIGITAL
lrwxrwxrwx  1 root  999    7 2008-05-02 20:33 floppy -> floppy0
drwxr-xr-x  2 root  999 4096 2008-05-02 20:33 floppy0
-rw-r--r--  1 root root    0 2008-11-26 14:09 .hal-mtab
-rw-------  1 root root    0 2008-11-26 13:18 .hal-mtab-lock
lrwxrwxrwx  1 root root   42 2008-11-01 21:08 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxrwxr-x  2 root fuse 4096 2008-07-18 00:28 ipod
drwxr-xr-x 13 noah noah 4096 2008-06-08 17:46 sdb1
noah@noah-desktop:~$ ls -la /media
total 28
drwxr-xr-x  7 root root 4096 2008-11-26 14:25 .
drwxr-xr-x 23 root root 4096 2008-10-16 20:40 ..
lrwxrwxrwx  1 root root    6 2008-05-02 20:33 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-05-02 20:33 cdrom0
lrwxrwxrwx  1 root root   45 2008-11-01 21:08 .directory -> /etc/kubuntu-default-settings/directory-media
drwx------  2 root root 4096 2008-11-11 15:18 EOS_DIGITAL
lrwxrwxrwx  1 root  999    7 2008-05-02 20:33 floppy -> floppy0
drwxr-xr-x  2 root  999 4096 2008-05-02 20:33 floppy0
-rw-r--r--  1 root root    0 2008-11-26 14:09 .hal-mtab
-rw-------  1 root root    0 2008-11-26 13:18 .hal-mtab-lock
lrwxrwxrwx  1 root root   42 2008-11-01 21:08 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxrwxr-x  2 root fuse 4096 2008-07-18 00:28 ipod
drwxr-xr-x 13 noah noah 4096 2008-06-08 17:46 sdb1
noah@noah-desktop:~$ 


---

### Post by taurus on 2008-11-26
> 
noah@noah-desktop:~$ sudo mkdir /media/sdb1
[sudo] password for noah:
noah@noah-desktop:~$ sudo mount -a
noah@noah-desktop:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 457G 326G 108G 76% /
varrun 998M 192K 998M 1% /var/run
varlock 998M 0 998M 0% /var/lock
udev 998M 68K 998M 1% /dev
devshm 998M 12K 998M 1% /dev/shm
lrm 998M 45M 954M 5% /lib/modules/2.6.24-21-rt/volatile
gvfs-fuse-daemon 457G 326G 108G 76% /home/noah/.gvfs
**[COLOR="Blue"]/dev/sdb1 294G 233G 47G 84% /media/sdb1[/COLOR]**
noah@noah-desktop:~$ 

Yes, now run the chown to change the ownership of /media/sdb1 so you can write to it whenever you want without using sudo/gksudo.

---

### Post by nynoah on 2008-11-26
Ok sorry if this is a redunant questions  (I am fearful because the other hard drive we looked at before with the broken Ubuntu install broke because of a failed Chown mod........long story, but I play stupid in this case till I know exactly what is going on)

I should run  > sudo chown -R noah:noah /media/sdb1
ls -la /media


Or should I some how be incorporating this into it because you put it in BLUE  > /dev/sdb1 294G 233G 47G 84% /media/sdb1


---

### Post by taurus on 2008-11-26
Everything is looking good now.  You are the sole owner of /media/sdb1 so if you run the command below (you don't have to post the output here if you don't wish too), you should see that you own every file & directory in /media/sdb1.  In fact, see if you can copy something to /media/sdb1 without using sudo.

```
ls -la /media/sdb1
```

---

