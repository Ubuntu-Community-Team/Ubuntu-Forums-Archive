---
title: "TRIM, windows compatible file systems"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by LinuxVirgin2000 on 2014-03-02
Hi,

What file systems are supported by TRIM and are also compatible with Windows 8.1?



EDIT:
[COLOR=#000000] I am dual booting and I need a shared partition with a file system that Windows can access and UBUNTU can TRIM[/COLOR]

---

### Post by Mark Phelps on 2014-03-02
> compatible with Windows 8.1? You do realize these are the Ubuntu forums, not the Windows 8 forums, right?

You should really check with the Windows 8 forum: eightforums.com

---

### Post by LinuxVirgin2000 on 2014-03-02
I mean which file systems are compatible with TRIM that UBUNTU uses. the reason for the question is because I am dual booting and I need a shared partition that Windows can access and UBUNTU can TRIM

---

### Post by whitesmith on 2014-03-02
It took me 15 seconds to find this in Wikipedia, "A Trim command (commonly typeset as TRIM) allows an operating system to inform a solid-state drive (SSD) which blocks of data are no longer considered in use and can be wiped internally." TRIM doesn't care about file systems because it operates at a lower level. It only cares about the hardware on SSDs.

---

### Post by LinuxVirgin2000 on 2014-03-02
Thanks for the reply whitesmith,

I have been trying to research this for weeks now, you may be right, but I know for sure that file system is an important consideration, there are tons of sources on the net which state linux can not TRIM NTFS, I don't know why this is but it is definitely true.

For this reason I thought about using FAT32 but I have seen sources which say windows can not trim FAT32 and one source saying it can

Also I have seen confusion about whether ubuntu can TRIM FAT32

Hence why I asked this question in hope to find a file system that both windows and ubuntu can TRIM so I can read/ write to it from both OS's

---

