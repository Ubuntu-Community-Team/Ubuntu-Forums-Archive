---
title: "Howto: Get Google Gadgets easily!"
date: 2008-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Vadi on 2008-06-07
Google Gadgets are now available [on Linux]("http://google-opensource.blogspot.com/2008/06/google-gadgets-for-linux.html"), but as of this moment, it's not in their Google Repository and they don't have an easy .deb. Thankfully, [getdeb.net]("getdeb.net") is making .debs of them, so they're quite easy to install on Ubuntu.
[CENTER]
[SIZE="6"]Installing[/SIZE][/CENTER]

[SIZE="4"]If you're on 32bit Ubuntu 8.10 "Intrepid Ibex"[/SIZE]

Download and install this .deb ([**click**]("http://www.getdeb.net/download/3637/0")).

[SIZE="4"]If you're on 64bit Ubuntu 8.10 "Intrepid Ibex"[/SIZE]

Download and install this .deb ([**click**]("http://www.getdeb.net/download/3638/0")).

[SIZE="4"]If you're on 32bit Ubuntu 8.04 "Hardy Heron"[/SIZE]

Download and install this .deb ([**click**]("http://www.getdeb.net/download/3645/0")).

[SIZE="4"]If you're on 64bit Ubuntu 8.04 "Hardy Heron"[/SIZE]

Download and install this .deb ([**click**]("http://www.getdeb.net/download/3646/0")).


**When** they finish installing, simply press Alt+F2, and type "ggl-gtk" to start them. You should see a small icon show up in your system tray, and a sidebar. Right click on any of them and select 'Add Gadgets' to show a menu.

**That's it**, you're done! Enjoy.

[SIZE="5"][CENTER]Optional[/CENTER][/SIZE]

[CENTER][SIZE="4"]Autostart[/SIZE][/CENTER]

If you'd like to have Google Gadgets start automatically, go to System - Preferences - Session, click 'Add', paste 'Google Gadgets' for the name and 'ggl-gtk' for the command. Click OK and Close, and you're good to go.

[CENTER][SIZE="4"]No Sidebar[/SIZE][/CENTER]

If you don't like the sidebar, then you can start Google Gadgets without it by doing "ggl-gtk -ns".

[SIZE="5"][CENTER]Uninstalling[/CENTER][/SIZE]

I couldn't find an entry for Google Gadgets in Add/Remove, so the only way to uninstall them is to go to Applications - Accessories - Terminal, and pasting this in:

> sudo apt-get remove google-gadgets

If you added them to be automatically started, go to System - Preferences - Sessions to remove them. That's it, you're good to go!


[SIZE="1"]Note: Google Gadgets also features a QT gui (ggl-qt), but I don't use KDE as the DE, so I don't know how to set them up there. If someone does, please let me know, and I'll include the instructions.[/SIZE]

[SIZE="1"]Changelog:
Dec 25th, '08: updated to version 0.10.4. Gadget Designer should work now, along with a lot of other optimizations being done.
Nov 13th, '08: updated to version 0.10.3
Aug 15th, '08: updated to version 0.10.1
Aug 11th, '08: fixed a typo, the command is "ggl-gtk" not "ggk-qtk". Thanks to starcannon for pointing it out.
Jul 18th, '08: updated to Google Gadgets 0.10.0
Jun 15th, '08: added the no sidebar option
Jun 15th, '08: google gadgets 0.9.3 are out. The changelog is missing, but the noticeable changes are that the sidebar is enabled by default in the gtk version, and it's way less buggier.
Jun 15th '08, switched from the PPA to getdeb as the PPA already missed 2 releases while getdeb.net had them.[/SIZE]

---

### Post by petedct on 2008-06-07
Hey Vadi. The link to click for installation seems to be dead. At least on my Windows box at work. I get "The page can not be displayed" in IE6.

---

### Post by Vadi on 2008-06-07
The installation link will only work on Ubuntu I'm afraid.

---

### Post by petedct on 2008-06-07
Would you post the code behind that link please?

---

### Post by Vadi on 2008-06-07
It simply does "apt:google-gadgets", utilizing a browser extension to install the "google-gadgets" package.

On Windows you'd have to use Google Gadget's installer.

---

### Post by petedct on 2008-06-07
Thanks. I'll give it a go when I get home to the serenity of my Ubuntu box.

---

### Post by DJ_Peng on 2008-06-07
Thanks, Vadi! I was wanting to add this. Now I just have to make sure I don't add too many games to it. I'll *never* get anything done if I do.:lolflag:

---

### Post by greyfox1 on 2008-06-07
After following the steps above I get the output below.  I have tried removing/reinstalling several times.  What's going wrong here??

rick@rick-desktop:~$ ggl-gtk
Failed to open zip file /usr/share/google-gadgets/resources.gg: No such file or directory
Not a regular file: /usr/share/google-gadgets/resources
Not a regular file: /
Initialize default_framework extension.
Initialize gtk_edit_element extension.
Initialize gtkmoz_browser_element extension.
Initialize gst_mediaplayer_element extension.
Initialize gtk_system_framework extension.
Initialize gst_audio_framework extension.
Demarshal failed. Type dismatch, message type: , expected: s
No slot registered to handle this reply.
No slot registered to handle this reply.
Demarshal failed. Type dismatch, message type: , expected: s
Demarshal failed. Type dismatch, message type: , expected: s
Initialize linux_system_framework extension.
Initialize smjs_script_runtime extension.
Register smjs_script_runtime extension.
ggl-gtk: symbol lookup error: ggl-gtk: undefined symbol: _ZN7ggadget3gtk17SupportsCompositeEv
rick@rick-desktop:~$

---

### Post by Prospero2006 on 2008-06-07
Worked perfectly. 
Nice job!

---

### Post by petedct on 2008-06-07
We have gadgets and the fun begins. I thank you.

---

### Post by Vadi on 2008-06-07
> **greyfox1 said:**
> After following the steps above I get the output below.  I have tried removing/reinstalling several times.  What's going wrong here??

I don't know, sorry. Please report the bug at their bugtracker ([click]("http://code.google.com/p/google-gadgets-for-linux/issues/entry")) and they'll look at it. Mention that you're using "0.9.1-0ubuntu0~ppa5" for the google gadgets version.

---

### Post by Anduu on 2008-06-07
I've been playing around with them for a bit.

Obviously they have a way to go with these.A lot of them don't work properly or they outright crash X.

We'll have to wait and see how developement goes.

---

### Post by FFighter on 2008-06-07
Thanks for this. 

I tried going the manual way and compile it, but too many dependency errors and no decent guide on the google code wiki. All the dependencies I was told to install I have, but the thing kept on breaking without useful error messages.

---

### Post by bgoody on 2008-06-07
Hi.  I had a lot of trouble until I noticed that there is a newer version around 0.9.2.  It compiles now for me.

Here are the instructions I follwed:

simple step by step instructions to install in ubuntu (hardy) so do you dont have to read through all the detail

   1. wget [http://google-gadgets-for-linux.googlecode.com/files/google-gadgets-for-linux-0.9.1.tar.gz](http://google-gadgets-for-linux.googlecode.com/files/google-gadgets-for-linux-0.9.1.tar.gz)
   2. tar zxvf google-gadgets-for-linux-0.9.2.tar.gz
   3. cd google-gadgets-for-linux-0.9.2/
   4. sudo apt-get install zlib1g-dev libmozjs-dev libcurl4-openssl-dev libxml2-dev libdbus-1-dev libmozjs-dev libgstreamer-plugins-base0.10-dev libcurl3-openssl-dev libdbus-1-dev libxul-dev libcurl3 libcurl3-dbg libcurl3-gnutls libcurl4-openssl-dev libcurl-ocaml libmozjs0d libmozjs0d-dbg libmozjs-dev g++-4.2-multilib g++ libqt4-dev
   5. sudo ldconfig
   6. ../../configure --enable-debug
   7. sudo make install 

(alternatively dont use sudo and set an alternate install directory, default /usr/local)

   1. export LD_LIBRARY_PATH=/usr/local/lib
   2. ggl-gtk 

An icon should show in the top right status bar, right click and add gadget!

That's from this post (near the bottom):
[http://code.google.com/p/google-gadgets-for-linux/wiki/HowToBuild](http://code.google.com/p/google-gadgets-for-linux/wiki/HowToBuild)

> **FFighter said:**
> Thanks for this. 

I tried going the manual way and compile it, but too many dependency errors and no decent guide on the google code wiki. All the dependencies I was told to install I have, but the thing kept on breaking without useful error messages.

---

### Post by BerT0 on 2008-06-07
Does not work for me. when i click the link it gets me this error.
--------------------------------
Can not install 'google-gadgets' (E:Unable to correct problems, you have held broken packages.) 
--------------------------------

I'm running a ubuntu 7.1 ver.

---

### Post by Vadi on 2008-06-07
Sorry, the instructions are for 8.04. For 7.10, you need to change "hardy" to "gutsy" in the Software - Sources line.

---

### Post by cartisdm on 2008-06-07
> **Vadi said:**
> Sorry, the instructions are for 8.04. For 7.10, you need to change "hardy" to "fiesty" in the Software - Sources line.


Don't you mean Gutsy?

---

### Post by cartisdm on 2008-06-07
I get the following when I click the link.  When I try to reload it fails and I get the following error.  And I changed "Hardy" to "Gutsy" so I'm assuming the problem is there...

[http://ppa.launchpad.net/googlegadgets/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://ppa.launchpad.net/googlegadgets/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found

---

### Post by DJ_Peng on 2008-06-08
> **Anduu said:**
> I've been playing around with them for a bit.

Obviously they have a way to go with these.A lot of them don't work properly or they outright crash X.

We'll have to wait and see how developement goes.
Yeah, unfortunately the Google Calendar gadgets won't remember which calendars I want to show, and the better looking aquarium gadgets never load. But I have my clock and my WeatherBug so I'm good for now.

Is there a way to force the order of the gadgets in the sidebar? I always have to move my clock to the top. It's not a major thing, just a really annoying one.

---

### Post by Vadi on 2008-06-08
> **cartisdm said:**
> I get the following when I click the link.  When I try to reload it fails and I get the following error.  And I changed "Hardy" to "Gutsy" so I'm assuming the problem is there...

[http://ppa.launchpad.net/googlegadgets/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://ppa.launchpad.net/googlegadgets/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 404 Not Found

Sorry, the PPA is for 8.04 only then. Either upgrade, or follow Google's instructions for compiling, or wait until they make a 7.10 .deb.

---

### Post by cor2y on 2008-06-08
Thanks for the links to the repos , quick question how do i associate google gadgets with compiz-fusion meaning i have more than one workspace and google gadgets can only appear on one work space unless i launch for example two sets of the same gadgets for each workspace.

---

### Post by Vadi on 2008-06-08
I don't know that yet myself. Normally you'd right-click on the title bar and select 'Always on Visible Workspace', but the gadgets don't offer a titlebar. I'll ask myself.

---

### Post by cartisdm on 2008-06-08
> **Vadi said:**
> Sorry, the PPA is for 8.04 only then. Either upgrade, or follow Google's instructions for compiling, or wait until they make a 7.10 .deb.

No fun.  I'd love to upgrade to Hardy but my 3945 wireless card doesn't seem to like the switch.  I tried day-of though and haven't tried since so maybe they fixed that problem.

---

### Post by Vadi on 2008-06-08
Yes, and people wanted an even newer kernel (and kernel drivers, which is what broke for your card) on 8.04. 

But hey, I found this report and some guy said he solved it ([click]("https://bugs.launchpad.net/ubuntu/+bug/226411")). Give that a try?

---

### Post by cartisdm on 2008-06-08
> **Vadi said:**
> Yes, and people wanted an even newer kernel (and kernel drivers, which is what broke for your card) on 8.04. 

But hey, I found this report and some guy said he solved it ([click]("https://bugs.launchpad.net/ubuntu/+bug/226411")). Give that a try?

Thanks for the quick reply.  I'll definitely look into that some more, with any luck I'll be up and running on Hardy in no time:)
[B]

Edit:  I made the upgrade to Hardy.  No wireless but I'll suck it up for now.  Google Gadgets is awesome by the way.  I do find it odd that they don't have a decent gmail gadget though...[/B]

---

### Post by aerobie on 2008-06-09
What window does Alt+F2 open up?

I'm running Hardy virtualized on a Mac and Alt+F2 opens up System Preferences in Leopard.

Thanks!

---

### Post by Vadi on 2008-06-09
It opens up a "run application" window. You can achieve the same effect by doing to applications - accessories - terminal, and typig the command there - although if you close the terminal, the gadgets will close too.

check your virtualization program to allow you to use keybindings when the focus is on the vm

---

### Post by guano on 2008-06-09
Many thanks for this Vadi (and to John Carr for creating the launchpad entry). Works fine in my laptop.

---

### Post by fjf on 2008-06-09
From:  [http://ubuntuforums.org/showthread.php?t=818267&highlight=google+gadgets&page=6](http://ubuntuforums.org/showthread.php?t=818267&highlight=google+gadgets&page=6)

> Also: to make windows stick to the desktop (IE, be on all desktops) in Compiz turn on the "window rules" plugin and put
Code:

class=Ggl-gtk

in the sticky section. Put it in Below to make them stay below.

As a general note to get window information (like class, title, etc.) type xprop in a terminal and then click on the the window in question. All you need -- and far more than you ever wanted -- to know will be right there.


> **cor2y said:**
> Thanks for the links to the repos , quick question how do i associate google gadgets with compiz-fusion meaning i have more than one workspace and google gadgets can only appear on one work space unless i launch for example two sets of the same gadgets for each workspace.

---

### Post by Vadi on 2008-06-09
I'd add that to the guide, except it's not working for me. I set both the "Below" and "Sticky" lines to be "class=Ggl-gtk", enabled the plugin, but the sidebar still appears only on one side.

---

### Post by fjf on 2008-06-09
Works for me!.

---

### Post by Vadi on 2008-06-09
Um, thanks, that really helped.

---

### Post by cartisdm on 2008-06-09
> **Vadi said:**
> Um, thanks, that really helped.

haha that's amusing.  sorry bro I'd try to help you out myself but I can't even get my gadgets to load anymore.  It just....stopped.  I can't open it anymore

---

### Post by Vadi on 2008-06-09
Try doing "ggl-gtk" in the terminal, what does it say?

---

### Post by cartisdm on 2008-06-09
> **Vadi said:**
> Try doing "ggl-gtk" in the terminal, what does it say?

I get the following output (which doesn't end, it just keeps erroring) and I weird square glitch thing in the center of my screen...

```
Failed to open zip file /usr/share/google-gadgets/resources.gg: No such file or directory
Not a regular file: /usr/share/google-gadgets/resources
Not a regular file: /
Initialize default_framework extension.
Initialize gtk_edit_element extension.
Initialize gtkmoz_browser_element extension.
Initialize gst_mediaplayer_element extension.
Initialize gtk_system_framework extension.
Initialize gst_audio_framework extension.
Demarshal failed. Type dismatch, message type: , expected: s
No slot registered to handle this reply.
No slot registered to handle this reply.
No slot registered to handle this reply.
org.freedesktop.DBus.Error.UnknownMethod: Method "GetProperty" with signature "s" on interface "org.freedesktop.Hal.Manager" doesn't exist

Initialize linux_system_framework extension.
Initialize smjs_script_runtime extension.
Register smjs_script_runtime extension.
Not a regular file: /
Register default_framework extension.
Register gtk_edit_element extension.
Register gtkmoz_browser_element extension, using name "_browser".
Register gst_mediaplayer_element extension.
Register gtk_system_framework extension.
Register gst_audio_framework extension.
Register linux_system_framework extension.
SimpleGtkHost: Load gadget /home/dan/.google/gadgets/downloaded_gadgets/DF83CBC5-6FAD-4074-BF03-8254392DEFA0.gg, with option gadget-0, succeeded
Not a regular file: /
Register default_framework extension.
Register gtk_edit_element extension.
Register gtkmoz_browser_element extension, using name "_browser".
Register gst_mediaplayer_element extension.

```


PS. A mod is more than welcome to condense that CODE text with a scroll bar.  I didn't know how to so I pasted it all in

---

### Post by Vadi on 2008-06-09
Wow. That looks really odd. Can you reinstall google gadgets? Go to System - Administration - Synaptic, search for 'google-gadgets', and reinstall. If it still happens after, report the issue at their bugtracker ([click]("http://code.google.com/p/google-gadgets-for-linux/issues/entry")).

---

### Post by cartisdm on 2008-06-09
I reinstalled via synaptic.  Now when I run the application I get a gray glitch window where the google gadgets should be.  I submitted the bug report to Google.  Next I think I'll try completely removing the package and running this How-to again...


**EDIT:  I completely removed the package. Rebooted. Updated. Rebooted. Followed How-To again. Failer. Oh well, it was fun while it lasted:(**

---

### Post by cdtech on 2008-06-09
worked for me, thanks.

HP dv9608nr laptop
kernel 2.6.24-18 64bit

---

### Post by zyxyellowxyz on 2008-06-10
This may sound like a stupid question, but I want to ask it anyways:

How would one go about installing them in Kubuntu?

[SIZE="1"]I have them on my Windows Desktop and I would love to have them on my Kubuntu desktop as well.[/SIZE]

---

### Post by Vadi on 2008-06-10
I don't know how to add a repository in Kubuntu. But you can download the .deb from here ([click]("http://launchpadlibrarian.net/15085183/google-gadgets_0.9.1-0ubuntu0%7Eppa5_i386.deb")), and launch "ggl-qt" instead of "ggl-gtk". Note that the sidebar is only supported in the GTK (Ubuntu) version.

---

### Post by TwiceOver on 2008-06-10
Just wanted to report in that it works fine on my Dell 1501 (except for not showing up on multiple workstations with compiz).  Looked cool but I couldn't find anything useful in the gadgets list.

One more bug, for me at least, running compiz I cannot change the gadget size.

---

### Post by hotpinkflamingo on 2008-06-10
How did you get yours to be transparent?
When following your installation instructions, when I try to run "ggl-gtk" I get an error that the file can't be found.  Then I tried "ggl-gtk -s -bg" and that opened the sidebar.
I didn't realize that you could use the gadgets without the sidebar.  When I close the sidebar, and try to "add gadgets", they don't display unless I have the sidebar open.  I don't really mind whether I have the sidebar or not, I just want it to be transparent.
My sidebar is solid black, though.

---

### Post by Vadi on 2008-06-10
I think you need to be running Compiz (desktop effects) for the transparency.

---

### Post by hotpinkflamingo on 2008-06-10
Oh, I see, thanks.  I can't use the desktop effects, as when I turn them on my screen goes blank white.  But that's another issue altogether lol.

---

### Post by zyxyellowxyz on 2008-06-10
> **Vadi said:**
> I don't know how to add a repository in Kubuntu. But you can download the .deb from here ([click]("http://launchpadlibrarian.net/15085183/google-gadgets_0.9.1-0ubuntu0%7Eppa5_i386.deb")), and launch "ggl-qt" instead of "ggl-gtk". Note that the sidebar is only supported in the GTK (Ubuntu) version.

I ran both, and it seems to run smoother in the ggl-gtk than ggl-qt

I still don't see the side bar, BUT the apps themselves aren't glitching out on me like they were with ggl-qt

(I forgot to mention that I also have gnome installed as well as kde. I honestly have no idea what ggl-gtk and ggl-qt are >_>)

---

### Post by SonicSteve on 2008-06-11
Has anyone tried this on 7.10 Gutsy? Google Desktop works nicely but there doesn't seem to be much info from running Google Gadgets on anything but Heron 8.04.

---

### Post by cor2y on 2008-06-11
> **fjf said:**
> From:  [http://ubuntuforums.org/showthread.php?t=818267&highlight=google+gadgets&page=6](http://ubuntuforums.org/showthread.php?t=818267&highlight=google+gadgets&page=6)


Like Vadi i tried this and it didn't work for me, at first i thought maybe it was because it was labeled as Ggl-gtk and not ggl-gtk but trying both didn't work.

Edit.
It took a total purge of compiz-fusion and then a reinstall for this to work for me.
added class=Ggl-gtk (the right syntax btw) to the windows rules plugin, both in sticky and below after the reinstall of compiz-fusion.
It didn't work off the bat for me even with a restarting of X or even a reboot before.

---

### Post by Vadi on 2008-06-15
New version out, 0.9.3. Check the guide for updated instructions - I switched it to getdeb.net because the PPA already missed 2 releases.

Google says a lot of bugs were fixed in this release, so if you were having trouble with them before, give them a try now.

---

### Post by cor2y on 2008-06-15
Anyway to disable the sidebar and just keep the gadgets in gnome for this new version?

---

### Post by Vadi on 2008-06-15
After some experimentation, "ggl-gtk -ns" did it.

---

### Post by cartisdm on 2008-06-15
> **Vadi said:**
> New version out, 0.9.3. Check the guide for updated instructions - I switched it to getdeb.net because the PPA already missed 2 releases.

Google says a lot of bugs were fixed in this release, so if you were having trouble with them before, give them a try now.

Which guide has been updated?  The one on this page?


**EDIT:  Nevermind, I just clicked on the .deb and saw that it is the 0.9.3 version so that answered my question:)**

---

### Post by snafilter on 2008-06-18
I get a "Failed to update gadget data..."

Running 64 bit Heron 
uname -a
Linux tron 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux


Failed to open zip file /usr/share/google-gadgets/resources.gg: No such file or directory
Not a regular file: /usr/share/google-gadgets/resources
Not a regular file: /
Initialize default_framework extension.
Initialize gtk_edit_element extension.
Initialize gtkmoz_browser_element extension.
Initialize gst_mediaplayer_element extension.
Initialize gtk_system_framework extension.
Initialize gst_audio_framework extension.
Demarshal failed. Type dismatch, message type: , expected: s
Demarshal failed. Type dismatch, message type: , expected: s
No slot registered to handle this reply.
No slot registered to handle this reply.
Demarshal failed. Type dismatch, message type: , expected: s
Demarshal failed. Type dismatch, message type: , expected: s
Initialize linux_system_framework extension.
Initialize smjs_script_runtime extension.
Register smjs_script_runtime extension.
Call DBusWatchCallBack, watch id: 3
Call DBusWatchCallBack, watch id: 5
Failed to update gadget metadata. Will retry after 7200000ms
Not a regular file: /usr/share/google-gadgets/google-gadget-browser
Not a regular file: /
Initialize gadget_browser_script_utils extension.
Register default_framework extension.
Register gtk_edit_element extension.
Register gtkmoz_browser_element extension, using name "_browser".
Register gst_mediaplayer_element extension.
Register gtk_system_framework extension.
Register gst_audio_framework extension.
Register linux_system_framework extension.
Register ggadget_browser_script_utils extension.
TRACE: begin loading metadata
Failed to update gadget metadata. Will retry after 16342305ms
Finalize gadget_browser_script_utils extension.

---

### Post by esc1 on 2008-06-18
The 64 deb works for me. Thanks.

---

### Post by TVMA on 2008-06-20
Rocking, thanks for posting this!

---

### Post by crjackson on 2008-06-23
You know, I really kind of like these gadgets except for one thing.  I can't figure out how to make the slate box (not the side panel, but the same color) either go away or go transparent like it is in vista.  I really would prefer gadgets that float on the desktop with out the square box around them showing.

Does anyone know if that's possible and how to do that?

---

### Post by fooman on 2008-06-23
> **crjackson said:**
> You know, I really kind of like these gadgets except for one thing.  I can't figure out how to make the slate box (not the side panel, but the same color) either go away or go transparent like it is in vista.  I really would prefer gadgets that float on the desktop with out the square box around them showing.

Does anyone know if that's possible and how to do that?

do you have compiz turned on?

---

### Post by Vadi on 2008-06-23
Hm I don't get the box. Try launching the gadgets without the sidebar?

(the box did appear randomly on my sis's computer, but I think she docked/undocked a bunch and it was without it)

---

### Post by crjackson on 2008-06-23
> **fooman said:**
> do you have compiz turned on?

No

---

### Post by crjackson on 2008-06-23
> **Vadi said:**
> Hm I don't get the box. Try launching the gadgets without the sidebar?

(the box did appear randomly on my sis's computer, but I think she docked/undocked a bunch and it was without it)

Box is there even without sidebar.

---

### Post by crjackson on 2008-06-24
Here's a screen shot without the side bar.

---

### Post by loneowais on 2008-06-24
i also get the same error while updating...


it say,

   "Failed to Update gadgets data, please try again"

My internet connection is fine

---

### Post by fooman on 2008-06-24
> **crjackson said:**
> Here's a screen shot without the side bar.

you need to turn on the "visual effects" (compiz).

go to > system > preferences > appearance

try the "normal" or "extra" setting.

---

### Post by Vadi on 2008-06-24
Yeah, I believe they require some kind of a compositor. After that restart them.

---

### Post by Mtuxland on 2008-06-24
Hi folks,
I have noticed that the Getdeb version of GoogleGadgets is GTK+ only.

If you need the Qt version, I've compiled it for i386 architecture; you can find it [here]("http://mtuxland.blogspot.com/2008/06/google-gadgets-qt-deb.html"). The blog is in italian, but it's sufficient to follow the first link for the qt compiled debian package.

Btw if you know a way to upload posts to blogger in different languages (for Wordpress, there is a plugin that enables language switching just by clicking on different flags, provided that the author has translated the contents) so people can read the post in their own language (I would be happy to translate in English/German my posts), please let me know!

Marco

---

### Post by crjackson on 2008-06-24
> **fooman said:**
> you need to turn on the "visual effects" (compiz).

go to > system > preferences > appearance

try the "normal" or "extra" setting.

Here's a screen shot with compiz turned on.  The box now has less opacity but it's still there.

---

### Post by crjackson on 2008-07-05
Well, I installed Ubuntu-Tweak and enabled an option to keep Compiz-Fusion and GoogleGadgets updated to the latest and greatest.  It brought in a bunch of updates and now it works perfectly.

No more black boxes where they should be.  I'm a happy camper...  Thanks for the suggestions.

---

### Post by DJ_Peng on 2008-07-06
Thanks for the tip about Ubuntu Tweak! I didn't realize they had an update out but I've got it updated now. I'm going to have to blog this tomorrow so more people know not just about the update but about the ability to keep the other apps updated.

---

### Post by Vadi on 2008-07-06
Just note that is uses a 3rd party repository that *someone* made - I couldn't find who or what. It's not any of Ubuntu's repositories.

---

### Post by M4rotku on 2008-07-06
I recieved this error when I tried to install:

> Could not install all dependencies.
Usually this is related to an error of the software distributor.

and the details offered were:

> E:Archive directory /var/cache/apt/archives/partial is missing.

---

### Post by Vadi on 2008-07-06
Can you install other things on your computer via .debs fine?

---

### Post by M4rotku on 2008-07-06
I have in the past, I haven't tried recently though.

---

### Post by M4rotku on 2008-07-06
Ok, i just installed Ubuntu Tweak via .deb,  So I am able to.

But i just got the same error after I tried to download Compiz from the Ubuntu Tweak menu.

---

### Post by Vadi on 2008-07-06
Yes, it looks like something is broken on your Ubuntu.

Try this guide: [http://liltux.wordpress.com/2007/06/15/howto-fix-e-archive-directory-varcacheaptarchivespartial-is-missing-error/](http://liltux.wordpress.com/2007/06/15/howto-fix-e-archive-directory-varcacheaptarchivespartial-is-missing-error/)

---

### Post by M4rotku on 2008-07-06
thanks Vadi, that was easier than I thought it would be.  Thank you for the link.

---

### Post by masterkoppa on 2008-07-07
I'm having a problem when I try to get gadgets. It hangs forever in Updating gadget data. Please Wait... I have Compiz enabled in extra. I installed from getdeb.com.

Any help is greatly appreciated

---

### Post by Vadi on 2008-07-18
Google Gadgets 0.10.0 are out, and I've updated my guide (to the latest getdeb.net packages). Unfortunately the changelog is missing, the news file is empty, and the only thing they said was "Major bugfixes and feature enhancements.". So, enjoy that anyway! 

Give it a try now if it wasn't working before.

---

### Post by MemoryDump on 2008-07-18
> **Vadi said:**
> Google Gadgets 0.10.0 are out, and I've updated my guide (to the latest getdeb.net packages). Unfortunately the changelog is missing, the news file is empty, and the only thing they said was "Major bugfixes and feature enhancements.". So, enjoy that anyway! 

Give it a try now if it wasn't working before.

the new 32bit download link isn't working :(

edit: just found a link that works:
[http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/go/google-gadgets_0.10.0-0~getdeb1_i386.deb](http://ftp1.srv.endpoint.nu/pub/software/getdeb/ubuntu/hardy/go/google-gadgets_0.10.0-0~getdeb1_i386.deb)

---

### Post by Vadi on 2008-07-18
getdeb.net chooses mirrors randomly from it's list - so you probably got a non-working mirror. Next time it happens, please record the url.

(and the mirror that I got now works ok)

---

### Post by northwestuntu on 2008-07-18
i just installed the latest version from google.  the 64 version and i go to start it and nothing?

i have awn.  does it not work with awn.

---

### Post by Mtuxland on 2008-07-23
I've compiled version 0.10 for both GTK and QT, you can find it here:
[http://mtuxland.blogspot.com/2008/07/google-gadgets-010-deb-qt-and-gtk.html]("http://mtuxland.blogspot.com/2008/07/google-gadgets-010-deb-qt-and-gtk.html")

I hope it will be useful!

Marco

---

### Post by Vadi on 2008-07-23
The current .debs are of the 0.10 version, it should be noted.

---

### Post by Orlsend on 2008-07-23
Thanks For this, Now Ubuntu has more Value!

---

### Post by Mtuxland on 2008-07-23
> **Vadi said:**
> The current .debs are of the 0.10 version, it should be noted.

Yes, but if I remember well, getdeb supports just GTK version.

---

### Post by Vadi on 2008-07-23
Ah yes, they support both 32 and 64bit gtk version.

---

### Post by northwestuntu on 2008-07-26
how come they don't call it google desktop like the windows version?

---

### Post by Vadi on 2008-07-26
Because there already was google desktop for linux, but no gadgets.

---

### Post by spotdog14 on 2008-08-08
Does this have an update yet?

---

### Post by Vadi on 2008-08-08
the current .debs are on version 0.10

---

### Post by DJ_Peng on 2008-08-10
Hopefully they'll add an About dialog. It can be a pain to have to go into Synaptic just to find out what version you're running.

---

### Post by Mtuxland on 2008-08-11
New version 0.10.1... you can find it here for GTK as well as for QT!

[URL="http://mtuxland.blogspot.com/2008/08/google-gadgets-0101-deb-qt-and-gtk.html"]http://mtuxland.blogspot.com/2008/08/google-gadgets-0101-deb-qt-and-gtk.html
[/URL]

The mime-type problem has been hand-corrected by me.

See you soon,
Marco

---

### Post by supertux on 2008-08-11
cool, thx i will try it out!

when i install it, it complains about libqt4-network...

---

### Post by Mtuxland on 2008-08-14
Can you post the exact error please?
What repos have you enabled?

---

### Post by Vadi on 2008-08-15
The links in the first post were updated to 0.10.1, cheers.

(I can't tell you what's new because they didn't make a changelog :()

---

### Post by eheyl on 2008-09-07
When I click either the icon or the sidbar itself to add gadgets, it looks like it crashes. I'm on 8.04 as well. Anyone have this prob?

---

### Post by Mtuxland on 2008-09-08
Start it from a shell and post the output after the crash.

---

### Post by srt4play on 2008-09-08
I installed from the getdeb.net link on the first page and it works good, but there are only five available gadgets.  How do I get more?

---

### Post by lukjad on 2008-09-08
Thanks! Just so that I know, I have a rather old PC at the moment. Is this hardware intensive? In other words, should I wait to get a new PC to install this?

---

### Post by dreameruk on 2008-09-09
I've just installed google gadgets and can also only see five gadgets. I've checked and I'm using the lasted version 0.10.1-0

---

### Post by killtacular on 2008-09-09
Hi, 

I installed the latest google gadgets package, but the .deb won't install.  
It says ```
Error:  Dependency not satisfiable libpango1.0-0
```

I'm not exactly sure what this means when I try to install the .deb.

Can anyone help out here?

Thanks

---

### Post by Vadi on 2008-09-09
Do you know what Ubuntu version are you on? It might be outdated.

---

### Post by Ripfox on 2008-09-09
> **srt4play said:**
> I installed from the getdeb.net link on the first page and it works good, but there are only five available gadgets.  How do I get more?

Same problem here.

---

### Post by woyzeckswoe on 2008-09-10
> **srt4play said:**
> I installed from the getdeb.net link on the first page and it works good, but there are only five available gadgets.  How do I get more?

same for me;)

thanks

---

### Post by Vadi on 2008-09-10
I'm not sure, I see more than 5. I actually have 50 pages when it's on "all"...

Try reporting your problems here: [http://code.google.com/p/google-gadgets-for-linux/issues/list](http://code.google.com/p/google-gadgets-for-linux/issues/list)

---

### Post by dreameruk on 2008-09-11
I'm using the last version of Ubuntu (just downloaded it last weekend) and when I'm on 'all' I can just see five gadgets :confused:

---

### Post by Ripfox on 2008-09-12
bump...how do you get all the gadgets?

---

### Post by Vadi on 2008-09-12
Tried posting an issue in the ggl forum?

---

### Post by srt4play on 2008-09-12
I uninstalled 0.10.1 and installed 0.10.0 from getdeb.net and now I see over 50 pages of gadgets.  I wonder if it's a packaging problem.

---

### Post by saravanan.2407 on 2008-09-13
i will give this a try..

---

### Post by dreameruk on 2008-09-13
I've just downloaded 0.10.0 from 
[http://www.linuxprograms.org/DOWNLOAD/Google_Gadgets_0100.html](http://www.linuxprograms.org/DOWNLOAD/Google_Gadgets_0100.html)

But now I only have 3 gadgets! :(

---

### Post by ericesque on 2008-10-06
A seemingly easier alternative would be to install screenlets-- which now supports google gadgets. :KS

---

### Post by Vadi on 2008-10-06
It actually supported them for months now...

---

### Post by DJ_Peng on 2008-10-07
Unfortunately that's not quite the solution we thought it was. I tried getting Screenlets to use the WeatherBug Gadget for the Google Sidebar and it didn't show a thing. I'll admit I may have misunderstood how to set it up, but from my experience it's a no-go. Which is a shame, since I'd much rather use Screenlets than the Google Gadgets Sidebar.

---

### Post by Vadi on 2008-10-07
You can undock the gadgets from the sidebar you know.

---

### Post by DJ_Peng on 2008-10-08
Damn. I had forgotten all about that. Thanks!

ETA: Actually if I undock the WeatherBug from the sidebar it hides when I minimize the rest of the dock so it's not as helpful as I'd like it to be. But no biggie. I'll poke around some more and see if I can see a way I've missed so far.

ETA2: I set the dock to autohide and that seems to help. Now I just have to make sure I don't run too many Screenlets and GGadgets at the same time on my rather underpowered old box.

---

### Post by alexeix on 2008-11-13
This doesn't seem to work on Ubuntu 8.10.

Anybody have any suggestions about how to install on Intrepid?
Thanks.

---

### Post by Vadi on 2008-11-13
I've updated the links for the new 0.10.3 version, for both 8.04 and 8.10. Let me know if it works now.

---

### Post by Mtuxland on 2008-11-17
I've also compiled Google gadgets 0.10.3... There are two packages, one for GTK and one for QT... They are 32bit Ubuntu 8.10 compatible.

You can find the packages here:
[URL="I've also compiled Google gadgets 0.10.3... There are two packages, one for GTK and one for QT... They are 32bit Ubuntu 8.10 compatible.  You can find the packages here:  http://mtuxland.blogspot.com/2008/11/google-gadgets-0103-deb-qt-and-gtk.html"]
http://mtuxland.blogspot.com/2008/11/google-gadgets-0103-deb-qt-and-gtk.html[/URL]

---

### Post by alexeix on 2008-11-18
Thanks guys.  It now works fine in 8.10!

:)

---

### Post by jlc on 2008-11-19
Works for me, 8.10/amd64, thanks!

---

### Post by crjackson on 2008-12-09
Ignore - I needed to research a little better before posting a question

---

### Post by Vadi on 2008-12-09
Would help better if you posted the question + answer though.

---

### Post by crjackson on 2008-12-09
> **Vadi said:**
> Would help better if you posted the question + answer though.

Not really. I wanted to know how to add it to a session so it would autostart. The answer was on the very first page.

I subscribed to this thread a long time ago before the information was posted there, so I didn't even check the 1st post prior to asking the question.

---

### Post by xRockTripodx on 2008-12-10
Thank you!  I love Ubuntu's community!  I'm relatively new to linux and didn't really want to build or compile (or whatever it is called) the package direct from the google gadgets site, so thank you so much!!  You made this very easy for me.  Now if only I had the patience to learn how to build my own packages.

---

### Post by Vadi on 2008-12-10
Thanks the team @ [http://www.getdeb.net/](http://www.getdeb.net/), they made it :)

---

### Post by DocHom on 2008-12-10
excellent How-to. It works nice on my machine. Ubuntu 8.04 32 bit. no problems to install, a lot of gadgets, my desktop looks better now.
Thank's VADI.

---

### Post by nabuko on 2008-12-24
Is there a way to get google gadgets 0.10.4? Need it to install the new google docs gadget.

---

### Post by Vadi on 2008-12-24
> **nabuko said:**
> Is there a way to get google gadgets 0.10.4? Need it to install the new google docs gadget.

I've asked getdeb.net for updated packages.

---

### Post by Vadi on 2008-12-24
It's published on [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by DJ_Peng on 2008-12-24
Thanks, Vadi. I had forgotten I'd gotten the gadgets from getdeb and was wondering when I might see an update.

---

### Post by Vadi on 2008-12-25
Updated all links on OP to 0.10.4. Here is the changelog:

>    * 0.10.4 - Dec 16th 2008
   o Following reported issues have been fixed:
     242, 246, 245, 253, 239, 249, 250, 243,
     234, 254, 255
   o Many optimizations in performance and
     memory consumption.
   o Support for NPAPI plugins (like Flash)
     has been improved a lot.
   o gtkmoz_browser_element has been improved a lot.
   o gtk host now supports running a gadget in
     standalone mode.
   o Gadget Designer has been improved a lot.
     And it now runs in standalone mode, just
     like an ordinary application.
   o gtk sidebar host has been improved a lot.
   o Many bugs related to qt host have been fixed.
   o Many other bugfixes.


---

### Post by DJ_Peng on 2008-12-26
I purged Epiphany this am to try to fix a problem with some extensions and in the process I had to dump gGadgets. I ended up in dependency hell for libqtwebkit1d but I got it fixed by snagging and installing [this package from Launchpad]("https://launchpad.net/ubuntu/intrepid/i386/libqtwebkit1d-dbg/0%7Esvn29752-1") (not sure if it was needed but I installed it anyway), which had a dependency of libqtwebkit1d, which I got from [this Launchpad page]("https://launchpad.net/ubuntu/hardy/i386/libqtwebkit1d/0%7Esvn29752-1"). It says it's for Hardy but once I installed it my gagdets worked without a hitch.

---

### Post by halovivek on 2008-12-29
Thanks i have installed and i am using it. really works fine for me in ubuntu 64 bit.

---

### Post by Slartibartfast_zzr on 2009-01-04
I have tried installing the version available in the standard repository (0.10.0 i think). several times under Hardy, but when I run the ggl-gtk command I get the following:

keith@keith-laptop:~$ ggl-gtk
Failed to open zip file /usr/share/google-gadgets/resources.gg: No such file or directory
Not a regular file: /usr/share/google-gadgets/resources
Not a regular file: /

The CPU is left running virtually flat out and the command hangs until you kill it with CNTL-C. I have waited for 10 mins for it to complete!

I have tried the screenlets app and this runs. (It is now uninstalled again).

I have Compiz installed running with 4 desktops and the rotating cube activated. Is this something to do with the problem? Any suggestions would be greatly appreciated, from a Ubuntu newby!

Thanks,

Keith

---

### Post by Vadi on 2009-01-04
Hmm, it seems there is some problem with them. Try installing the gadgets from the first post in the thread.

---

### Post by ms2756 on 2009-01-05
Thanks, that's pretty useful.

---

### Post by northwestuntu on 2009-01-06
what's up with this new gadgets.  whenever the box slides out when you select something it just flashes like crazy and then crashes.  the sidebar everything is fine, but you have anything outside that and it flips.

---

### Post by Vadi on 2009-01-06
Bug with gadgets and the version of xulrunner that comes with Ubuntu. The developers fixed it, next version will work fine.

---

### Post by Slartibartfast_zzr on 2009-01-16
Thanks Vadi, using the link on the first page cured the problem I had. I mistakenly thought that the repository version would be more stable! Does anybody know how to install alternative apps from the .gg file? I want to use the photo app, but it does not seem to recognise my pictures directory on my .ext3 drive. I was thinking of trying photooogle instead.

---

### Post by alexeix on 2009-01-20
I have Google Gadgets installed, but the number of gadgets available from within the application seems to be pretty limited.

Can anyone advise where I can download more and if there's a list of recommended ones - a 'best of', if you will...?

:)

---

### Post by harindrawisnu on 2009-02-05
great... i almost reinstall my intrepid ibex with [gadgetOS]("http://repo.undip.ac.id/ISO/gOS/")
thanks, so i don't have to back up all my stuff...

---

### Post by MedellinManDem on 2009-02-18
> **alexeix said:**
> I have Google Gadgets installed, but the number of gadgets available from within the application seems to be pretty limited.

Can anyone advise where I can download more and if there's a list of recommended ones - a 'best of', if you will...?

:)

I changed the setting to "English US" as opposed to "English UK" and there were far more.

All the best

---

### Post by kedarm on 2009-02-20
I installed Google Desktop and then, Google Gadgets as well.. But, the problem is the following -


1) I cannot add any new gadgets. When I try to add, it gives me just four options - analog clock, RSS feed, daylight and photos. How do I add more gadgets?

2) My RSS feeds cannot connect to the net. I cannot understand why, as it should be using the same network settings that firefox uses, right?

Thanks..

---

### Post by suzhe on 2009-02-21
> **kedarm said:**
> I installed Google Desktop and then, Google Gadgets as well.. But, the problem is the following -


1) I cannot add any new gadgets. When I try to add, it gives me just four options - analog clock, RSS feed, daylight and photos. How do I add more gadgets?

2) My RSS feeds cannot connect to the net. I cannot understand why, as it should be using the same network settings that firefox uses, right?

Thanks..

You may wait for a while and try again. It takes some time to download gadgets list.

---

