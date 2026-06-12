---
title: "Recovering Lost Files"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by brenan on 2008-05-01
I just downloaded Ubuntu from a Live disc. I foolishly sped through the installation process without backing up any of my data. On the select a disk step there were two options other than manually editing the partition, but one was indented and I had to select both, or choose the manual option. I choose the auto, and now I cannot get back to Windows XP. Is it possible to recover what I've lost or did Ubuntu clear out everything? Is there any way to restore my computer to the way it was?

---

### Post by Monicker on 2008-05-01
You MIGHT be able to recover some data, but the chances are very slim, unless you pack it away now and send it to a professional recovery service.

I actually did that myself once, and purchased a Windows recovery app which was able to get some of the files back, but the results were so poor that I might as well have not bothered.

If the data is critical, you may be able to recover it, but the price would be very high.

---

### Post by brenan on 2008-05-01
So from what I've described its clear that XP has been blocked out?

---

### Post by Monicker on 2008-05-01
> **brenan said:**
> So from what I've described its clear that XP has been blocked out?

I'm not positive that you actually overwrote your XP partition, based on your description.

Open gparted from within Ubuntu, and see whether or not it shows an ntfs partition for XP.  If the partition is there, it may just be that you don't have a grub entry to let you get to XP.

---

### Post by cubeist on 2008-05-01
> **brenan said:**
> So from what I've described its clear that XP has been blocked out?

However, like Monicker mentioned, a professional data recoverer may be able to get quite a bit recovered.  This is because erasing data takes a long time, so instead of erasing, the installer just writes over top of existing data...sometimes recovery will be able to pull some of that base layer data back up...but it is also usually fragmented...

This is assuming the installer over-wrote your xp partition

---

### Post by brian_p on 2008-05-01
> **brenan said:**
> I just downloaded Ubuntu from a Live disc. I foolishly sped through the installation process without backing up any of my data. On the select a disk step there were two options other than manually editing the partition, but one was indented and I had to select both, or choose the manual option. I choose the auto, and now I cannot get back to Windows XP. Is it possible to recover what I've lost or did Ubuntu clear out everything? Is there any way to restore my computer to the way it was?

Run

```
sudo cfdisk
```

to see the state of the partitions on the first hard disk. Post the output if you wish.

---

### Post by brenan on 2008-05-02
sda1        Boot        Primary   Linux ext3                      246955.81
sda5                    Logical   Linux swap / Solaris              3100.94

No sign of XP.

---

### Post by brian_p on 2008-05-02
> **brenan said:**
> sda1        Boot        Primary   Linux ext3                      246955.81
sda5                    Logical   Linux swap / Solaris              3100.94

No sign of XP.

Looks like it's gone. cfdisk says your disk size is 250 GB. Is tha correct?

---

