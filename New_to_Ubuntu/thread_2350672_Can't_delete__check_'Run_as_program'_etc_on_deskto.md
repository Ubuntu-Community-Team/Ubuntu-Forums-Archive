---
title: "Can't delete / check 'Run as program' etc on desktop, can on laptop (fresh install)"
date: 2017-01-26
forum: New to Ubuntu
---

### Post by fartypants on 2017-01-26
Hello,

Very new to Linux, so I'd need an explanation step-by-step, preferably a safe solution as well :p.

Basically, this is the problem:

Installed Ubuntu on both laptop and desktop. On laptop it works fine, can delete everything and when I right-click a file, I can check 'Run as program' and such. Something I needed to do when following certain instructions to install f.e. Netbeans.
On the laptop it's installed on a singular SSD, with nothing else on it.

On desktop, I can't do the things above, even though there is only 1 account, which is the administrator (= same as root, right?). Desktop-Ubuntu is a dualboot with Windows 10. Windows installed on a SSD, Ubuntu on a seperate HDD (which is used by Windows to install programs that don't need to fill up the SSD).

More details:
-Never had another account on (n?)either laptop or desktop.
-Both are fresh installs (laptop few days ago, desktop today).
-Both installs from exact same physical USB-install, no installer-software changes at all.

I googled some solutions, and figured out it probaly has something to do with permissions. But the solutions were different and overall too confusing for me as a new user.


Hope you can help!

---

### Post by ajgreeny on 2017-01-26
Are the files that do not offer the "Run as program" sitting on the  disk shared with Windows, and therefore an NTFS filesystem?

NTFS file systems do not understand nor use Linux file permissions, and in order to see that option from a right click the file must have execute permissions, not possible on NTFS.

---

### Post by fartypants on 2017-02-08
It's with any and all files. Linux has its own partition(&#8800; disk?), that partition is on the same HDD that I use for some programs installed on Windows (but not Windows itself, that's on a separate disk, an SSD.

---

### Post by leunam12 on 2017-02-08
I think that what ajgreeny wants to know is if the partition is NTFS since you seem to be saying in your first post that the files are being shared with Windows.

---

### Post by Impavidus on 2017-02-08
> **fartypants said:**
> ..., which is the administrator (= same as root, right?).
Not exactly. Root is the user who can do everything on a Linux system. On Ubuntu, you cannot login as root. The administrator is an ordinary user with ordinary privileges, except for one thing. The administrator can act as root by using sudo.

> **fartypants said:**
> It's with any and all files. Linux has its own partition(&#8800; disk?), that partition is on the same HDD that I use for some programs installed on Windows (but not Windows itself, that's on a separate disk, an SSD.
Indeed, partition &#8800; disk. A disk (AKA drive) is the physical thing connected to your motherboard with a so-many-pin connector, storing hundreds of billions of bytes. A partition is a chunk of those bytes formatted in such a way that it can be interpreted as a collection of directories and files with owners, permissions etc. Confusingly, Windows uses the word drive for both.

Linux cannot be installed on a Windows partition, Windows cannot read a Linux partition, so you must have both a Windows and a Linux partition on the hard drive. But Linux can read and write Windows partition. The thing is, if you have stored your files on the Windows partition (so you can access them from Windows), you cannot execute them on Linux as the Windows partition doesn't support Linux-style permissions. Even worse, Windows doesn't always properly unmount its partitions, in which case Linux can only mount them read-only, giving even more limited access.

I assume you can execute or write some files (delete is also a kind of write), or you wouldn't even be able to login.

---

