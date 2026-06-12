---
title: "beginner creating a raid"
date: 2016-12-25
forum: New to Ubuntu
---

### Post by godfatherdaddyfu on 2016-12-25
Hello,
I am a beginner with Ubuntu. I have an older PC that I would like to use a basic file server or storage. 
I have installed Ubuntu desktop on the primary drive that is 73 GB.
It also has 4 500 GB drives that have been formatted to NTFS. These drives have nothing on them and would like to create a raid 0 with these and make them one larger drive.
Have no idea how to create a raid with ubuntu. I have searched some of the apps and didn't find anything.

The larger plan I have is having a second PC that will have KODI home theatre and use the Ubuntu as just a storage PC. I tried to install freenas on it and got a lot of errors while trying to install. So I decided to stick to ubuntu.
Any help would be greatly appreciated.

---

### Post by ian-weisser on 2016-12-25
Installing RAID: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

An alternative to RAID 0 is LVM: [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

Try them both. They are free.

---

### Post by SeijiSensei on 2016-12-26
Personally I'd opt for RAID 5 with four drives.  RAID 0 provides no redundancy, and if one drive fails the entire array can go down.  With RAID 5 you'll get 3 x 500 GB, or 1.5 terabytes, of usable storage with the fourth drive used for "parity."  If one drive fails in a RAID 5, the array will continue to function while you replace the device.  When you do so, it will be rebuilt from the remaining drives.  Don't hesitate to replace a failed drive.  If another one dies in a RAID 5, you'll lose everything that isn't backed up.

And remember the adage, RAID is not a substitute for backups.  If you do not have an external backup device, I recommend something like this: [http://www.newegg.com/Product/Product.aspx?item=N82E16822178817](http://www.newegg.com/Product/Product.aspx?item=N82E16822178817)

---

### Post by godfatherdaddyfu on 2016-12-31
Thank you both for your quick replies. Sorry for my latte response. 
I looked at this page [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) 
it talks about installing on a raid, which I don't want to do. I have a primary drive that is 73 GB. I will keep looking.

---

### Post by ian-weisser on 2016-12-31
Oh, then you seem to be looking for the 'mdadm' package, and [instruction]("https://raid.wiki.kernel.org/index.php/RAID_setup").
You are wise to not boot from raid. Needless complexity.

---

### Post by SeijiSensei on 2017-01-01
In broad terms I'd create the RAID device with mdadm and format it with ext4.  Then I'd mount it as /home which is the directory where all the users' files are stored.

---

### Post by kevdog on 2017-01-02
I wondering if his setup wouldn't be ideal for using ZFS since he doesn't want to boot from the RAID disk.  ZFS is kind of like RAID -- however it's able to perform snapshots and backups in a very easy manner.  ZFS offers equivalent RAID1 and RAID2 levels, however I'll admit 500 Gb drives -- even four of them -- are kind of paltry for a backup.  It might be worth honestly just going out and investing in a few 4-8 Tb drives and skip the RAID thing with the 500Gb drives.

---

