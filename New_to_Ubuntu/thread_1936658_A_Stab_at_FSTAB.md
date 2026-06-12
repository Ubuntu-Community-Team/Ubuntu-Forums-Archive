---
title: "A Stab at FSTAB"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by lile001 on 2012-03-06
I was involved in a long discussion about installing a hard drive that ended up discussing fstab.  Now, keep in mind, I have absolutely no idea what I am doing here, and this is a [ahem] stab in the dark.  I am trying to get some drives that I added to mount at boot time.  


here is a stab at fstab. The "f" has the same meaning as the "F" in RTFM, I beilieve.  here goes.  I have been beating my brains out trying to understand some Community Documentation about fstab, but it isn't sinking into my thick head very well.  

It would have been really handy if the first three or four pages of gibberish i found about fstab had bothered to mention this way to find out about UUIDs.  I just learned what they are yesterday, so I am really not sure I understand any of this stuff: 

     Code:
     sudo blkid 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="5450-4444" TYPE="vfat" 
 /dev/sda2: LABEL="RECOVERY" UUID="F2DCD958DCD917A5" TYPE="ntfs"  
/dev/sda3: LABEL="OS" UUID="8A20DBB920DBAB09" TYPE="ntfs"  
/dev/sda5: UUID="c1231a18-734c-4df2-b917-c7d8177fea45" TYPE="ext4"  
/dev/sda6: UUID="97d9f6ea-ad97-4fbd-aef7-ee4993a098ef" TYPE="swap" 
 /dev/sdb1: LABEL="Bigdrive1" UUID="2d3d8a4a-95c4-4056-992a-c5cb9d3895bc" TYPE="ext3"
 /dev/sdb2: LABEL="Bigdrive2" UUID="698b3511-cbb6-44e1-b991-bf7fbf1813cf" TYPE="ext2" 

So I have added these lines to a copy of fstab (not the original!)  
 
    Code:
     # /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda5 during installation 
UUID=c1231a18-734c-4df2-b917-c7d8177fea45 /               ext4    errors=remount-ro 0       1 
# swap was on /dev/sda6 during installation 
UUID=97d9f6ea-ad97-4fbd-aef7-ee4993a098ef none            swap    sw              0       0 
#NEW AND PROBABLY ERROR-RIDDLED STUFF ADDED BY ME: 
#LABEL=OS
UUID=8A20DBB920DBAB09 /media/     ntfs    defaults    0    2 
#LABEL=Bigdrive1  
UUID=2d3d8a4a-95c4-4056-992a-c5cb9d3895bc /media/    ext3    defaults    0    2
 #LABEL=Bigdrive2  
UUID=698b3511-cbb6-44e1-b991-bf7fbf1813cf /media/    ext2    defaults    0    2 


OK, what have I got screwed up in that file?

---

### Post by Grenage on 2012-03-06
You want independent mount points ;)

You're listing them all as /media, and they need to be different:

/media/drive1
/media/drive2

You'll probably need to create the mount points first:

```
sudo mkdir /media/drive1
sudo mkdir /media/drive1
```

---

### Post by lechien73 on 2012-03-06
Hi,

Well...on first look, you're trying to mount all 3 drives to /media. You need to create directories in /media and mount the drives to that, so open a terminal window and type:

```
sudo mkdir /media/OS
sudo mkdir /media/Bigdrive1
sudo mkdir /media/Bigdrive2
```

Then adjust your fstab as follows:

```
#LABEL=OS
UUID=8A20DBB920DBAB09 /media/OS ntfs defaults 0 2 
#LABEL=Bigdrive1 
UUID=2d3d8a4a-95c4-4056-992a-c5cb9d3895bc /media/Bigdrive1 ext3 defaults 0 2
#LABEL=Bigdrive2 
UUID=698b3511-cbb6-44e1-b991-bf7fbf1813cf /media/Bigdrive2 ext2 defaults 0 2 
```

Hope this helps :)

---

### Post by oldfred on 2012-03-06
Your mount point is not automatically your label unless you use Nautilus.

From your post. You cannot directly mount /media but have to mount to the mount points you create first, labels do not have to be the mount point which can get confusing. I have labeled a partition Data but mounted it as data. Since Linux is case sensitive Data was not data.

do this first:
# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/OS
sudo mkdir /media/Bigdrive1  
sudo mkdir /media/Bigdrive2


#LABEL=OS
UUID=8A20DBB920DBAB09 /media[COLOR=Red]/OS[/COLOR]     ntfs    defaults    0    2 
#LABEL=Bigdrive1  
UUID=2d3d8a4a-95c4-4056-992a-c5cb9d3895bc /media/[COLOR=Red]Bigdrive1[/COLOR]    ext3    defaults    0    2
 #LABEL=Bigdrive2  
UUID=698b3511-cbb6-44e1-b991-bf7fbf1813cf /media/[COLOR=Red]Bigdrive2[/COLOR]    ext2    defaults    0    2

Was there some reason you used ext2? Unless a small partition and Bigdrive2 is a misnomer, having a journal adds to reliability, so ext3 or better still ext4.

---

### Post by Morbius1 on 2012-03-06
One other minor thing you might consider is changing this:
```
 UUID=8A20DBB920DBAB09 /media/OS ntfs defaults 0 2
```To this:
```
 UUID=8A20DBB920DBAB09 /media/OS ntfs defaults,windows_names 0 0
```Assuming you actually want write access to your windows partition, "windows_names" will prevent you from saving a file with a name that Windows cannot interpret.

---

### Post by oldfred on 2012-03-06
@Morbius1
Good to see you in this thread. I do not know all the details of mounting you do, and in previous thread OP wanted bind also. So I am sure he will ask some more questions.

[http://ubuntuforums.org/showthread.php?t=1936019](http://ubuntuforums.org/showthread.php?t=1936019)

---

### Post by lile001 on 2012-03-06
Hooray!  I will try all these wonderful suggestions and see if it works.

---

### Post by lile001 on 2012-03-06
It worked, partially.  

I believe fstab is now mounting the three drives succssfully.  

rc.local says the following:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount --bind "/media/OS/Users/Qhyrrae" "/home/qhyrrae/WindowsFiles"
mount --bind "/media/OS/Users/Larry" "/home/larry/WindowsFiles"
mount --bind  "/media/Bigdrive1/larry" "/home/larry"
mount --bind  "/media/Bigdrive1/qhyrrae" "/home/qhyrrae"
exit 0
```

However the first two bindings 
mount --bind "/media/OS/Users/Qhyrrae" "/home/qhyrrae/WindowsFiles"
mount --bind "/media/OS/Users/Larry" "/home/larry/WindowsFiles"
are not working - I don't see any windows files in the local WindowsFiles folder I have created on my /home folder. 

This is getting really close!  I wonder what is wrong with the two bind statements?  They have worked in the past.

---

### Post by lechien73 on 2012-03-06
To me it looks like the same problem :)

You need to have unique mount points. So, the first two bindings are being overwritten by the last two.

---

### Post by LewisTM on 2012-03-06
Also, you can put bind mounts in fstab itself
For example by adding these lines:
```
/media/OS/Users/Qhyrrae /home/qhyrrae/WindowsFiles none defaults,bind 0 0
/media/OS/Users/Larry /home/larry/WindowsFiles none defaults,bind 0 0
/media/Bigdrive1/larry /home/larry/Bigdrive none defaults,bind 0 0
/media/Bigdrive1/qhyrrae /home/qhyrrae/Bigdrive none defaults,bind 0 0
```

---

### Post by lile001 on 2012-03-06
> **lechien73 said:**
> To me it looks like the same problem :)

You need to have unique mount points. So, the first two bindings are being overwritten by the last two.

OK, this is the key concept here.  I kept playing Whack-A-Mole with these statements, and only the last two would take effect.  I'd move them around and a different statement would work.  This was confusing, but you've shed some light on it.  

"unique" isn't the way I'd describe it  - apparently "a subdirectory of a bind folder cannot be a bind folder".  If this is the case, only the last bind statement takes effect.  

So here is what I have done that finally worked:

in rc.local I have these statements:
```
mount --bind  "/media/Bigdrive1/larry" "/home/larry/Files"
mount --bind  "/media/Bigdrive1/qhyrrae1" "/home/qhyrrae/Files"
mount --bind "/media/OS/Users/Qhyrrae" "/home/qhyrrae/Windowsfiles"
mount --bind "/media/OS/Users/Larry" "/home/larry/Windowsfiles"
mount --bind "/media/Bigdrive1/Shared" "/home/larry/Shared"
mount --bind "/media/Bigdrive1/Shared" "/home/qhyrrae/Shared"

```

This corresponds to three folders under the user's home folder:  Files, Shared, and Windowsfiles. 

Files is the normal looking stuff you'd see (Documents, etc),  Windowsfiles is the Windows OS stuff in the User's My Documents folder, and Shared is a common area that we store music and pictures that we both want to access.  Both users can get to the Shared folder and changes in it by one are seen by the other.  

hidden files are still going to be directly under home, but they don't take up so much room so that should be fine.  

The advantage is that I can see all three places from one area (it confuses my wife no end to try to surf around the Linux file system to find the Shared folder) but there is lots of drive space available. 

This is a little bit of an unusual case because earlier I painted myself into a corner by not allowing Linux enough room for the files I needed to transfer. I probably could have reinstalled Linux and started over, with who-knows-what new problem.  I decided i wanted to see the Windows stuff and the Shared stuff all at a glance, so I needed to solve the bind problem anyway.  

Hopefully this thread will be useful to someone else, as I have made every possible mistake along the way as usual.

---

### Post by lechien73 on 2012-03-07
Grand job...glad you have it working now :)

If you get chance, please could you use the **Thread Tools** menu above the posts and mark the issue as [SOLVED]?

Thanks & enjoy!!

---

