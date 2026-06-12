---
title: "chkdsk equivalent in Ubuntu"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Traceur-UK on 2008-05-20
Right, so my Windows installation has gone down (again). I've tried running Windows tools to recover it without loss of data but they're all failing me. What I need to do is access the drive within Ubuntu so I can back up all the files I need to keep before reformatting the partition and reinstalling Windows.
But the disk requires a check. Which I can't do as I can't access my Windows partition.
Is there any software that can do the check from WITHIN ubuntu so I don't need to use Windows to do it (the equivalent of chkdsk /f)?

I also tried:
sudo mount -t ntfs-3g /dev/sdb2 /media/windows -o force
but the same error came up.
Thanks in advance.

---

### Post by quelx on 2008-05-20
ntfsck

part of ntfsprogs

```
sudo apt-get install ntfsprogs
```

then

```
sudo ntfsck /dev/sd??
```

where the ?? is the drive letter and partition number

---

### Post by Mark_in_Hollywood on 2008-05-20
Hmmm, if you have an Ubuntu CD, run the LiveCD session.

Once the desktop is up and running, open Places/Computer and find your drives and right click and check that the drives are NOT MOUNTED.

from then on, making sure no drives are mounted, go to Applications/Accessories. Pull down the terminal, (I would right click and add the Terminal to the panel for temporary ease, maybe text editor and screenshot, too).

Open the terminal and go to town.

---

### Post by Traceur-UK on 2008-05-20
I installed ntfsprogs but apparently ntfsck isn't in there.
Now going to boot into the live cd

---

### Post by Traceur-UK on 2008-05-20
Still no luck within the live CD.
Why can't it find ntfsck even though I've installed ntfsprogs?

OK I fixed it. Turns out ntfsck hasn't been implemented into ntfsprogs yet (or at least, in the version I was using. I also read it on a site).
I used ntfsfix to schedule a disk check next time Windows boots (it reboots itself after the Windows splash screen). I didn't see the check, but upon booting into Ubuntu to do more fiddling, I tried the partition and it mounted. Brilliant. Time to do some backing up and then fix my blasted Windows installation.

---

### Post by signseeker on 2008-05-20
> **Traceur-UK said:**
> Still no luck within the live CD.
Why can't it find ntfsck even though I've installed ntfsprogs?

OK I fixed it. Turns out ntfsck hasn't been implemented into ntfsprogs yet (or at least, in the version I was using. I also read it on a site).
I used ntfsfix to schedule a disk check next time Windows boots (it reboots itself after the Windows splash screen). I didn't see the check, but upon booting into Ubuntu to do more fiddling, I tried the partition and it mounted. Brilliant. Time to do some backing up and then fix my blasted Windows installation.

Fixing windows? - heh. If you mean it in a way similar to 'fixing a cat' you don't need to - it was built that way.

---

### Post by Traceur-UK on 2008-05-20
Well... get it worki-
hmm that doesn't sound accurate either.
I want it to boot. Dammit, I want to play TF2. So now I have to go through the long and arduous process of backing everything up and reinstalling it.

---

