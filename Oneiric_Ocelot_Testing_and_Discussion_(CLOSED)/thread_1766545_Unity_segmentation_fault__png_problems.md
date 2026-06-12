---
title: "Unity segmentation fault / png problems"
date: 2011-05-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by afv on 2011-05-24
Hi all,

Unity started to segmentation fault after today updates, and I thought it was related to the new gnome-session:

> 
** (<unknown>:28948): WARNING **: Unable to texture /usr/share/unity/3/search_magnify.png: Couldn't recognise the image file format for file '/usr/share/unity/3/search_magnify.png'
Segmentation fault

Program received signal SIGSEGV, Segmentation fault.
0x00007fffe4e458b4 in PlacesStyle::TextureFromFilename(char const*) () from /usr/lib/compiz/libunityshell.so
...



but after downgrading the gnome-session packages and some others I realized I can't even see any png icons/images.
eog, for example, gives me "Could not load image 'search_magnify.png'. Unrecognised image file format".

Already downgraded most of today updates but the problem still persists.

---

### Post by Harry33 on 2011-05-24
> **afv said:**
> Hi all,

Unity started to segmentation fault ...
... I realized I can't even see any png icons/images.
eog, for example, gives me "Could not load image 'search_magnify.png'. Unrecognised image file format".
Already downgraded most of today updates but the problem still persists.

So you are sure the issue began only after todays updates?
If so, could you please list all packages here you have updated.

---

### Post by afv on 2011-05-24
> **Harry33 said:**
> So you are sure the issue began only after todays updates?
If so, could you please list all packages here you have updated.

I'm sure, booted the computer in the morning and everything was OK. These were the updates (I already downgraded them all):


> 
Commit Log for Tue May 24 12:55:08 2011


**Upgraded the following packages:**
dbus (1.4.8-3ubuntu1) to 1.4.8-3ubuntu3
dbus-x11 (1.4.8-3ubuntu1) to 1.4.8-3ubuntu3
glib-networking (2.28.6.1-0ubuntu1) to 2.28.6.1-0ubuntu2
gnome-keyring (3.0.0-3) to 3.0.2-1
libbluray0 (0.2~git20110213.20739ed-0ubuntu3) to 0.2~git20110427.8b86664-1
libdbus-1-3 (1.4.8-3ubuntu1) to 1.4.8-3ubuntu3
libdirac-encoder0 (1.0.2-3ubuntu1) to 1.0.2-4
libgck0 (3.0.0-3) to 3.0.2-1
libgcr-3-0 (3.0.0-3) to 3.0.2-1
libgnome-keyring0 (3.0.0-2) to 3.0.2-2
libpam-gnome-keyring (3.0.0-3) to 3.0.2-1
libpcap0.8 (1.1.1-5) to 1.1.1-6
libwww-perl (6.01-3) to 6.02-1

**Installed the following packages:**
libauthen-ntlm-perl (1.08-1)
libbluray-bdj (0.2~git20110427.8b86664-1)
liblwp-protocol-https-perl (6.02-1)



Commit Log for Tue May 24 17:32:10 2011

**Upgraded the following packages:**
ecryptfs-utils (87-0ubuntu1) to 88-0ubuntu1
evince (3.0.0-4ubuntu2) to 3.0.2-0ubuntu1
evince-common (3.0.0-4ubuntu2) to 3.0.2-0ubuntu1
gcalctool (6.0.1-0ubuntu1) to 6.0.2-0ubuntu1
gnome-control-center (1:3.0.1.1-1ubuntu1) to 1:3.0.2-1ubuntu3
gnome-control-center-data (1:3.0.1.1-1ubuntu1) to 1:3.0.2-1ubuntu3
gnome-session (2.32.1-0ubuntu20) to 3.0.2-0ubuntu1
gnome-session-bin (2.32.1-0ubuntu20) to 3.0.2-0ubuntu1
gnome-session-common (2.32.1-0ubuntu20) to 3.0.2-0ubuntu1
gnome-settings-daemon (3.0.1-1ubuntu4) to 3.0.2-1ubuntu1
libecryptfs0 (87-0ubuntu1) to 88-0ubuntu1
libevince3-3 (3.0.0-4ubuntu2) to 3.0.2-0ubuntu1
libgnome-control-center1 (1:3.0.1.1-1ubuntu1) to 1:3.0.2-1ubuntu3
librsvg2-2 (2.32.1-1ubuntu1) to 2.34.0-0ubuntu2
librsvg2-common (2.32.1-1ubuntu1) to 2.34.0-0ubuntu2
software-center (4.1.2) to 4.1.3


---

### Post by lucazade on 2011-05-24
same png/svg issue here.. tried to downgrade svg libs but w/o success.

---

### Post by Quackers on 2011-05-24
Same updates run here (which is my gnome3/gnome-shell desktop) with big problems.
No desktop background and none available in settings.
Evolution starts and then seg faults after about 30+ different errors.
Some of the Applications icons have gone for a walk
Top panel has 3 or 4 icons missing, but if I click on where they should be they still work :-)
Gnome-shell is no longer an option during login.  :-(

---

### Post by Harry33 on 2011-05-24
> **lucazade said:**
> same png/svg issue here.. tried to downgrade svg libs but w/o success.

Is that a Unity issue at all.
Have you tried this png (portable network graphics) or svg (scalable vector graphics) rendering with gnome-panel session or with gnome-shell session?

---

### Post by amauk on 2011-05-24
On my machine at least, I can get a semi-working GUI environment with```
metacity --replace &
```
Can at least launch stuff via terminal and use alt+tab to switch windows

---

### Post by lucazade on 2011-05-24
> **Harry33 said:**
> Is that a Unity issue at all.
Have you tried this png (portable network graphics) or svg (scalable vector graphics) rendering with gnome-panel session or with gnome-shell session?

Not strictly related to unity I believe because same happens with gnome-panel session.
Screenshots took now and before when everything was working :)

---

### Post by Harry33 on 2011-05-24
> **Quackers said:**
> Same updates run here (which is my gnome3/gnome-shell desktop) with big problems.
No desktop background and none available in settings.
Evolution starts and then seg faults after about 30+ different errors.
Some of the Applications icons have gone for a walk
Top panel has 3 or 4 icons missing, but if I click on where they should be they still work :-)
Gnome-shell is no longer an option during login.  :-(

Hmm, that really ruins png and svg rendering.
There was no bug report on this yet.
Could some one report this?

I would downgrade the latest packages librsvg2-2 and librsvg2-common first and then all the latest gnome-session packages.
But I doubt this is because of the session packages. I have them installed without problems and I had the Gnome3 PPA session packages installed before that.
I also have the latest dbus, gnome-control-center and gnome-settings-daemon packages installed.

---

### Post by SevenMachines on 2011-05-24
Rebuilding libgdk-pixbuf2.0-0 seems to fix it

---

### Post by Harry33 on 2011-05-24
> **lucazade said:**
> Not strictly related to unity I believe because same happens with gnome-panel session.
Screenshots took now and before when everything was working :)

Lucazade, you do have the panel icon images (svg) missing.

---

### Post by afv on 2011-05-24
> **Harry33 said:**
> Is that a Unity issue at all.
Have you tried this png (portable network graphics) or svg (scalable vector graphics) rendering with gnome-panel session or with gnome-shell session?

I guess it isn't a unity issue, but it makes unity seg fault (that was the first thing I noticed after the updates).

At gnome classic there are some transparent icons at the panel and some "unknown".

gnome-screenshot&#8230;

> 
Unable to save the screenshot to disk:
Image type 'png' is not supported



edit:

> **SevenMachines said:**
> Rebuilding libgdk-pixbuf2.0-0 seems to fix it

Reinstalling libgdk-pixbuf2.0-0 did the trick, thanks!

I'll begin to upgrade the packages again and see if there's one responsible for this&#8230;

---

### Post by lucazade on 2011-05-24
> **Harry33 said:**
> Lucazade, you do have the panel icon images (svg) missing.

yep, icons on gnomepanel are missing (humanity .svg).. wallpaper is default one warty.png... SevenMachines pixbuf suggestions seems nice.

edit: i can confirm reinstalling libgdk-pixbuf2.0-0 did the trick

---

### Post by afv on 2011-05-24
I confirm it's update of **librsvg2-2** and **librsvg2-common** that causes the problem.

Reinstalling **libgdk-pixbuf2.0-0** solves the problem.

Bug reported:
[https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/787778](https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/787778)


edit:

This seems to be solved after the last update of libgdk-pixbuf2.0-0:

> 
gdk-pixbuf (2.23.3-0ubuntu3) oneiric; urgency=low

 * libgdk-pixbuf2.0-0.postinst.in: use the correct multiarch directory


Downgraded librsvg2, upgraded libgdk-pixbuf2.0-0 and then librsvg2 and couldn't replicate the problem this time. :)

-

---

### Post by Quackers on 2011-05-24
Hmm, I ran the updates but it didn't solve my issues (the main one being that I had no gnome-shell option at login. I also installed librsvg2-bin (as recommended when right-clicking on librsvg2-2 and logged out and back in.
Now logging in to something called GNOME actually starts gnome-shell. Everything is back to normal here, including evolution :-)

On login I now also get the "Ubuntu" option, which if I try it, gives me a Unity session, but with dodgy looking top panel text and icons. Just like Unity on my other install :-)

Actually there is now a slight difference in appearance. I resized the icons under the Applications tab in Activities and those icons have now reverted to original size.

---

### Post by Harry33 on 2011-05-25
> **Quackers said:**
> Hmm, I ran the updates but it didn't solve my issues (the main one being that I had no gnome-shell option at login. I also installed librsvg2-bin (as recommended when right-clicking on librsvg2-2 and logged out and back in.
Now logging in to something called GNOME actually starts gnome-shell. Everything is back to normal here, including evolution :-)

On login I now also get the "Ubuntu" option, which if I try it, gives me a Unity session, but with dodgy looking top panel text and icons. Just like Unity on my other install :-)

Actually there is now a slight difference in appearance. I resized the icons under the Applications tab in Activities and those icons have now reverted to original size.

Yes this is the way it goes:
1) Session Ubuntu => Unity (with Unity2D fallback)
2) Session Gnome => Gnome-shell (with Gnome-panel3 fallback, if gnome-panel GTK+3 is installed)
3) Session Ubuntu Classic => Ubuntu Classic (only if gnome-session-fallback is installed)

---

### Post by Quackers on 2011-05-25
I've got one missing then :-)  At login screen I'm getting

GNOME - which boots gnome-shell
Recovery Console - which just opens a terminal window on the login screen background
Ubuntu - which boots Unity (with dodgily rendered fonts/icons in the panel)
User Defined Session - which boots gnome-shell

EDIT
I installed gnome-session-fallback and I now get another entry at login

GNOME Classic - which boots to the classic desktop with dodgily rendered panel icons/text and the error message below (but I obviously do have the Nvidia drivers loaded)

---

### Post by Harry33 on 2011-05-25
Although I do not experience any issues with the latest (2.34.0-0ubuntu4) librsvg packages,
I still get an error during the installation (upgrading) process:
```
Postinstallation script error, error on configuring librsvg2-common.
```

I get the same error when I upgrade the package set gdk-pixbuf (2.23.3-0ubuntu3).

---

