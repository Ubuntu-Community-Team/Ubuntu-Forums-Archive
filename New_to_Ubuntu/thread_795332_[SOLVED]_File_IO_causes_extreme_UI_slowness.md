---
title: "[SOLVED] File IO causes extreme UI slowness"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by timandjulz on 2008-05-15
Summary: Copying from / to physically separate raid5 volume has severe impact on GUI.  Suggestions for kernel or file system tweaks?

Hi all,

When copying multi-gigabyte files via Nautilus from / to another physical disk GUI becomes very unresponsive.  Usable but there is obvious severe impact on the UI.  CPU activity is minimal (16-30% on a quad core per gnome-system-monitor).  When running vmware VMs I can barely use them.

/ is on one drive, the target is on physically separate raid5 drives.

It seems like reading from / should not impact performance this much since writing is the slow part.

Running: Hardy Heron, 8GB memory, quadcore Intel, root on /sda2, target on LVM raid5 across 3 500G drives spread across two controllers.  I have tried ext3 and xfs.

Are there some tweaks I can do to the kernel?  Or use another file system?  Any other suggestions?

Thanks,
Tim

---

### Post by spiderbatdad on 2008-05-15
This may not be the ideal solution, but I can transfer large files with relatively no impact and very quickly (2000+kb/s) by using a file server. I have apache2 set up to host the files. This of course requires the client to run an os of its own...sounds like you are doing that anyway with VM?

---

### Post by timandjulz on 2008-05-15
I am trying to keep everything on the same machine.  I am consolidating to save electricity.  :)

That is an interesting thought though.  Maybe I could redirect the IO through the network interface to throttle it, thus hopefully having less of an impact.  Problem with that is Samba blows up when I try to run it.  :confused:

Anyway, for now I am going to focus on keeping my config simple.  Thanks for the suggestion though!

---

### Post by spiderbatdad on 2008-05-15
As a test I just did this: Plopped hardy_alpha.iso into my public_folder in a browseable index folder, opened my browser at put localhost in the address bar, save the file to my desktop at 6656kb/s with no noticeable impact to my gui. I could have done it from the terminal too of course with wget.

---

### Post by timandjulz on 2008-07-02
Solution is to copy the files through terminal and [use ionice]("http://ubuntuforums.org/showthread.php?t=846449") to throttle.

---

