---
title: "Moving, removing, reducing partitions on Ubuntu/Vista system"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by phil81uk on 2008-07-13
Morning,

I used the Disk Manager in Vista to make space for Ubuntu. However it would only reduce the Vista partition by 50GB even though there is still another 35GB free space. It also wont allow partitions to be moved around.

I want to reduce the Vista Partition further (as it still has 35GB free space).

I want to delete the Dell recovery partition.

I then need to move partitions to make use of the free space left by the Dell Recovery.

I have both ext3, swap, NTFS partitions, and some other that I don't know what it's for (came with three or so partitions - apparntly normal for Dell).

I have Partition Magic. Will it work with Linux partitions (if I run it from Vista?)

---

### Post by nirkir on 2008-07-13
You can use partition editor (gparted). It allows you to change partition sizes (much like Partition Magic).

You can install it using synaptic.

---

### Post by phil81uk on 2008-07-13
Thanks, I ran gparted and it looks a sinch to use! However it cannot read my Vista or Dell partition and hence only gives the option to delete it!

I think I will give Partition Magic a go.

---

### Post by phil81uk on 2008-07-13
Ah, only Partition Magic dont work with Vista. I read that ntfsprogs allows gparted to work with NTFS. How do I install this? Their Wiki does not give beginners instructions.

---

### Post by hyper_ch on 2008-07-13
did you defrag the vista partition?

---

### Post by bumanie on 2008-07-13
As unfortunate as it may be, the best way to alter vista partitions is with the vista partitioner (which you used already). Gparted is known not to be too great with vista, but works fine with xp. Vista will probably reduce further if you do the operation again, but defrag as hyer_ch says.

---

### Post by gazzadtfan on 2008-07-13
Hi

I'm having a similar problem to phil81uk. I was dual booting Ubuntu with Vista.(Separate Drives) Everything was fine until I tried resizing the Vista drive with GParted to give me another partition for data.

I now cannot boot into Vista. I can only boot into Ubuntu using Supergrub but it doesn't help me with Vista.

When resizing I must admit I forgot to defragment.

I have thought about going back to scratch with the restore drive but I can't get into it. I read about using a Windows XP disc to fix the mbr but it doesn't allow me to do that either.

One of the main reasons I decided to dual boot with Vista was that I can't get any sound with Ubuntu for my Soundblaster X-Fi card. (Any word on drivers for this card yet by the way?)

I'm in a bit of a quandry. How can I get back to a dual booting system with either Vista or XP and Ubuntu?

Please Help

gazzadtfan

---

### Post by phil81uk on 2008-07-13
I defraged but it only allows an extra 300mb shrinkage (when I reran the Vista Partition Manager). Even though there is 35GB free space!

I will try degragging again and again. Maybe there's a better defragmenter than the Windows one?

---

### Post by pjvandehaar on 2008-07-17
Im having a problem similar to this, as my computer has 25gb free, and i cant get any more room for ubuntu. it has a 40gb hard drive, and in windows defragmenter, it shows what i think is the swap file right at the end of the partition. also, unmoveable files are spread out all through the free space. now i can't repartition anyways, though, since gparted seems to have a problem with my xp partition.
any help would be appreciated.

Edit: I just tried to download Qtparted, but it had an error with missing files in root/qtparted or something like that

---

### Post by sea_monkey987 on 2008-07-17
Vista has a problem when anything resizes its partition.  This includes gparted and probably Partition Magic (can't speak for it since I don't have it).  What happens is Vista expects your partition table to be one way - the way it was when you last booted vista - if it finds that this has changed on its system partiton (c: most of the time), it will refuse to boot.  So, in short, [COLOR="Red"]RESIZING C: (or whatever vista's drive is) FROM GPARTED WILL RENDER RENDER VISTA UN-BOOTABLE[/COLOR].  See this thread to fix vista if it already won't boot: [http://ubuntuforums.org/showthread.php?t=846627](http://ubuntuforums.org/showthread.php?t=846627)

The reason the vista partitioner will not shrink your drive any further is because you have files that are at the point physically on the disk.  This can be any type of file.  If it is a system file, like the page file or part of the MFT, then you're pretty much out of luck with Vista's partitioner and defragmenter.


NOTE:  Resizing linux partitions from gparted does not affect vista mainly because M$ refuses to acknowledge Linux's existance and Vista marks linux partitions as 'Unknown'.

---

### Post by phil81uk on 2008-07-17
I read that Perfect Disk will move system files, so I downloaded and ran the trial version. I did not work for me. My remaining option is to delete vista, resize the partition, and reinstall. However, if reinstalling Vista using factory install disks then it might over write everything on the entire hard drive (depends on manufacturer).

---

### Post by sea_monkey987 on 2008-07-17
Can somebody confirm, if phil81uk should be able to use gparted at this point to resize his vista partition and then repair it using the vista repair disc?  I'm concerned how gparted handles fragmented data when resizing (even if one has already defragmented the said partition numerous times).

---

### Post by phil81uk on 2008-07-17
I may as well give it a go as I'm resorting to reinstall. If it doesn't work then I return to the plan of reinstalling it.

I need to find out if Dell installation discs will install onto my new partition or if they will wipe the entire hard drive. I know for a fact that the Thinkpad disks wipe the entire drive, and recreate the Restore partition and everything. But I think that on my old Dell I deleted everything and was able to install without the recovery partition.

---

