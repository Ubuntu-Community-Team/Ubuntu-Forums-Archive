---
title: "Question about upgrading from 8.04 to 8.10."
date: 2008-09-08
forum: New to Ubuntu
---

### Post by opendevlite on 2008-09-08
Ubuntu 8.04 LTS has support for 3 years, right.

My question is, is that what is the difference from upgrading 8.04 to 8.10 and not upgrading it, but still just installing the updates of 8.04 for the next 3 years?

---

### Post by dRock1286 on 2008-09-08
From my experience in the past, there really is very little in upgrading.  Although, some updates for programs will only work in the newer version of Ubuntu; however, I have also had luck with updates working fine.  I plan on running 8.04 for a long while until I see something that I really want in a newer release.  The choice, then, is up to you.

---

### Post by bikeboy on 2008-09-08
8.04 will recieve few, if any version number updates to software. That is, it won't get much in the way of updates that add features. Instead, it will get bug fixes and security updates to increase/maintain its stability.

Updating to 8.10 on the other hand will bring new versions of software that are designed as feature upgrades. The downside is that there could be regressions or losses of stability.

edit: One more thing, 8.10 will receive a newer kernel, one of the principal advantages of this is support for newer hardware. Of course, if all your hardware works fine already this won't be a factor.

---

### Post by Liviu-Theodor on 2008-09-08
One difference would be:
[LIST]when you upgrade from 8.04 to 8.10, you must upgrade after that to  every new version (probably 9.04, 9.10, and so on).
[/LIST]
[LIST]when you do not upgrade, you would have to upgrade only to a LTS version.
[/LIST]

I think is better to have the LTS version, with the updates. The other way you would be more prone to some errors caused by upgrades (I never run into one, but others did).

---

### Post by billgoldberg on 2008-09-08
> **opendevlite said:**
> Ubuntu 8.04 LTS has support for 3 years, right.

My question is, is that what is the difference from upgrading 8.04 to 8.10 and not upgrading it, but still just installing the updates of 8.04 for the next 3 years?

Ubuntu 8.04 will only receive security upgrades for the next few years.

This makes it safe and stable, but the software will be old.

Ubuntu 8.10 will come out with the new gnome version, new nautilus, compiz fusion, ... 

So the main difference is between 8.04 and 8.10 will be

8.04 will be supported longer. 8.10 has newer software and might not be as stable.

----

And just a tip, it's better to do a clean install from cd than upgrading using the update manager.

Don't dist upgrade yet, 8.10 is still in Alpha.

---

### Post by opendevlite on 2008-09-08
thanks guys, i have another question, if i choose to upgrade from 8.04 to 8.10.  Does my current installed softwares, will still be there?  Like for example if i have VLC installed will it still be there, or will the upgrade delete the software?

How about my Gnome panel settings will it be change back to its defaults or not?

---

### Post by Sef on 2008-09-08
> thanks guys, i have another question, if i choose to upgrade from 8.04 to 8.10. Does my current installed softwares, will still be there? Like for example if i have VLC installed will it still be there, or will the upgrade delete the software?

How about my Gnome panel settings will it be change back to its defaults or not?

Your software will be upgraded to whatever version is in Ibex, unless it has been removed (in Hardy, but not Ibex.)  

Panels should still be the same.  

However, it is best before upgrading to **back up** your data, and burn a Live CD that works, just in case there is a problem with the upgrade.

---

### Post by Liviu-Theodor on 2008-09-26
Another difference would be:

[LIST]
[*]when you upgrade from 8.04 to 8.10, you would have all programs up-to-date, but some of them will be in beta or even alpha stage.
[/LIST]
[LIST]
[*]when you do not upgrade, some programs will not be the latest version available, but all programs will be tested first, so they wil surely work.
[/LIST]
I say this only for the programs installed from the repositories, of course.

Update to my previous [post]("http://ubuntuforums.org/showpost.php?p=5748264&postcount=4"):
> I think is better to have the LTS version, with the updates. The other way you would be more prone to some errors caused by upgrades (I never run into one, but others did).
This is valid for servers or for computers used in production environment. But if you want something as *cool and new* as possible, you should upgrade to the newest version available.

---

### Post by robert shearer on 2008-09-26
H> However, it is best before upgrading to **back up** your data, and burn a Live CD that works, just in case there is a problem with the upgrade.

A good live cd backup can be found here....
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

and from the Remastersys forum.....

> You can use Remastersys to backup a fully updated system.

  The key is to make sure your /home/(your_username) does not contain a lot of large files, such as MP-3s, videos, pictures, etc.
  Move all such files to a separate data partition, and you will find that your system easily compresses to a file size of less than 4 gigabytes.  Mine generally is just a bit over 1 gig. 
  Before Remastering your system, be sure to unmount any other partitions, except for your / and /home, unmount any mounted network drives, and unplug any USB thumb-drives or hard drives, otherwise, Remastersys will include those in the backup, making the ISO file too large.  

Also look for the following folder:  /var/cache/apt/archives.  That folder is where Klikit, (and presumably Ubuntu and other Ubuntu-based distros}, store the DEB files for all the programs installed on your system.  The DEB files are binary installers, and once the program is installed, they are no longer needed, unless you need to reinstall the program for some reason.  You can copy the entire folder to your storage partition, or use AptonCD to make a backup disk, then you can safely delete the contents of the original folder ( do a "sudo apt-get clean") , which can free up a half a Gigabyte or more.

---

