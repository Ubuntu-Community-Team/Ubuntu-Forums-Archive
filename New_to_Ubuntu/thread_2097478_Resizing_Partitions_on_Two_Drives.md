---
title: "Resizing Partitions on Two Drives"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by OldPlatypus on 2012-12-23
Hello all!  

I am currently running a dual boot with Ubuntu 12.10 on one small, hard drive and Win7 on a separate, larger drive.   Since I'm getting more comfortable with Ubuntu, and using it  a lot more than Windows, I'd like to resize the Windows installation, keeping room for the few things I still need there, and add the extra space to Ubuntu.

Is there a simple way to do this without reinstalling everything?

---

### Post by ibjsb4 on 2012-12-23
Maybe a separate data partition would work for you.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by OldPlatypus on 2012-12-23
That looks exactly like what I'm looking for.  :)

Will I have to use a Windows partition tool to resize the Windows drive?

---

### Post by westie457 on 2012-12-23
> **OldPlatypus said:**
> That looks exactly like what I'm looking for.  :)

Will I have to use a Windows partition tool to resize the Windows drive?

Yes, that would be the best tool to use. Windows tools for Windows tasks.

Using a live tool such as Gparted to shrink the Windows partition will cause Windows to invoke a 'chkdsk /r' because the size of the partition has changed. At worst Windows would not start.

A couple of things to consider: defrag the Windows drive at least twice and temporarily remove 2 files (pagefile.sys and hiberfil.sys) to maximise the amount of space to reclaim from Windows.

[COLOR="Blue"]The first one is more important than the last two.[/COLOR]


As already suggested you could format the new space using Windows to NTFS and use it as a data partition available to both operating systems.

---

