---
title: "hard drive inaccessible"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-29
So this is what it says when i try to open my hard drive.




Cannot mount volume.

You are not privileged to mount the volume 'Zopiac128_160'.




help?

---

### Post by damis648 on 2008-04-29
try

```
sudo mount /dev/XXX /media/disk
```

and replace XXX with the drive listing (SDA1, SDB1, etc...)

---

### Post by Zopiac on 2008-04-29
> **damis648 said:**
> try

```
sudo mount /dev/XXX /media/disk
```

and replace XXX with the drive listing (SDA1, SDB1, etc...)

zopiac@zopiac:~$ /dev/sda1 /media/disk
bash: /dev/sda1: Permission denied

---

### Post by lwvmobile on 2008-04-29
what is the output of 

```
sudo fdisk -l
```

---

### Post by Zopiac on 2008-04-29
> **lwvmobile said:**
> what is the output of 

```
sudo fdisk -l
```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc85a3fbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16709   134215011    7  HPFS/NTFS
/dev/sda2           16710       19457    22073310   83  Linux

---

### Post by Helios1276 on 2008-04-29
> **Zopiac said:**
> zopiac@zopiac:~$ /dev/sda1 /media/disk
bash: /dev/sda1: Permission denied

Should you use capitals for the drive name in the command?

---

### Post by lwvmobile on 2008-04-29
Ok, give this a shot

```
sudo mkdir /media/#name
```

for #name, just whatever you want to call the mounted partition

then

[HTML]sudo mount -t ntfs /dev/sda1 /media/#name[/HTML]

again, where #name is what you just used the last time.

Post back if this works, so we can get this into fstab for you so it will stick.

---

### Post by Zopiac on 2008-04-29
> **lwvmobile said:**
> Ok, give this a shot

```
sudo mkdir /media/#name
```

for #name, just whatever you want to call the mounted partition

then

[HTML]sudo mount -t ntfs /dev/sda1 /media/#name[/HTML]

again, where #name is what you just used the last time.

Post back if this works, so we can get this into fstab for you so it will stick.

zopiac@zopiac:~$ sudo mkdir /media/Zopiac
zopiac@zopiac:~$ sudo mount -t ntfs /dev/sda1 /media/Zopiac
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/Zopiac -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/Zopiac ntfs-3g force 0 0
zopiac@zopiac:~$

---

### Post by lwvmobile on 2008-04-29
Do you have windows installed on that partition your trying to mount. If so, boot into it and run a scandisk, and then shut down windows properly. Then retry the previous post.

---

### Post by sirdrakey on 2008-04-29
i have the same problem but with an external drive same error message but it is just data mainly videos no os and it loaded with the live cd no problem?

---

### Post by Zopiac on 2008-04-29
> **lwvmobile said:**
> Do you have windows installed on that partition your trying to mount. If so, boot into it and run a scandisk, and then shut down windows properly. Then retry the previous post.

my windows knowledge/memory is dwindling fast, so it seems. scandisk? i know of checkdisk, but when i tried to run that my computer gave me a blank screen and pretty much did absolutely nothing. any other ideas? all i can think of is backing up files and reformatting that hard drive...

---

### Post by lwvmobile on 2008-04-29
Sirdrakely, just as a quick thing to try, I haven't done it before so I can't vouch for it, but

```
sudo apt-get install ntfsprogs
```

then 

```
sudo ntfsfix /dev/xxxx
```

where xxxx is the partition in question

then try to mount it again.

---

### Post by lwvmobile on 2008-04-29
> **Zopiac said:**
> my windows knowledge/memory is dwindling fast, so it seems. scandisk? i know of checkdisk, but when i tried to run that my computer gave me a blank screen and pretty much did absolutely nothing. any other ideas? all i can think of is backing up files and reformatting that hard drive...

Yeah, I hear you, but I think if you go to start-run and do a cmd, or otherwise just find a command prompt, the command is

```
chkdsk -r
```

But you may not have to do that, perhaps just successfully boot and shutdown windows will be good enough.

Alternatively, you may want to try what I suggested moments ago, which is in your case:

[HTML]sudo apt-get install ntfsprogs[/HTML]

then

[HTML]sudo ntfsfix /dev/sda1[/HTML]

and try to mount it again with

[HTML]sudo mount -t ntfs /dev/sda1 /media/Zopiac[/HTML]

---

### Post by Zopiac on 2008-04-29
the thing is, its not called zopiac, thats just what i want it to be called :)
its really: Zopiac128_160

do i put that instead?

---

### Post by Zopiac on 2008-04-29
DP!

zopiac@zopiac:~$ sudo mount -t ntfs /dev/sda1 /media/Zopiac128_160
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
zopiac@zopiac:~$

---

### Post by sirdrakey on 2008-04-29
> Going to empty the journal ($LogFile)... OK
Error opening partition device : No such device or address
Failed to startup volume : No such device or address
Remount failed : No such device or address


empty the journal scared me then it failed a second later it opens a new window with my drive on it so it's working for me now i'll share it with my network and restart to see if it remounts without hassle

thanks lwvmobile

---

### Post by lwvmobile on 2008-04-29
Hmmm... I am confused now.

Do you use any encryption program or back up program with Windows like Norton Ghost or anything like that.

---

### Post by Zopiac on 2008-04-29
> **lwvmobile said:**
> Hmmm... I am confused now.

Do you use any encryption program or back up program with Windows like Norton Ghost or anything like that.

Me? no, i dont think so.......ccleaner is the closest i get ;)

---

### Post by lwvmobile on 2008-04-29
Just for fun, try:

```
sudo umount /dev/sda1
```

then try remounting

```
sudo mount -t ntfs /dev/sda1 /media/zopiac
```

or whatever you originally named the folder in /media/

---

### Post by Zopiac on 2008-04-29
zopiac@zopiac:~$ sudo umount /dev/sda1
[sudo] password for zopiac: 
zopiac@zopiac:~$ 
zopiac@zopiac:~$ sudo mount -t ntfs /dev/sda1 /media/zopiac
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
zopiac@zopiac:~$ 
zopiac@zopiac:~$ sudo mount -t ntfs /dev/sda1 /media/zopiac128_160
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
zopiac@zopiac:~$ sudo mount -t ntfs /dev/sda1 /media/Zopiac128_160
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
zopiac@zopiac:~$

---

### Post by lwvmobile on 2008-04-29
At this point, I am beginning to believe there may be a corruption issue with that NTFS partition. I have noticed that many times Windows can continue to boot a corruption NTFS partition, but if it truly is corrupted you may have issues with that drive or partition in Windows in the future.

My final suggestion for attempting to mount the partition:

```
sudo mount -t ntfs /dev/sda1 /media/zopiac -o force
```

If this doesn't work, then I really do not have any other suggestions at this point. Perhaps somebody else has some ideas, but I would run a hardware diagnostic dft on that hard drive to verify it is in good shape and back up what you may need as a precaution at this point.

---

