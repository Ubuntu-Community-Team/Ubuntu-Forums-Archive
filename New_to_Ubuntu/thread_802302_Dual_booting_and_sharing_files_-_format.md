---
title: "Dual booting and sharing files - format?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by chchandler on 2008-05-21
I have been playing around with dual-booting HH & XP.  So far, so good.  I only have a 40G HD, so space is a bit tight.  There's a 120G on the way, and I plan on doing the following:

1.  Install the IBM Rescue/Recovery to bring it back to original state, with XP.

2.  Update XP as needed.

3.  Install HH, manually editing partition tables.

What I want is to have a partition for my files that HH and XP can both access, so I can work on docs from either OS.  So, I think that means I will need the following partitions:

1. IBM Rescue (about 5G)
2. Windows XP (20G or so...)
3. / (10G or so...)
4. /home (all the rest...around 82G)
5. Swap (3G - I have 1.5G of RAM)

I know I can only have 4 partitions of one type, but can have more of another... confusing!  Will the HH install allow me to have 5 and handle them correctly?

I heard mention once that a linux swap partition could only be 2G max - still true?

Should the /home partition be NTFS or FAT32?  I hear that HH can now read/write well to NTFS, then I hear no, it can't, better use FAT32, even tho it is more prone to problems.  

If I copy my current /home to a usb drive, can I then copy it back into the new /home partition, even though the old one was ext3 and the new one will be different?

Thanks in advance!

---

### Post by lswest on 2008-05-21
first off, you can only have **4** main partitions, and your other partitions must be within an extended partition.  It basically just groups free space into an area which is seen as 1 partition, instead of however many are inside that space.  Then i would just recommend using /home as ext3 and install the ext3 support from [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) in windows, so you can read and write to your /home partition.  Then a swap partition can be any size, but i would say more than 2GB is overkill, and i'd suggest 1GB for your system.  And lastly, you can tar your home folder (just hit <ctrl>+h and then <ctrl>+a when in your /home/username/ folder, and choose "create archive" and then choose ".tar.gz" as the file extension, and then untar it back into the new /home folder and it should work fine.

---

### Post by chchandler on 2008-05-21
Right, I knew there was a 4 partition limit.  How, mechanically, do I make 5?  Do I make one for IBM Recovery, one for Windows, and one for an extended partition, which I then divide into /, /home and swap?  

I've got the fs-driver already, forgot to mention.  Works well.  Also, thanks for the tar idea.  I had just copied all the files the first time I did it.

---

### Post by chchandler on 2008-05-21
More research is leading me to re-think the use of fs-driver.  It's ext3 support is not real good at error recovery.  Not shutting down XP cleanly can cause your linux share to become unusable until you can load a repair utility.

It does make a nice mapped drive so you can create a shortcut right to your /home...

Still, I'm now leaning more towards a large FAT32 or NTFS /home partition that both OS's can access.  If that means I have to do without the IBM Rescue partition, then so be it.  I've got the CD's if need be.

Wish I could find more about HH and it's handling of NTFS, though.  Anyone else doing this?

---

### Post by Sabata on 2008-05-21
> **chchandler said:**
> Still, I'm now leaning more towards a large FAT32 or NTFS /home partition that both OS's can access.  If that means I have to do without the IBM Rescue partition, then so be it.  I've got the CD's if need be.

Wish I could find more about HH and it's handling of NTFS, though.  Anyone else doing this?
FYI, I have a similar thread going right now.
[http://ubuntuforums.org/showthread.php?t=802742](http://ubuntuforums.org/showthread.php?t=802742)
One poster said NTFS works fine and gives a work-around if your NTFS partition doesn't shut down cleanly.
> **Paqman said:**
> NTFS on Linux is pretty good now. The only problem i've heard of people having is that sometimes the NTFS drive won't be cleanly shut down. This results in a flag being set on that partition that prevents it from mounting. The solution is to simply boot into Windows and shut down. This clears the flag and allows you to mount it in Linux.

I'd say always go with NTFS over FAT32. It supports larger files and picks up significantly less fragmentation.
Hope that helps some.

---

### Post by chchandler on 2008-05-21
Thanks!  I have read that thread, plus the psychocats page.  They seem to like ext3 for the large /home that serves as a shared partition, relying on ext2fs for windows access... which I am using now a bit and had no issues in my brief experience with it.  It seems easy to use from the XP side, you can make a shortcut to your files easy.

The possible downside is if XP crashes and the ext3 partition (mounted as ext2 in XP) is mounted, then booting into XP will not mount it again, as it will appear damaged.  It looks like booting into Linux will automatically fix it, tho it may take some time.  

I'm strongly leaning in this direction:

1. IBM Rescue & Recovery, 6GB or so
2. Windows XP NTFS, 20 GB
3. /, ext3, 20 GB
4. /home, ext3, 73 GB or whatever is left
5. /swap, ext3, 1GB
 #'s 3, 4 and 5 would be extended partitions.

Mostly I am in Ubuntu.  When I need to work in XP I can use the fs to access my docs, etc. and if XP crashes, it would mean a reboot into Ubuntu and some time wasted while it checked integrity of /home.

At least, that's the way I'm understanding it so far....

---

### Post by bodhi.zazen on 2008-05-21
To be honest, IMO the most stable and versatile file system for sharing is FAT. The only limitation you may have with FAT is for very large files. Support for FAT is very good in both Windows and Linux without installing any additional drivers.

NTFS is IMO #2. NTFS support is very good with Linux, but there are occasional *rare* problems.

ext2 #3 choice. fs_driver is available for windows although why try to push your luck and go all the way to ext3 ? The fs_driver (windows) does not support permissions. ext3 == ext2 + a journal. The fs_driver does not use the journal so there really is no need to use ext3.

I see you are wanting to know about partitioning, that is good. Take a peek at these links :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

