---
title: "Large files transfer problems for WD Mybook"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by LiamGaerity on 2008-06-09
Hi all. I recently followed the forum post [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087") for creating a backup tar file and believe I have successfully done so. However, when I go to transfer that file to my WD 1 Tb External Hard drive, at exactly 4.0 Gb of transfer I receive an error that says **Error: Cannot write to file; file transfer too large** Can anyone help, please?

---

### Post by BandD on 2008-06-09
What file format is the WD eternal?  FAT32 per chance?  If so, the Fat32 filesystem has a maximum size of 4GB.  So that may be your issue.  

If this is the case you'll have to re-format your external to ext3 or, if you use it with Windows as well, NTFS so you can accomidate a larger maximum file size.

---

### Post by LiamGaerity on 2008-06-09
BandD: Thank you for such a prompt reply. Yes, when I checked the file format, it's FAT32. Do you ( or anyone else) have any suggestions on the best way to reformat to NTFS? I do have some files already on there, as well as the default software that came with the HD. Also, if I convert to NTFS, will linux have any problems reading and writing to that drive?

---

### Post by michaelaly on 2008-06-09
Best way is to copy all the files to another source, reformat the drive and then copy them back. It's a pain, but the safest way.
Alternativly you could partition the drive and format 1/2 or a 1/4 of it at a time, assuming you have enough free space. 

NTFS works great under Gutsy and Hardy Heron, I have a 500gb NTFS external drive with no issues using NTFS.

---

### Post by Frak on 2008-06-09
Just backup your files, then use [GPartED]("apt:gparted") to format the External to NTFS.

BTW, click the link to install GPartED automatically.

---

### Post by LiamGaerity on 2008-06-25
Frak (or anyone who knows), so I'm having problems reformatting from FAT32 to NTFS. When I click on the external drive in GPARTED, I don't have the option to convert to NFTS, or any other options for that matter. Any suggestions?

---

### Post by Inxsible on 2008-06-25
Could you take a screenshot of it and post it here please.

---

### Post by Inxsible on 2008-06-25
> **Frak said:**
> Just backup your files, then use [GPartED]("apt:gparted") to format the External to NTFS.

BTW, click the link to install GPartED automatically.
btw...frak, is that link pointing to OzOs's apt:foo program?

I am on a windows machine at work...so I can't really check. But apt:foo is really great for newbies :)

---

### Post by Frak on 2008-06-25
> **Inxsible said:**
> btw...frak, is that link pointing to OzOs's apt:foo program?

I am on a windows machine at work...so I can't really check. But apt:foo is really great for newbies :)
It's a feature of ubufox, and extension created by Ubuntu just for installing apps over firefox. :)

---

### Post by Frak on 2008-06-25
> **LiamGaerity said:**
> Frak (or anyone who knows), so I'm having problems reformatting from FAT32 to NTFS. When I click on the external drive in GPARTED, I don't have the option to convert to NFTS, or any other options for that matter. Any suggestions?
Assuming you are running Windows XP, go to Start -> Run... -> Then type cmd and press enter. Then type the following, where drive letter is... your drive letter (like C)

```
convert *drive letter*: /fs:ntfs

```

Example, mine was
```
convert c: /fs:ntfs
```

It should restart and convert the filesystem, just wait until its done. If it doesn't restart, don't worry, it can do it without restarting sometimes.

---

### Post by LiamGaerity on 2008-06-25
Okay, So here's the screen shot. As you can see, I don't have the option to click on NTFS.

Frak, I'm actually working on my Hardy OS at the moment. Is there a way to convert to NTFS from Ubuntu? Just to test things out, I converted the hard drive to ext3. If I use this under Vista, do you think I will have any problems?

Thank you all for your replies.

---

### Post by Neo0351 on 2008-06-25
try this
```
sudo apt-get install ntfsprogs
```
then try gparted again

---

### Post by LiamGaerity on 2008-06-25
Neo, thanks!!! That worked.

To anyone: Is there any advantage to using NTFS over ext3. I The Virus (i.e. Vista) on my computer that I use. Will have any problems using my external hard drive if it's formatted as ext3 instead of NTFS?

---

### Post by Frak on 2008-06-25
> **LiamGaerity said:**
> Neo, thanks!!! That worked.

To anyone: Is there any advantage to using NTFS over ext3. I The Virus (i.e. Vista) on my computer that I use. Will have any problems using my external hard drive if it's formatted as ext3 instead of NTFS?
1. Vista CANNOT read Ext3 natively (you need a special driver, I use [FS-Driver]("http://www.fs-driver.org/"))
2. Ext3 actually has advantages over NTFS. The major one is near 0 fragmentation.

---

### Post by Neo0351 on 2008-06-25
you're welcome.  if u want to use ur hard drive on a windows machine, it is best to use ntfs.  windows doesnt natively support ext3.

---

### Post by LiamGaerity on 2008-06-25
Okay, so when I convert to NTFS, how do I rename and reset the permissions to the hard drive? I figured out how to do that when it was formated as ext3 (using e2lable), but that doesn't work now.

---

### Post by Inxsible on 2008-06-25
ntfs drives will not hold permissions.

I use my 500 GB WD external drive as EXT3. I don't have the hassle of defragging it every now and again. Also, I can use it in Vista, because I changed the type to NTFS.

So the filesystem is EXT3, but Vista sees it as NTFS. and then I use fs-driver to access the contents.

---

### Post by LiamGaerity on 2008-06-25
Inxsible: I think I see what you're saying and appreciate the recommendation.

To those that are interested in renaming their USB external hard drive formatted in NTFS/FAT32/Ext3 ... etc, visit [https://help.ubuntu.com/community/RenameUSBDrive#head-d7cc17fc255331bb5e09b61586206b8ed66e4c3c]("https://help.ubuntu.com/community/RenameUSBDrive#head-d7cc17fc255331bb5e09b61586206b8ed66e4c3c")

---

### Post by krustybaguette on 2011-04-04
> **Frak said:**
> Just backup your files, then use [GPartED]("apt:gparted") to format the External to NTFS.

BTW, click the link to install GPartED automatically.

I suspect my problem is (about to be) solved. My 2TB WD MyBook drive is visible from Windows7 but not my Linux Mint installation on my Lenovo laptop. I never bothered to check the file format of the WD drive before plugging it into my Netgear WNDR3400 router. The router supports networking USB devices. 

I have sufficient space (I think) on my laptop hard disk and/or an external usb disk to move everything over while I format the network hdd as NTFS. Question is can I leave it on the network while I format it or should I plug it directly into my laptop? I can access the network via an RJ45 cable which would be a bit faster than my wireless g but would doing the copying and formatting be appreciably faster with a direct usb 2 connection?

---

