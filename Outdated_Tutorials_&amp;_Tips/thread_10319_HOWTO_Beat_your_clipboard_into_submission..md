---
title: "HOWTO Beat your clipboard into submission."
date: 2005-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by dare2dreamer on 2005-01-06
Normally, when you copy something in an X application and you close it, the content of the clipboard is lost. This is probably one of the biggest reasons why people keep saying that copy & paste in Linux "doesn't work".

GNOME Clipboard Daemon is a program that keeps the content of your X clipboard in memory, so the clipboard won't get lost even after you close the application you copied from. It's a daemon - it has no GUI. You start it and it'll run in the background and Just Work(tm).

To set this up under Ubuntu:

1. Download binary from [http://members.chello.nl/~h.lai/gnome-clipboard-daemon/](http://members.chello.nl/~h.lai/gnome-clipboard-daemon/)
2. Extract archive
3. sudo cp gnome-clipboard-daemon /usr/bin
4. Computer > Desktop Preferences > Sessions, flip to Startup Programs tab.
5. Add /usr/bin/gnome-clipboard-daemon to startup programs.
6. Log out, saving your session
7. Log back in, enjoy a behaving clipboard.

---

### Post by spartas on 2005-01-06
A godsend!  When I first installed ubuntu in September, I didn't know much about linux at all, (and I didn't know that if you copied something and then closed the app, it would disappear) so this is the savior of my day.  I wish I knew this existed about 2.5 months ago.

---

### Post by dare2dreamer on 2005-01-06
Yeah, I'm secretly hoping some Ubuntu development decision-maker allows this to be added to the default installation.

For the miniscule amount of overhead it needs, this seems like a really beneficial addition that fits right into the Ubuntu "it just works" philosophy.

---

### Post by wolovids on 2005-01-06
I've been using this for a long time now.  It is ESSENTIAL!

Ubuntu should really look into making this into Hoary and starting it up when an xsession starts just like numlockx does.

---

### Post by wallijonn on 2005-01-06
[QUOTE=spartas]I didn't know that if you copied something and then closed the app, it would disappear.[/QUOTE]

:D

I take it you came from the Windows world. :D

Great tip, **dare2dreamer**. 

It's going into my "install-history" log so that I have a step-by-step guide to getting my machine back to a previous state if and when I have to completely rebuild my system. It's now over 300 lines. :D

-Wally

---

### Post by rider343 on 2005-01-06
Great aplication!!!  =D>

---

### Post by Quest-Master on 2005-01-06
This MUST go into the default installation. :D

---

### Post by TravisNewman on 2005-01-06
That's a BRILLIANT idea. I wish I'd been doing that for years.

---

### Post by wallijonn on 2005-01-10
You may need to change the Priority to 60 or 70 when you add it to your startup windows session, otherwise the gnome welcome screen may hang.

---

### Post by dare2dreamer on 2005-01-12
Really? I've had it at priority 50 (default when you add an application to startup session) and its never given me a lick of trouble.

Out of curiousity, what might it conflict with?

---

### Post by piedamaro on 2005-01-12
Yeah, great little app. I'm using it since 2 years.
However it was never included into gnome, cause they need a better overall approach to clipboard monitoring.
Finally with gtk-2.6 a persistent clipboard manager is embedded in the tooltik!

---

### Post by wallijonn on 2005-01-12
[QUOTE=dare2dreamer]Really? I've had it at priority 50 (default when you add an application to startup session) and its never given me a lick of trouble.

Out of curiousity, what might it conflict with?[/QUOTE]

Another "50".

---

### Post by dare2dreamer on 2005-01-12
Always wondered how the priorities worked. Thanks for the heads up before I added something else to my session and blew something up.

I took a look at the rest of the startup apps (in session manager, not the startup tab), and several of them start at 60 and 70. Out of curiousity, what keeps them from conflicting in a similar manner to what you describe?

> Another "50".

---

### Post by jdodson on 2005-01-12
this is great, thanks for the howto.

one question, you mentioned that it has "little" overhead, ok so how little is little?  250k of ram, 10k?  just wondering if anyone knows.  if it is a meg that is hardly little as all those applets in gnome really add up on my system at least.

---

### Post by wallijonn on 2005-01-13
[QUOTE=dare2dreamer]Out of curiousity, what keeps them from conflicting in a similar manner to what you describe?[/QUOTE]

Usually /usr/share/gnome/default.session is before you login. Everything after the login will usually default to 50. (Just login and open Windows Sessions - the list should be very short). If you close all your open programs you'll see how they disappear from the Sessions manager window. Any program you open thereafter will have a "50", whether it is a Root Terminal, RhythmBox, FireFox, The GIMP, OpenOffice, etc. Your manual startup / Sessions startup program should be listed in .gnome2/session-manual. ANyway, for whatever reason I had a hangup when I added 'clipboard-daemon', so I just bumped it up a little and have never had another hang where the gnome-screen fails to close.

---

### Post by _obelix_ on 2005-04-27
[QUOTE=dare2dreamer]Normally, when you copy something in an X application and you close it, the content of the clipboard is lost. This is probably one of the biggest reasons why people keep saying that copy & paste in Linux "doesn't work".

GNOME Clipboard Daemon is a program that keeps the content of your X clipboard in memory, so the clipboard won't get lost even after you close the application you copied from. It's a daemon - it has no GUI. You start it and it'll run in the background and Just Work(tm).

To set this up under Ubuntu:

1. Download binary from [http://members.chello.nl/~h.lai/gnome-clipboard-daemon/](http://members.chello.nl/~h.lai/gnome-clipboard-daemon/)
2. Extract archive
3. sudo cp gnome-clipboard-daemon /usr/bin
4. Computer > Desktop Preferences > Sessions, flip to Startup Programs tab.
5. Add /usr/bin/gnome-clipboard-daemon to startup programs.
6. Log out, saving your session
7. Log back in, enjoy a behaving clipboard.[/QUOTE]

Hi,
i post the tutorial on german Ubuntu Forum. Additionally there i ask howto compile GNOME Clipboard Manager.

A User give a link to Debian Binarys and it works great:

[GNOME Clipboard Manager](http://gcm.sourceforge.net/) 
[German Ubuntu Forum](http://www.ubuntuusers.de/viewtopic.php?p=29636#29636) 
[Debian Packages](http://linux.org.by/debian/pool/main/g/gcm/) 

Before run gcm, please stop gnome-clipboard-daemon.

Regards

Obelix

---

### Post by trash on 2005-05-25
YAY!!
worked on pc but not on mac.. (the binaries that is).

Another vote for making this daemon part of the Ubuntu standard install!!

---

### Post by 1337sithlord on 2006-03-03
w00t tyvm

edit - it works with most apps, but not firefox... oh well, close as i will ever come to a fully functional clipboard ;)

---

### Post by christofer.c.bell on 2006-09-28
> **wallijonn said:**
> It's going into my "install-history" log so that I have a step-by-step guide to getting my machine back to a previous state if and when I have to completely rebuild my system. It's now over 300 lines. :D

-Wally

There's no need to do that.  Once you have a system up and running as you like, do this:

$ dpkg --get-selections > selections-snapshot.`date +%Y%m%d%H%M%S`

(You can store it in any file you like.)

To bring a new system up to par, after installing the OS, transfer that file over and run this:

$ sudo dpkg --set-selections < selections-snapshot.20060928
$ sudo apt-get dselect-upgrade

As you change your installed software over time, you can continue to save "snapshots" of your installed software state and go back to it at any time.

Hope this helps keep your documentation a bit more trim. ;)

---

### Post by bobpaul on 2007-05-29
> **christofer.c.bell said:**
> There's no need to do that.  Once you have a system up and running as you like, do this:
That only gets things installed with dpkg. There's still no *.deb for clipboard-monitor.

> **piedamaro said:**
> Yeah, great little app. I'm using it since 2 years.
However it was never included into gnome, cause they need a better overall approach to clipboard monitoring.
Finally with gtk-2.6 a persistent clipboard manager is embedded in the tooltik!

So... it's been a couple of years and now Fiesty uses gtk-2.10. Any idea when the persistent clipboard will become a reality?

---

