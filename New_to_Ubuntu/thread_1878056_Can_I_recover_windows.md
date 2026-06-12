---
title: "Can I recover windows?"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by Cuil22 on 2011-11-09
Hi, I recently erased windows 7 from my compaq presario cq56 notebook and replaced it with ubuntu 11.10. How do I get windows 7 back? (I need it for certain features) I noticed that there is a small non ntfs parition on my hardrive. Is the best case scenario to contact my manufacturer and purchase recovery cds for my notebook? I backuped my files, music, etc. Help is appreciated thanks.

---

### Post by mastablasta on 2011-11-09
you should have made recovery CD's before you installed Ubuntu. 
 
Yes maybe that small partition can do the install if it is recovery partition. 
 
In any case you will need to create empty disk space onto which you will install the windows and then after install you will need to use the liveCD to recover grub.
 
read more here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by bluexrider on 2011-11-09
There are 2 windows recovery CD's here

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by mick222 on 2011-11-09
> **bluexrider said:**
> There are 2 windows recovery CD's here

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

  Those look like repair discs and wont install windows7 seems to me the op wiped windows the small partition is probably swap. 
 Use gparted to see your partitions if there is a small ntfs partition it might be possible to use that to restore windows.

---

### Post by Mark Phelps on 2011-11-09
> **bluexrider said:**
> There are 2 windows recovery CD's here

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

As already guessed, those are REPAIR CDs, not reinstall CDs.

To the OP: How large is the "small" partition.  If it is several GB, then it is likely to be a Recovery partition, but with Linux on the PC, recovery is most likely not going to work -- because your Linux partition is occupying the space the recovery would write to.

If you obtain full-restore CDs, they most likely will erase the drive in order to restore Win7, effectively wiping out Ubuntu.

---

### Post by bluexrider on 2011-11-09
ok then

---

### Post by mysteriousdarren on 2011-11-11
Better start from scratch with a reinstall or try using Ubuntu for a while and see how it works for your own needs. If need be you can always go back to Windows, but why would you ever want to do that? :)

---

### Post by Mark Phelps on 2011-11-11
> **mysteriousdarren said:**
> ... but why would you ever want to do that? :)

Guess you didn't see the part in the original post where the OP clearly stated 

> How do I get windows 7 back? (I need it for certain features)


---

### Post by rushikesh988 on 2011-11-11
if there is some NTFS frive present on your system and if it is more than 8 GB .then there are some chances that you can recover your windows..some manufactures give hard disk recovery option too just like I have... try pressing F11 on boot ...and find if GRUB has option micosoft windows recovery...

---

### Post by BillyBoa on 2011-11-11
The only way as it was covered above is to ask your retailer to give you a Win7 installation copy. This is very difficult because usually they give you only the re-installation copy. In such a case you have only the re copy, ask in torrents to download an installation copy, install it and then over it do the re-installation, formatting the HDD and using your authentic Windows key.
After all this you can continue with resizing Windows partition and installing Ubuntu.

---

### Post by Mark Phelps on 2011-11-12
> **BillyBoa said:**
> The only way as it was covered above is to ask your retailer to give you a Win7 installation copy. This is very difficult because usually they give you only the re-installation copy. In such a case you have only the re copy, ask in torrents to download an installation copy, install it and then over it do the re-installation, formatting the HDD and using your authentic Windows key.
After all this you can continue with resizing Windows partition and installing Ubuntu.

This is generic advice, which might otherwise be useful -- but the OP clearly stated that they have a notebook -- and those come preformatted with a highly customized Win7 installation -- which are NOT going to be available anywhere except from the notebook vendor.

To the OP: best bet would be to contact the laptop vendor and see what they will do regarding sending you a set of full-restore CDs (or DVD).  They will probably charge you for it, but it will be a LOT less than purchasing Win7 retail.

---

### Post by Terl on 2011-11-12
Sometimes the vendors leave a recovery portion on your hard drive.  It may still be there.  When your computer starts up on the splash screens you may see something like "Press F11 to start recovery" or something along those lines.  If you see that, it might be possible to restore the computer back to the way it was when you got it.

Also, look at any documentation that came with your laptop; often it has a section describing what to do if you need to restore the computer to its original state.

---

### Post by fleamour on 2011-11-12
Official Window's DVDs images are available here:

[http://techpp.com/2009/11/11/download-windows-7-iso-official-direct-download-links/](http://techpp.com/2009/11/11/download-windows-7-iso-official-direct-download-links/)

But as already mentioned, if netbook is highly customized, then these may not be of use?

---

