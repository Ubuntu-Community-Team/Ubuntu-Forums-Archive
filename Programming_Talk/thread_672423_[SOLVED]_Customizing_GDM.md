---
title: "[SOLVED] Customizing GDM"
date: 2008-01-19
forum: Programming Talk
---

### Post by quandary on 2008-01-19
Hi,

I am customizing the Gnome Display manager.

My problem is, that every time I compile and install, there seems to be no changes commited to my system.

I had this before when customizing the gnome-session, and there it was that the gnome-session executable wasn't copied to /usr/sbin... so i had to overwrite the gnome-session file, and the changes suddenly appeared.

Now I have the changed file "gdm-binary", and thought maybe i have to copy it to /usr/sbin, but there is no file named "gdm-binary" in sbin, nor anywhere else on the system...

I thought it could be /usr/sbin/gdm, so i renamed gdm-binary to gdm, and copied it there. But the only thing that happened was for Ubuntu to start Xubuntu on startup, which is not what i want...

Previously I changed the "gdmsetup" executable, and there the changes also only took effect when i manually copied the file over, after typing "make install"...

Also, the filesize is of the compiled versions is rather much larger than the size of the original files. I suppose there is debug information in it. But there is no "make release". How do i tell make not to include debug information?

---

### Post by quandary on 2008-01-19
bump.

---

### Post by stroyan on 2008-01-19
The debian/rules for gdm does copy gdm-binary to /sbin/gdm in the rule for target binary-post-install/gdm::
It seems that copying that to /sbin/gdm would be enough to try out your new build.
But I would favor using a debian package build and install instead of copying one file at a time.
Here is the sequence I would use. (This assumes 7.10 with architecture i386.)
```
mkdir gdm_source
cd gdm_source
apt-get source gdm
sudo apt-get build-dep gdm
cd gdm-2.20.1/
#edit things
debuild --root-cmd=fakeroot binary
sudo dpkg -i ../gdm_2.20.1-0ubuntu1_i386.deb
```
I don't know why gdm would switch from ubuntu/metacity to xubuntu/xfce mode.  It isn't clear to me where that preference is recorded.

---

### Post by quandary on 2008-01-20
Excellent, i found out you really have to copy all files by hand, not just the one you modified...
 

Now, debuild is nicer, and did the job. No more manual work, great! Thanks!

---

