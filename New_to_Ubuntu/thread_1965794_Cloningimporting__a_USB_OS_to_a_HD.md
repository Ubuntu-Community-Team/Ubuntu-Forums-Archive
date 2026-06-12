---
title: "Cloning/importing  a USB OS to a HD?"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-26
I have developed a good working 11.10 OS on a 16 GB USB flash drive.

I have 3 other PC's.

My initial ideas was "Have USB, will travel".

An ideal Configuration Management system would have allowed me to develop the system on one flash drive and dd it to other flash's.

I have been able to boot a Dell 2400 from a Live CD and it runs, but the USB boot have not been solved.

It was suggested that I let 11.10 install directly to the Dell C: drive for a dual boot system.

Assume that it worked, 11.10 would be at step one upgrades, additions, tweaks, etc; all of which are on my 16 GB flash.

There it lies, a fully developed OS, it is so tempting.

A global question:

If you have 11.10 installed and running on a HD, can you use import the fully developed OS using the 16 GB as the source?

---

### Post by jerrrys on 2012-04-26
Should work.  If you want to boot from usb, grub must be installed.  And if you want to copy to another HDD, you still need to add to boot menu.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+grub&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=install+grub&sa=Search&cof=FORID:9)

I find clonezilla easier to work with.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by oldfred on 2012-04-26
Yes & no.

You cannot use it as an installer but can copy it and have to edit several things to make it work. Some have used dd - but dd's nickname is Data Destroyer, so you have to be careful as it is very powerful and therefore dangerous. dd only really works from same size to same size partitions. You can also just use rsync, but still have to edit settings.

Because many users have issues with the edits I normally suggest a clean install, & copy /home over with rsync. That will include all your user settings & data. If you have installed a lot of apps you can export that list & reinstall (data from them was in /home). And if you manually edited system settings you may need to copy those from /etc. So clean install is not totally easy either.

Others who have done full copy may be able to explain better. In your case your backup is just copying system to your new install partitions.

My backup procedure is to backup everything I need to do a clean install and then restore my system to the way it was. And I normally do clean installs to a new partition, so I have old install to go back to and find something I have missed. 

Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

I used this to create my own backup script.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

If you want a gui for rsync.
[https://help.ubuntu.com/community/rsync#Grsync](https://help.ubuntu.com/community/rsync#Grsync)
discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

