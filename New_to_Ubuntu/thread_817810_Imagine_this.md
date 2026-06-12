---
title: "Imagine this"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by PinkFloydFan on 2008-06-04
I have 3 HD's:

1 is the Windows XP (NTFS)
2 is a FAT 32 drive
3 Is the Ubuntu drive

On both Windows & Ubuntu I have Thunderbird installed whith the same email account. So I decided to have all the email files on the FAT32 disk.

Which works great in Windows, but when I restart Ubuntu, and than open Thunderbird it says I have no permisions to open the folder on the drive.

If I select that folder manually in Thunderbird, it works.

But I think I need to mount the FAT32 drive during boot up of Ubuntu.

And this is where I am stuck. As a newbie I have no idea how to do this.

Any help will be greatly appreciated!

---

### Post by me208 on 2008-06-04
Open System>>Preferences>>Sessions under the Startup Programs tab make a new entry using the "add" button. Name it whatever you want, I suggest something simple like "Mount fat32 Volume". As the command enter 
```
sudo mount /location/of/drive
```
where "/location/of/drive" is the "dev" location of the drive, it should be something like /dev/sda (for a SATA drive, I cant rember what it is for a IDE drive)

Hope that helps!

---

