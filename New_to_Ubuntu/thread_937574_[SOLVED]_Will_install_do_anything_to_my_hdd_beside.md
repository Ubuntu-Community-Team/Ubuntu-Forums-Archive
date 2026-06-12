---
title: "[SOLVED] Will install do anything to my hdd besides write to C drive?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by b0yd07 on 2008-10-04
I remember installing ubuntu onto my families old pc and the nightmare it created with trying to get it off. What had happened was I installed it on to an external drive and it ended up doing some crazy stuff to the internal drive as well... couldn't start the computer to the windows install without the external with ubuntu connected.

I want to try it again though. I think.

I recently got a Lenovo Y510 laptop and this thing has three partitions. The hard drive has the recovery partition like most do, and then the rest is divided into a small C partition for windows and the rest is devoted to D, which is meant for documents and everything else. When I do the recover process, all of D is left intact, and C is restored to factory conditions.

Now if I install unbuntu to the C partition and don't like it, will recovering the system bring it EXACTLY back the way it was? I realize windows will certainly make it back, but will grub or anything be installed outside of the C drive parameters? I guess in short, does installing this do anything to my hard drive but write in the partition I tell it to? I don't really know what the MBR is, but that was definitely what the problem was last time. Do you guys foresee any situations with that?

Thanks for any help. -Mike

---

### Post by jerome1232 on 2008-10-04
Really that depends on the recovery tool, I hope to god it has the foresight to re-write the MBR when it does a recovery, other wise it's not a very good recovery tool :)

I doubt you have the original xp/vista install discs but they can be used to attain a recovery console and run 2 commands that causes windows to re-write the mbr.


Basically the MBR is just the first 53? sectors of your disk and is set asid to hold boot information, windows puts it's ntldr there which boots up windows. Linux generally using grub, the grand unified boot loader, which is capable of booting many operating systems.


One thing I think you may be interested in trying is a wubi install, you just install ubuntu from within windows, it doesn't involve any repartitioning and can be uninstalled from within windows as if it were a windows program. It leaves the windows boot loader intact and just adds itself as an entry.

---

### Post by b0yd07 on 2008-10-04
Alrighty. I take it the MBR is outside the bounds of the C drive then?

I guess I'll call lenovo back and ask if it does rewrite the mbr. Two questions though:
-Do most built in recovery tools rewrite the mbr or not? Would it be mentioned or just assumed? I looked it up and all I see is just the C drive being talked about here.
-Assuming the tool does redo the mbr, I have absolutely nothing else to worry about then?

---

### Post by jerome1232 on 2008-10-04
1: I would assume they do, it makes good common sense, but it never hurts to check. And yes MBR is not actually part of your first partition (your c: )

2: Well I wouldn't say absolutely (I mean if your not paying attention and you delete every partition on the computer during the install then you've done away with the recovery partition.

Any time you start playing with partitions I would recommend at least backing up important documents/pictures etc... to another hard drive or to dvd's. I have all of mine on DVD's and a backup on am USB drive as well and I'm one lucky sob to have had them due to a stupid mistake I once made. (I destroyed my hdd and my backup hdd and had to restore from the dvd's, which were 2 months out of date but it's alot better than nothing)

One thing you'll notice is linux doesn't refer to partitions as  drive letters (c, d, e) it refers to disks by letters, partitions by numbers. So first disk, first partition (in windows this would be c: ) is sda1 first drive second partition would be sda2 Second drive first partition sdb1.

So when you do the install you will probably have existng in this order sda1 (your c: ), sda2 (d: ) sda3 (your recovery partition)

---

