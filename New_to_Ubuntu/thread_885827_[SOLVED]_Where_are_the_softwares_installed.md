---
title: "[SOLVED] Where are the softwares installed??"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by diwas on 2008-08-10
When I install any packages where does it gets "installed into" (by default)? 
I mean is it the /home folder?? Or somewhere else?

Helps appreciated.
Thank you.

---

### Post by SunnyRabbiera on 2008-08-10
Usually linux apps are installed into usr/bin or usr/lib depending.
Games are intalled under usr/games.
Your home directory is for personal files, it contains no real applications unless you untar a app like firefox off the web or something like that.
The home directory is more like my documents under windows then anything else.

---

### Post by bpowell2005 on 2008-08-10
> **diwas said:**
> When I install any packages where does it gets "installed into" (by default)? 
I mean is it the /home folder?? Or somewhere else?

Helps appreciated.
Thank you.

That's a loaded question! Generally, the executable part of the program ends up in /bin...but there are all kinds of exceptions. I'm told the linux file system is more logical that Windows...I believe it, I'm just still not used to how it works.

Configuration files / directories of installed programs will reside in the /home directory of the user...so you'll see lots of configuration files in your home directory (they're generally hidden) if you do a ls -ah (list files, attributes hidden)

---

### Post by okey666 on 2008-08-10
I think the software gets installed into many places.
This is the locations of various files instaled by an opera deb:
> usr/share/opera/svg-sabd.dat
usr/share/opera/svg-se.dat
usr/share/opera/svg-sebd.dat
usr/share/opera/encoding.bin
usr/share/icons/
usr/share/icons/hicolor/
usr/share/icons/hicolor/22x22/
usr/share/icons/hicolor/22x22/apps/
usr/share/icons/hicolor/22x22/apps/opera.png
usr/share/icons/hicolor/32x32/
usr/share/icons/hicolor/32x32/apps/
usr/share/icons/hicolor/32x32/apps/opera.png
usr/share/icons/hicolor/48x48/
usr/share/icons/hicolor/48x48/apps/
usr/share/icons/hicolor/48x48/apps/opera.png
usr/share/icons/hicolor/16x16/
usr/share/icons/hicolor/16x16/apps/
usr/share/icons/hicolor/16x16/apps/opera.png
usr/share/doc/
usr/share/doc/opera/
usr/share/doc/opera/copyright
usr/share/doc/opera/LGPL.gz
usr/share/doc/opera/changelog.gz
usr/share/man/
usr/share/man/man1/
usr/share/man/man1/opera.1.gz
usr/share/applications/
usr/share/applications/opera.desktop
usr/share/pixmaps/
usr/share/pixmaps/opera.xpm
usr/share/menu/
usr/share/menu/opera
usr/lib/
usr/lib/opera/
usr/lib/opera/plugins/
usr/lib/opera/9.51/
usr/lib/opera/9.51/missingsyms.so
usr/lib/opera/9.51/spellcheck.so
usr/lib/opera/9.51/opera
usr/lib/opera/9.51/works
usr/lib/opera/9.51/operaplugincleaner
usr/lib/opera/9.51/operapluginwrapper
usr/lib/opera/9.51/operapluginwrapper-native
usr/lib/opera/9.51/operapluginwrapper-ia32-linux
usr/bin/
usr/bin/opera
etc/
etc/opera6rc.fixed
etc/opera6rc

---

### Post by SunnyRabbiera on 2008-08-10
> **okey666 said:**
> I think the software gets installed into many places.
This is the locations of various files instaled by an opera deb:

Technically yes, but the main application usually goes into usr/bin.

---

### Post by The Titan on 2008-08-10
if you go to the package in synaptic and right click there is an option like view installed files or something like that, sorry, i havent used gnome in a while =|.  But that is useful for finding where an application installed too....

---

### Post by diwas on 2008-08-10
Oh damn. I actually upgraded my harddrive today...and my Filesystem is like arnd 5GEGS. So i wanted to increase the size without formattin and reinstalling it.

Is there anyway to do that??

---

### Post by SunnyRabbiera on 2008-08-10
> **The Titan said:**
> if you go to the package in synaptic and right click there is an option like view installed files or something like that, sorry, i havent used gnome in a while =|.  But that is useful for finding where an application installed too....

Indeed.
Open up synaptic located under system > administration > synaptic package manager
after that go to "settings" and then to "preferences" and in the "general" tab put a check in the first box and hit "apply".
Easy

---

### Post by diwas on 2008-08-10
??

---

### Post by SunnyRabbiera on 2008-08-10
> **diwas said:**
> ??

That is how you can find out where crap is downloaded to when you use your installer.

---

### Post by diwas on 2008-08-10
> **diwas said:**
> Oh damn. I actually upgraded my harddrive today...and my Filesystem is like arnd 5GEGS. So i wanted to increase the size without formattin and reinstalling it.

Is there anyway to do that??

any solution??

---

### Post by SlalomMan on 2008-08-10
You upgraded your HD, and your linux filesystem is 5GB? (That's what I got from the message, unless you're using some uber tech talk that went whoosh over my head)

If you have free space on your HD, you can install gparted, a great partition editor using 
```
sudo apt-get install gparted
``` It may ask for some other dependencies to be installed. This will only work for shrinking other partitions, if you want to work on your ubuntu partition, you can either use GParted from the Ubuntu LiveCD or download the Gparted LiveCD and burn it. Either should work. If you need help using gparted, just let me know.

---

### Post by diwas on 2008-08-10
Yes, you got that right.

But its like I want to "move" the current OS to another partition.

---

### Post by SlalomMan on 2008-08-10
Move it to another partition? Or just make the partition bigger? Or move the OS to the new hard drive?

---

### Post by The Titan on 2008-08-10
> Indeed.
Open up synaptic located under system > administration > synaptic package manager
after that go to "settings" and then to "preferences" and in the "general" tab put a check in the first box and hit "apply".
Easy

I know, i was saying that you could see where the files were installed. (Note: This was the original topic of the thread) =P

---

### Post by diwas on 2008-08-11
> **SlalomMan said:**
> Move it to another partition? Or just make the partition bigger? Or move the OS to the new hard drive?


Actually i need the process of 2 of the question mentioned above.

1. Make the partition bigger.
2. Move the OS to the new hard drive.

Actually i currently want to make my "Filesystem" partition bigger...and in the future...(in about 2-3 weeks) i would like to move the OS to another partition.

Is this possible???

---

### Post by diwas on 2008-08-12
bump

---

