---
title: "Installation Bombed Out!!"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by David F on 2008-06-28
I'm relatively new to Ubuntu + Linux but have run the last couple of Ubuntu versions as a most welcome replacement for Windoze. With the 8.04 release I thought I'd be smart and try downloading the new OS rather than waiting for a CD. Bad idea!! Installation took an eternity so I went to bed and left it to it. Next morning installation had jammed with 17 minutes (Ubuntu time) still to go, in the midst if installing Samba. Now when I boot I get an error pop-up telling me "Failed to initialise HAL!" and half the system won't run - mouse buttons are back-to-front and can't be altered, can't download email, Firefox won't load, lost my second monitor, shut-down sequence is corrupted, and so on. I scanned the threads, found one that suggested "sudo /etc/init.d/dbus restart" but that didn't help. Another thread suggested "roll-back" but how?
Any advice on how to get my system properly functional again will be most welcome

---

### Post by pytheas22 on 2008-06-28
Did you do a clean install of Hardy or do you mean that you upgraded over the Internet?

If it was a clean install, something's definitely wrong with your CD.  Even on a really old computer, it shouldn't take more than an hour to install Ubuntu (on new machines it should be less than fifteen minutes).  Try burning the CD again at a slow speed and checking it for defects before you use it.

If it was an online upgrade, those often don't work as advertised.  I always do a clean installation.  If you keep /home on a separate partition, it's really not much of a hassle.

You can also burn an alternate (text-based) CD, which has an option to upgrade Ubuntu (the normal live CD doesn't).  This can be a more reliable and faster way to upgrade, especially if you have a slow or flaky Internet connection.

---

### Post by ajgreeny on 2008-06-28
You can also check the md5sum of your downloaded iso file to check that it is not corrupted in the download.  I assume you got the live CD up and running after burning it.  If so do that again and then in nautlius (double click the "Computer" icon on the desktop) double click on the icon for your windows install.  OK, I'm assuming you are on line to this forum on your windows install; if not then you have problems and need to navigate to the iso file somehow.
Now open a terminal and cd to the folder where the iso file is, possibly ```
cd /media/windows/path/to/download/folder
``` and then type ```
md5sum ubuntu-8.04-desktop-i386.iso
```Wait for the terminal to finish and compare the output of that with the figure which can be foung [here]("https://help.ubuntu.com/community/UbuntuHashes")
The figures should match exactly, if not your download as well as possibly your burn is faulty.

---

### Post by David F on 2008-06-28
Thanks guys.

My previous upgrades have been from the Ubuntu-supplied CD, however this time I was too impatient to wait for a CD so I up-graded via the internet. No, I didn't download the .iso file and burn a CD, I just used the on-line upgrade.

So, from your comments it seems I need to do a re-install. I asked a couple of weeks ago for a CD from Canonical so rather than downloading the .iso file I'll wait patiently for that to arrive and then I'll do the re-install. I've been without Ubuntu for a couple of months already so I'll continue to put up with XP until the CD arrives and then upgrade.

That said, I'm interested in pytheas22's comment about a possibly faster and more reliable upgrade by burning an alternate (text-based) CD. From where? 

Thanks again.

---

### Post by David F on 2008-06-28
Disregard that last question. I just browsed the Ubuntu site and found the alternate CD download location. And once again impatience has gotten the better of me - I'm already downloading it and will burn a CD!

---

