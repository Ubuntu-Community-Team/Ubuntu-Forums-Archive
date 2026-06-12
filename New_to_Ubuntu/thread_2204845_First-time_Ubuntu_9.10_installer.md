---
title: "First-time Ubuntu 9.10 installer"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by DukeNukem_2417 on 2014-02-10
Right, I'll spare the backstory about my old PC with the SCSI hard drive and just say this: I have no idea how to get Ubuntu 9.10 to run on the thing.  

I've installed it at least 3 times, and every time I try to run from the SCSI hard drive, I get "No such device: 44f4edc7-1953-4b9f-a19d-eb4ce3685fd7".  And yes, that's the entire message.  I try to boot from the other hard drive partitions, I get similar messages.  The install never made it seem like I had any hard drive problems, I installed the boot loader to the correct drive, but when it gets to the GRUB menu where I choose how to run Ubuntu, it just doesn't work.  

My question is: Do I need to format the drive and reinstall again, or is this a hardware issue?

---

### Post by CharlesA on 2014-02-10
Have you tried a newer version of Ubuntu? 9.10 is ancient. 12.04 is the current Long Term Support release and 13.10 is the current normal release.

Otherwise check what UUID that drive is using by booting a livecd and running this:

```
sudo blkid -c /dev/null
```

---

### Post by DukeNukem_2417 on 2014-02-10
I may have to try that....thanks for the advice, and cool avatar pic.  :)

---

### Post by mörgæs on 2014-02-11
I don't know what you mean by 'old', but if performance is a problem then Lubuntu is worth considering.

---

### Post by DukeNukem_2417 on 2014-02-11
Well, I may have to look into Lubuntu...after I get a new hard drive.  Turns out one of my attempts to wipe the hard drive before installing Ubuntu may have borked it; my tech guy said to run Darik's Boot and Nuke on it, but I'm considering just getting a new 320-gig hard drive.

---

### Post by sudodus on 2014-02-11
Attempts to wipe a hard drive seldom borks it. It may bork the file system or partition table, but it is usually possible to create a new partition table and new file systems with ***gparted*** (when booted from another drive, for example an Ubuntu or Lubuntu install CD/DVD/USB drive).

If gparted fails, you can try to wipe the first megabyte (not the whole drive), and then try again with gparted.

Can you 'see it' with parted or gparted? Post the output of this command in a reply

```
sudo parted -l
``` (at the end: space minus ell)

---

### Post by DukeNukem_2417 on 2014-02-11
Parted Magic sees it, but claims that the filesystem is still messed up.  

I may have to use the partition editor on that to get the thing working....

---

### Post by buzzingrobot on 2014-02-11
> **DukeNukem_2417 said:**
> ... I get "No such device: 44f4edc7-1953-4b9f-a19d-eb4ce3685fd7...

Just guessing here....

but that "44f4edc7-1953-4b9f-a19d-eb4ce3685fd7" looks suspiciously like a UUID string that would be found in /etc/fstab. (If you're unfamiliar with /etc/fstab, it's the file that identifies drives and partitions to the system.  If fstab contains an error, there is a very good chance the machine won't boot.

One kind of fstab error could be incuding a non-existent drive.  I've seen that happen in old Linux installs when the USB drive that contains the install image, and the user booted off of, was incorrectly added to /etc/fstab. In some cases, the installer would see the USB stick as /dev/sda and put the bootloader there. The drive I considered /dev/sda was actually /dev/sdb to the installer.  So, when I removed the USB stick, the machine would not boot.

Current partitioning routines in installers do the right thing and ignore the USB drive.  You can choose manual partitioning and be sure it is not selected.

---

### Post by sudodus on 2014-02-11
> **DukeNukem_2417 said:**
> Parted Magic sees it, but claims that the filesystem is still messed up.  

I may have to use the partition editor on that to get the thing working....

That might work too :-) It might be the same or a very similar version of gparted (as the version that comes with the Ubuntu install iso files).

---

### Post by DukeNukem_2417 on 2014-02-11
Indeed...if d-ban somehow fails to work, I may have to try this idea.  

The fact that everyone here has been quick to reply with the advice is pretty encouraging, as well.

---

### Post by CharlesA on 2014-02-11
Well once dban runs and wipes the drive, try installing a version of Ubuntu or one of it variants that is still supports. 12.04, 13.04, and 13.10 are the currently supported ones.

---

### Post by sudodus on 2014-02-11
I'm sorry, but 13.04 passed end of life in January, so the only current Ubuntu desktop versions are 12.04 LTS and 13.10.

---

### Post by DukeNukem_2417 on 2014-02-11
D-BAN's at 66% now; when it's finished, and I have a chance to run the install, I'll post an update.

---

### Post by CharlesA on 2014-02-11
> **sudodus said:**
> I'm sorry, but 13.04 passed end of life in January, so the only current Ubuntu desktop versions are 12.04 LTS and 13.10.

Thanks for the correction. :) I forgot they had a 9 month release cycle now.

---

### Post by DukeNukem_2417 on 2014-02-11
Well, the D-BAN/re-install failed.  My only other theory is that I put the boot loader on the wrong partition or somethin---(hd0 instead of sda).  So, do I wipe the drive again, re-install and install the boot loader to sda, or should I just get a new hard drive?

---

### Post by CharlesA on 2014-02-11
Which version did you try doing the reinstall with?

---

### Post by sudodus on 2014-02-12
I suggest that you try to create a new partition table with ***gparted*** booted from a live drive, for example made from an Ubuntu desktop iso file.

If you fail, I can help you wipe (only) the first megabyte.

This method requires that gparted and parted can see the device (as /dev/sda or /dev/sdb ...). We can start with 'no partition table or a borked partition table' but the disk hardware must be recognized as a device (a mass storage device).

---

### Post by DukeNukem_2417 on 2014-02-12
Parted Magic detected that the sda partition was missing a software package; I'll get the name of said package this afternoon and post it, but other than that, I'm about to just give up and either get a new hard drive or find another PC altogether to put Ubuntu on.  The one I'm trying to use had a hard drive issue back in 2011 that nearly lost all my data on it, most of which was only just recovered last December via Hiren's Boot CD---I wanted to put Ubuntu on that machine as a way to sort of resurrect it after that near-catastrophic data loss.

---

### Post by sudodus on 2014-02-12
It seems parted magic can see /dev/sda.

Can the specific program ***gparted*** see it too?

---

### Post by DukeNukem_2417 on 2014-02-12
I don't have gparted, to be honest---I was running Parted Magic from a copy of Hiren's Boot CD.

---

### Post by sudodus on 2014-02-12
***Gparted*** comes with all Ubuntu family desktop iso files, so if you have an Ubuntu CD/DVD/USB install drive, you have gparted :-)

---

### Post by DukeNukem_2417 on 2014-02-12
Hmmm....so I should use the "Try Ubuntu Without Changing Your Computer" option to use GParted?

---

### Post by sudodus on 2014-02-12
Yes. But when you start editing the partitions you will actually change your computer ;-)

---

### Post by DukeNukem_2417 on 2014-02-12
Figured that.    And it'll be worth the change.  UPDATE: gparted sees the hard drive, but says it's not mounted.  What do I do now?

---

