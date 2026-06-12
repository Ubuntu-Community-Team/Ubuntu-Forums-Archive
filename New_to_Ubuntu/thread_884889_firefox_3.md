---
title: "firefox 3"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-09
the images do not load when i visit a website on ff3 that came as default web browser with hardy.
i tried downgrading to firefox 2.but when i try to install an add on in firefox 2,it successfully loads that add on but,finally fails in installation,stating an installation error.thus frustrated i remove ff2 by synaptic,and install ff3.but this time ff3,reduced in terms of functionality(doesn't even copy any text......and other such things) looks pretty messed up like ff2.i reboot ubuntu into recovery mode and repair broken packages,i boot back normally,and my ff3 starts working out of the box except for the problem of image loading.i want to remove completely ff from the HDD and all the files associated,and then reinstall ff2 right from the scratch so that my add ons do not fail to install.how can that be done?i mean even if i choose complete removal for them in synaptic they still remain on the HDD,i want a complete removal of ff and its associated files....how should i do this?

---

### Post by stonecoldjha on 2008-08-09
plz help me remove ff completely,i mean all traces of ff.

---

### Post by bpowell2005 on 2008-08-09
> **stonecoldjha said:**
> the images do not load when i visit a website on ff3 that came as default web browser with hardy.
i tried downgrading to firefox 2.but when i try to install an add on in firefox 2,it successfully loads that add on but,finally fails in installation,stating an installation error.thus frustrated i remove ff2 by synaptic,and install ff3.but this time ff3,reduced in terms of functionality(doesn't even copy any text......and other such things) looks pretty messed up like ff2.i reboot ubuntu into recovery mode and repair broken packages,i boot back normally,and my ff3 starts working out of the box except for the problem of image loading.i want to remove completely ff from the HDD and all the files associated,and then reinstall ff2 right from the scratch so that my add ons do not fail to install.how can that be done?i mean even if i choose complete removal for them in synaptic they still remain on the HDD,i want a complete removal of ff and its associated files....how should i do this?

I'm not sure FF3 by itself is the problem. I've been running Firefox 3 no problem since I installed Hardy...loads images and everything. The only time I had odd Firefox behavior was when I completely filled up my Ubuntu partition (on a Virtual installation).

Can you post the output of "df -h" so we can see what kind of free space you have? You might have inadvertently filled up your root or home partition and this could be causing your problems.

---

### Post by stonecoldjha on 2008-08-09
the output of df -h was as below

sonu@sonu-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9             7.6G  3.8G  3.5G  52% /
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   64K 1014M   1% /dev
devshm               1014M   36K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1              30G   15G   15G  51% /media/sda1
/dev/sda3              21G  5.5G   16G  27% /media/sda3
/dev/sda5              30G  106M   30G   1% /media/sda5
/dev/sda6              30G   14G   16G  48% /media/sda6
/dev/sda7              33G   25G  7.3G  78% /media/sda7
gvfs-fuse-daemon      7.6G  3.8G  3.5G  52% /home/sonu/.gvfs
sonu@sonu-desktop:~$

---

### Post by pi.boy.travis on 2008-08-09
You really shouldn't totally obliterate Firefox.  It has lots of components, such as the Gecko rendering engine that Ubuntu really needs.

---

### Post by bpowell2005 on 2008-08-09
> **stonecoldjha said:**
> the output of df -h was as below

sonu@sonu-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9             7.6G  3.8G  3.5G  52% /

gvfs-fuse-daemon      7.6G  3.8G  3.5G  52% /home/sonu/.gvfs
sonu@sonu-desktop:~$

Well, that's plenty of space in your home partition, 3.5 gig available should cause problems with Firefox. I'm not sure why FF won't load images for you. Try disabling all of your add-ons or plug-ins for Firefox...perhaps one of them is causing a conflict.

---

### Post by stonecoldjha on 2008-08-09
i have already uninstalled all my plugins.

---

### Post by bpowell2005 on 2008-08-09
> **stonecoldjha said:**
> i have already uninstalled all my plugins.

Okay. How about you shutdown firefox. Rename your ~/.mozilla/firefox directory to firefox_old. Then restart Firefox...it should notice the missing configuration directory, and build a new one for you from scratch...this may correct any odd settings in there.

---

### Post by stonecoldjha on 2008-08-09
it doesn't help.

---

### Post by pi.boy.travis on 2008-08-09
Why not try another browser?  There are lots of them out there!  I use Opera, but if you are looking for an open source browser, try epiphany.

---

### Post by bpowell2005 on 2008-08-09
Hmmm..okay, only other thing I can think of, is check your preference (Edit, preferences) Content tab, make sure "Load images automatically" is checked. If not checked, no images get loaded.

I can't figure what's causing your cut and paste problem with FF3.

---

### Post by silkstone on 2008-08-09
Let's start again!

There should be nothing wrong with Firefox if it's installed correctly and you have all the correct add-ons for displaying media files.

If you've tried to install FF2, make sure that is completely removed.

Next, completely remove Firefox 3 with Synaptic.

Now go to your Home folder, enable View Hidden Files, and navigate to the .mozilla/firefox folder. Delete xxx.default, and also the profiles.ini file.

Note that this will lose all your bookmarks and configuration, but I think you probably need to start again.

Now reinstall Firefox 3 with Synaptic.

If you still have a problem with anything, look at this tutorial and follow it through - it's not as long as it looks because it covers all versions of Ubuntu.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by stonecoldjha on 2008-08-09
but,isn't there a way to completely uninstall my firefox,erasing all about firefox from the hard drive,and then installing ff2,so that installation of add ons doesn't show any error.

---

### Post by stonecoldjha on 2008-08-09
i mean a complete removal from the hard drive.is there a way out?

---

### Post by pi.boy.travis on 2008-08-09
Totally removing Firefox will break other Ubuntu features.

---

### Post by hovzio on 2008-08-09
> **stonecoldjha said:**
> i mean a complete removal from the hard drive.is there a way out?

My boss was having the same problem, funny FF3 is running great for me. I ended up  removing firefox 3, including configuration files in ~/.mozilla* and installed FF2.(on my bosses box) I tried many things but this was the only thing that helped. The funny thing was I installed epiphany and was having the same problem with pictures. Good luck:)

---

