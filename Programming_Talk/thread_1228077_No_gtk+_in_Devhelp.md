---
title: "No gtk+ in Devhelp"
date: 2009-07-31
forum: Programming Talk
---

### Post by swappo1 on 2009-07-31
Hello,

I am using Devhelp with gedit while learning gtk+.  Gedit has a plugin where if you put your cursor next to a function or object and hit F2, Devhelp will bring up the reference to that function or object in Devhelp.  It seems to be working for GObject reference manual but not for Gtk reference manual.  If I look in the contents section of Devhelp, I see alot of manuals, including a manual for PYGTK2.0, but I don't see any for gtk+ in C.  How do I get gtk+ for Devhelp?  This would really be a big help since it is so time consuming searching through the gtk docs looking for functions since it is not always clear which object they are associated with.

---

### Post by JordyD on 2009-07-31
Have you tried ```
sudo apt-get install libgtk2.0-doc
```?

---

### Post by swappo1 on 2009-08-01
I am running Fedora 11 on this computer. Is gtk-doc-1.11-4.fc11.noarch the equivalent of libgtk2.0-doc in Ubuntu?

I have the following installed:
> hopchewer@hopchewer ~]$ rpm -qa | grep gtk | sort
aiksaurus-gtk-1.2.1-19.fc11.i586
authconfig-gtk-5.4.10-1.fc11.i586
avidemux-gtk-2.4.4-6.fc11.i586
fusion-icon-gtk-0.1.0-0.6.5e2dc9git.fc11.noarch
GConf2-gtk-2.26.2-1.fc11.i586
gnome-python2-gtkhtml2-2.25.3-5.fc11.i586
gtk+-1.2.10-68.fc11.i586
gtk2-2.16.2-1.fc11.i586
gtk2-devel-2.16.2-1.fc11.i586
gtk2-engines-2.18.2-1.fc11.i586
gtk-doc-1.11-4.fc11.noarch
gtkhtml2-2.11.1-5.fc11.i586
gtkhtml3-3.26.3-1.fc11.i586
gtkmathview-0.8.0-3.fc11.i586
gtkmm24-2.16.0-1.fc11.i586
gtkmm24-devel-2.16.0-1.fc11.i586
gtk-nodoka-engine-0.7.2-4.fc11.i586
gtk-sharp2-2.12.7-4.fc11.i586
gtksourcecompletion-0.5.2-2.fc11.i586
gtksourceview2-2.6.2-1.fc11.i586
gtksourceview2-devel-2.6.2-1.fc11.i586
gtkspell-2.0.15-1.fc11.i586
ibus-gtk-1.1.0.20090612-1.fc11.i586
libcanberra-gtk2-0.12-1.fc11.i586
PackageKit-gtk-module-0.4.8-2.fc11.i586
pygtk2-2.14.1-1.fc11.i586
pygtk2-codegen-2.14.1-1.fc11.i586
pygtk2-devel-2.14.1-1.fc11.i586
pygtk2-doc-2.14.1-1.fc11.noarch
pygtk2-libglade-2.14.1-1.fc11.i586
pygtksourceview-2.6.0-1.fc11.i586
python-slip-gtk-0.1.15-3.fc11.noarch
usermode-gtk-1.100-2.i586
webkitgtk-1.1.8-1.fc11.i586
xdg-user-dirs-gtk-0.8-3.fc11.i586


---

### Post by JordyD on 2009-08-01
Not sure, really. I don't use Fedora. But it looks like you have a gtk+ package in there, so you might want to see if your repos have a gtk+-doc or something like that if gtk2-doc isn't there.

---

### Post by PmDematagoda on 2009-08-03
gtk2-devel-docs is what you probably need.

---

### Post by kiran r on 2010-12-26
try to run devhelp in root mode from terminal....

---

