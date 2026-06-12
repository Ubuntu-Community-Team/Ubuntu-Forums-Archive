---
title: "Dual boot xp and ubuntu with xp first... problem"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Onay on 2008-08-01
I had xp installed only, things were up and running, standard xp bootloader loaded up xp. I wanted to dual boot with ubuntu but I wanted a middle "shared" partition to keep all of my files between the two (music, pics, vids, etc.) so I partitioned it myself. I simply shrunk the xp partition, created a fat32 shared partition, then made ext3 and swap partitions to house ubuntu.

The installer installed grub, automatically added xp, but now when I select the xp option it goes into the original boot up splash screen (windows icon and blue loading bar), then immediately jumps to the blue screen of death for a fraction of a second. I tried seeing what it was telling me and I think it says something about an unmountable boot volume or something, though I'm not sure. I know that the MBR isn't the problem cause grub launches windows just fine.

I cannot execute fixmbr or fixboot or chkdsk via the recovery console because the recovery console disc doesn't even recognize any partitions, although gparted clearly can see my partition table and view all 4 partitions created. Is there any way to solve this so I don't have to reinstall xp again?

---

### Post by Titan8990 on 2008-08-01
I would try chkdisk -r form a live Bart's PE CD. You will need a Windows XP backup from the CD. Here is a link to some more info on Bart's PE: [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by Onay on 2008-08-01
Alright thanks but for some reason all windows recovery CD's think that my partition table is different from what it actually is (at least according to ubuntu)

---

### Post by kansasnoob on 2008-08-01
> I cannot execute fixmbr or fixboot or chkdsk via the recovery console because the recovery console disc doesn't even recognize any partitions, although gparted clearly can see my partition table and view all 4 partitions created. Is there any way to solve this so I don't have to reinstall xp again?

OK, I've been playing with a lot of different distros the past few days, so maybe some of my questions are stupid.

Can you boot into Ubuntu OK?

If the answer is yes, then open Gparted (aka: Partition Editor) from your mounted Ubuntu OS. If it's not there you'll have to install Gparted from either synaptic or apt.

What I want to know is how much "free space" XP has/had when you resized with Gparted.

Now, it sounds like you have the XP recovery disc, eh? If not don't worry yet.

---

### Post by Titan8990 on 2008-08-01
If he can get into the recovery console I would assume that he has the "real" XP disk. I had this same problem recently and I fixed it with chkdisk -r in Bart's PE. It worked even though Bart's PE didn't recognize my filesystem type either.

---

### Post by kansasnoob on 2008-08-01
What I'm looking for is how much of the XP partition is "used". Like this:

[ATTACH]79776[/ATTACH]

You may or may not have to install ntfsprogs to be able to read that.

---

### Post by kansasnoob on 2008-08-01
> **Titan8990 said:**
> If he can get into the recovery console I would assume that he has the "real" XP disk. I had this same problem recently and I fixed it with chkdisk -r in Bart's PE. It worked even though Bart's PE didn't recognize my filesystem type either.

I don't doubt that. But I have in the past crunched a Win partition too tight and had to do some resizing to give things room to breathe.

---

### Post by Onay on 2008-08-01
I had just recently installed this xp, and approximately 6.5gb was being used out of the 30gb partition. Problem is I never defragged before I partitioned, so that may present an issue.

Testdisk reported that my backup bootsector didn't match my regular bootsector, fixed that, still getting the same error. It now says that the bootsectors are okay and should be in working order.

Other info I guess would be my ntfs partition has the boot flag on it but I doubt that's an issue. Uggh I need to find a cd and try that bart pe thing

---

### Post by Onay on 2008-08-01
More info...

[http://www.youtube.com/watch?v=oYFQkal4vjw](http://www.youtube.com/watch?v=oYFQkal4vjw)

That's what it looks like... BSOD comes up and runs on a reboot cycle. After watching it a few times I'm sure it has the unmountable_boot_volume error that comes up.

Gparted bootable disc tells me that my ntfs partition has an error (! by it) and it won't even tell me how much space is used any more. Info on the warning states that "ERROR: $Bitmap size is smaller than expected (982977 != 982976). Basically gparted cannot even mount the ntfs drive according to the status.

---

### Post by Onay on 2008-08-01
I can see the files in my ubuntu installation and everything seems to be there... boot.ini, ntldr... is there a way I can replace one of those or something?

And another thing too, although it might be unrelated. When booting up into safe mode, it hangs loading the driver "agp440.sys". I use an agp graphics card, but it has never been a problem, and I don't think that it could possibly make my drive unmountable. And trying to resolve that conflict through the recovery CD is useless because the CD looks at my hard drive and sees one big unallocated heap of space instead of the partitions that are all there.

---

