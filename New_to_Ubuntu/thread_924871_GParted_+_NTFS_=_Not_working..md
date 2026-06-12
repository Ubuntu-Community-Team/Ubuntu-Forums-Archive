---
title: "GParted + NTFS = Not working."
date: 2008-09-20
forum: New to Ubuntu
---

### Post by metacognition on 2008-09-20
Hi, I need help resizing my Windows XP Partition so I can make room for a fresh Ubuntu install. I burnt the GParted LiveCD and booted from it. (After defragmenting.) It shows my NTFS partition but I can't resize it. 
Any help? 

I also can't access my Windows XP except through Safe Mode due to an error, which is why I'm using Ubuntu.

---

### Post by Pro-reason on 2008-09-20
You may need to run CHKDSK on the drive from Windows.

Also, do “sudo fdisk -l” on the Ubuntu command line, to get info about your drives.

---

### Post by egalvan on 2008-09-20
> **metacognition said:**
> Hi, I need help resizing my Windows XP Partition so I can make room for a fresh Ubuntu install. I burnt the GParted LiveCD and booted from it. (After defragmenting.) It shows my NTFS partition but I can't resize it. 
Any help? 

I also can't access my Windows XP except through Safe Mode due to an error, which is why I'm using Ubuntu.

It sounds as if your NTFS partition is in a "dirty" state, probably from a bad shut-down. Which may also be the root of your "Safe Mode" error.

Linux-type partition software doesn't like working with dirty drives.
If it's NTFS, it will refuse, but also has an option to "force mount at your peril".

There is a set of NTFS utilities. I don't know exactly.

Linux partitions can be "cleaned up" with fsck

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

And I use Parted Magic LiveCD for partition, formatting and testing drives. I much prefer it over the other LiveCD's.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by Shazaam on 2008-09-20
"There is a set of NTFS utilities. I don't know exactly."

ntfsprogs. You can install it with Synaptic. One of the utilities is ntfsfix.

---

### Post by egalvan on 2008-09-20
> **Shazaam said:**
> "There is a set of NTFS utilities. I don't know exactly."

ntfsprogs. You can install it with Synaptic. One of the utilities is ntfsfix.

Yeah, what he said...

Shazaam!

---

### Post by metacognition on 2008-09-20
Could someone please "step-by-step" this for me?

Apparently, I haven't Ubuntu completely installed yet. Which is why I'm asking for assistance.

I've used the Gparted LiveCD and the Partition Magic LiveCD, but I can't resize the NTFS partition. According to egalvan, it's in a "Dirty State."

If I use the Ubuntu LiveCD, would that work with 'ntfsprogs?'

---

### Post by egalvan on 2008-09-20
> **metacognition said:**
> Could someone please "step-by-step" this for me?

Apparently, I haven't Ubuntu completely installed yet. Which is why I'm asking for assistance.

I've used the Gparted LiveCD and the Partition Magic LiveCD, but I can't resize the NTFS partition. According to egalvan, it's in a "Dirty State."

If I use the Ubuntu LiveCD, would that work with 'ntfsprogs?'

Can you get a screen shot of the partition window under Parted Magic ?
(I hope you meant PartED Magic & not PartITION Magic)

It may proved some clues.

"Come Watson, the game is a-foot!"

---

### Post by metacognition on 2008-09-20
Right, PartED Magic. Apparently, it has "atleast 13 bad sectors." It has instructions but I don't want to go through all of it.

Damn, there were alot.

PS. Where and what is 'ntfsresize?' As in, where to get it bro?

PSS. ntfsresize is command prompt. Lol.

---

