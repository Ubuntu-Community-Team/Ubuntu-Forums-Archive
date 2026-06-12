---
title: "hal.dll missing/corrupt, can't find ubuntu\winboot\wubildr.mbr to copy into c:/"
date: 2014-04-10
forum: New to Ubuntu
---

### Post by jessica8 on 2014-04-10
Hello. I'm going to apologize because this is probably a very simple thing to find, but I'm lost as I was not the person to install Ubuntu onto this computer. It's a secondhand computer, that the previous owner had installed Ubuntu onto alongside Windows XP - but has the hal.dll missing problem and won't boot into Ubuntu. I'm using Knoppix booted from a cd instead of Win XP and booting into Windows safe mode, because I figure I'm safer from any post-end of life vulnerabilities if I'm never online with XP. I read the hal.dll error thread [here]("http://ubuntuforums.org/showthread.php?t=1696696&page=3") and followed the link to the WubiGuide [here]("https://wiki.ubuntu.com/WubiGuide"), but I can't find wubildr in the Ubuntu files to copy into C:/. I have Windows set to show hidden files, including system files. I don't know where the previous owner installed the Ubuntu partition; I downloaded a program to view Ubuntu files through Windows (Ext2 IFS [here]("http://fs-driver.org/")) but still couldn't find the file. I don't really understand what a Ubuntu partition should look like or what anything is here. There aren't any folders labelled "ubuntu" or "winboot" that I could find, or anything similar, in fact there are several Windows files. I'll summarize what I did find:

The Ext2 program revealed two drives that Windows hadn't been able to read, which I labelled Y:/ and Z:/ in the setup of the program.

Y:/ is 46.9mb in total size with 39.2mb of free space and contains several files, extensions including .exe, .bts, .ini, .dmp, .lst, .mdm, .mlm, .com, .bat, .msm, .sys, .up, and .bin, and a folder labelled "dell" which contains a few more files, extensions including .bmp, .exe, and .bat. 

Z:/ is 3.99gb in total size with 404mb of free space and contains a few files, extensions including .ini, .sp1, and .com, and three folders, labelled "img" "minint" and "System Volume Information". 

Inside "img" is four files, extensions .ghs and .gho. 

Inside "minint" is several files, extensions including .inf, .bin, .exe, .com, .sys, .sif, and .ini, and several folders: 

"fonts" (containing font files), 
"help" (containing .hlp files), 
"inf" (containing .inf files), 
"msagent" (containing a folder "intl" which contains .dll files), 
"shell" (containing several folders: "ghost", "nav", "ndd", "pca", "shared", "utilities", "v2i", and several files, plus various files inside the listed folders), 
"system32" (containing three folders: "config" "drivers" and "mui", and several files, extensions .dll, .exe, .nls, and .cod),
and "WinSxS" (containing the folders: "manifests", "setuppolicies", and several folders with names similar to this: x86_microsoft.tools.visualcplusplus.runtime-libraries_ ............. etc). 

Inside "System Volume Information" is one folder, labelled "_restore{46DE8921-1D39-44D2-A9E9-64119261F211}", which in turn contains one folder "RP1590" which contains a .log file.

(I realize I did not list what some of the files and folders contained, I only listed what I thought might be important to deciphering what the previous owner did when installing. I can list more information if it's needed.)

Also: I have checked the C:/boot.ini file mentioned in the Wubi Guide, and it mentions wubildr, so I'm certain the previous owner must have used Wubi when they installed.

I really appreciate any help.

---

### Post by monkeybrain20122 on 2014-04-10
Well xp should be removed as MS no longer supports it, so should wubi as it is also deprecated and never a real way to use Ubuntu. My suggestion, wipe the hard drive of Windows XP, get a xubuntu or lubuntu 13.10/ xubuntu 12.04 iso (since Ubuntu probably doesn't run too well on very old hardware) and do a fresh install.

---

### Post by Xanthius on 2014-04-10
I can appreciate the level of detail of this post as it must have taken a long time to write down. However I'm afraid trying to "fix" windows (especially XP) is a lost cause.

As monkeybrain said; XP is no longer supported by Microsoft so there will be no more security updates and since 30% of all computers still run XP I can only imagine the severity of the viruses will only increase for that platform.

However I do have one thing to add, scan the HDD for cluster errors cause a missing dll's is usually a result of damaged sectors.

---

### Post by grahammechanical on 2014-04-10
I have not read all your post. Please may I point out that Ubuntu is not installed on its own partition. Wubi.exe is a Windows program that will install Ubuntu inside Windows as if it was a Windows application. We get the impression of dual booting but actually we are not. We are running Windows and Ubuntu in Windows.

I have never used Wubi.exe but I am fairly certain that you do not have a separate and different Ubuntu partition. I suggest that you look for signs of Ubuntu inside the Windows folder structure. In Programs, perhaps? I cannot say for sure.

It might be simpler to recover all the data that you need. although most of that might be from the previous owner and of no interest to you. And then install Ubuntu or one of its flavours as a direct installation using all the hard disk.

Regards.

---

### Post by jessica8 on 2014-04-10
Thank you for the prompt responses! I will look into how to wipe the hard drive. I wasn't intending to continue using XP, but to repair Ubuntu so that I could use it as an alternative to XP rather than Knoppix which I am using more as a temporary fix. I was under the impression that it was a dual boot, and that it would be simpler to repair the install of Ubuntu that's already there, but if wiping the hard drive entirely and starting clean with Ubuntu is possible and not complicated for a beginner to attempt then I would rather do that.

---

### Post by oldfred on 2014-04-10
hal.dll missing has almost never been that, but an issue with boot.ini. And boot.ini is requried to have both Windows and wubi entry to boot wubi. So maybe something with that is the issue. But only worth trying to fix if you have data in wubi you want to recover.

Depending on how old system is, the Xubuntu or Lubuntu versions usually are better for older hardware. Full Ubuntu is designed more for newer systems and now Unity needs a decent video card/chip to run well.

       Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
Lubuntu is an Operating System that is using LXDE.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by jessica8 on 2014-04-10
Thank you for the resources, I will look into that!

---

### Post by Impavidus on 2014-04-10
Wubi uses a virtual partition, which is just a file from Windows's point of view. It's named root.disk and should be several GB large. If you can find it and you want to keep files from the wubi Ubuntu, make a backup of that file. You should be able to extract the files from it when you have installed (Lu/Xu/U)buntu as a proper system – or using any live disk.

Installing Ubuntu is often easier than fixing it, especially if you don't want to keep Windows anyway. Basically, tell the installer in a single click (well, two, it asks for confirmation) to wipe the entire drive and install Ubuntu to it.

---

### Post by jessica8 on 2014-04-10
So the Ubuntu install will wipe the drive for me? I don't need to use a data destruction program first? Thanks for the additional info. I'm not worried about saving anything from Wubi, all of my files are backed up and anything there will be from the previous owner.

---

### Post by Impavidus on 2014-04-11
The installer will not securely wipe the drive, but it will delete the Windows file system along with all files. Unless you have reason to believe the previous owner put illegal stuff on it and the police is coming to seize your computer and search the hard drive for deleted files, this is good enough. If you want, you can securely wipe the drive using the live disk. Run the live disk, open a terminal and use [one of these suggestions from ask ubuntu]("http://askubuntu.com/questions/17640/how-can-i-securely-erase-a-hard-drive"). It has some interesting discussion too.

---

