---
title: "Disk format for a 10GB file on 16 GB USB stick?"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by Mariane on 2012-11-14
Hi, 

I would like to give a 10GB file to a friend. She bought a 16GB USB disk (SanDisk Cruzer) for that. But when I try to copy I get the error message "file too large". 

I think it comes from a file system that does not allow files larger than 4GB. So I would have to format the USB stick. 

Which disk format should I use (my friend has a mac, so I cannot use ext3), please? And how do I do it? 

Thank you

---

### Post by The Cog on 2012-11-14
FAT won't hold more than 4G. If your friend can read NTFS, that should do the trick.

---

### Post by pkadeel on 2012-11-14
> **Mariane said:**
> Hi, 

I would like to give a 10GB file to a friend. She bought a 16GB USB disk (SanDisk Cruzer) for that. But when I try to copy I get the error message "file too large". 

I think it comes from a file system that does not allow files larger than 4GB. So I would have to format the USB stick. 

Which disk format should I use (my friend has a mac, so I cannot use ext3), please? And how do I do it? 

Thank you
Other than FAT family, Mac supports HFS and UDF only.
Mac OS X can however support other file systems aswell 
[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Supporting_operating_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Supporting_operating_systems)

---

### Post by sisco311 on 2012-11-14
You can split the file:
```
split -db 4000M largefile largefile
```

Then join the parts:
```
cat largefile* > largefile
```

---

### Post by HermanAB on 2012-11-14
Format the schtick with NTFS.

$ man mkfs.ntfs

---

### Post by Cheesemill on 2012-11-14
I didn't think that Macs supported NTFS without having to install additional software.

---

### Post by coffeecat on 2012-11-14
> **Cheesemill said:**
> I didn't think that Macs supported NTFS without having to install additional software.

MacOSX can read NTFS out of the box, but cannot write to it. There was a hack that you could do to Snow Leopard (perhaps Lion) iirc to give it NTFS write capability, but it was not reliable. Reliable NTFS write requires the Mac version of ntfs-3g to be installed. However, formatting the USB stick NTFS in Ubuntu would seem to be one way of achieving what the OP requires since a Mac will be able to read this.

@Mariane, you can install Gparted in Ubuntu or use Disk Utility to format the USB stick NTFS. Or you could consider sisco311's solution, since the cat command in the Mac terminal would be the same.

---

### Post by dannyboy79 on 2012-11-14
you could pack it into a rar set.

```
rar a -v100000k filename.xxx.rar filename.xxx
```

that will make 1gb rar files that can then be reassembled on a mac. You wouldn't have to reformat the usb stick.

---

### Post by Lars Noodén on 2012-11-14
You can use the Mac's native format, HFS+, on Linux.  She will be able to read that.  NTFS should be avoided.  You need to install a few packages: hfsplus and maybe also hfsprogs and hfsutils.

---

### Post by dannyboy79 on 2012-11-14
Mac can read fat32 just fine and with my solution there is no need to reformat the flash drive at all. I am sure there are unrar capabilties on the Mac

[http://unrarx.com/](http://unrarx.com/)

---

