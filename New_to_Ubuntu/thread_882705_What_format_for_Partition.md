---
title: "What format for Partition?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-08-07
Hi,

I'm going to dual boot my PC with Windows XP. If I create a shrared data partion how should I format it? I recal reading somewhere that you should not use NTFS as that can mess up the windows partition. Is this true? or should I format it as FAT32?

Thanks
Mariane

---

### Post by mevets on 2008-08-07
Ubuntu will be able to read NTFS, but its not perferred. You could use FAT32 but you might want to consider ext3. If you install ext2ifs in windows it wont have any problem reading that partition and its really easy to use.

---

### Post by Paqman on 2008-08-07
NTFS support for Linux used to be a little buggy, but it's pretty good now. Likewise the Ext3 support for Windows. Either one is fine.

FAT32 is like NTFS in that both systems can read/write to it, but gets very fragmented, can't handle large files well, and is basically obsolete for hard drives.

---

### Post by billgoldberg on 2008-08-07
> **Paqman said:**
> NTFS support for Linux used to be a little buggy, but it's pretty good now. Likewise the Ext3 support for Windows. Either one is fine.

FAT32 is like NTFS in that both systems can read/write to it, but gets very fragmented, can't handle large files well, and is basically obsolete for hard drives.

I have found the NTFS support in Ubuntu pretty good.

I have my external HDD's formatted as fat32, but only because that's the only FS my PS3 will read.

Should I have the choice I would pick on of the linux FS.

I'm a ReiserFS fan, but ext3 has better (3rd party) support in Windows.

--

I don't see how a ntfs partition on your HDD could mess up Windows.

---

### Post by finer recliner on 2008-08-07
use ntfs-3g in linux to read/write windows files (included in ubuntu by default)

and use ext2ifs in windows to read/write linux files.

haven't had a problem using either {knock on wood}

---

### Post by Paqman on 2008-08-07
> **billgoldberg said:**
> 
I don't see how a ntfs partition on your HDD could mess up Windows.

Me neither. About the worst thing i've ever seen is that Ubuntu will occasionally refuse to mount an NTFS partition because it wasn't shut down cleanly. That's cured by a simple boot up and shutdown of Windows.

---

### Post by Joeb454 on 2008-08-07
> **billgoldberg said:**
> I'm a ReiserFS fan

You support a [Filesystem that kills your wife]("http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=220529437#Features") ;) (I need to find whoever added that part, and buy them a drink for making me :lolflag:) *hint* Check the far right column...

> **Paqman said:**
> Me neither. About the worst thing i've ever seen is that Ubuntu will occasionally refuse to mount an NTFS partition because it wasn't shut down cleanly. That's cured by a simple boot up and shutdown of Windows.

You can force mount the drive. I can't remember how exactly, but I've done it before :)

---

### Post by Majorix on 2008-08-07
> **Joeb454 said:**
> You can force mount the drive. I can't remember how exactly, but I've done it before :)

It is done by adding "-o force" to your mount command. But it is not safe to do this.

---

### Post by sayakb on 2008-08-07
FAT32 is bad (max 4GB file size). NTFS would be the best choice.

---

### Post by louieb on 2008-08-07
NTFS, ext3, fat32. None of them are perfect.  
:KSMy rule of thumb use the file system native to the OS you use the most.

---

### Post by billgoldberg on 2008-08-07
> **Joeb454 said:**
> You support a [Filesystem that kills your wife]("http://en.wikipedia.org/w/index.php?title=Comparison_of_file_systems&oldid=220529437#Features") ;) (I need to find whoever added that part, and buy them a drink for making me :lolflag:) *hint* Check the far right column...



You can force mount the drive. I can't remember how exactly, but I've done it before :)

Hahaha.

Thanks for that link.

Buy him a drink from me too :p

---

### Post by mariane_08 on 2008-08-07
> **Paqman said:**
> Me neither. About the worst thing i've ever seen is that Ubuntu will occasionally refuse to mount an NTFS partition because it wasn't shut down cleanly. That's cured by a simple boot up and shutdown of Windows.

Thanks everyone for the advice! I didn't realise there was so much cross format support. My concern stemmed from someone who I thought (perhaps wrongly?) made the comment that a shared date partition in NTFS could somehow cause Linux to corrupt the Windows one. Don't ask me how it's just what I was told! I'm please to hear it's a myth! Anyway I'll probably use ext3 for it as I intend to move away from windows as I become more comfortable in Linux. I'm enjoying it more and more !!

---

