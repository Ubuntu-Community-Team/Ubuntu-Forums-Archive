---
title: "COOL STUFF: squashfs -- the ultimate in archiving"
date: 2005-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2005-12-05
Anyone who's carefully examined a LiveCD or remastered one has dealt with compressed loopback images before. These are file system images frozen in time, then compressed in GZip. There are three major forms of these popular with Linux: cloop, cramfs, and squashfs. The Ubuntu kernel supports all of these. Cramfs has severe (256MB max) size limits, while cloop is _slightly_ slower than squashfs and also much harder to make (the entire image has to fit inside RAM).

For more information on Squashfs, see [http://squashfs.sourceforge.net/](http://squashfs.sourceforge.net/).



**WHAT IS IT FOR?**
Any time that you have compressible data that takes up relatively large amounts of space that you don't change very often. You can also use it as a backup archiving format. For me, I compressed down my UT2004 install from 5.8GB to 2.2GB -- over 50% saved space! Great for systems with limited amounts of storage space. With a bit of effort, you can surely compress large portions of the Ubuntu OS to make a HD install roughly the same size as the 600MB LiveCD image!

There are some limitations... Consult the sourceforge link above for more info. Namely, the filesystem is **read only** (much like a traditional livecd) and is limited to 4GB per image (though you can make as many images as you'll possibly need)! Performance is acceptably fast but there is an impact due to the compression (though gzip decompresses very lightly)

**EXPRESS Guide to making Squashfs images**:
First, do **sudo apt-get install squashfs-tools** to get the necessary commands installed.

Next, just run **sudo nice +10 mksquashfs /path/you/want/to/squash /path/to/store/squash_image -info**, and wait patiently for the process to finish. Since it uses maximum power gzip, it will use 100% CPU for a considerable amount of time depending on the size of the folder to squash. Final compression is approximately equal to a tar.gz archive of the same contents. (nice +10 simply prioritizes the process as LOW so other work is virtually unaffected... only idle CPU is devoted to squashing. You can even play 3D games while the process commences)

You will end up with a squash_image file. To mount on /mnt (as an example), type **sudo mount /path/to/store/squash_image /mnt -t squashfs -o loop**. To make permanent, add the following to /etc/fstab:
```

/path/to/store/squash_image /mnt squashfs loop 0 0

```



The next time you see a kernel developer for Ubuntu, tell him **THANK YOU** for including the squashfs patch in the Ubuntu Breezy kernel!

---

