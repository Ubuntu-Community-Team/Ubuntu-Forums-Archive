---
title: "Windows 8.1 dual boot install with xubuntu...."
date: 2014-03-06
forum: New to Ubuntu
---

### Post by newbietwo on 2014-03-06
I had to purchase (for work purposes) a Windows 8.1 product key this morning from this link.

[http://windows.microsoft.com/en-us/windows-8/upgrade-product-key-only](http://windows.microsoft.com/en-us/windows-8/upgrade-product-key-only)

I want to keep my xubuntu and install Windows 8.1 alongside it. When clicking link above how do I install 8.1 and an exe installer file on a Linux only machine????  Also, do I have to install a Windows 8 Pro iso to upgrade?  Confused.  Any help would be appreciated.

---

### Post by nunecas123 on 2014-03-06
You should get an ISO to boot from it. It would be so much easier if you installed Ubuntu after Windows - it would do all the work for you.
Steps(keep in mind that you should have a primary NTFS partition on your hard-drive because EXT filesystems are not detected on Windows):
1. Get a bootable USB or DVD of your Windows 8.1
2. Install it with your key
3. Boot from Ubuntu and go to the terminal and write this command: 
```
[COLOR=#000000]sudo update-grub
```

Tell us the results. It should work after this.[/COLOR]

---

### Post by newbietwo on 2014-03-06
Thanks for the reply...

You don't happen to have a Windows 8.1 Pro ISO link?  I can only find Enterprise and I don't think that will do me much good.

---

### Post by sandyd on 2014-03-06
> **newbietwo said:**
> I had to purchase (for work purposes) a Windows 8.1 product key this morning from this link.

[http://windows.microsoft.com/en-us/windows-8/upgrade-product-key-only](http://windows.microsoft.com/en-us/windows-8/upgrade-product-key-only)

I want to keep my xubuntu and install Windows 8.1 alongside it. When clicking link above how do I install 8.1 and an exe installer file on a Linux only machine????  Also, do I have to install a Windows 8 Pro iso to upgrade?  Confused.  Any help would be appreciated.

Do you have some form of windows already?
If you  dont, you have to have some form of Windows (the links says If you're upgrading to Windows 8, this PC must be running Windows 7, Windows Vista, Windows XP with Service Pack 3 (SP3), Windows 8 Release Preview, Windows 8 Consumer Preview, or Windows Developer Preview. ) before using the upgrade key. This means that if you dont have some form of windows, you will have to buy a dvd to install.

---

### Post by nunecas123 on 2014-03-06
There are unofficial ISOs of Windows 8.1 Pro, and they're not directly from Microsoft. I don't know if you want to risk it or not?

---

### Post by newbietwo on 2014-03-06
i thought that an existing form of windows was no longer needed at install and you could install from upgrade.  disappointing.  [http://www.theregister.co.uk/2013/09/17/windows_81_full_version_software/](http://www.theregister.co.uk/2013/09/17/windows_81_full_version_software/)

---

### Post by nunecas123 on 2014-03-06
Only if you use Hiren's BootCD and get on Mini Windows XP to extract the ISO from the upgrade software that they give. That's a good idea.

---

### Post by GandalfTheNerd on 2014-03-06
I had a pretty horrible time doing something very similar. My biggest mistake was not to turn off fast boot. Warning - upgrading to Windows 8.1 turns it on again! Once I had rebuilt the entire system, the Ubuntu installation was very straightforward. You can see the gory details here [http://ubuntuforums.org/showthread.php?t=2202980](http://ubuntuforums.org/showthread.php?t=2202980) if you wish.

---

