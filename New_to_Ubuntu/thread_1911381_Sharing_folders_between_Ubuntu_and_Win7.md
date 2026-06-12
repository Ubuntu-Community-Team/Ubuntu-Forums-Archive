---
title: "Sharing folders between Ubuntu and Win7"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by flight ltnt on 2012-01-18
Hi, I've been following this [tutorial]("http://www.http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") to create a dual boot laptop.  I've managed created the partitions as suggested and installed Win7 and Ubuntu 11.10.  The locations for Documents, Music and Pictures have been amended in Win7 to reflect the new folders on the Storage partition however I've come unstuck when I'm trying to make the folder access change for Ubuntu for these folders.

Both NTFS drives are displayed under devices when I open the Home Folder.

Any advice and guidance is much appreciated to get me past this final hurdle!

---

### Post by Double.J on 2012-01-18
Hi there, am I right in thinking that you've got it all set up dual booting and working fine except that when ubuntu tries to write anything to the windows partitions it fails, or nautilus just blanks out the options?

---

### Post by flight ltnt on 2012-01-18
Hi, dual booting is working fine.  I've created folders on the "Storage" partition (Music, Documents, Photos etc) and have linked to them without a problem but I'm having a problem in creating that link in Ubuntu.

What I'm trying to achieve is if I store a file say in Documents on the "Storage" partition I can access it from either OS.

---

### Post by Double.J on 2012-01-18
it sounds like the partitions aren't mounted using the ntfs-3g driver.

Try to unmount the partitions with
```

sudo umount /dev/sdaX

``` Where X is the partition number.

Then try mounting with 
```

sudo mount -t ntfs-3g /dev/sdaX /mountpoint

``` Where X is the partition again, and the mountpoint is the directory to mount at.

Then make this perminent by adding entries for them in the /etc/fstab file
```

sudo nano -w /etc/fstab

```

the entries to add should look like
> 
#name for partition
/dev/sdaX   /mountpoint   ntfs-3g   rw,auto,user,exec,sync   0 0

things to change here - partition number and mountpoint :)

hope it helps!

---

### Post by Double.J on 2012-01-18
Sorry I forgot the links!

Probably best to use syslink to do it. first work out which home folder directories you want to share with windows - for example I can see any reason not to share pictures?

First rename your current pictures directory to Pictures.old - go to your home directory, then:
```

sudo mv Pictures Pictures.old

```

then create a syslink that will redirect to the shared windows pictures folder

```

ln -s /path/to/pictures/directory /home/username/pictures

```

Hope it helps :)

---

### Post by flight ltnt on 2012-01-18
I should have mentioned that I'm new to Ubuntu so still getting to grips with things.  I believe that the partitions are mounted.

I've attached a screen shot of the partition of my HDD.  sda1 is Win7, sda2 is Ubuntu and sda3 is the Storage partition to hold all my data.

[ATTACH]211097[/ATTACH]

---

### Post by Double.J on 2012-01-18
The partitions are definately mounted at the moment, they are showing up in the left hand column of the file manager as 21GB filesystem and storage. see if you have write access to them by clicking on them and then right clicking the mouse in the files window - is new folder blanked out or can you make one?

---

### Post by flight ltnt on 2012-01-18
I can create a "test" folder.  In addition to the folders I created previously there are a few extras that have appeared and a couple of files:-

[ATTACH]211098[/ATTACH]

---

### Post by Double.J on 2012-01-18
Excellent! that means that you have write access to it so it's all working as should be! 

No need to worry about those files - they're for windows, you just don't normally see them - just be careful not to delete them ;)

In terms of getting it working, your done! :)

I'll add a little more of the info I mentioned earlier just in case you want to integrate your shared "storage" partition a bit more into ubuntu? If not, just stop reading and have a nice, strong.. coffee you've earned it!

1) changing where the storage partition mounts- Currently your storage partition is mounting at /media; this is where ubuntu sticks removable flash drives and such later on. Mounting it at /mnt instead is better practice as it won't show up as a drive in your launcher all the time, and ubuntu doesn't make much use of /mnt anyway! Open up a terminal (ctrl+alt+t)and make a new directory to mount at
```

sudo mkdir /mnt/storage

```

2)Get the partition to mount at /mnt/storage automatically when you turn the machine on. This is useful if you're using it to store your media as you can just open up your music player and it can find your files straight away without you having to mount the drive. Again open a terminal and enter
```

gksudo gedit /etc/fstab

```
and paste in the following line
> 
#NTFS Storage Partition
/dev/sda3   /mnt/storage   ntfs-3g   rw,auto,user,exec,sync   0  0


this means that it will now mount at /mnt/storage when ubuntu starts. You can of course use almost any directory you want but /mnt, /home/username and making your own such as /data are the most common :)

in post 5 I showed you an example of how rename the folders in your home directory and then make a link from that directory to the folders in your storage parition. Setting this up would mean that clicking on a folder such as Pictures in ubuntu's home would take you to Pictures in the storage partition? you have to rename and make a link for each folder you'd want to link - I'd suggest pictures, downloads, videos, music and documents - not desktop, templates or examples - leave these as ubuntu only!

Enjoy! :D

Ps don't repeat these steps for the windows primary partition - nothing bad will happen, it's just not good practice to have it mounted when you don't need it to be as it contains all the system stuff for windows to work :)

---

### Post by solarpowertoast on 2012-01-18
> #NTFS Storage Partition
/dev/sda3 /mnt/storage ntfs-3g rw,auto,user,exec,sync 0 0

I believe you could replace rw,auto,user,exec,sync with defaults

```
/dev/sda3 /mnt/stroage ntfs-3g defaults 0 0
```

That's how I've always mounted my NTFS drives for dual boot and I've never had any problems.

gnu/mirow, if you know a reason not to, I'd like to know.  I'm always open to improving my setups.

---

### Post by Double.J on 2012-01-18
> **solarpowertoast said:**
> I believe you could replace rw,auto,user,exec,sync with defaults

```
/dev/sda3 /mnt/stroage ntfs-3g defaults 0 0
```

That's how I've always mounted my NTFS drives for dual boot and I've never had any problems.

gnu/mirow, if you know a reason not to, I'd like to know.  I'm always open to improving my setups.

Hi Solarpowertoast (awesome name btw!) 

I just prefer to use sync instead of async and user instead of nouser really, the rest are just the basics that apply of defaults - I don't think that user/nouser make much difference in ubuntu as root account is disabled, but I believe it's better practice across distros? In reality either should work just fine - after all system partitions use defaults as ... um default lol!

---

### Post by solarpowertoast on 2012-01-18
> I just prefer to use sync instead of async and user instead of nouser really, the rest are just the basics that apply of defaults - I don't think that user/nouser make much difference in ubuntu as root account is disabled, but I believe it's better practice across distros? In reality either should work just fine - after all system partitions use defaults as ... um default lol!

Thanks for the advice, gnu/mirow.  I just modified my fstab file to reflect it.  Glad you like my name!

---

### Post by flight ltnt on 2012-01-19
gnu/mirow

Thanks for your help.  I've made the changes you referred to in post 9 but after rebooting I get the following message:-

An error occurred while mounting /mnt/storage.

Press S to skip mounting or M for manual recovery.

---

### Post by solarpowertoast on 2012-01-19
Try typying ```
sudo mount -a
```
into the terminal.  That will remount your fstab partitions so you can confirm if it works.  It should also tell you the error that is causing it not to mount on bootup.

Also, do you have more than one Harddrive in this computer?  If so, a good practice is to use the partition's UUID rather than sdXX.  to find the UUID type
```
sudo blkid
```
Then, in the /etc/fstab, replace
```
/dev/sda3
```
with the UUID of that partition.  for, instance:

> UUID=XXXXXXXXXXXXXXXXXXXXXXXXXXXX /mnt/storage ntfs-3g rw,auto,user,exec,sync 0 0

---

### Post by flight ltnt on 2012-01-19
Hi Solarpowertoast,
 
I've run that command and got the following message:-
 
Mount is denied because the NTFS volume is already exclusively opened.  The volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser' command.
 
I've only got one HDD in my laptop and it's partitioned as per an earlier screenshot:-
 
sda1 ntfs 19.53Gb for Win7
sda2 ext4 19.53Gb for Ubuntu
sda3 ntfs 107.04Gb for Storage
sda4 extended 2.94Gb
sda5 linux-swap 2.94Gb

---

### Post by solarpowertoast on 2012-01-19
Did Windows shut down correctly?  The only thing I can think of is that Ubuntu thinks Windows is still accessing it.  I could be wrong. but try booting into Windows, then restarting and booting into Ubuntu.  Hopefully this will give Windows a chance to properly dismount it.

---

