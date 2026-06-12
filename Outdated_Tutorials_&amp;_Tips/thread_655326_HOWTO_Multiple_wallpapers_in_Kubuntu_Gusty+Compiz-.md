---
title: "HOWTO: Multiple wallpapers in Kubuntu Gusty+Compiz-Fusion"
date: 2008-01-01
forum: Outdated Tutorials &amp; Tips
---

### Post by javielillo on 2008-01-01
Hi everyone!
Because I don't see any tutorial to apply this patch for KDE desktops I decided to do my own tutorial & share it, writing every step that I made for those that don't have a good knowledge of compiling packages etc...

Here is my first howto. Enjoy! (I hope that this help some Kubuntu Gusty users)

[[IMG]http://img444.imageshack.us/img444/6063/screenshotkde358compizfqk3.th.jpg[/IMG]](http://img444.imageshack.us/my.php?image=screenshotkde358compizfqk3.jpg) [[IMG]http://img259.imageshack.us/img259/3323/screenshotkde359compizfqi2.th.jpg[/IMG]](http://img259.imageshack.us/my.php?image=screenshotkde359compizfqi2.jpg)  [[IMG]http://img259.imageshack.us/img259/3993/screenshotkde360compizfhb0.th.jpg[/IMG]](http://img259.imageshack.us/my.php?image=screenshotkde360compizfhb0.jpg) [[IMG]http://img166.imageshack.us/img166/1860/screenshotkde361compizfac4.th.jpg[/IMG]](http://img166.imageshack.us/my.php?image=screenshotkde361compizfac4.jpg)

I made .deb packages for Kubuntu Gusty & I posted the download links at the end of the HOWTO.

First of all, **[get the patch from this page.](http://www.kde-apps.org/content/show.php/KDesktop+transparency+support?content=59864)**

I made all these steps to get successfully multiple wallpapers in Kubuntu 7.10 with compiz (Wallpaper plugin required):
**1º)** I install every dependency (build-essential, ...), I don't know if I forgot to include other required packages :S
```
sudo aptitude install build-essential fakeroot debhelper debconf kdebase-dev kdelibs-dev
```


**2º)** Download the source (in my case the sources were downloaded & unpacked automatically in my home folder):
```
sudo apt-get build-dep kdebase
sudo apt-get source kdebase
```


**3º)** I go to the kdebase-3.5.8 source code sub-folder called kdesktop & I apply the patch (before I copied the patch inside that kdesktop folder, in my case, exactly in ~/kdebase-3.5.8/kdesktop/).
I patch it with the command:
```
patch -p1 < kdesktop-transparency.patch
```
Note: I don't know if is normal or not but I was forced to create manually 2 text files without data inside called kdesktopapp.h and kdesktopapp.cpp to continue patching the required files...

**4º)** Open the kdesktop/Makefile.in & edit the next things:
1. Find line starting with
"for file in minicli.cpp"
```
for file in minicli.cpp startupid.cpp kshadowengine.cpp kshadowsettings.cpp kdesktopshadowsettings.cpp kfileividesktop.cpp ; do \
```
and insert kdesktopapp.cpp into list of cpp-files (in my case was located at the line 1464).
```
for file in kdesktopapp.cpp minicli.cpp startupid.cpp kshadowengine.cpp kshadowsettings.cpp kdesktopshadowsettings.cpp kfileividesktop.cpp ; do \
```

2. to the end of line starting with
"libkdeinit_kdesktop_la.all_cpp.cpp:"
```
libkdeinit_kdesktop_la.all_cpp.cpp: $(srcdir)/Makefile.in $(srcdir)/minicli.cpp kdesktopsettings.h $(srcdir)/startupid.cpp klaunchsettings.h $(srcdir)/kshadowengine.cpp $(srcdir)/kshadowsettings.cpp $(srcdir)/kdesktopshadowsettings.cpp $(srcdir)/kfileividesktop.cpp krootwm.moc minicli.moc startupid.moc lockeng.moc desktop.moc pixmapserver.moc kdiconview.moc kcustommenu.moc bgmanager.moc xautolock.moc
```
add "kdesktopapp.moc" (in my case was located at the line 1460).
```
libkdeinit_kdesktop_la.all_cpp.cpp: $(srcdir)/Makefile.in $(srcdir)/minicli.cpp kdesktopsettings.h $(srcdir)/startupid.cpp klaunchsettings.h $(srcdir)/kshadowengine.cpp $(srcdir)/kshadowsettings.cpp $(srcdir)/kdesktopshadowsettings.cpp $(srcdir)/kfileividesktop.cpp krootwm.moc minicli.moc startupid.moc lockeng.moc desktop.moc pixmapserver.moc kdiconview.moc kcustommenu.moc bgmanager.moc xautolock.moc kdesktopapp.moc
```

3. Just before previous line add
```

kdesktopapp.moc: $(srcdir)/kdesktopapp.h
$(MOC) $(srcdir)/kdesktopapp.h -o kdesktopapp.moc
```


**5º)** After these changes on the kdebase folder build the deb packages, someone called Dred wrote me:
```
dpkg-buildpackage -rfakeroot -uc -b
```
but I used that one
```
dpkg-buildpackage -rsudo -uc -b
```
(and because I made some wrong things I was forced to run "make distclean" command before the dpkg-buildpackage command)


**6º)** The new .deb packages are located on the home folder. I installed the new created package called kdesktop_3.5.8-0ubuntu2_i386.deb (where is located the changes):
sudo dpkg -i kdesktop_3.5.8-0ubuntu2_i386.deb
(in my case I was forced to downgrade from *ubuntu**2.1**_i386.deb packages to *ubuntu**2**_i386.deb using the command "sudo dpkg -i *.deb", installing ALL the .deb packages from the home folder. If you had other .deb files in the home folder be aware about what more will be installed :P )


**7º)** Go to the ~/.kde/share/config/ folder and edit the kdesktoprc file to include the next code:
```
[Background Common]
BackgroundOpacity=90 (0 = fully transparent / 100 = opaque)
```


**8º)** I made a script to kill & restart the kdesktop with the command "--bg-transparency" that xonestonex wrote. Save it in a text file with execution permission and copy it to the ~/.kde/Autostart/ folder to be loaded at the KDE start, the script code could be more optimized but works for me and I called it kdesktop-transparency.sh, test it before you copy the file into that folder to verify that works.
```
#!/bin/sh
# Kills KDesktop & after is re-launched with the command "kdesktop --bg-transparency".
# Should be loaded at the start of KDE load.
# Be sure that .kde/share/config/kdesktoprc has this new section:
# [Background Common]
# BackgroundOpacity=90 (0 = fully transparent / 100 = opaque)

local pid

pid=$(ps ax |grep "kdesktop " |grep -v grep|awk '{print $1;}')
echo -n "Killing Kdesktop (process $pid)... "
kill -9 $pid
echo "Killed."
kdesktop --bg-transparency 2> /dev/null
echo "Kdesktop ON with transparency support for Compiz's Wallpaper plugin)"

```

This script must be started before Compiz is loaded, then you could put the Compiz command at the end of the file or use the Fusion-icon after the script execution (I tried with success both methods) or run manually compiz after the desktop is loaded.


If Compiz-Fusion not have the Wallpaper plugin (that was my case) visit the tutorial page for install additional plugins:
```
http://forum.compiz-fusion.org/showthread.php?t=5303
```
From the list of plugins we only need the wallpaper.tar.gz download (I no post the download link because it could be modified & here could become outdated/obsolete :P )


Finally, here is the link to download the binaries for Kubuntu (I had to downgrade some KDE packages (exactly the kdebase packages) from *ubuntu**2.1**_i386.deb to *ubuntu**2**_i386.deb so I would like to try later how to build the latests sources):
- Patched Kdesktop deb package:
[http://massmirror.com/df3d3bf528463823e2a1466e8734a082.html](http://massmirror.com/df3d3bf528463823e2a1466e8734a082.html)
- All  kdebase .deb packages for Kubuntu Gusty that I got with this HOWTO:
[http://massmirror.com/05bc6f62c9e2f5006ff9730696922aba.html](http://massmirror.com/05bc6f62c9e2f5006ff9730696922aba.html)

**Note:** about Wallpaper plugin of Compiz-Fusion every image should have the next format:
```
file:/location Of Your Image:100
```
An example of one of my added images:
```
file:/home/javielillo/mis_cosas/imagenes/Bleach - Orihime Inoue.jpg:100
```


Special thanks for xonestonex (who made the patch) and specially Dred (that told us what was necessary to modify in one file to be able to compile the deb packages) from this [page](http://www.kde-apps.org/content/show.php/KDesktop+transparency+support?content=59864)

---

### Post by ll PaSt ll on 2008-04-18
I'm still fairly new to Linux, tried many KDE Distros such as OpenSuse, Fedora, Slackware (fast but way too much configuring), Mint, etc. I love Kubuntu best (currently on Hardy from Gutsy and Feisty). Tried GNOME Distros as well and it just doesn't cut it for me, I love flexibility.

Im going to give as much info as I know for understanding **PATCH** and to possibly get info as well as providing info to those not understanding **patch** such as my self.

First let me say your tutorial is really nice, still, just a little bit too much for my beginner's behind to understand. Getting stuck a number 3.
Im pretty new at this, more like a decent noob, but I can't seem figure out this **PATCH**.

I might be understanding this wrong so please correct me.

1st thing is I tried to understand **PATCH** by entering in the terminal:
```
man code
```

Now that I **only** understand the purpose of:
```
patch -p1 < [location&name_of_patch]
```

I don't think I understand what I apply it to.

But, from my understanding, I am replacing or adding something with the text [COLOR="Blue"]located here:[/COLOR]
[http://www.kde-apps.org/CONTENT/content-files/59864-kdesktop-transparency.patch](http://www.kde-apps.org/CONTENT/content-files/59864-kdesktop-transparency.patch)

to the kdesktop source code? (in my case; located somewhere in /home/mycomputer/kdebase-3.5.9/kdesktop)

or am I **making a new file** with the containing text replicating the kdesktop source code exactly (eg. same source code file type?), but with a slightly different name? (eg. such as main.cc to kdesktop-transparency? but containing the text in the patch?)

And, is main.cc the source code you all speak of?

This is the closest tutorial on **patch** [COLOR="Blue"]I have found:[/COLOR]
[http://www.linuxjournal.com/article/6183](http://www.linuxjournal.com/article/6183)

Maybe someone else can help figure this out with the provided information and/or explain a little bit more, **or** provide a link that lets beginners understand more on **patch**.

thanx

---

### Post by techphets on 2009-05-04
Will this work on Jaunty?

---

