---
title: "Package operation failed when downloading from ubuntu software centre"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by dynex1992 on 2012-07-30
hi everyone. i keep trying to download stuff from the ubuntu software centre and i keep getting this at the end of the download. it also says its installed 

Package operation failed

installArchives() failed: Selecting previously unselected package ettercap-graphical. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 172942 files and directories currently installed.) 
Unpacking ettercap-graphical (from .../ettercap-graphical_1%3a0.7.4.2-1_amd64.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Processing triggers for hicolor-icon-theme ... 
Setting up avg2012flx (2012.1793) ... 
Installing 'avgd' service initscripts... 
ln: failed to create symbolic link `/etc/init.d/avgd': File exists 
dpkg: error processing avg2012flx (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ettercap-graphical (1:0.7.4.2-1) ... 
Errors were encountered while processing: 
 avg2012flx 
Setting up avg2012flx (2012.1793) ... 
Installing 'avgd' service initscripts... 
ln: failed to create symbolic link `/etc/init.d/avgd': File exists 
dpkg: error processing avg2012flx (--configure): 
 subprocess installed post-installation script returned error exit status 1

i think its something to do with the avg antivirus i downloaded but didn't work. 
any help is appreciated

---

### Post by egeezer on 2012-07-30
You're right about the avg - note the "error processing avg" that keeps coming up.  I've never used avg, but I would think if you removed it you could do all the software downloads you wanted.    I would suggest you bring up Synaptic Package Manager, type avg in the search bar, and mark the avg entries for removal.  That should quiet it down, and you can go about adding your software (and it would be a lot quicker and more efficient to add it from Synaptic, too).  Again, search, then mark for installation.  If you want to add avg back in later, just install what you removed previously.

---

### Post by dynex1992 on 2012-07-30
hi, thanks for a reply
would that remove avg from my windows 7 as well as ubuntu?

---

### Post by jonnyboysmithy on 2012-07-30
So you were trying to install ettercap but because avg had a problem it wouldn't install.
If you don't need avg I would just remove it. Then try again. 

What file did you use to install avg?

---

### Post by dynex1992 on 2012-07-30
i think it was a .deg file off the internet. that didn't work so i tried another file which didn't do nothing either so i gave up and just deleted the folders. im not to sure how its detecting it 
i have got avg on my windows 7, would that cause a problem?

---

### Post by dynex1992 on 2012-07-30
thanks
did as you said and its now working fine

---

### Post by jonnyboysmithy on 2012-07-30
No Avg on windows doesn't have anything to do with having it installed on ubuntu.
If you still want to install it use the .deb 
I find they usually work. [http://download.avgfree.com/filedir/inst/avg2012flx-r1793-a5062.i386.deb](http://download.avgfree.com/filedir/inst/avg2012flx-r1793-a5062.i386.deb)

For more info on security have a read on [this sticky thread]("http://ubuntuforums.org/showthread.php?t=510812").

---

