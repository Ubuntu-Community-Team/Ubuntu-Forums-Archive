---
title: "Failed Partition -- Disk Space Missing"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by JazonEsti on 2008-08-26
I tried partitioning my 160 GB HD in to 2 -- 10 GB and 150 GB. While partitioning power went off, and now I have only 150 GB left. I can't see the missing disk space. I'm using GParted.

How do I recover the missing disk space? Thanks!

---

### Post by iaculallad on 2008-08-26
> **JazonEsti said:**
> I tried partitioning my 160 GB HD in to 2 -- 10 GB and 150 GB. While partitioning power went off, and now I have only 150 GB left. I can't see the missing disk space. I'm using GParted.

How do I recover the missing disk space? Thanks!

What outputs when you:

```
sudo fdisk -l
```

---

### Post by JazonEsti on 2008-08-26
I'm on Ubuntu Live CD right now. Any way to do that while in this mode? 

Now that I noticed it, GParted reports it as 148.34 GB disk, while Ubuntu itself when I mount it reports that it's a 159.3 GB media.

---

### Post by iaculallad on 2008-08-26
> **JazonEsti said:**
> I'm on Ubuntu Live CD right now. Any way to do that while in this mode? 

Now that I noticed it, GParted reports it as 148.34 GB disk, while Ubuntu itself when I mount it reports that it's a 159.3 GB media.

Same process: Applications->Accessories->Terminal and issue the command so we could see if fdisk could still read the hidden partition.

---

### Post by shane19174 on 2008-08-26
Are you using GParted from within Ubuntu or the GParted live CD? I don't think it should make a difference, but I do remember once getting something weird from within Ubuntu and getting correct info from the GParted CD.

"I'm on Ubuntu Live CD right now. Any way to do that while in this mode?"
Does your question refer to the "sudo fdisk -l" suggested by iaculallad? If so, just open Applications -> Accessories -> Terminal and enter the command. If that's not what you meant, sorry. (An sorry for the overlap: I was still typing when iaculallad posted his reply.)

Shane

---

### Post by JazonEsti on 2008-08-26
Oh I have to run it on Terminal. Sorry. 

Here are the results:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000be24a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19364   155541298+  83  Linux
/dev/sda2           19365       19457      747022+   5  Extended
/dev/sda5           19365       19457      746991   82  Linux swap / Solaris

```

I can't understand what it says. =)

---

### Post by aretalha on 2008-08-26
notice that 160 gb hdd is 149 in size ,some programs report it as 160 and some report it as 159 but its real size is 149 gb

---

### Post by shane19174 on 2008-08-26
Well, it's certainly seeing a 160 GB hard drive there. Maybe you should just do your partitioning again with GParted.

aretahla: what exactly do you mean? I take it you're talking about the difference between gigabytes and gibibytes or whatever they're called, right? I.e., the difference between a GB as 1024 MB or as 1000 MB (which allows manufacturers to "cheat" on HDD sizes)?

---

### Post by JazonEsti on 2008-08-26
If it's 160 GB, why can GParted only report only 148 GB? 

How can I recover the missing space using GParted?

Free disk space is only 137 GB after fresh install.

---

### Post by shane19174 on 2008-08-26
It looks like we might be talking at cross purposes. Like aretalha pointed out, what a manufacterer markets as a 160 GB HDD is in reality a 149 GB HDD. That is 160000000000 bytes does not equal 160 GB but (because 1 KB is 1024 bytes, 1 MB is 1024 KB, etc) something closer to 149 GB. GParted (I just checked) will give the lower, more accurate, number. So it looks like there's nothing missing.

---

### Post by JazonEsti on 2008-08-26
Okay, so my HD is fine? Isn't the 10 GB loss a bit too much?

---

### Post by shane19174 on 2008-08-26
I can't really say. If you want to know what's occupying the space, just open Applications -> Accessories -> Disk Usage Analyzer, and click Scan Filesystem.

Note also that the program indicates "total filesystem capacity," which should be of interest in determining if your total HDD is available/visible to Ubuntu, along with "used" and "available" space.

---

### Post by JazonEsti on 2008-08-26
It's actually weirder. 

Total FileSystem Capacity is 294.3 GB. Available is 289 GB. Filesystem occupied 2.1 GB.

---

### Post by shane19174 on 2008-08-26
Is there a second or external hard drive attached? That might explain things. I was assuming only one disk, but if there are more then the Disk Usage Analyzer might just confuse things. If there are external disks (including USB sticks etc?) try unmounting them and run the Analyzer again. I don't know what else to say.

---

