---
title: "Dual Boot Dilemna"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by kush2 on 2014-07-10
Hello all,

I currently have Ubuntu 14.04 dual booted with Windows 8 Consumer Preview. Since Windows Consumer preview has long expired and using it now only give headache, I have decided to revert back to Windows 7, giving me simple dual of Win 7/Ubuntu 14.04

Now, as I understand if I want to downgrade windows, all my files will be lost. But is that true even in case of dual boot? 

I want to retain maximum data, if possible. Also, I want to know best procedure here to downgrade windows. {Since I guess it could be case of installing Windows after Linux, which is troublesome}

---

### Post by grahammechanical on 2014-07-10
It all depends on where your data files are. Are they on the Windows 8 partition? Or are they on the Ubuntu partition? Or are they on some other partition?

I do not think that downgrading an operating system is an accurate term to use. Installing another OS over the previous OS is what we actually have to do. You install Windows 7 into the partition that Windows 8 is in. Do that and any files in that partition will be lost but not the files in the Ubuntu partition or any other partition.

You need to make sure that the Windows installer does not use the entire disk. And you need to be aware that the Windows installer will put its boot loader in charge of booting from the hard disk and that means that you will not be able to load Ubuntu because the Windows boot loader is not designed to detect and offer to load any operating systems other than those by Microsoft.

But it is a simple matter to load a live Ubuntu session, mount the hard disk, open a terminal and run

```
sudo grub-install /dev/sda
```

I have done this myself on one occasion. Or you can install in the live session and run Boot Repair. We can even down load and burn an ISO image of Linux Secure Remix which is Ubuntu with Boot Repair and OS-Uninstaller already installed.

[http://sourceforge.net/projects/linux-secure/](http://sourceforge.net/projects/linux-secure/)

[http://sourceforge.net/p/linux-secure/wiki/Home/](http://sourceforge.net/p/linux-secure/wiki/Home/)

Regards.

---

### Post by oldfred on 2014-07-10
Is Windows 8 installed in UEFI or BIOS boot mode?

Some installs of Windows rewrite partition table and if Linux partition is in extended partition Windows seems to forget to write it also. Best to back up partition table.

If BIOS based with MBR(msdos)
       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by kush2 on 2014-07-11
Hello, 

Thanks for replies. Just to clarify Linux is my primary OS. 

I have a related

---

### Post by Mark Phelps on 2014-07-11
> I want to downgrade windows

There really is no practical way to do this.  When you "upgrade" from one Windows version to the next, doing an in-place upgrade, the installer creates a Windows.old folder and archives the prior Windows version stuff into that folder.  Then later, if you decide to "downgrade" back to the prior Windows version, you can do that and the current OS files and folders are overwritten by the saved stuff in that folder.

But -- if you only have one version of Windows on the PC, there is no option to "downgrade" to an older version; instead, you have to do a clean-install of the older version -- meaning you will lose everything from the current version.

---

