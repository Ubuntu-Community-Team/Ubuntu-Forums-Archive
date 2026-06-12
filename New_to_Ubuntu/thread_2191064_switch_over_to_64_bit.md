---
title: "switch over to 64 bit"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by mcsheffrey on 2013-11-30
I am currently running 32 bit 13.10, would it be possible to upgrade to the 64 bit version when version 14.04 comes out, and how would I do this.

---

### Post by The Cog on 2013-11-30
I think you need to do a complete clean install to change from 32 to 64 bit architecture.
If you can back it up and restore it afterwards, all your home directory (data and settings) should be valid on both architectures.

---

### Post by 3rdalbum on 2013-11-30
You'll need the Ubuntu 14.04 Desktop CD. Boot up from the CD as though you were going to do a fresh install, and run the installer.

When it asks you what disk you want to erase, select the Upgrade option instead. It will do a clean install of the new 14.04, but will not delete your home directory, and it will install the same repository software that you had before, albeit a newer version.

If you don't get the Upgrade option, click on Something Else, click on your current / partition and click Edit. Set the partition to have the mountpoint "/". Click your current /home partition (if you have one) and set its mountpoint to /home. DO NOT CLICK THE "FORMAT" CHECKBOX. Proceed with the installation and it'll do the same kind of upgrade.

---

