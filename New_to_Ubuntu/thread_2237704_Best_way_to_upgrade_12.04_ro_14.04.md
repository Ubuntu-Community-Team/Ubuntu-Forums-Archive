---
title: "Best way to upgrade 12.04 ro 14.04?"
date: 2014-08-03
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-08-03
I've got several 12.04 machines and want to upgrade them all to 14.04.  Is there a BEST way to pull this off with the least amount of glitch-probability?  Like should I just start with a new USB-mounted 14.04 download?  And if so, how do I get the 12.04 machine to boot from the USB drive?  Also, is there a better way of re-installing all of the programs than doing it from scratch via Software Center?

Thank you for any help on this!  It is a bit intimidating . . .

---

### Post by mooreted on 2014-08-03
The best way is to backup your data and do a clean install. If you want to try just doing an in-place upgrade, first back up your data, open a terminal and do:

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by riverguy99 on 2014-08-03
Thanks for the quick reply! I've heard enough times that a clean install is highly preferred, so that's what I'll do.  But I have no idea how to get the current 12.04 machine to boot from the USB drive.  Is three an easy way to change the boot order?  I've also got a 13.10 machine to upgrade, so would that use the same process?

---

### Post by oldfred on 2014-08-03
Should be the same process or all systems.

Your computer should have both BIOS boot order and one time boot key. I usually set hard drive first, so during boot system is not checking DVD or USB ports, but you can change boot order in BIOS. If one time key works that often is easier as then you have not changed any settings. 
With my motherboard & flash drives they are seen as hard drives. They must be fully configured as bootable drives and plugged in when rebooting and they show up as another hard drive, not any of the USB boot options.

You should already be backing up what you need. But that would include all of /home except you do not need temporary files, possibly /etc if you manually configured any hard ware. And export a list of installed apps. It is a very long text file as it includes everything in detail, but can be manually edited. if need be.

Still essentially what I do:
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 Other applications if data not separate
apache, any sqldb, tomcat, web folders, etc


 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
      
 From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

While I think I have reasonably good backups for a desktop user, I cheat and just install the new version to another 25GB partition while keeping old version. Then if I have forgotten anything I still can boot or go back and copy something I missed. But I have all data in separate data partitions that I just have to mount in new install, so new install is just a basic install, with some scripted configuration.

---

### Post by riverguy99 on 2014-08-03
Again, thank you much!  Especially the backup info is very useful for me right now.  I'll try the boot thing when I get the chance here in the next day or two, although I still have no idea how to access that "one-time boot key."

---

### Post by oldfred on 2014-08-03
UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

If different brands or model of computer BIOS and boot key may vary. Often f12 but see chart by brand above.

---

