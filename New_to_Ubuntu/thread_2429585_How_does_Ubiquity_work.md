---
title: "How does Ubiquity work?"
date: 2019-10-20
forum: New to Ubuntu
---

### Post by eclipticccccccc on 2019-10-20
More specifically, how does it install Linux and other packages to the hard drive? Does it copy the packages from the installer OS? I can't find my way around the source code.

---

### Post by crip720 on 2019-10-20
It copies all from installer, except for certain packages(gparted?), it can also download third party packages if you okay it.  It is the reason the installer OS is over 4GBs to download and why you can try Ubuntu from installer without installing.

---

### Post by oldrocker99 on 2019-10-22
It does install gparted, too useful an app to not include. One of the great things about the live session is that gparted can by used on all the unmounted disks easily.

---

### Post by oldfred on 2019-10-22
If you watch details during install, you will see it uninstalling lots.
I see it uninstall gparted, many language packs, lmv & encryption (since I do not use that) and a lot of other things.
One of the first things I do is reinstall gparted, but I know I cannot use on main working drive, but can use it on sdb & all my flash drives.

Not sure why if I specify English at beginning of install, why it copies all the language packs and then uninstalls them.

---

### Post by oldrocker99 on 2019-10-25
The things which are being deleted are the installation packages; once they've been installed, there is no reason to keep them on the disk.

It **isn't deleting** the installed packages. That would be destructive! It really isn't nothing to be upset about, and I have never, in 11 years, not had gparted in the System folder after installation.

It installs all the language packs in case a separate non-English user might want to use the system. They take up very little space. It's really nothing for you to worry about!

---

### Post by crip720 on 2019-10-30
I can be remembering incorrect, but I think one of first things I install after installation is gparted.  Just did a fast google search on gparted and quite a few were about installing gparted on ubuntu since it is not installed at installation.  There might be a way to have it installed, but I just installed it after.

---

### Post by TheFu on 2019-10-30
Did a fresh 19.10 install today.
```
$ gparted

Command 'gparted' not found, but can be installed with:

sudo apt install gparted

```
But that is to be expected for a minimal, non-GUI install.  There are lots of different ubuntu variants. Some may not install packages that others commonly do.

OTOH, I see LXD snap got installed without being requested, which seems like a huge waste.  lxd snap was removed successfully, BTW.

---

