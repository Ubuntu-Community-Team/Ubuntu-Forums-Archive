---
title: "[SOLVED] can't watch youtube videos in FF3"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ninja senses on 2008-06-20
anyone have a solution?  I chercked my add-ons and there is a bunch of video plugins already there, why arent they playing?

---

### Post by monkey56657 on 2008-06-20
Among the list of plugins is there one called "Shockwave Flash" or a Flash alternative?

Also, Does the youtube player show up but just not play? Or can't you see the player at all?

---

### Post by ninja senses on 2008-06-20
> **monkey56657 said:**
> Among the list of plugins is there one called "Shockwave Flash" or a Flash alternative?

Also, Does the youtube player show up but just not play? Or can't you see the player at all?

Yes shockwave flash 8.0 r99 Gnash 0.8.1  <- is what it says

The whole youtube(or any video online really) doesnt show up

---

### Post by kansasnoob on 2008-06-20
I'd start by adding the Medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Make sure you add the GPG key!

Then open Synaptic and make sure the Medibuntu repo is "checked".

Software Sources should look like this:

[ATTACH]74702[/ATTACH]

[ATTACH]74703[/ATTACH]

[ATTACH]74704[/ATTACH]

Then click "Reload" in synaptic and wait until it's done running.

Now use the search feature in synaptic and install all of this:

gstreamer (ALL gstreamer - good, bad and ugly - if it starts with gstreamer install it)

sun-java6 (ALL sun-java6 except "doc" and "source") - doc wastes space and source breaks things!

flashplugin-nonfree

NOT RELATED but you'll likely want it later anyway:

acroread

non-free-codecs

---

### Post by kattman on 2008-06-20
get the Flash plugin from Synaptic Package Manager
You want the flashplugin-nonfree

---

### Post by Dynaflow on 2008-06-20
Follow this guide and all should be well with Flash:  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

(There's also a comprehensive troubleshooting section at the bottom of the first post for both Flash and Java, each of which plays a role in getting Flash video to run.)

---

### Post by kansasnoob on 2008-06-20
Sorry at least one of those screenshots came out bad:

[ATTACH]74707[/ATTACH]

[ATTACH]74708[/ATTACH]

---

### Post by ninja senses on 2008-06-21
> **Dynaflow said:**
> Follow this guide and all should be well with Flash:  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

(There's also a comprehensive troubleshooting section at the bottom of the first post for both Flash and Java, each of which plays a role in getting Flash video to run.)

some of the commands arent working for me in the terminal.:confused:  Im on gutsy

---

### Post by Dynaflow on 2008-06-21
> **ninja senses said:**
> some of the commands arent working for me in the terminal.:confused:  Im on gutsy

There are a couple parallel sets of instructions for most of the steps in the tutorial, one for Hardy users and one for pre-Hardy Ubuntu users.  Are you using the pre-Hardy instructions?

---

### Post by ninja senses on 2008-06-21
> **Dynaflow said:**
> There are a couple parallel sets of instructions for most of the steps in the tutorial, one for Hardy users and one for pre-Hardy Ubuntu users.  Are you using the pre-Hardy instructions?

yes.

---

### Post by Fedz on 2008-06-21
Maybe consider [Adobe FlashPlayer 10](http://labs.adobe.com/downloads/flashplayer10.html).

Goto: Places > Home > View > Show Hidden Files.

Find **.**mozilla > plugins and delete libflashplayer.so (if available).

Or uninstall from SPM.

   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Hope this helps :-)

---

### Post by alienexplorers on 2008-06-21
Using Adobe Flash Plugin 10 and have been watching YouTube video's for the last half hour.  I have not had a burp or anything.  Seems to work very well.

---

### Post by ninja senses on 2008-06-21
> **Fedz said:**
> Maybe consider [Adobe FlashPlayer 10](http://labs.adobe.com/downloads/flashplayer10.html).

Goto: Places > Home > View > Show Hidden Files.

Find **.**mozilla > plugins and delete libflashplayer.so (if available).

Or uninstall from SPM.

   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Hope this helps :-)


that did it, thanks a bunch man!!

---

### Post by bluzepher on 2008-06-21
this is great info.

thanks

---

### Post by hazman on 2008-06-22
i watch youtube music videos thru totem movie player and it works fine once you install all the plugins you just choose your video it searches as youtube click and play

---

