---
title: "Forcing Unity installation comes closer"
date: 2011-07-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-29
Yesterday I noticed new Usb-creator (usb-creator-gtk 0.2.31) was changed to depend on gir1.2-unity-3.0 and libunity4.
Now also new Brasero (libbrasero-media3-1 3.0.0-1ubuntu3) depends on unity (unity4).

I say this again, I do not endorse ripping down the freedom of choice.
If I choose to use gnome-shell, why am I compelled to install unity packages?

---

### Post by SevenMachines on 2011-07-29
I think theres probably a lot of people who are feeling the same sort of frustration :)

---

### Post by MacUntu on 2011-07-29
Have you filed a bug report?

Besides, this has nothing to do with freedom of choice. You are still free to use GNOME Shell, aren't you? You are still free to recompile the software without links to Unity. You are still free to choose another distribution. Don't confuse "Why isn't Ubuntu exactly the way I want it to be" with ripping down your freedom of choice.

---

### Post by SevenMachines on 2011-07-29
Think its to do with enabling launcher progress business in ubuntu? Not a bug I'd think.

---

### Post by Harry33 on 2011-07-29
> **MacUntu said:**
> Have you filed a bug report?

Besides, this has nothing to do with freedom of choice. You are still free to use GNOME Shell, aren't you? You are still free to recompile the software without links to Unity. You are still free to choose another distribution. Don't confuse "Why isn't Ubuntu exactly the way I want it to be" with ripping down your freedom of choice.

Do not think, that this is where this ends.
Right now (if I use usb-creatro or brasero) I have to install Unity libraries.
What next? Are you saying soon that even though I have to install the complete unity,
I can still use gnome-shell.
Well it would be the same now if i had to install KDE libraries too.
The freedom means it is left for me to choose whether I need unity or kde libraries.

I did not install those libraries, however. I chose to uninstall usb-creator and brasero.

There is this bug report I made:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/817718](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/817718)

---

### Post by dino99 on 2011-07-29
> **Harry33 said:**
> 

I did not install those libraries, however. I chose to uninstall usb-creator and brasero.


be happy, you get a lighter system :) (like me)

---

### Post by lucazade on 2011-07-29
I gave up fighting with these dependencies, not funny to deal with.
I usually find some way to make these unwanted pieces to not eat system resources.

---

### Post by MacUntu on 2011-07-29
> **Harry33 said:**
> Do not think, that this is where this ends.

Until there's feedback on your bug report, we don't even know if it has started yet.

Why the need to spread FUD ("Forcing Unity installation comes closer")?

---

### Post by SevenMachines on 2011-07-29
Still king of the dependencies on my computer is the magnificent kcachegrind, unforunately its the only kde needing program I have, and it wants pretty much it all! Still worth it though :)

---

### Post by MacUntu on 2011-07-29
Tell me about it, I'm a Kile user. :P

---

### Post by jbicha on 2011-07-29
Harry33, please calm down.

People make mistakes. You filed a bug report. I expect the bug will be fixed reasonably soon. Give the devs a bit of time. Your bug is definitely not the most critical thing going on in Ubuntu this week.

These comments do not encourage Ubuntu developers to want to help you:
"I say this again, I do not endorse ripping down the freedom of choice."
"Do not think, that this is where this ends."

No, the Ubuntu developers are not trying to force Unity on you, but it is the flagship desktop for Ubuntu. It would be a whole lot less stressful for you if you just kept Unity and ubuntu-desktop installed. Do you seriously need the few hundred megabytes of hard drive space (at most) it takes to keep the defaults in addition to your preferences? And if you're not running Unity, it isn't really using your RAM either.

Alternatively, there are a whole lot of other distros that don't even have Unity in their repositories so you wouldn't have to worry about these issues.

---

### Post by SevenMachines on 2011-07-29
> **MacUntu said:**
> Tell me about it, I'm a Kile user. :P
Ironically I've just noticed kcachegrind also comes with a qt version qcachegrind, we build the kde one... Might look into getting qcachegrind done as well

[EDIT] Sorry, drifting a bit off topic, its a friday thing

---

### Post by sanderd17 on 2011-07-29
> **MacUntu said:**
> Tell me about it, I'm a Kile user. :P

Same here, Gummi looks promising though [http://gummi.midnightcoding.org/?page_id=4](http://gummi.midnightcoding.org/?page_id=4)

---

### Post by 3vi1 on 2011-07-29
Not a bug.

The program calls those libraries, so it needs those libraries.  Should the author really have to write and maintain their own checks for every type of desktop integration rather than just call the libraries that already do it?  All to save a minuscule 500kBish of space in sidecar libraries?

You might as well be filing bugs complaining that usb-creator-gtk makes you install the gtk libraries.  Just because someone doesn't run KDE doesn't mean they won't need Qt libraries when they run a GUI developed for that desktop.

---

### Post by buzzmandt on 2011-07-29
Agreed, NOT a bug and will be set as such on any bug reports.

Just as 3vi1 said the program calls for those libraries/dependencies.

The only fix for this is a new ubuntu flavor for gnome 3.  This way dependencies are independent of main ubuntu branch.  Just the same way that kubuntu has it's own dependencies as does lubuntu, xubuntu, etc.

A gnome-shell*buntu will have it's own dependencies for gnome-shell, not unity.

---

### Post by Harry33 on 2011-07-29
> **buzzmandt said:**
> 
...
The only fix for this is a new ubuntu flavor for gnome 3.  This way dependencies are independent of main ubuntu branch.  Just the same way that kubuntu has it's own dependencies as does lubuntu, xubuntu, etc.

A gnome-shell*buntu will have it's own dependencies for gnome-shell, not unity.

I can agree on that one.

---

### Post by Harry33 on 2011-07-29
Anyways, marking this as solved (for me at least).
I have uninstalled the applications (usb-creator and brasero) that bothered me.

---

### Post by seeker5528 on 2011-07-29
> **Harry33 said:**
> If I choose to use gnome-shell, why am I compelled to install unity packages?

> libunity is a shared library to be able to interact with the launcher
and add places in Unity environment.

Don't know why it would be 'Depends' instead of 'Recommends', but it's not like you are being forced to install Unity.

EDIT: I did add an anti-dependency comment to the bug report, a series of questions in response to an earlier comment. 

Later, Seeker

---

### Post by pferraro on 2011-07-29
> **SevenMachines said:**
> Think its to do with enabling launcher progress business in ubuntu? Not a bug I'd think.

Then it's just sloppy packaging.  This logic ought to reside in a separate brasero-unity and usb-creator-unity packages, instead of patching this stuff into the main packages (thus diverting further from the upstream debian packages).

---

### Post by seeker5528 on 2011-07-29
> **buzzmandt said:**
> The only fix for this is a new ubuntu flavor for gnome 3.  This way dependencies are independent of main ubuntu branch.  Just the same way that kubuntu has it's own dependencies as does lubuntu, xubuntu, etc.

A gnome-shell*buntu will have it's own dependencies for gnome-shell, not unity.

If it was just usb-creator-gtk that had the dependency I might accept that logic, since it is a single application with a single purpose that other *buntus may choose to include or not, people may choose to install or not. But libbrasero-media is a normal library depended on by other applications people using Gnome in particular since Brasero is a dependency of the Gnome desktop metapackage, looks like soundjuicer is too, but could also be expected to be installed by people using other non-Unity environments....

```
libbrasero-media3-1
  Reverse Depends: brasero (= 3.0.0-1ubuntu3)
  Reverse Depends: brasero-cdrkit (= 3.0.0-1ubuntu3)
  Reverse Depends: goobox (>= 2.90.1-1)
  Reverse Depends: libbrasero-media3-dev (= 3.0.0-1ubuntu3)
  Reverse Depends: rhythmbox-plugin-cdrecorder (>= 2.90.1~20110329-1ubuntu5)
  Reverse Depends: sound-juicer (>= 2.32.1+20110330-1)
brasero
  Reverse Depends: gnome-desktop-environment (>= 1:2.30+7ubuntu3)
gnome-desktop-environment
  Reverse Depends: gnome (= 1:2.30+7ubuntu3)
```

Later, Seeker

---

### Post by Harry33 on 2011-07-30
> **seeker5528 said:**
> If it was just usb-creator-gtk that had the dependency I might accept that logic, since it is a single application with a single purpose that other *buntus may choose to include or not, people may choose to install or not. But libbrasero-media is a normal library depended on by other applications people using Gnome in particular since Brasero is a dependency of the Gnome desktop metapackage, looks like soundjuicer is too, but could also be expected to be installed by people using other non-Unity environments....

```
libbrasero-media3-1
  Reverse Depends: brasero (= 3.0.0-1ubuntu3)
  Reverse Depends: brasero-cdrkit (= 3.0.0-1ubuntu3)
  Reverse Depends: goobox (>= 2.90.1-1)
  Reverse Depends: libbrasero-media3-dev (= 3.0.0-1ubuntu3)
  Reverse Depends: rhythmbox-plugin-cdrecorder (>= 2.90.1~20110329-1ubuntu5)
  Reverse Depends: sound-juicer (>= 2.32.1+20110330-1)
brasero
  Reverse Depends: gnome-desktop-environment (>= 1:2.30+7ubuntu3)
gnome-desktop-environment
  Reverse Depends: gnome (= 1:2.30+7ubuntu3)
```

Later, Seeker

This is a good point.
Saying the application calls for libunity is not the whole truth.
Of course it calls for it, because Canonical has patched it to do so.
The original gnome brasero application does not call for libunity.
And because the brasero (and who knows what next too) is used widely outside unity, it is IMO a wrong dependency.

---

### Post by 3rdalbum on 2011-07-30
> **Harry33 said:**
> This is a good point.
Saying the application calls for libunity is not the whole truth.
Of course it calls for it, because Canonical has patched it to do so.
The original gnome brasero application does not call for libunity.
And because the brasero (and who knows what next too) is used widely outside unity, it is IMO a wrong dependency.

Not necessarily.

If Brasero has been patched to use the Unity progress bars, then this support probably can't be put into a brasero-unity package, and therefore you'll need the libunity package to install this new Brasero.

This is really a non-issue. Packagers list dependencies so you don't get error messages about "you're missing this library". Why would Canonical bother to package Brasero in this way to cause you to reinstall Unity? What would be the gain for them, if you're not using Unity anyway?

Take off your conspiracy theory hat, please.

---

### Post by buzzmandt on 2011-07-30
> **3rdalbum said:**
> Not necessarily.

Take off your conspiracy theory hat, please.

Agreed
I see nothing labled unity in brasero.  It has to call on some gnome libs because it is a gnome app and unity is a gnome app, there will be cross references on occasion since they might just use a same lib.  
```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ aptitude show brasero
Package: brasero                         
State: not installed
Version: 3.0.0-1ubuntu3
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 1,094 k
Depends: libbrasero-media3-1 (= 3.0.0-1ubuntu3), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.28.0), libgstreamer-plugins-base0.10-0 (>= 0.10.0),
         libgstreamer0.10-0 (>= 0.10.15), libgtk-3-0 (>= 3.0.0), libice6 (>= 1:1.0.0), liblaunchpad-integration-3.0-1 (>= 0.1.17), libnautilus-extension1 (>= 1:2.91), libpango1.0-0 (>=
         1.14.0), libsm6, libtotem-plparser17 (>= 2.32), libxml2 (>= 2.7.4), gstreamer0.10-plugins-base (>= 0.10.0), gnome-icon-theme, gvfs, brasero-common (>= 3.0), brasero-common (< 3.1)
Recommends: brasero-cdrkit
Suggests: vcdimager, libdvdcss2
Conflicts: nautilus-cd-burner
Description: CD/DVD burning application for GNOME
 Brasero is a simple application to burn, copy and erase CD and DVD media: audio, video or data. It features among other things: 
 * On-the-fly burning 
 * Multisession support 
 * On-the-fly conversion of music playlists in all formats supported by GStreamer 
   
 This package contains the main binary, the burning plugins and the nautilus extension. 
 
 The following packages, if installed, will provide Brasero with added functionality: 
 * cdrdao to burn combined data/audio CDs and for byte-to-byte copy 
 * GStreamer backends to support more audio formats 
 * vcdimager to create VCDs or SVCDs 
 * libdvdcss2 to copy encrypted DVDs
Homepage: http://www.gnome.org/projects/brasero/

```

---

### Post by Harry33 on 2011-07-30
> **buzzmandt said:**
> Agreed
I see nothing labled unity in brasero.  It has to call on some gnome libs because it is a gnome app and unity is a gnome app, there will be cross references on occasion since they might just use a same lib.  
...


You are looking at the wrong package.
See this:
> librasero-media (3.0.0-1ubuntu3)
Depends on:
brasero-common (>= 3.0)
brasero-common (<< 3.1)
dvd+rw-tools
libappindicator3-1 (>= 0.2.92)
libburn4 (>= 1.1.0.pl01)
libc6 (>= 2.7)
libcairo2 (>= 1.10.0)
libcanberra-gtk3-0 (>= 0.25)
libgdk-pixbuf2.0-0 (>= 2.22.0)
libglib2.0-0 (>= 2.28.0)
libgstreamer-plugins-base0.10-0 (>= 0.10.12)
libgstreamer0.10-0 (>= 0.10.15)
libgtk-3-0 (>= 3.0.0)
libisofs6 (>= 1.1.2)
libnotify4 (>= 0.7.0)
libpango1.0-0 (>= 1.14.0)
libtotem-plparser17 (>= 2.32)
**libunity4 (>= 3.4.6)**
libxml2 (>= 2.7.4)

Also:
> brasero (3.0.0-1ubuntu3) oneiric; urgency=low
  * debian/patches/013_unity_launcher_progress: Display burn progress
    in Brasero's Unity launcher icon.

---

### Post by buzzmandt on 2011-07-30
I stand corrected.  time for a gnome-shell*buntu line is all i can say.

---

### Post by 3vi1 on 2011-07-30
Maybe I can put it a different way, such that you feel better about the fact that these packages require some minor unity support libs.

Here you can see that it's not a bug... because the packages (usb-creator, for this example) do actually call the unity libraries.

```
diff -Nru usb-creator-0.2.30/debian/control usb-creator-0.2.31/debian/control
--- usb-creator-0.2.30/debian/control	2011-05-19 16:58:35.000000000 +0000
+++ usb-creator-0.2.31/debian/control	2011-07-28 16:26:59.000000000 +0000
@@ -34,6 +34,7 @@
  gir1.2-gtk-3.0,
  gir1.2-pango-1.0,
  gir1.2-glib-2.0,
+ gir1.2-unity-3.0,
  python-dbus
 Description: create a startup disk using a CD or disc image (for GNOME)
  Startup Disk Creator converts a USB key or SD card into a volume from which you
diff -Nru usb-creator-0.2.30/usbcreator/frontends/gtk/frontend.py usb-creator-0.2.31/usbcreator/frontends/gtk/frontend.py
--- usb-creator-0.2.30/usbcreator/frontends/gtk/frontend.py	2011-05-19 16:55:40.000000000 +0000
+++ usb-creator-0.2.31/usbcreator/frontends/gtk/frontend.py	2011-07-28 16:12:38.000000000 +0000
@@ -25,6 +25,7 @@
 from gi.repository import Gtk
...
+        self.unity = UnitySupport(parent=self)
 
```

Now, how is this a good thing?  Well... since every package that wants to integrate with Unity's notifications calls this really small support library instead of building the code into their application... you actually end up with much *less* space used after you install a couple of apps that do this.

Also, when a bug in the integration is found, you don't have to needlessly update all your apps when just the one small lib can be updated.

TLDNR:  Don't worry.  Be happy.  :)

---

### Post by Harry33 on 2011-07-30
> **3vi1 said:**
> Maybe I can put it a different way, such that you feel better about the fact that these packages require some minor unity support libs.

Here you can see that it's not a bug... because the packages (usb-creator, for this example) do actually call the unity libraries.
...
Now, how is this a good thing?  Well... since every package that wants to integrate with Unity's notifications calls this really small support library instead of building the code into their application... you actually end up with much *less* space used after you install a couple of apps that do this.

Also, when a bug in the integration is found, you don't have to needlessly update all your apps when just the one small lib can be updated.

TLDNR:  Don't worry.  Be happy.  :)

Brasero is part of Gnome, an upstream application.
Of course, if it is modified or patched, it calls for additional libraries.
The issue is not that.
The issue is, that also gnome-shell is in the ubuntu oneiric repositories.
Brasero should be made for gnome-shell too.
Now I would need to install unity library even though I do not have unity installed at all, I do not have unity notification system installed either.
What good is it then to have the unity library installed.

Surely I can install all the packages there are available in the repos.
The issue is, that I do not want to do so.

---

### Post by jerrylamos on 2011-07-30
[www.ubuntu.com](www.ubuntu.com) says

"Your PC, your way

Choose from thousands of free apps in the Ubuntu Software Centre so you can customise your computer just how you like it."

It's getting pretty hard to customize my computer.  Maybe Mark Shuttleworth should remove that statement....

As a tester I try whatever "they" throw over the wall....variant I'm doing is Unity-2D because as a photo taker I prefer clean sharp crisp images not fuzzy fading ones...at a price in processor cycles to boot. 

Jerry

---

### Post by seeker5528 on 2011-08-01
> **3vi1 said:**
> Now, how is this a good thing?  Well... since every package that wants to integrate with Unity's notifications calls this really small support library instead of building the code into their application... you actually end up with much *less* space used after you install a couple of apps that do this.

Also, when a bug in the integration is found, you don't have to needlessly update all your apps when just the one small lib can be updated.

None of that is an issue. Considering the size of the library, size is only a minor issue, if you are *that* worried about HDD space, it seems like you got bigger issues.

It really comes down to one thing... Since the library only provides a useful function if the Unity launcher is running, why is the support hacked into multiple applications in a way that those applications fail if the library is not there? 

It just seems to go against the grain and the response to the bug report indicating 'run time checking adds complexity' is not very satisfactory. Short term I could accept that they just wanted to get the feature into some applications and get some testing on it, but long term doing the run time checking definitely seems like the better way to go in terms of getting upstream to integrate patches enabling the support and getting other distributions that may want to supply Unity to enable the support in the applications.

Later, Seeker

---

### Post by 3rdalbum on 2011-08-02
> **jerrylamos said:**
> [www.ubuntu.com](www.ubuntu.com) says

"Your PC, your way

Choose from thousands of free apps in the Ubuntu Software Centre so you can customise your computer just how you like it."

It's getting pretty hard to customize my computer.  Maybe Mark Shuttleworth should remove that statement....

Why? Because installing a CD burning program pulls in a library as a dependency?

Note that it doesn't pull in the whole of Unity, it just pulls in a library related to Unity.

So what, really? Feel free to remove the actual libunity.so file if you really don't want it in there.

---

### Post by EkuquoL on 2011-08-02
Unity is a skinned or scheme version of Gnome.

---

### Post by sgage on 2011-08-02
> **EkuquoL said:**
> Unity is a skinned or scheme version of Gnome.

No, Unity is a shell on top of the Gnome stack. In Natty, it used the Gnome 2.3.x stack, in Oneiric, 3.1.x.

Gnome Shell is the official Gnome Project shell for Gnome 3.

---

