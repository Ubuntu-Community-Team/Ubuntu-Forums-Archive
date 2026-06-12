---
title: "Defragment hard drive"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by EdforUB on 2012-01-30
I have recently tried Ubuntu on an XP OS computer.  I would appreciate it very much if you would kindly advise how it is possible to get utility tools to defragment and clean the hard drive.  Also I had Kaspersky Internet security when I last used the Windows XP OS.  Can I continue with Kaspersky and if so kindly advise.
Kind regards

---

### Post by carl4926 on 2012-01-30
Windows has a tool to defrag

It's not necessary in Linux

---

### Post by amauk on 2012-01-30
Under normal circumstances, you should never need to de-fragment a Linux EXT partition

See here for a nice explanation of why
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

The only circumstances where EXT begins to fragment is
- When you're using 95%+ of space
in which case, you've got bigger problems than a bit of file fragmentation

- When large files (many gigabytes) are being constantly modified
Eg. a busy database, or a HTPC that's recording and deleting lots of video

In the second case, EXT is not the ideal filesystem to use
instead, something like reiserFS or XFS is better suited

---

### Post by sanscents on 2012-01-30
> **EdforUB said:**
> ICan I continue with Kaspersky and if so kindly advise.
Kind regards

There is no need for a Windows AV program to run in Linux.  Does Kapersky even make a Linux version?

---

### Post by grahammechanical on 2012-01-30
Here are some links that might be useful

[https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall]("https://wiki.ubuntu.com/UncomplicatedFirewall?action=show&redirect=UbuntuFirewall")

[https://help.ubuntu.com/community/Gufw]("https://help.ubuntu.com/community/Gufw")

[https://help.ubuntu.com/community/Firestarter]("https://help.ubuntu.com/community/Firestarter")

They are about firewalls on Ubuntu.

Regards.

---

