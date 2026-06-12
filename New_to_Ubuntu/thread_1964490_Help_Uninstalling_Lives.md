---
title: "Help Uninstalling Lives"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by Syndacate on 2012-04-24
Running 10.04.

I installed version 1.3.2 from the repos.  This version is outdated (current stable is 1.3.12 (latest dev version is 1.6.1).  Minor update, sure, though I still kind of want the latest stable.  Though I don't feel like re-compiling to update, so as far as pre-made packages go the author directs you to getdeb.net, where they have a later version than the repos (1.4.6 for 10.04):
[http://www.getdeb.net/software/LiVES](http://www.getdeb.net/software/LiVES)

I've tried uninstalling lives & lives-data and running aptitude with the auto-remove command.  Whenever I download it from getdeb.net it installs version 1.3.2.

I can't figure out exactly what I'm doing wrong..  Any help is appreciated!

---

### Post by anejo on 2012-04-24
Mmm... if the getdeb apt:lives is pointing to the wrong stuff then why not just download it from
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

Even if you only get the main lives_._._ package you'll be able to pick up the dependencies (via your install method). Sure its long-winded but it beats getting the wrong version and besides, that way you can decide whether you want stable or testing

---

### Post by Syndacate on 2012-04-24
> **anejo said:**
> Mmm... if the getdeb apt:lives is pointing to the wrong stuff then why not just download it from
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

Even if you only get the main lives_._._ package you'll be able to pick up the dependencies (via your install method). Sure its long-winded but it beats getting the wrong version and besides, that way you can decide whether you want stable or testing

That has 1.3.4, lol.

I feel like it's not pointing to the wrong place though (though I don't exactly know how to check), I feel like I'm not removing something properly.

Either way, I don't have the ridiculous disk space it seems lives needs to operate :(.

---

### Post by anejo on 2012-04-26
> **Syndacate said:**
> That has 1.3.4, lol

Umm... read and select properly!

```
wheezy (testing) (video): Video Editing system ...
1.6.1~ds1-1

```

---

### Post by sandyd on 2012-04-26
Why on earth would you want to introduce debian stuff into the mix?
[https://launchpad.net/~ferramroberto/+archive/lives](https://launchpad.net/~ferramroberto/+archive/lives)

---

### Post by anejo on 2012-04-26
I never want to ever introduce Debian stuff into the mix (at least not intentionally!).

But every once in awhile, a something.deb that one wants to test with, might be available in the Debian repository and not in Ubuntu's. The something.deb typically might not be in the main Ubuntu repos yet... and typically is developed for the Linux community and is not something unique to Debian per se. So getting a deb elsewhere has never broken my installation (yet).

It's simply convenience... and in Syndacate's case, this could--although I didn't check there--just as easily gotten off the Ubuntu packages and again, given the specifics from Syndacate, I guess that version he was looking for would be available in universe anyway!

Let's not confuse the use of a .deb with something Debian... necessarily.

---

### Post by Syndacate on 2012-04-26
> **anejo said:**
> Umm... read and select properly!

```
wheezy (testing) (video): Video Editing system ...
1.6.1~ds1-1

```

My bad, only checked stable.

Didn't matter much anyway :( (read below).

> **anejo said:**
> I never want to ever introduce Debian stuff into the mix (at least not intentionally!).

But every once in awhile, a something.deb that one wants to test with, might be available in the Debian repository and not in Ubuntu's. The something.deb typically might not be in the main Ubuntu repos yet... and typically is developed for the Linux community and is not something unique to Debian per se. So getting a deb elsewhere has never broken my installation (yet).

It's simply convenience... and in Syndacate's case, this could--although I didn't check there--just as easily gotten off the Ubuntu packages and again, given the specifics from Syndacate, **I guess that version he was looking for would be available in universe anyway!**

Let's not confuse the use of a .deb with something Debian... necessarily.

I was just looking for an updated version which was able to fix an issue I had with a previous one.

Few problems cropped up.  When I went to install 1.6.1 it asked for as a dependency:
```
liboss-salsa-asound2
```

No problem I said at first, then I check the repos....well this package wants to basically install every package I have.  Laundry list of **** it wants to remove:
```

aisleriot alsa-utils bluez-alsa brasero chromium-browser
  chromium-browser-l10n chromium-codecs-ffmpeg compiz compiz-gnome couchdb-bin
  desktopcouch empathy esound-clients espeak evolution evolution-couchdb
  evolution-exchange evolution-indicator evolution-plugins f-spot firefox
  firefox-branding firefox-gnome-support gbrainy gdm gdm-guest-session
  gnome-about gnome-applets gnome-control-center gnome-do gnome-do-docklets
  gnome-do-plugins gnome-games-common gnome-mag gnome-mahjongg gnome-media
  gnome-orca gnome-panel gnome-power-manager gnome-session
  gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-user-guide
  gnome-user-guide-en gnome-user-share gnome-utils gnomine gstreamer0.10-alsa
  gstreamer0.10-plugins-bad gwibber gwibber-service ia32-libs icedtea6-plugin
  indicator-applet indicator-applet-session indicator-me indicator-sound
  lib32asound2 libaccess-bridge-java libaccess-bridge-java-jni libasound2
  libasound2-plugins libbonoboui2-0 libbrasero-media0 libcanberra-gtk-module
  libcanberra-gtk0 libcanberra-pulse libcanberra0 libesd0 libespeak1 libflite1
  libgail-gnome-module libgnome-pilot2 libgnome2-0 libgnome2-perl
  libgnome2.24-cil libgnomepanel2.24-cil libgnomeui-0 liblpint-bonobo0
  libmetacity-private0 libpanel-applet2-0 libportaudio2 libportmidi0
  libsox-fmt-alsa libvisual-0.4-plugins lives metacity mousetweaks mplayer
  mplayer-nogui nautilus-sendto-empathy nautilus-share openjdk-6-jre
pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 python-desktopcouch
  python-desktopcouch-records python-gnome2 python-gnomeapplet python-pyatspi
  python-pygame python-speechd quadrapassel rdesktop rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store skype smplayer smplayer-themes
  smplayer-translations sox speech-dispatcher system-config-printer-gnome
tomboy transmission-gtk tsclient ubuntu-desktop ubuntu-docs usb-creator-gtk
  vinagre vlc vlc-nox vlc-plugin-pulse wine wine1.2 xulrunner-1.9.2 yelp
```

992MB worth of packages it wants to remove...

Uhh...what?  The hell does removing the java run-time environment have to do with an alsa replacement?  This is crazy-talk :-\.  Think it needed 1.0.16 IIRC.

Not quite comfortable with that big a change on my main system..  God knows what would break.  So I checked with 1.3.4 and the only thing it needed was libjack0, which I pulled from debian.org, and it installed fine.

Unfortunately the issue wasn't resolved by 1.3.4, so bleh.  I'd like to install alsa but that's a crazy change...

---

### Post by Syndacate on 2012-04-26
> **sandyd said:**
> Why on earth would you want to introduce debian stuff into the mix?
[https://launchpad.net/~ferramroberto/+archive/lives]("https://launchpad.net/%7Eferramroberto/+archive/lives")

I just added it and updated to 1.4.9.  Not quite sure who's PPA that is, I don't think it's official....don't know how to remove PPA's either :-P.

Issue still persists in 1.4.9 but I suppose I'll just use a work-around.

Thanks for your time, guys.  Not quite sure what the hell ALSA is trying to do :-\.

---

### Post by anejo on 2012-04-26
Geeezzz... Sorry Bud!
Yeah I reckon I would give this one a miss until the version you want makes it to stable
And the ppa removal thingy can be real simple actually...
Find 'Software Sources' (either via Synaptic, System Settings or in the Applications folder/menu)
The 'Other Sofware' tab should list the ppas that are subscribed to
Select from the button choices for whatever next steps...

---

### Post by sandyd on 2012-04-26
> **anejo said:**
> I never want to ever introduce Debian stuff into the mix (at least not intentionally!).

But every once in awhile, a something.deb that one wants to test with, might be available in the Debian repository and not in Ubuntu's. The something.deb typically might not be in the main Ubuntu repos yet... and typically is developed for the Linux community and is not something unique to Debian per se. So getting a deb elsewhere has never broken my installation (yet).

It's simply convenience... and in Syndacate's case, this could--although I didn't check there--just as easily gotten off the Ubuntu packages and again, given the specifics from Syndacate, I guess that version he was looking for would be available in universe anyway!

Let's not confuse the use of a .deb with something Debian... necessarily.
Because Ubuntu and Debian have different versions of packages, there are times where installing an updated package from Debian will screw up all the deps, because it is newer than the version that the deps were compiled against.

Imagine taking glib from Debian and installing that in Ubuntu. Most of your GTK programs would instantly screw up, cause they weren't compiled against it. And once it happens, downgrading involves the cascading pinning of thousands of packages.

Its happened before, and most of those people ended up reinstalling their systems, since it doesn't have anything to do with ppa-purge.

---

### Post by anejo on 2012-04-26
> **sandyd said:**
> Imagine taking glib from Debian and installing that in Ubuntu. I agree 100% and that's an example of the kinda thing I was saying I wouldn't do.
There are however many non-system debs that work just fine.
Your explanation is worth these posts--so do take note if you do this--and should be adhere to 99% of the time.

Thanks!

---

### Post by Syndacate on 2012-04-26
> **anejo said:**
> Geeezzz... Sorry Bud!
Yeah I reckon I would give this one a miss until the version you want makes it to stable
And the ppa removal thingy can be real simple actually...
Find 'Software Sources' (either via Synaptic, System Settings or in the Applications folder/menu)
The 'Other Sofware' tab should list the ppas that are subscribed to
Select from the button choices for whatever next steps...

Yeah, I'll keep an eye on it, see what happens.  Maybe the package will get updated in that PPA.  I would cave and compile from source but if the package needs the new ALSA it really makes no difference.

I don't know why ALSA wants to change all that, but sound in Linux is finicky enough, IMO.  I don't want to hose the system - this is my daily.

> **sandyd said:**
> Because Ubuntu and Debian have different versions of packages, there are times where installing an updated package from Debian will screw up all the deps, because it is newer than the version that the deps were compiled against.

Imagine taking glib from Debian and installing that in Ubuntu. Most of your GTK programs would instantly screw up, cause they weren't compiled against it. And once it happens, downgrading involves the cascading pinning of thousands of packages.

Its happened before, and most of those people ended up reinstalling their systems, since it doesn't have anything to do with ppa-purge.

Yup.  Though most of the time they work.  Really depends how integrated the system is.  A core lib like GTK vs an external user-land app, y'kno?

> **anejo said:**
> I agree 100% and that's an example of the kinda thing I was saying I wouldn't do.
There are however many non-system debs that work just fine.
Your explanation is worth these posts--so do take note if you do this--and should be adhere to 99% of the time.

Thanks!

Yeah, but this is kind of core dependent because of all the system media stuff it requires.

---

