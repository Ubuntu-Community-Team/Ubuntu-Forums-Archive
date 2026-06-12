---
title: "Side by Side OS"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by EquuaPotesta on 2013-05-04
At the moment I have Windows 7 installed on the same partition as Ubuntu 13.04.

What I'm wanting to do is uninstall Ubuntu to roll back to 12.04 (13 just doesn't work as well for me)

Is this possible to do without reformatting the partition? I don't want to lose the Win7 but i also don't want to keep the ubuntu.

possible?

---

### Post by BluNova on 2013-05-04
How have you installed them on the same partition are you sure you don't mean on the same drive

---

### Post by EquuaPotesta on 2013-05-04
It's one partition. Using the option to "Install Ubuntu side by side with windows 7"

---

### Post by Impavidus on 2013-05-04
If they are indeed on the same partition your Ubuntu has to be wubi (and I'm not sure there is a 13.04 wubi). In that case back up your files, uninstall 13.04 using the uninstaller in windows and install 12.04.

If you were mistaken and don't have them on the same partition (sounds more plausible), backup your files, insert your 12.04 live disk and run the installer. Choose manual partitioning and point it to your old partitions. If you have a separate home partition you don't have to format it. Strictly speaking, it may not be necessary to format the 13.04 root partition, but it will be cleaner if you do so nonetheless.

PS: Just reading your next post. The option "Install side by side" means installing Ubuntu on its own partition, next to Windows on the same computer and presumably same hard disk, *not* on the same partition.

---

### Post by UltimateCat on 2013-05-04
Hi:

I have been running Linux for about 4 years now and helping folks all over the globe install Linux-
I have never come across a single partition that holds 2 operating systems. (if) so your a complete Genius! ! Mate!

To be certain of this partition and other partitions on your computer; open the terminal and run this command so you will know exactly what partition to delete- re-format-etc...
Run as :root"
```
fdisk -l

```

I'm in a dual boot: Windows 7 and Fedora 17-
See what my partitions look like-
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    38637567    19317760   27  Hidden NTFS WinRE
/dev/sda2   *    38637568    39354367      358400    7  HPFS/NTFS/exFAT
/dev/sda3        39354368   525322287   242983960    7  HPFS/NTFS/exFAT
/dev/sda4       525324288   976773119   225724416    5  Extended
/dev/sda5       525328384   567271423    20971520   83  Linux
/dev/sda6       567273472   575662079     4194304   83  Linux
/dev/sda7       575664128   584052735     4194304   82  Linux swap / Solaris
/dev/sda8       584054784   592443391     4194304   83  Linux
[root@ redhatcat]# 



```

The first 3 partitions are my Windows 7 Home Premium:-
4,5,6,7 and 8 are my Fedora partitions
Now I created additional partitions because it was recommended in the documentation but....
Typically you only should have your journaling file system and a swap--

---

### Post by EquuaPotesta on 2013-05-04
Well I'm happy to say that I think I was wrong about the makeup of my drive. Here's the output from terminal:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   437192703   218595328    7  HPFS/NTFS/exFAT
/dev/sda2       437194750   488396799    25601025    5  Extended
/dev/sda5       437194752   480008191    21406720   83  Linux
/dev/sda6       480010240   488396799     4193280   82  Linux swap / Solaris

```

If I'm reading this correctly, then I'm seeing the Win7 partitions (first two) then the last two are Ubuntu and the Swap partition?

---

### Post by Cheesemill on 2013-05-04
> **UltimateCat said:**
> I have been running Linux for about 4 years now and helping folks all over the globe install Linux-
I have never come across a single partition that holds 2 operating systems. (if) so your a complete Genius! ! Mate!

That is exactly how Wubi works :)

---

### Post by Paqman on 2013-05-04
> **EquuaPotesta said:**
> Well I'm happy to say that I think I was wrong about the makeup of my drive. Here's the output from terminal:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   437192703   218595328    7  HPFS/NTFS/exFAT
/dev/sda2       437194750   488396799    25601025    5  Extended
/dev/sda5       437194752   480008191    21406720   83  Linux
/dev/sda6       480010240   488396799     4193280   82  Linux swap / Solaris

```

If I'm reading this correctly, then I'm seeing the Win7 partitions (first two) then the last two are Ubuntu and the Swap partition?

The first one is Windows, the second is an extended partition (which is a not a real partition, but a bit of on-disk trickery) which contains your Ubuntu and swap partitions.

---

### Post by EquuaPotesta on 2013-05-04
> **Paqman said:**
> The first one is Windows, the second is an extended partition (which is a not a real partition, but a bit of on-disk trickery) which contains your Ubuntu and swap partitions.

So could i safely wipe the 3rd through 4th and put the Ubuntu install on that without disturbing the windows 7 install?

---

### Post by Paqman on 2013-05-04
Yep.

What is it about 13.04 that isn't working for you? It might be easier to fix than doing a full reinstall.

---

### Post by EquuaPotesta on 2013-05-04
> **Paqman said:**
> Yep.

What is it about 13.04 that isn't working for you? It might be easier to fix than doing a full reinstall.

Well my favorite part of Ubuntu (back when I was on 12.04) was how I could close the lid of my laptop after a class, and it would go into sleep mode. Then I could open it, tap a few keys to wake it up, and it would be up and running in seconds.  For some reason on 13.04, the machine continues to run after I close the lid (as in it just turns off the display). Figured this out the hard way when i opened my back to find a very hot laptop with a dead battery.  The other part I didn't like was a glitch I found with hibernating.  When I eventually do get the machine to fully sleep, upon awaken, the screen won't turn back on, so I have to do a hard reset in order to get back on.  I've done some research for a fix but there hasn't been anyone that i can find with this type of situation on 13.04. The previous posts were all over 10.04 (and a few other releases) and were never solved.

---

### Post by Mark Phelps on 2013-05-05
> **UltimateCat said:**
> Hi:

I have been running Linux for about 4 years now and helping folks all over the globe install Linux-
I have never come across a single partition that holds 2 operating systems. (if) so your a complete Genius! ! Mate!
Wubi creates a single file (root.disk) INSIDE an existing Windows NTFS partition -- which Ubuntu then treats as a Linux filesystem.  So basically, the single NTFS partition does hold two different OSs.  But -- this is because Wubi is a variant of virtualization.

Essentially, this is similar to using Virtualbox to create a space for Ubuntu, inside an NTFS partition, and installed Ubuntu there.

---

### Post by BluNova on 2013-05-05
I'm sure you change what the computer does when the lid closes in the power settings

---

### Post by EquuaPotesta on 2013-05-05
> **BluNova said:**
> I'm sure you change what the computer does when the lid closes in the power settings

That's not my issue. My issue is how when I tell it to suspend or hibernate, it won't wake up the display again until I do a hard shutdown.

---

