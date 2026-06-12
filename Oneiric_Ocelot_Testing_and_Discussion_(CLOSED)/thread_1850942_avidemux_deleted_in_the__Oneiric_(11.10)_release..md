---
title: "avidemux deleted in the  Oneiric (11.10) release."
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mmasroorali on 2011-09-27
I am trying Ubuntu 11.10 beta2 right now and as I found at [http://www.ubuntuupdates.org/packages/show/354328](http://www.ubuntuupdates.org/packages/show/354328), avidemux has been deleted in the Oneiric (11.10) release.

Could anybody know the reason behind this? 

What is our alternative? 

I found avidemux very useful.

---

### Post by nothingspecial on 2011-09-27
Moved to Ubuntu +1 (Oneiric Ocelot)

---

### Post by mmasroorali on 2011-09-27
> **nothingspecial said:**
> Moved to Ubuntu +1

Would you mind putting in one line more? Because what exactly is meant by Ubuntu +1? I find Ubuntu +1 (Oneiric Ocelot) at [http://ubuntuforums.org/forumdisplay.php?f=403](http://ubuntuforums.org/forumdisplay.php?f=403), but we are also talking about Oneiric Ocelot.

What is it I might be missing?

---

### Post by cariboo on 2011-09-27
Check the very top of the page, you'll see something like the screenshot.

As far as avidemux is concerned, there were/are quite a few packages that failed to build with the conversion to GTK-3, the only thing I can suggest is to keep an eye on the avidemux page on [https://launchpad.net](https://launchpad.net).

---

### Post by SevenMachines on 2011-09-27
This one maybe?
[https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096)
In progress...

---

### Post by mc4man on 2011-09-27
I would think that they should be able to square this, the 2.5.X version is gtk2 and or qt4 which isn't a big issue in 11.10.

The 2.5 does need a patch to use the more current versions of libx264, like the one used in debian mm  - 03_x264-115.diff
(just to see went ahead a built a slightly modified DMM source here using 11.10 libs, went ok and the avidemux packages installed & run (though there were an uncomfortable # of dpkg-shlibdeps: warning's

The other option would be for ubuntu to move to 2.6 which is likely gtk3 & may be ok with the current libx264, but don't see that happening

---

### Post by alphacrucis2 on 2011-09-27
> **mc4man said:**
> I would think that they should be able to square this, the 2.5.X version is gtk2 and or qt4 which isn't a big issue in 11.10.

The 2.5 does need a patch to use the more current versions of libx264, like the one used in debian mm  - 03_x264-115.diff
(just to see went ahead a built a slightly modified DMM source here using 11.10 libs, went ok and the avidemux packages installed & run (though there were an uncomfortable # of dpkg-shlibdeps: warning's

The other option would be for ubuntu to move to 2.6 which is likely gtk3 & may be ok with the current libx264, but don't see that happening

As far as I know the 2.6 version is still considered experimental by the developer. I did install a daily build (qt version) in Natty a couple of months ago and it seemed to be workable.

---

### Post by alphacrucis2 on 2011-09-27
> **SevenMachines said:**
> This one maybe?
[https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096)
In progress...


I wonder why they are trying to build 2.5.4 when the Avidemux devs released a bug fix version 2.5.5 in June.

---

### Post by mc4man on 2011-09-27
The 2.5.5 will still need an x264 patch to use in 11.10 (tested here with a straight up cmake build/install & debian package build - using default 11.10 libs
The 2.6 builds fine, no patch needed (qt4) - the inc. deb build script is cute but seems ok. (likely only dpkg will install the .debs

If you wish to try will attach patch lifted from DMM sources

---

### Post by alphacrucis2 on 2011-10-01
Hi mc4man,

As they are still having trouble getting 2.5 to build, I decided to try avidemux 2.6 from source on Oneiric 64. As Avidemux only supply 32 bit debs for 2.6 I used the latest source snapshot from

[http://www.avidemux.org/nightly/source/](http://www.avidemux.org/nightly/source/)

I followed Mr Mean's instructions here:

[http://avidemux.org/admWiki/doku.php?id=build:install_2.6](http://avidemux.org/admWiki/doku.php?id=build:install_2.6)

Used the specified bash script to compile source and build the deb files:

bash bootStrap.bash --deb

This creates qt version but the above wiki explains what to do if you want gtk.

The first time it failed miserably because when I extract the source tar, I didn't check the option to recreate the directories so it dumped all the files into a single folder which confused the script as it expects the various source files to be sitting in specific sub directories. As soon as I sorted that out the bootStrap.bash script ran correctly and created four deb files which I installed. The 2.6 version works ok for me but I gather the dev Mr Mean doesn't consider it ready for release yet.

The only problem I have though is the unity launcher. I have to run avidemux3_qt from terminal. If I then right click on the launcher and select "Keep in Launcher", the avidemux icon stays there but clicking on the icon to start avidemux doesn't actually work. Not sure why at this time.

---

### Post by mc4man on 2011-10-01
The main issue on 11.10 is a package build for amd_64, I'd think it could be worked out, will see what M. Pitt thinks next week.
(I got a straight up build to work for 64 bit by not passing a ld flag, don't know myself how to prevent that  in a package build scenario, 32 bit is fine for package

The launcher icon for your 2.6 build represents the binary - can't be saved.

What you might want to do is create a .desktop that Exec= to the binary  & use that, should be fine.

(The 2.6 built fine with no x264 patch as a straight up build, (qt4), but 11.10 will not be using it, it's 2.4/5 or nothing

---

### Post by alphacrucis2 on 2011-10-01
Thanks. I used 

 gnome-desktop-item-edit ~/.local/share/applications/ --create-new

To create new avidemux shortcut and started from that. Then the keep in launcher works.

---

