---
title: "Can't suddenly boot into Windows 7? Ubuntu works fine."
date: 2015-05-09
forum: New to Ubuntu
---

### Post by srdjan4 on 2015-05-09
So I'm really new to Ubuntu and I did make it work. 
Ubuntu and Win7 ran fine for months. Now when I try to choose Windows 7 form the GRUB menu, the display goes black for 2 seconds and goes back to the menu.
So I cant boot into Win.
Everything was fine last night, not it doesn't work.

Boot Repairs thingy. 
[http://paste.ubuntu.com/11041230/](http://paste.ubuntu.com/11041230/)

---

### Post by ansus on 2015-05-09
You can start the PC and tap F12 and select start from HDD and select Windows 7. Boot repair is available also. hope this helps.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
sudo add-apt-repository ppa:kranich/cubuntu
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

---

### Post by coffeecat on 2015-05-09
@ansus, srdjan4 has already installed boot repair (probably from the yannbuntu ppa). Hence the pastebin link.

@srdjan4, I suggest you don't add the ppa:kranich/cubuntu repository. I don't see how that would help.

You have grub installed to the boot sector of sda1, which looks to be your Windows C: partition. It should not be there. That is probably what is preventing Windows from booting. I'm surprised that boot repair did not comment on this, but whatever, have a look at this:

[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

My preference would be to use a Windows 7 repair disk (or Microsoft Windows 7 install disk) and run bootrec.exe /fixboot from it. **Do not run bootrec.exe /fixmbr.** If you do you will overwrite grub in the MBR which is where it is meant to be. If you don't have a Windows 7 repair disk, there is a link in that page which will explain how to create or download a Windows 7 repair disk. 

I see from the linked page that testdisk is also recommended for this. I didn't know that you could do this with testdisk, but yannbuntu (the author of the page and of boot repair) knows what he is talking about

---

### Post by ansus on 2015-05-10
srdjan4
For Ubuntu 14.04 and newer: suggested that ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
sudo add-apt-repository ppa:kranich/cubuntu
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

---

### Post by coffeecat on 2015-05-10
Yes, I missed that Yannubuntu recommends the kranich/cubuntu PPA for 14.04 and newer. However, both the yannubuntu and kranich/cubuntu PPA repositories are showing the same version number - currently 4ppa33 - for boot-repair for 14.04.

[https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair?field.series_filter=trusty](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair?field.series_filter=trusty)

[https://launchpad.net/~kranich/+archive/ubuntu/cubuntu?field.series_filter=trusty](https://launchpad.net/~kranich/+archive/ubuntu/cubuntu?field.series_filter=trusty)

Which makes me curious about the reason yannubuntu is recommending the kranich/cubuntu PPA for boot-repair. Whatever the reason, the OP's pastebin report shows the likely problem. I think we need to find out which repository srdjan4 used for their boot-repair before recommending they add another.

---

### Post by oldfred on 2015-05-10
I think Yann must not have updated that page.
He was very slow in updating Boot-Repair's ppa to include 14.04 and later, so others created downloads. His fix was just to change trusty to precise to make it work.

Boot-Repair ppa currently has these:
 Precise, Trusty, Vivid, & Utopic all should work now with current ppa

The author of bootinfoscript .meierfra, also suggested using testdisk to restore backup boot sector of NTFS partitions if backup is valid. But links to that site are not valid any more.

Not sure if fixBOOT in Windows works. The issue is with grub in partition boot sector, Windows does not even think the partition is NTFS. It may see it as RAW, or unformatted.

Windows does have a command to totally create a new boot sector.
      
 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later


 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by coffeecat on 2015-05-20
> **oldfred said:**
> I think Yann must not have updated that page.

Just as a coda to all this, I see that Yannubuntu updated the boot repair page yesterday and removed all reference to the kranich/cubuntu PPA.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

