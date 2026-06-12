---
title: "Hard Disks not mounting after using Storage Device Manager"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by TaiwanTom on 2013-06-01
After using Storage Device Manager my disks do not automatically mount anymore.  One doesn't mount at all.   I have tried to uncheck the read-only box in Storage Device Manager and to check a few other boxes but none of the changes I make "stick."  Even after hitting apply.  Any ideas what could be going wrong?

---

### Post by vanadium on 2013-06-01
Using storage device manager is not always a good idea. You first may want to remove the lines from the config file /etc/fstab that storage device manager has put there. Post here the output of the terminal command
```

cat /etc/fstab

```
and we will be able to tell you what lines to remove again.

Please also tell what Ubuntu version you are using.

---

### Post by TaiwanTom on 2013-06-02
Thank you for your prompt response,

fstab:
proc                                       /proc              proc  nodev,noexec,nosuid                 0  0  
UUID=1906c9d3-d4f1-4ba7-a353-697c31aa43f4  /                  ext3  defaults                            0  1  
UUID=4a8d37a5-cac4-441b-b632-1512ac4b4dfb  none               swap  sw                                  0  0  
/dev/fd0                                   /media/floppy0     auto  rw,user,noauto,exec,utf8            0  0  
/dev/sdb2                                  /media/Torrent     ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdc2                                  /media/Linux       ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sda4                                  /media/FilesPrime  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdb1                                  /media/sdb1        vfat  defaults                            0  0  
/dev/sdc1                                  /media/sdc1        ntfs  nls=iso8859-1,users,umask=000,user  0  0  


version:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise

---

### Post by MidnightGrey on 2013-06-03
> **TaiwanTom said:**
> Thank you for your prompt response,

fstab:
proc                                       /proc              proc  nodev,noexec,nosuid                 0  0  
UUID=1906c9d3-d4f1-4ba7-a353-697c31aa43f4  /                  ext3  defaults                            0  1  
UUID=4a8d37a5-cac4-441b-b632-1512ac4b4dfb  none               swap  sw                                  0  0  
/dev/fd0                                   /media/floppy0     auto  rw,user,noauto,exec,utf8            0  0  
/dev/sdb2                                  /media/Torrent     ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdc2                                  /media/Linux       ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sda4                                  /media/FilesPrime  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdb1                                  /media/sdb1        vfat  defaults                            0  0  
/dev/sdc1                                  /media/sdc1        ntfs  nls=iso8859-1,users,umask=000,user  0  0  


Hi there,

You may want to wait for more expert opinions before acting, but heres my response: when mounting partitions using the /dev/sd**x** these can shift around and change, especially if they are attached to external drives which you take off/on. I would suggest trying the following:
1) backup your fstab
> $ cp /etc/fstab /etc/fstab.bak
2) delete the following lines:
> /dev/fd0                                   /media/floppy0     auto  rw,user,noauto,exec,utf8            0  0  
/dev/sdb2                                  /media/Torrent     ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdc2                                  /media/Linux       ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sda4                                  /media/FilesPrime  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sdb1                                  /media/sdb1        vfat  defaults                            0  0  
/dev/sdc1                                  /media/sdc1        ntfs  nls=iso8859-1,users,umask=000,user  0  0  

3) restart
4) After restart, look at blkid
> $ blkid 

Are your (unmounted) partitions visable in blkid? If so you can go ahead and mount them manually (or re-config fstab to mount them at-start up).

---

### Post by Morbius1 on 2013-06-03
[1] Never use Storage Device Manager ( pySDM ) again as long as you live.
[COLOR=#0000cd]*This will be an easy promise to keep since it has been completely removed from the Ubuntu repositories from 12.10 and beyond.*[/COLOR]

[2] To piggyback on          MidnightGrey's post you might want to post the output of the following command so people here can clean things up:
```
sudo blkid -c /dev/null
```
[COLOR=#0000cd]*You have too many partitions to have them identified as /dev/sdxy as          *[/COLOR][COLOR=#0000cd]*MidnightGrey mentioned. They should be designated by UUID instead which the command above will list for you. This isn't really your fault its pySDM which was written some time during the Eisenhower administration and not maintained since.*[/COLOR]

[3] There are templates you can use for ntfs and fat32 internal partitions, something like these:
> UUID=DA9056C19056A3B3 /media/D_Drive ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
UUID=C4DB-C1B0 /media/E_Drive vfat defaults,utf8,umask=000,uid=1000 0 2

---

### Post by TaiwanTom on 2013-06-03
Thanks a lot everyone, That seems to have done the trick.  I didnt get the "couldn't mount press 's' to skip mounting or..." message at boot up, and all drives are now mountable, but only manually.  

Only one disk is external, and it is never removed.  The other two are internal.  How should I solve this?  Further edits to fstab?

tom@Death-star:/$ sudo blkid -c /dev/null
/dev/sda1: LABEL="Windows" UUID="C4808E6A808E6332" TYPE="ntfs" 
/dev/sda2: UUID="1906c9d3-d4f1-4ba7-a353-697c31aa43f4" TYPE="ext3" 
/dev/sda4: LABEL="Files Prime" UUID="5874C4B574C496E2" TYPE="ntfs" 
/dev/sda5: UUID="4a8d37a5-cac4-441b-b632-1512ac4b4dfb" TYPE="swap" 
/dev/sdb1: LABEL="EFI" UUID="70D6-1701" TYPE="vfat" 
/dev/sdb2: LABEL="Torrent" UUID="1CDD-5D19" TYPE="exfat" 
/dev/sdc1: LABEL="Movies" UUID="BCD8585CD858174C" TYPE="ntfs" 
/dev/sdc2: LABEL="Backup" UUID="1CE846D5E846ACB8" TYPE="ntfs"

---

### Post by MidnightGrey on 2013-06-03
to mount a ntfs partion, add this line to your /etc/fstab:
```
UUID=C4808E6A808E6332 /media/Windows ntfs auto,user,exec,rw,windows_names 0 0
```

do this for each of your NTFS partitions, make sure to match the UUIDS.

I am not familiar with the exFAT (is that a SSD?), but the same code should work, if not, then just remove the line in fstab later.
```
UUID=1CDD-5D19 /media/Torrent exfat auto,user,exec,rw,windows_names 0 0
```

Lastly, your vfat i think is Your Windows Boot Loader. If so you should just leave it out and dont touch it if you want to ever go  back into windows again.
You can also do this to lock yourself out from mounting it:
```
UUID=70D6-1701 /media/efi nouser,ro,noexec 0 0
```

---

### Post by TaiwanTom on 2013-06-03
Thanks MidnightGrey,
From what I read things can be tricky when using FUSE to mount exfat volumes.  Is it possible to set it to auto-mount?

That's an important one, because I have multiple applications that launch at start-up that need to refer to it.

---

### Post by MidnightGrey on 2013-06-03
Hey sorry i did some ninja edits you may not have seen, does that answer your question?

Also i am not an expert with exfat at all, so take my advice lightly.

---

### Post by TaiwanTom on 2013-06-03
That helps, thanks again.  

I remember looking at that 200 MB partition and wondering what it was there for.

exfat is a strange format, and I'm not sure why I formatted this way.  This disk, a long time ago was the boot drive for another machine, but now its just an external.  My current boot drive is one of the internals.  So the boot loader on my vfat volume shouldn't be important right?

Is there a way to do away with it without reformatting the whole disk?

---

### Post by MidnightGrey on 2013-06-03
Unfortunately theres no way around it other than to format the partition. 
If your Torrents partition isnt too big you can copy over the files to another drive/format/move back i guess.

---

### Post by Morbius1 on 2013-06-03
Well, at this point too many cooks will definitely spoil this broth but ....

> UUID=C4808E6A808E6332 /media/Windows ntfs auto,user,exec,rw,windows_names 0 0
There's no need for auto and rw since they are in the defaults. user is silly, you haven't addressed the inability to send something to the trash correctly, character encoding is missing, and  .... 
> UUID=70D6-1701 /media/efi nouser,ro,noexec 0 0
Do you want the system to guess what filesystem to use? And at best I'll give you the benefit of the doubt and guess it's a typo that you used "nouser" and really meant to use "noauto" if it is in fact the "windows boot loader".

---

### Post by MidnightGrey on 2013-06-03
yea you're write i wrote pretty hastely. feel free to correct it.

---

### Post by TaiwanTom on 2013-06-04
Thanks guys,
So what I need to do is add the lines MidnightGrey posted, with Morbius1's corrections to fstab?  

Its funny that Morbius mentioned it, but my trash can does have some strange limitations on how much data can be sent there.  Does that mean I should or should not add 'user' to the line?  

Thanks again, and sorry my ignorance has dragged this out over a few days.

---

### Post by Morbius1 on 2013-06-04
An ntfs line should look something like this which will take care of most contingencies:
```
 UUID=5874C4B574C496E2 /media/FilesPrime ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```

Here is the definition of the "user" option:
> user:    Allow an ordinary user to mount the filesystem.  The name of the mounting  user  is
              written  to  mtab so that he can unmount the filesystem again.
First Sentence: Why do you want an ordinary user to mount the partition. The whole idea of having it in fstab is so the ordinary user doesn't have to do anything.

Second Sentence and the one most pertinent in this discussion: During the booting process there is only one user at the moment the system reads the instructions in fstab and that is root. Only root will be able to unmount the partition. The user option is meaningless in this situation since that is the default behavior. 

The only practical use of "user" is when you also add "noauto" but that means the partition will not mount at boot forcing the user to mount it manually.

---

