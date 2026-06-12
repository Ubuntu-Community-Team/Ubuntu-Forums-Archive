---
title: "Windows cant see hard-drive after ubuntu installed"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by good2talk on 2008-05-17
Hi to all members!

I am a new user. Just installed ubuntu but got stuck:

(1) I wanted to install ubuntu as multiboot but something went wrong. When I tried to reinstal Windows, it cant see find the hard-drive but ubuntu runs well from the HDD. :confused:

Question:
How to reinstall the Windows please?

(2) Firefox has pulldown menu for eBay but its for .com and I want co.uk. I have downloaded uk version but cant install it. 

Question:
How to install it please? I cant see any exe file from the download. Clicked all files but no luck.

All your help will be much appreciated.

Kind regards

---

### Post by volkswagner on 2008-05-17
Did you select use entire disk during install?

---

### Post by ladr0n on 2008-05-17
> **good2talk said:**
> Hi to all members!

Firefox has pulldown menu for eBay but its for .com and I want co.uk. I have downloaded uk version but cant install it. 

Question:
How to install it please? I cant see any exe file from the download. Clicked all files but no luck.

.exe files are a M$ thing.  In linux, programs are installed either through binary packages (.deb files for Ubuntu and other Debian-based distros) or by compiling source code (usually distributed in .tar.gz or .tar.bz files)

Some other versions of linux use .rpm files for programs, but the method for installing these in Ubuntu is messy and doesn't always work.

The ebay thing sounds like a firefox extension though.  Firefox handles the installation of those by itself (and should have done that for you without making you download a file).  What kind of file is this and where did you get it?

---

### Post by autocrosser on 2008-05-17
Also, please post your Grub menu list--this is located @ /boot/grub/menu.lst

You can't modify it as a normal user & don't try just yet--just copy/paste the file here so we can help you.

---

### Post by good2talk on 2008-05-17
> **volkswagner said:**
> Did you select use entire disk during install?

Yes, I did without knowing the trouble!

---

### Post by wolfen69 on 2008-05-17
your windows is now gone.

---

### Post by FreakTech on 2008-05-17
Windows cannot see your drive because you have it formatted as ext3, which windows cannot read.  You need to download a gparted cd and adjust your partitions, and then reinstall windows.

---

### Post by AndyCooll on 2008-05-17
> **good2talk said:**
> (2) Firefox has pulldown menu for eBay but its for .com and I want co.uk. I have downloaded uk version but cant install it. 

Question:
How to install it please? I cant see any exe file from the download. Clicked all files but no luck.

All your help will be much appreciated.

Kind regards
You don't download the ebay uk search engine addon.

Click on this link: [Mycroft Project: ebay uk search engine plugins]("http://mycroft.mozdev.org/download.html?name=ebay+uk&sherlock=yes&opensearch=yes&submitform=Search")
Then click on one of the top two links. It will ask if you want to install the plugin and you say yes.
Done!

:cool:

---

### Post by good2talk on 2008-05-17
> **FreakTech said:**
> Windows cannot see your drive because you have it formatted as ext3, which windows cannot read.  You need to download a gparted cd and adjust your partitions, and then reinstall windows.

I tried it with ubuntu live. Windows Restore CD checking the system and say no hard disc connected. I tried reformatting to FAT32 and NTFS still cant find the C drive.

---

### Post by cariboo on 2008-05-17
You have to use a Windows install CD to reformat your hard drive and install Windows. From what you've said you completely wiped out your windows install. To repartition your hard drive use gparted. To install it either use synaptic or from a console type:
```
sudo apt-get install gparted
```

Once you've installed it you can find it under System|Administration|Partition Editor.

Once gparted starts I would suggest you partition half your hard drive for Windows and use the other half for Ubuntu. You have to install windows first and then install Ubuntu.

Hope this helps

Jim

---

### Post by volkswagner on 2008-05-17
> **good2talk said:**
> I tried it with ubuntu live. Windows Restore CD checking the system and say no hard disc connected. I tried reformatting to FAT32 and NTFS still cant find the C drive.

Boot your Ubuntu cd live.  Go to system>Administration>Partition Editor

Do you see your newly created NTFS partition?

You can also run from the live CD

```
sudo fdisk -l
```


Is the disk is showing up as NTFS or Fat32, but now with windows restore CD?

Is your restore CD from the PC manufacturer?  You disk may no longer be active in your bios.  I have had this happen after Xubuntu install.  I needed to use an old windows boot floppy to set the partition as active and boot.

Your recovery disk should be able to recognize an unformatted drive.

---

