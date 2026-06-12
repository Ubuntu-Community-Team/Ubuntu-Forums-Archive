---
title: "XP drive not showing after dual boot"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by mrnewtothis on 2013-01-23
I have a dual boot of Ubuntu 10 4 and XP Pro and have three user accounts set up on both.

It is when I am in the main user account that is the one that the computer starts in automatically that I have the problem that the XP section of the drive is no where to be found.
It has not always been like that, it is just over the last couple of weeks or so

Although it is found if I log out of the first user account and into any of the others.

I have looked in places and tried to search for it through the MY computer but for some reason it is not there.
There is a file that only has numbers and letters like 746C464764 for example if I go through My Computer/Files system and down to Media but it states I do not have the permissions to open that file.

I am wondering if there is something not right with what ever maps out the system in this user account as I have also been having problems trying to use dd rescue for an external drive that I asked about on here.

[http://ubuntuforums.org/showthread.php?p=12457383#post12457383](http://ubuntuforums.org/showthread.php?p=12457383#post12457383)

---

### Post by cepal on 2013-01-23
it's probably due to dirty NTFS filesystem of your widnows data. Boot into Windows, they automatically clean the filesystem, reboot into Linux, you should again see it.

This probably have happened when you shot down the Linux without clean unmount of the NTFS. To prevent this, I'd recommend to put the NTFS filesystem into autofs, so it only mounts when you really need it, and unmounts once you close all open files on it and some time out. This is not a 100% solution, but would cut down the amount of such situations you are in.

You didn't provide much information, so my resopnse is just a guess. It's possible you just updated something in your Ubuntu and the newer version stopped auto mounting the NTFS, or the UUID has changed and the path in /etc/fstab is no longer valid (happens when you e.g. resize partitions by Partition Magic or Gparted from a System Rescue CD).

You can also force checkdisk from Windows - in that case you'd need to reboot into windows once again, as the full checkdisk (on NTFS only) runs in sort of single mode during windows startup (when scheduled, not always!).

As this isn't a Windows support forum, I guess you need to look elsewhere would you not know how to run checkdisk in Windows etc.

As for how to put the NTFS into Autofs, there has been several guides for Ubuntu, so just google them, it would be waste of my time to look them up for you!

Good luck!

---

### Post by cepal on 2013-01-23
oh actually there is one more thing I can recall... If you mount the NTFS via /media, then from some Ubuntu upgrade, there is a new "FEATURE" mounting these devices under /media/{username}/{mountname} (e.g. /media/mrnewtothis/Windows ). But it won't create the /media/{username} path, so you just might need to create (under root) that path and don't forget to chown it to your user!

---

### Post by mrnewtothis on 2013-01-24
Thanks for that Cepal went looking for chow and found this

[http://askubuntu.com/questions/6723/change-folder-permissions-and-ownership](http://askubuntu.com/questions/6723/change-folder-permissions-and-ownership)

Using the  gksu nautilus  method, where I found it was marked as mounted, so i unmounted it and it vanished then I restarted the computer and it is working again.

Thanks again Cepal

---

