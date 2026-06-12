---
title: "Alpha 2 releasaed"
date: 2011-07-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-07-07
A little after the fact:

> Welcome to Oneiric Ocelot Alpha 2, which will in time become 
Ubuntu 11.10.

Pre-releases of Oneiric Ocelot are *not* encouraged for anyone 
needing a stable system or anyone who is not comfortable running 
into occasional, even frequent breakage.  They are, however, 
recommended for Ubuntu developers and those who want to help 
in testing, reporting, and fixing bugs.

Alpha 2 is the second in a series of milestone images that 
will be released throughout the Oneiric development cycle.  

New packages showing up for the first time include:
      * Linux Kernel 3.0-rc5 
      * gcc 4.6.1 compiler 
      * Firefox 5.0 
      * Thunderbird 5.0 
      * A Mesa 7.11 snapshot. 
  
You can download Alpha 2 images here:

   [http://cdimage.ubuntu.com/releases/oneiric/alpha-2/](http://cdimage.ubuntu.com/releases/oneiric/alpha-2/) 
   (Ubuntu, Ubuntu Server)

Additional images are also available at:

   [http://uec-images.ubuntu.com/releases/oneiric/alpha-2/](http://uec-images.ubuntu.com/releases/oneiric/alpha-2/) 
   (Ubuntu Server Cloud )
   [http://cdimage.ubuntu.com/xubuntu/releases/oneiric/alpha-2/](http://cdimage.ubuntu.com/xubuntu/releases/oneiric/alpha-2/)
   (Xubuntu)
   [http://cdimage.ubuntu.com/edubuntu/releases/oneiric/alpha-2/](http://cdimage.ubuntu.com/edubuntu/releases/oneiric/alpha-2/)
   (Edubuntu)


Alpha 2 includes a number of software updates that are 
ready for wider testing.  This is quite an early set of images, 
so you should expect some bugs.  For a more detailed description 
of the changes in the Alpha 2 release and the known bugs (which 
can save you the effort of reporting a duplicate bug, or help 
you find proven workarounds), please see:

  [http://www.ubuntu.com/testing/](http://www.ubuntu.com/testing/)


If you're interested in following the changes as we further 
develop Oneiric, we suggest that you subscribe initially to the
ubuntu-devel-announce list. This is a low-traffic list (a few 
posts a week) carrying announcements of approved specifications, 
policy changes, alpha releases, and other interesting events.

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)


Enjoy,

Kate Stewart, on behalf of the Ubuntu release team.


---

### Post by ronacc on 2011-07-07
any idea when lubuntu A2 will arrive ?

---

### Post by cariboo on 2011-07-07
I can't find any info on it, I guess we'll have to wait until phillw chimes in with the news.

---

### Post by VinDSL on 2011-07-07
YES!

That's what I'm been waiting for...  :D

Thanks!

---

### Post by iClouseau88 on 2011-07-07
Hi,

I installed June 13 build of Ubuntu 11.10 and updated almost daily since then.  I guess after today's update, I got Alpha 2, n'est-ce pas?

Just want to make sure.  Thanks!

---

### Post by Alwimo on 2011-07-07
I'm downloading the oneiric-desktop-amd64.iso via transmission, and it says the tracker gave an error, that the download is not authorised for use with the tracker. 

Also, I'm currently using 11.04 at the moment, contrary to what it might say under my name at the moment.

---

### Post by iClouseau88 on 2011-07-07
> **iClouseau88 said:**
> Hi,

I installed June 13 build of Ubuntu 11.10 and updated almost daily since then.  I guess after today's update, I got Alpha 2, n'est-ce pas?

Just want to make sure.  Thanks!

Hi again,

Just sudo updated and safe-upgraded 2 minutes ago. I got:

gcc:4:4.6.0-3ubuntu1 (latest version)

Uname -r: (kernel) 3.0-3-generic

I guess this is NOT Alpha 2?

:confused:

---

### Post by VinDSL on 2011-07-07
Installation worked like a charm!

It even came up in beautiful 3D - without having to install nVidia-current.

```

vindsl@Zuul:~$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p
Thu Jul  7 20:17:11 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0-3-generic
unity 4.2.0
nvfx_screen_get_param:94 -  Warning: unknown PIPE_CAP 29
**[COLOR="Red"]OpenGL vendor string:   nouveau[/COLOR]**
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 7.11-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

**[COLOR="Red"]Unity supported:          yes[/COLOR]**

```


Don't think I've seen that before...  ;)

---

### Post by cariboo on 2011-07-07
You can use zsync to update your current iso without having to download the whole thing.

---

### Post by VinDSL on 2011-07-08
> **iClouseau88 said:**
> I guess this is NOT Alpha 2?

:confused:
Well...

[LIST=1]
[*]I've never seen nouveau drivers work better than nVidia-current.

[*]My RAM usage is less than half of what it was, 2 hours ago.

[*]This machine is flying like the wind!!!
[/LIST]

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-7-jul-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-jul-2011(2).png")[/INDENT]


Walks, talks, and quacks like A2, IMO...  :D

---

### Post by lucazade on 2011-07-08
> **VinDSL said:**
> 
[*]I've never seen nouveau drivers work better than nVidia-current.


oh! time to try again nouveau... I always had hard freeze in the latest version, hope this time.. well, better to not say anything before try :)

---

### Post by as2000 on 2011-07-08
> **VinDSL said:**
> 

[[IMG]http://vindsl.com/images/vindsl-desktop-7-jul-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-jul-2011(2).png")[/INDENT]



Pardon my ignorance,what is that info bar on the right part of your screenshot called?

---

### Post by VinDSL on 2011-07-08
> **as2000 said:**
> Pardon my ignorance,what is that info bar on the right part of your screenshot called?
That's Conky, conkyForecast, plus a couple of Lua scripts.  The data dump is in my sig.  ;)

---

### Post by VinDSL on 2011-07-08
> **lucazade said:**
> oh! time to try again nouveau... I always had hard freeze in the latest version, hope this time.. well, better to not say anything before try :)
So far, so good!

I'm going to button up the install, then try some online Flash games.  If they work, I'll continue running nouveau for a while.

Sure would make life easier...

---

### Post by iClouseau88 on 2011-07-08
@VinDSL,

I love your wallpaper!  Care to post the link on how to get the "instrument gauges" and readings on the right hand column of it?

Thanks!

---

### Post by VinDSL on 2011-07-08
> **iClouseau88 said:**
> I love your wallpaper!  Care to post the link on how to get the "instrument gauges" and readings on the right hand column of it?
Thanks!

The wall is called "Black Tile":  [http://www.wallpaperpimper.com/Black-Tile-wallpaper-14709](http://www.wallpaperpimper.com/Black-Tile-wallpaper-14709)

You'll probably have to GIMP it (I did) because it only comes in 2 sizes.

The stuff on the right-side is from a package called Conky.  I have a link to a HOWTO and data dump, in my sig.

If you have any Conky questions, you can ask here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)


On topic:  I finished the fresh A2 install - checked for upgrades - and 151 were waiting for me.  Hello!?!?!? 

```

The following packages will be upgraded:
  accountsservice apport apport-gtk banshee banshee-extension-soundmenu
  banshee-extension-ubuntuonemusicstore baobab base-files bind9-host binutils
  compiz compiz-core compiz-gnome compiz-plugins-default cpp-4.6 dbus dbus-x11
  dnsutils duplicity empathy empathy-common firefox firefox-globalmenu
  firefox-gnome-support gcc-4.6 gcc-4.6-base gconf2 gconf2-common
  gir1.2-appindicator-0.1 gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-glib-2.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0 gir1.2-pango-1.0 gir1.2-peas-1.0
  gnome-bluetooth gnome-control-center gnome-control-center-data
  gnome-desktop3-data gnome-doc-utils gnome-screenshot gnome-search-tool
  gnome-session gnome-session-bin gnome-session-common gnome-system-log
  gnome-utils-common gvfs gvfs-backends gvfs-fuse jockey-common jockey-gtk
  libaccountsservice0 libappindicator1 libappindicator3-1 libatk1.0-0
  libatk1.0-data libbind9-60 libdbus-1-3 libdbus-glib-1-2 libdecoration0
  libdns69 libegl1-mesa libegl1-mesa-drivers libgail-3-0 libgail-3-common
  libgbm1 libgcc1 libgconf2-4 libgirepository-1.0-1 libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libglib2.0-0 libglib2.0-bin libglib2.0-data
  libglu1-mesa libgnome-bluetooth8 libgnome-control-center1
  libgnome-desktop-3-2 libgomp1 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2-perl libisc62 libisccc60 libisccfg62 libjson-glib-1.0-0
  liblightdm-gobject-0-0 liblwres60 libopenvg1-mesa libpango1.0-0
  libpeas-1.0-0 libpeas-common libperl5.12 libplist1 libpoppler-glib6
  libpoppler13 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libquadmath0 libsdl1.2debian
  libsdl1.2debian-pulseaudio libstdc++6 libupower-glib1 libutouch-frame1
  libutouch-geis1 light-themes lightdm lightdm-greeter-example-gtk mountall
  nautilus-sendto-empathy network-manager-gnome perl perl-base perl-modules
  policykit-desktop-privileges poppler-utils python-appindicator python-apport
  python-gnomekeyring python-imaging python-oauth python-problem-report
  python-wnck python3.2 python3.2-minimal software-center update-manager
  update-manager-core upower vinagre vino xorg-docs-core xserver-common
  xserver-xorg-core xserver-xorg-input-synaptics zeitgeist zeitgeist-core
151 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 88.9 MB of archives.
After this operation, 3,391 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

``` 

How can this be?

Gotta love those Alphas...  :D

---

### Post by VinDSL on 2011-07-08
Bwahahaha!  Here's a classic for you...

I'm sitting here, thinking... 

[LIST]
[*]You shouldn't do those 151 upgrades.  Don't do it!

[*]Everything is running perfect. Leave it alone!

[*]Enjoy the clean install.  Do the upgrades tomorrow.
[/LIST]

Half-hour later I do the upgrades.  LoL!

BOOM!  100% CPU usage!  And, Nautilus is now broken.   :D

I kicked myself, for a while, then did a top.  Aha!  Ubuntu One is the culprit.

Soooo, I decide to purge Ubuntu One.  Only problem is, it's going to remove Tomboy (Huh? What? Why? I dunno...)

Moments before pushing the enter key, I rethink the idea, and do another upgrade.  Guess what?!?!?  Ubuntu One upgrades are now available.

I performed the Ubu One upgrades.  CPU usage immediately dropped to 10%, and Nautilus started working again.

Heh!  That does it for the upgrades... for one day.  

I'm quitting while I'm ahead!  ;)

---

### Post by el_koraco on 2011-07-08
I don't get it, why does RAM usage climb exponentially when you install the proprietary drivers?

---

### Post by VinDSL on 2011-07-08
> **el_koraco said:**
> I don't get it, why does RAM usage climb exponentially when you install the proprietary drivers?
I guess I don't understand the question.

When I do a fresh, Live-CD install, I elect to NOT upgrade the files during installation.

Why, you may ask?  Because, I've had too many flaky (alpha/beta) installs doing this.  

Upgrading during installation of final releases is fine, but you're just begging for problems with test releases, IMO.

I did a fresh A2 install (no upgrades during installation) and everything worked great.

I installed all my favorite apps, et cetera.  Everything still worked great.

Then, I bit the bullet, and did the 151 upgrades.  Boom!  Luckily, the next set of upgrades fixed it (Ubuntu One).

Anyway, all is well now.  Tomorrow is another day.

It'll break again, guaranteed!  But, that's half the fun, yes?  :)

---

### Post by el_koraco on 2011-07-08
I didn't mean why RAM usage climbs on your install when you install proprietary drivers, I meant in general :D

Any time I use radeon, my install hovers around 150 - 300 MB on light, and maybe up to 600 with heavy stuff. When I use fglrx, I start at lilke 250, and go up to 1.1 GB  or higher with a five applications open. 

Don't understand what the deal is, is it shared memory with the graphics card, so that when you install the proprietary drivers it spikes? You said it yourself, with nouveau, your RAM usage dropped by more than half, which is kinda the same situation I'm in.

---

### Post by t.rei on 2011-07-08
Wow, this alpha2 brings lots and lots of new breakage on it's way to get more UI elements from gtk2 to gtk3. Indicators are practically inoperational today due to libindicator3-6 not being updated as it seems.

---

### Post by charliewhizbeez on 2011-07-08
> **VinDSL said:**
> Well...

[LIST=1]
[*]I've never seen nouveau drivers work better than nVidia-current.

[*]My RAM usage is less than half of what it was, 2 hours ago.

[*]This machine is flying like the wind!!!
[/LIST]

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-7-jul-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-jul-2011(2).png")[/INDENT]


Walks, talks, and quacks like A2, IMO...  :D

Wow, unity looks fantastic!!

Is it more customizable?

Is the menu at all different?

---

### Post by dino99 on 2011-07-08
its conky (on the right side)

---

### Post by Jerry N on 2011-07-08
I downloaded the Alpha 2 Alternate Install ISO today and burned it to a DVD using Nero in Windows(wouldn't fit on a CD) just like I have done more than a hundred times.  However, the DVD would not boot, no matter what I tried. Other CDs/DVDs boot so it is not a CD/DVD drive problem. 

No biggie - I will just wait for the next Alpha, or maybe the Beta.

Jerry

---

### Post by as2000 on 2011-07-08
> **VinDSL said:**
> That's Conky, conkyForecast, plus a couple of Lua scripts.  The data dump is in my sig.  ;)

Thanks! Gonna sit down with a pot of coffee and set this up!

---

### Post by Quackers on 2011-07-08
> **as2000 said:**
> Thanks! Gonna sit down with a pot of coffee and set this up!

A big pot :wink:

---

### Post by VinDSL on 2011-07-08
> **t.rei said:**
> Wow, this alpha2 brings lots and lots of new breakage on it's way to get more UI elements from gtk2 to gtk3. Indicators are practically inoperational today due to libindicator3-6 not being updated as it seems.
I noticed that indicator-session and indicator-sound were broken, last night.

apt-get upgrade wouldn't touch them, e.g. they were on hold.

Synaptics wouldn't upgrade them either, so I tried a "wash, rinse, and style" (remove-purge-reinstall).

Purging indicator-session and indicator-sound was successful, but I couldn't reinstall them due to dependencies on libindicator3-6.

Checkmate!  A2 won.  I lost.  Time to go to bed...  LoL!  :D

Then I awoke, there was an upgrade for libindicator3-6 waiting in the wings.

I did the following:
[LIST=1]
[*]Upgraded libindicator3-6
[*]Installed indicator-session & indicator-session-gtk2
[*]Installed indicator-sound & indicator-sound-gtk2
[*]Restart
[/LIST]
... and all is good now.

BTW, every time I've had a problem with an indicator not working, it was because the "indicator-<whatever>-gtk2" package wasn't also installed, so make sure BOTH versions are installed, for all of the indicators that you are running.  ;)

---

### Post by VinDSL on 2011-07-08
> **as2000 said:**
> Thanks! Gonna sit down with a pot of coffee and set this up!
> **Quackers said:**
> A big pot :wink:
Me too!

First pot of "black magic" on its way...  :)

---

### Post by VinDSL on 2011-07-08
> **Jerry N said:**
> I downloaded the Alpha 2 Alternate Install ISO today and burned it to a DVD [...]

**[COLOR="Red"]DVD would not boot, no matter what I tried.[/COLOR]** [...]

Other CDs/DVDs boot so it is not a CD/DVD drive problem. [...]

No biggie - I will just wait for the next Alpha, or maybe the Beta [...]
Don't be so sure it isn't the ISO - they're hyrids now!  :D

> 
**Colin Watson** cjwatson at ubuntu.com 
*Wed Jun 15 21:22:34 UTC 2011*

[B][COLOR="Red"]As of tomorrow's daily builds, all Oneiric amd64 and i386 CD images on
cdimage.ubuntu.com can also be written directly to a USB device.[/COLOR][/B]  You
can still use usb-creator if you need to enable persistent storage on
the USB stick, but if all you need is to install from the stick then
this simplifies the process.

There is a small size cost to this feature; part of this is partition
alignment to 1MB "cylinders" (since the image now has to simultaneously
look like a CD and a partitioned USB disk), and part of it is a second
directory tree whose size is roughly proportional to the number of files
in the image.  On the server CD (and probably the alternate CD too,
though I haven't measured that), this came out to about 5MB, but as luck
would have it I found a way to save about the same amount by hardlinking
some files together, so the size there stays roughly the same.  On the
desktop CD, unfortunately, we lose about 1MB (although I consider myself
to have "paid" for this by way of the 2MB or so we gained by switching
to live-build ...).  If this becomes a problem close to release time,
then we may be able to shave off a bit at the possible cost of some
USB-booting compatibility on a few machines by dropping the 1MB
alignment.  See the recent thread on pkg-libburnia-devel for details.

I realise that we're behind a number of other major distributions on
this.  The delay was because (like Debian) we couldn't simply use
isohybrid because that would break jigdo downloads, so we had to switch
to xorriso as the CD image generator on these architectures for its new
JTE support, and by the time all that landed in Debian I didn't really
want to cram it into 11.04.  

See [http://blog.einval.com/2011/01/07#isohybrid_CDs](http://blog.einval.com/2011/01/07#isohybrid_CDs) for the gory details,
and thanks a lot to Steve, Thomas, and George for their hard work on
that.

[B][COLOR="Red"]Please file bugs on[/COLOR] [https://bugs.launchpad.net/ubuntu-cdimage](https://bugs.launchpad.net/ubuntu-cdimage) [COLOR="Red"]if this
change causes the _IMAGE TO STOP WORKING_ on machines where it previously
worked.[/COLOR][/B]

Cheers,

-- 
Colin Watson                                       [cjwatson at ubuntu.com]



Just for giggles, you might want to read this:

[http://ubuntuforums.org/showpost.php?p=10945413&postcount=1](http://ubuntuforums.org/showpost.php?p=10945413&postcount=1)  [COLOR="Blue"](HOWTO:VinDSL Write Oneiric amd64 or i386 Daily Build CD/USB images directly to USB stick)[/COLOR]

It explains what's going on with the Hybrid CD/USB Images, blah, blah, blah.  ;)

---

### Post by VinDSL on 2011-07-09
> **VinDSL said:**
> I guess I don't understand the question. [...]
> **el_koraco said:**
> I didn't mean why RAM usage climbs on your install when you install proprietary drivers, I meant in general [...] :D

You said it yourself, with nouveau, your RAM usage dropped by more than half, which is kinda the same situation I'm in.
WoW!  You don't know how right you are!

UbuOO has been a snooze today - no upgrades, et cetera.

I was sitting here, drinking coffee, and bored (bad scenario), so I decided to test the theory.

After doing a cold boot:
[LIST]
[*]Measured the RAM usage (Nouveau), sitting idle @ the desktop (192M)

[*]Installed nVidia-common. Measured RAM usage during install (258M) 

[*]Did a cold boot.

[*]Measured RAM usage sitting idle @ desktop (688M)

[*]Removed nVidia-common.  Measured RAM usage during removal (756M +95.2M swap)

[*]Did a cold boot.

[*]Measured RAM usage (Nouveau), sitting idle @ the desktop (192M)
[/LIST]
You're right!

Unbelievable difference - and I have the screenies to prove it...  :D

---

### Post by mc4man on 2011-07-09
> **el_koraco said:**
> I don't get it, why does RAM usage climb exponentially when you install the proprietary drivers?

It's from the gl enabled cairo, actually a little  worse now than in the past.
Also has the side effect of increasing some of the small mem leaks still present

---

### Post by el_koraco on 2011-07-09
It's much worse with Kwin and fglrx. At least with Compiz or Metacity, I get some kind of dynamic memory allocation, so I can open applications with little problems, other than my total RAM limit. The last time I used Kubuntu, I just couldn't multitask with fglrx, the system was freezing on five apps open. 

I just can't figure out what the deal is, I've looked at some bugs relating to both Compiz and Kwin, but couldn't reproduce what is described as memory leaks. Plus, top and System monitor don't show anything freaking out. 

Didn't have a chance to test it with Mutter, because we're still waiting on a working Catalyst to go with GS. It's pathetic as usual.

---

### Post by el_koraco on 2011-07-09
> **mc4man said:**
> It's from the gl enabled cairo, actually a little  worse now than in the past.
Also has the side effect of increasing some of the small mem leaks still present

Aaaah, so that's it. I have my sister's laptop fixed up with Maverick, on Intel drivers. No such problems there.

---

### Post by mc4man on 2011-07-09
> **el_koraco said:**
> Aaaah, so that's it. I have my sister's laptop fixed up with Maverick, on Intel drivers. No such problems there.
It first showed in natty - nvidia drivers only. Because there was no advantage to users from gl enabled cairo and no fix in sight cairo was reverted at the last minute removing gl support.

The same thing is occurring in O, though this time it's less likely gl will be removed, possibly more like it's either fixed or too bad.
(though again, at least to date, there is no advantage to gl enabled cairo for regular users

It's pretty straightforward to re-build the cairo source as ubuntu packages removing the --with-gl option, an adjustment is needed to the symbols file for successful package builds
On machines w. 2GB or more mem not the issue as 1GB machines (unless one is ok with swap use,  - some are, some aren't depending on use case ect.

---

### Post by el_koraco on 2011-07-09
> **mc4man said:**
> It first showed in natty - nvidia drivers only. Because there was no advantage to users from gl enabled cairo and no fix in sight cairo was reverted at the last minute removing gl support.


I have the same thing happening in Maverick. Not as bad as in Kubuntu Natty, though. Thanks for the explanation, I'd been racking my brain on this one.

---

### Post by pulpo69 on 2011-07-10
i updated today to alpha2, when i boot i get the message:

/run/udev/ not writable  falling back /dev/.udev/

in the login screen the mouse-cursor is frozen and i can do
nothing.  Any help?

---

### Post by Quackers on 2011-07-10
The /run/udev message is nothing new and is not serious. The lack of pointer use and keyboard is the main problem for me. You appear to be only the third person to have mentioned this.

---

### Post by pulpo69 on 2011-07-10
is there any solution for the pointer and keyboard-problem?

---

### Post by Quackers on 2011-07-10
I haven't found one yet. But don't give up! It could be that one of the updates messed things up, not sure. It's possible that an update may fix it :-)
You may need to chroot in to run that update though.

---

### Post by pulpo69 on 2011-07-10
i can recovery in grub and then choose netroot, so i can do the updates. i hope the problem will be solved soon.

---

### Post by Quackers on 2011-07-10
Yes, I'll keep my fingers crossed too :-)

---

### Post by VinDSL on 2011-07-10
I was having keyboard problems (desktop install) and pointer problems (running the Live-CD), last week.

I don't know if you remember this thread (or even saw it)...

[INDENT][http://ubuntuforums.org/showthread.php?t=1795642](http://ubuntuforums.org/showthread.php?t=1795642)[/INDENT]


If I remember correctly - and, broadly speaking - control of the keyboard and mouse wasn't getting passed off to something-or-another during the boot process, if the LightDM config file specified "vt=active".

The workaround was to specify "vt=7" in the LightDM config file.

Recently, an update asked me if I wanted to keep my current LightDM config file, or allow it to be modified.

I looked at the diff, and it wanted to change "vt=active" (on my fresh A2 install) to "vt=0".

Since I had success with "vt=7" (on my A1 install), I let it modify the line to "vt=0".  And, I haven't had any problems.

Anyway, if you guys are running LightDM, you might want to play around with that setting, or at least check it out.

Just a thought...

---

### Post by Quackers on 2011-07-10
No keyboard dude - at al, here. At no time during or after booting does it work. ctrl+Alt+F1 doesn't work to drop to a command line. 
Sadly some time ago I disabled recovery line in grub and now I'm paying the price :-) I can't change it back, even through chroot. I tried ```
sed s/'GRUB_DISABLE_LINUX_RECOVERY="true"'/'#GRUB_DISABLE_LINUX_RECOVERY="true"'/g -i /etc/default/grub
``` but sadly no change in the grub menu entry for this installation after running update-grub in the system with "controlling grub".
So messing with any files just isn't possible at the moment.
Any ideas? :-)

---

### Post by jerrylamos on 2011-07-10
> **Quackers said:**
> No keyboard dude - at al, here. At no time during or after booting does it work. ctrl+Alt+F1 doesn't work to drop to a command line. 

For whatever reason here, I've had Ctrl-Alt-F2 work when F1 didn't.

But I'm running Live "persistent".  No installs for a few days, and then on USB hard drive.  the hard drive is a left over laptop drive with a $10 case.

This is from an Acer Aspire one netbook.  Some people have had keyboard/mouse problems with this model, for whatever reason again I don't.  Now the "dread update" will likely rear it's head...

Jerry

---

### Post by pulpo69 on 2011-07-10
if i get to lightDM login screen, mouse cursor is frozen and keyboard doesn't work. If i plug out the mouse and keyboard connectors and plugin again keyboard and mouse works. (both usb connected)

---

### Post by sgage on 2011-07-10
> **VinDSL said:**
> After doing a cold boot:
[LIST]
[*]Measured the RAM usage (Nouveau), sitting idle @ the desktop (192M)

[*]Installed nVidia-common. Measured RAM usage during install (258M) 

[*]Did a cold boot.

[*]Measured RAM usage sitting idle @ desktop (688M)

[*]Removed nVidia-common.  Measured RAM usage during removal (756M +95.2M swap)

[*]Did a cold boot.

[*]Measured RAM usage (Nouveau), sitting idle @ the desktop (192M)
[/LIST]
You're right!

Unbelievable difference - and I have the screenies to prove it...  :D

Yes, nouveau has come along nicely. I see similar differences in RAM usage as what you show here. Unfortunately, nouveau seems to make the GPU run significantly hotter.

Running with nouveau also enables suspend/resume to work on my computer now, which it did not with the nvidia drivers.

---

### Post by Quackers on 2011-07-10
> **pulpo69 said:**
> if i get to lightDM login screen, mouse cursor is frozen and keyboard doesn't work. If i plug out the mouse and keyboard connectors and plugin again keyboard and mouse works. (both usb connected)

Similar here for the usb mouse, but I'm not delving into the laptop to unplug the keyboard. It seems it's some sort of detection problem whilst booting.

---

### Post by sgage on 2011-07-10
Here's another little nouveau vs. nvidia issue I've confirmed:

In nouveau, the window buttons (min/max/close) don't give any visual cues when you hover over them or click them - in nvidia they do.

(I should also note that my machine DOES suspend/resume properly with nvidia - the fault was with a gimmick I tried to make the boot process a bit less ugly.)

---

### Post by VinDSL on 2011-07-10
> **sgage said:**
> Unfortunately, nouveau seems to make the GPU run significantly hotter.[...]
Interesting!

How's the GPU temp?

Here's mine:
```

$ sudo nvclock -i
Xlib:  extension "NV-CONTROL" missing on display ":0".
-- General info --
Card: 		nVidia Geforce 7600GT
Architecture: 	NV4B/G73 B1
PCI id: 	0x2e0
GPU clock: 	558.900 MHz
Bustype: 	AGP (BR02)

-- Pipeline info --
Pixel units: 3x4 (011b)
Vertex units: 5x1 (11111b)
HW masked units: None
SW masked units: None

-- Memory info --
Amount: 	256 MB
Type: 		128 bit DDR
Clock: 		702.000 MHz

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 82C
Fanspeed: 31.1%

-- VideoBios information --
Version: 05.73.22.25.88
Signon message: XFX C328 7600GT VGA BIOS
Performance level 0: gpu 560MHz/memory 1400MHz/1.30V/31%
VID mask: 3
Voltage level 0: 1.30V, VID: 2

```

---

### Post by sgage on 2011-07-10
> **VinDSL said:**
> Interesting!

How's the GPU temp?

Here's mine:
```

$ sudo nvclock -i
Xlib:  extension "NV-CONTROL" missing on display ":0".
-- General info --
Card: 		nVidia Geforce 7600GT
Architecture: 	NV4B/G73 B1
PCI id: 	0x2e0
GPU clock: 	558.900 MHz
Bustype: 	AGP (BR02)

-- Pipeline info --
Pixel units: 3x4 (011b)
Vertex units: 5x1 (11111b)
HW masked units: None
SW masked units: None

-- Memory info --
Amount: 	256 MB
Type: 		128 bit DDR
Clock: 		702.000 MHz

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 82C
Fanspeed: 31.1%

-- VideoBios information --
Version: 05.73.22.25.88
Signon message: XFX C328 7600GT VGA BIOS
Performance level 0: gpu 560MHz/memory 1400MHz/1.30V/31%
VID mask: 3
Voltage level 0: 1.30V, VID: 2

```

With nouveau, my GPU temps are mid to upper 80's (I hit 90 this morning). With nvidia, same loads, same ambient temperature, low 70's. I don't believe I'm the first to mention this phenomenon.

BTW - I'm running a GeForce 8500 GT.

---

### Post by el_koraco on 2011-07-10
It's similar with fglrx. I think the OSS drivers don't have downclocking capabilities like the proprietary drivers, and the fan management is generally much worse. It's the only reason I bother installing AMD's disgrace.

---

### Post by ikt on 2011-07-11
Is it just me or was this alpha 2 released a month earlier than normal?

---

### Post by jbicha on 2011-07-11
Alpha 2 was released right on time: [https://wiki.ubuntu.com/OneiricReleaseSchedule](https://wiki.ubuntu.com/OneiricReleaseSchedule)

---

### Post by seeker5528 on 2011-07-11
> **Quackers said:**
> No keyboard dude - at al, here. At no time during or after booting does it work. ctrl+Alt+F1 doesn't work to drop to a command line.

No 'Ctrl'+'Alt'+'F1' was happening to me to, but using 'SysRq'+'R' to change the keyboard input from raw to xlate mode, 'Ctrl'+'Alt'+'F1' works for me again, until I stop a display manager then start either the display manger or an xsession again, then I have to do the SysRq thing again.

After reading other posts about this, USB keyboard and mouse work for me, have not tried rebooting yet to see of they work on boot up or have to be unplugged and plugged in again.

EDIT: No keyboard or mouse is happening with GDM or typing 'startx' at the command line, so doesn't seem to be a lightdm thing.

Later, Seeker

---

### Post by Quackers on 2011-07-11
The workaround for the lack of keyboard/mouse input is
mv /run/udev /run/udev.old

post #27 here
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/807306](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/807306)

---

### Post by ikt on 2011-07-12
> **jbicha said:**
> Alpha 2 was released right on time: [https://wiki.ubuntu.com/OneiricReleaseSchedule](https://wiki.ubuntu.com/OneiricReleaseSchedule)

I mean compared to previous releases.

[https://wiki.ubuntu.com/NattyReleaseSchedule](https://wiki.ubuntu.com/NattyReleaseSchedule)

There was a 2 month break between Alpha 1 and Alpha 2 during the natty cycle, oneiric was released with a 1 month break between A1 and A2.

---

### Post by cariboo on 2011-07-12
Alpha 1 was released June 2nd, alpha 2 was released July 7th, that looks like more then a month to to me. :)

Check the releases schedule sticky.

---

### Post by ikt on 2011-07-12
> **cariboo907 said:**
> Alpha 1 was released June 2nd, alpha 2 was released July 7th, that looks like more then a month to to me. :)

Oneiric:

[http://www.timeanddate.com/date/durationresult.html?d1=2&m1=06&y1=2011&d2=07&m2=07&y2=2011](http://www.timeanddate.com/date/durationresult.html?d1=2&m1=06&y1=2011&d2=07&m2=07&y2=2011)

Natty:

[http://www.timeanddate.com/date/durationresult.html?d1=02&m1=12&y1=2010&d2=03&m2=02&y2=2011](http://www.timeanddate.com/date/durationresult.html?d1=02&m1=12&y1=2010&d2=03&m2=02&y2=2011)

Am I really the only one seeing the alpha ship a month earlier than normal?

I mean it doesn't bother me, it's exactly what I wanted (which is probably why I noticed it). I made some posts back in the old natty forum. Just surprised nobody has mentioned anything :s

---

### Post by andrewabc on 2011-07-14
> **ronacc said:**
> any idea when lubuntu A2 will arrive ?

I'm also eagerly awaiting. Want to test as it will be used for web browser dedicated OS (probably on usb stick).

[http://people.ubuntu.com/~gilir/](http://people.ubuntu.com/~gilir/)
[https://lists.launchpad.net/lubuntu-desktop/](https://lists.launchpad.net/lubuntu-desktop/)

---

### Post by wildmanne39 on 2011-07-15
I am downloading Alpha 2, but is it not possible to just upgrade from one to two?

---

### Post by Quackers on 2011-07-15
If your alpha1 is fully updated that should be the same afaik.

---

### Post by wildmanne39 on 2011-07-15
> **Quackers said:**
> If your alpha1 is fully updated that should be the same afaik.Hi, thank you that is what I thought but I was not sure I am pretty new to development. I appreciate the reply.

---

### Post by andrewabc on 2011-07-15
> **wildmanne39 said:**
> Hi, thank you that is what I thought but I was not sure I am pretty new to development. I appreciate the reply.

Yes you were correct. Just keep updating and you have latest version. Although by the very end when final released I'd suggest doing a format/reinstall as most likely some 'crud' and leftover stuff or settings from alpha 1 that will be different than final.

---

