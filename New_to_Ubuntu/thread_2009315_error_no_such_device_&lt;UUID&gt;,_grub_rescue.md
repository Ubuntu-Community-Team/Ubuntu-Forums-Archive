---
title: "error: no such device &lt;UUID&gt;, grub rescue"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by ResistanZ on 2012-06-24
I've been having a lot of problems with Ubuntu on this laptop. I've had to reinstall it like 3 times already and each time only lasts a week before another problem comes up. Anyway, if possible, I'd like some help fixing this instead of having to reinstall again. I ran Boot-Repair once and that didn't fix it, here's the information from my boot.

[http://paste.ubuntu.com/1057722/](http://paste.ubuntu.com/1057722/)

The problem it says is that there's no such device when I boot up, even after I tried using Boot-Repair to fix it. I don't know much about Ubuntu, but I was reading other posts with the same problem and I tried "sudo blkid" (not sure what this does to be honest) and the UUID shows up on there, the same one that Grub says doesn't exist.

---

### Post by kansasnoob on 2012-06-24
Please consider this just chatter. Over the past couple of development cycles I've been focused almost entirely on desktop environment issues so I've fallen out of touch with solving boot issues. In fact I'm just now learning the ins-n-outs of [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"), and I don't see anything glaringly wrong with those results, but **I'm curious why you'd install on a laptop with no SWAP**?

I'd think that shouldn't effect grub but I'm just dying of curiosity, and since I've been out of the loop regarding boot issues I am once again truly a noob :redface:

Apologies for sort of stepping on your thread but I'm going to subscribe in case I might be able to contribute and/or learn something. If nothing else consider this a free bump ;)

---

### Post by ResistanZ on 2012-06-24
Well, when I tried to install Ubuntu with a partition for a swap file, the installer would hang indefinitely. I tried it so many times, using 3 different live CDs and 1 live USB. The only way I got it to install correctly was by having only 1 partition. It's possible that this is why I have so many problems with the OS.

Update: after fooling around with Boot-Sector and fsck, I got it to the Ubuntu maintenance she;;, which is a step up from the Grub rescue, I believe. But now I get the error "file system check or mount failed"... Anyone with any advice?

Update: This is the latest output from BootInfo: [http://paste.ubuntu.com/1057941/](http://paste.ubuntu.com/1057941/)

---

### Post by kansasnoob on 2012-06-24
> Well, when I tried to install Ubuntu with a partition for a swap file, the installer would hang indefinitely. I tried it so many times, using 3 different live CDs and 1 live USB. The only way I got it to install correctly was by having only 1 partition.

That's certainly odd in my experience but please hang in there for some true advice. I'm sure there's an explanation.

---

### Post by drs305 on 2012-06-24
Are you sure your BIOS is booting the sda drive first?

If you hadn't mentioned the issue with creating partitions my guess would be that it's a BIOS limitation.

At the grub rescue prompt, try running these commands:

```
ls (hd0,1)/
```

Do you see "initrd.img.old" but not "initrd.img" ?

```
ls (hd0,1)/boot
```
Do you see "initrd.img-3.2.0-**23**-generic-pae" but not "vmlinuz-3.2.0-**23**-generic-pae" ?

If the answer is yes then it means BIOS and GRUB can't see your system files because they are too far into the drive. We can go from there once you reply.

---

### Post by ResistanZ on 2012-06-24
Hmm. I screwed around with Boot-Repair and ended up screwing up my Grub too badly to know how to fix. So I just reinstalled again. This is like the 4th or 5th time? :\

Anyways, this time I just used the normal install instead of advanced settings and it seems it created an extension partition and a swap partition. And the filesystem seems to be clean. Hopefully this won't be a problem anymore!

---

### Post by YannBuntu on 2012-06-26
Hello
If your system is ok now, please could indicate your current [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ?
(it may help us understand what the initial problem was).

---

### Post by audiomick on 2012-06-26
Keep in mind that mechanical problems are also a possibility. Really basic things like bad contacts on the plug where the drive plugs in. Or maybe the drive is starting to have problems of some sort. Give that some thought if the problem crops up again. 

I used to have a problem on this desktop that the system would periodically not find the drive at boot, more or less the same as what you are describing. The solution was a new SATA cable on the drive.

---

