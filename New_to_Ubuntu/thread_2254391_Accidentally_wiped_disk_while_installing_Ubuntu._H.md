---
title: "Accidentally wiped disk while installing Ubuntu. How to reinstall Windows 8?"
date: 2014-11-26
forum: New to Ubuntu
---

### Post by lynn5 on 2014-11-26
So I downloaded Ubuntu and had a few issues and a new update so I reinstalled Ubuntu. When reinstalling I clicked to wipe the disk thinking it'd only remove Ubuntu but it ended up causing a lot more problems. Afterwords I ran boot-repair and it came up with this link: [http://paste.ubuntu.com/9259158/](http://paste.ubuntu.com/9259158/) . At about this time I figured out I wiped Windows 8.1 from the disk as well. Is it possible to solve this and if so how?

---

### Post by yancek on 2014-11-26
Nope.  The wipe the disk thing means what is says.  Your windows is gone.  You might be able to save some folders/files using Testdisk, see the link below.   There is a link on the page to a Step by Step tutorial on using it.  Otherwise, it's reinstall windows.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Impavidus on 2014-11-27
I hope you had backups of your files. Else testdisk may recover some files, but not your entire Windows system. To get Windows back you need a Windows install disk or a set of recovery dvds.

As yancek wrote above, wipe the disk indeed means wipe the entire disk. Linux usually does exactly as it says.

---

### Post by flaymond on 2014-11-27
When you choose to wiped your disk. Every files, software or for suit- ***everything*** is gone.There's no way to get Windows 8.1 back unless purchase it legally from your computer provider.


But, you can dodge this from happen if you got a Windows 8.1 installer CD/DVD or you got backup.



If you don't have money or don't want to waste money on Windows operating system. Try install Linux back (but first check with MD5sum).


for windows 8.1 computer, I prefer to use UEFI method.


Also, please remeber, always backup your files and also your Linux installer if something like this happened again.

---

### Post by oldfred on 2014-11-27
Some vendors will offer the recovery set of DVDs for a nominal charge.
And some retailers will make a set for you, but if they charge very much then it is cheaper just to purchase a new copy of Windows.
Only the vendor set works with the product key in your UEFI.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by Mark Phelps on 2014-11-27
One thing you could try is recovering the former Windows partitions.  You can do this by downloading and burning a CD of the Minitool Partition Wizard Boot CD, booting from that, and seeing if it gives you the options of recovering the Windows partitions.  You never know -- it might work.

---

