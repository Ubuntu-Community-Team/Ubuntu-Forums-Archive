---
title: "Problem with external hard drive recognition"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by mzdutchdoll on 2008-06-07
I recently bought a laptop and am running Ubuntu which I am loving aside from the fact that it fails to recognize my external hard drive. As I am new to Ubuntu I would appreciate some help. I have a 2 year old IBM thinkpad with 2 usb slots. My external hard drive requires the use of both. 1 cord being for power only. On my pc it would recognize the device and prompt me about it. i have searched this OE high and low and can't find any recognition of it even being plugged in. But it gets power and lights up as usual.

---

### Post by rickycodie on 2008-06-07
what is the format of the external hard drive?

---

### Post by nebu on 2008-06-07
maybe its a problem with the usb versions.... it had happened to me once on a desktop... where the hard drive was v2.0 and the port was v1.0

---

### Post by waspbr on 2008-06-07
hmmm, don't know if this applies to you, but I have an HP tx1320us and I used ndiswrapper to make the wireless work, at some point one of my usb ports would not work in hardy. This was because ndiswrapper broke something, It got solved eventually after I removed ndiswrapper and installed a newer version. 

Also it could be that your laptop may need a boot line such as irqfixup or irqpool to sort things up, I would recommend searching the forums for your laptop model and check if anyone else has had the same problem.

---

### Post by mzdutchdoll on 2008-06-07
I have no idea but I was using it previously on my Dell desktop. I didn't ever format it so it's just how it came in the box, so standard format I guess? My dell always automatically recognised it.

---

### Post by cariboo on 2008-06-07
Plug it in and check dmesg in a terminal you should see something similar to this:

```
[40289.624274] scsi 6:0:0:0: Direct-Access     LEXAR    JD FIREFLY       1100 PQ: 0 ANSI: 0 CCS
[40289.662652] sd 6:0:0:0: [sde] 1981440 512-byte hardware sectors (1014 MB)
[40289.665522] sd 6:0:0:0: [sde] Write Protect is off
[40289.665527] sd 6:0:0:0: [sde] Mode Sense: 43 00 00 00
[40289.665530] sd 6:0:0:0: [sde] Assuming drive cache: write through
[40289.684624] sd 6:0:0:0: [sde] 1981440 512-byte hardware sectors (1014 MB)
[40289.687492] sd 6:0:0:0: [sde] Write Protect is off
[40289.687496] sd 6:0:0:0: [sde] Mode Sense: 43 00 00 00
[40289.687499] sd 6:0:0:0: [sde] Assuming drive cache: write through
[40289.687505]  sde: sde1

```

If you look at the last line you see in my case sde: sde1. Your case will be different of course. To mount this I would issue the command:

```

sudo mount /dev/sde1 /media/disk
```

It now should be mounted on /media/disk.

You may have to create a directroy in /media call disk:

```
sudo mkdir disk
```

That should do it.

Jim

---

### Post by mzdutchdoll on 2008-06-09
> **cariboo907 said:**
> Plug it in and check dmesg in a terminal you should see something similar to this:

```
[40289.624274] scsi 6:0:0:0: Direct-Access     LEXAR    JD FIREFLY       1100 PQ: 0 ANSI: 0 CCS
[40289.662652] sd 6:0:0:0: [sde] 1981440 512-byte hardware sectors (1014 MB)
[40289.665522] sd 6:0:0:0: [sde] Write Protect is off
[40289.665527] sd 6:0:0:0: [sde] Mode Sense: 43 00 00 00
[40289.665530] sd 6:0:0:0: [sde] Assuming drive cache: write through
[40289.684624] sd 6:0:0:0: [sde] 1981440 512-byte hardware sectors (1014 MB)
[40289.687492] sd 6:0:0:0: [sde] Write Protect is off
[40289.687496] sd 6:0:0:0: [sde] Mode Sense: 43 00 00 00
[40289.687499] sd 6:0:0:0: [sde] Assuming drive cache: write through
[40289.687505]  sde: sde1

```

If you look at the last line you see in my case sde: sde1. Your case will be different of course. To mount this I would issue the command:

```

sudo mount /dev/sde1 /media/disk
```

It now should be mounted on /media/disk.

You may have to create a directroy in /media call disk:

```
sudo mkdir disk
```

That should do it.

Jim
thanks for that Jim I will get my friend to try that for me on the weekend. I'm having another issue now but this time with firefox not instaling java. We tried everything today and it won't work :( no more yahoo games for me! I'm almost thinking of reverting back to xp...that is sadly how much I enjoy my game time on yahoo lol.

---

### Post by waspbr on 2008-06-10
the good news is that java works, you need to isntall it from synaptic tho, you can either install openjdk or sun jre

---

### Post by mgmiller on 2008-06-10
You should not be using the mount command for external usb drives.  You should be using the pmount command.

First, you need to figure out where it is being seen in /dev
so run the command:
```
sudo fdisk -l
```

and look for the entry for the drive.  You may need to unplug and replug the USB cable for it to appear.

Once you know the device name use the pmount command to mount it.

If the fdisk command showed you the drive is /dev/sdg and you want to mount it as "backup"
enter the command:
```
pmount /dev/sdg1 backup
```

Look in /media and you will see a new folder called backup.  

To unmount the drive, use the command pumount with the name of the mount point.
For our example:
```
pumount backup
```
and the entry should disappear from /media

You can now make buttons for your panel to mount and unmount and save a bookmark in nautilus for the mounted location to semi automate the whole thing.

---

### Post by mzdutchdoll on 2008-06-11
I am really confused now but I will get my friend to help me out, I can't attempt any of that coding stuff on my own. I am a Windows girl from way back and have only been using Ubuntu for just short of a week. :lolflag:

---

### Post by mzdutchdoll on 2008-06-11
Just writing again to say the external hardrive issue has just been solved about 10 minutes ago :) Thanks so much to everyone for your tips!!! I'll have to start a new thread though regarding Java because even after following the advice above it's not working!! :(

---

