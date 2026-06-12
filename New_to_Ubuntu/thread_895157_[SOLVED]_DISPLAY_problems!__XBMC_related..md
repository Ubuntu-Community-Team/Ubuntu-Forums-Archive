---
title: "[SOLVED] DISPLAY problems!  XBMC related."
date: 2008-08-19
forum: New to Ubuntu
---

### Post by pelle@xburk on 2008-08-19
I'm trying to run XBMC on Ubuntu Hardy Heron 8.04 AMD64.

First I added the necessary repositories using:

```

$ sudo gedit /etc/apt/sources.list

```

Then I installed the AMD64 version using Synaptic.

When I try to launch XBMC from either the menu-bar or the terminal, a black window pops up, then it quickly disappears.  The console says:

```

$ xbmc
Xlib:  extension "XINERAMA" missing on display ":1.0".
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9
Segmentation fault (core dumped)

```

I was reading around on the XBMC forums and found out that the DISPLAY should be set to 0.0 for XBMC to work, so I:

```
$ export DISPLAY=:0.0
```

Cause my DISPLAY was set to 1.0.  The members on the XBMC forum said that it had something to do with dual monitors.  I have a DVI-D to HDMI cable from my computer to my TV, so is that why my DISPLAY was set to 1.0?  Will I be able to run XBMC while I'm using my TV and computer screen as cloned?

Also, after I made the DISPLAY=:0.0, XBMC starts, but it's the wrong resolution for my screen and I only see part of the menu.

[IMG]http://img242.imageshack.us/img242/466/xbmcerrormm7.png[/IMG]

Does anybody know how I can fix this?

---

### Post by biriachan on 2008-08-21
I had the save problem with XBMC using the PPA Hardy Repository.  Changed to the SVN PPA Repository and it fixed the Resolution issues I was having.

[http://xbmc.org/forum/showthread.php?p=185738]("http://xbmc.org/forum/showthread.php?p=185738")

SVN PPA (daily builds)

deb [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) feisty main
deb-src [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) feisty main
deb [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) gutsy main
deb [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) hardy main
deb [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) intrepid main

Hope that helps.

---

### Post by anjilslaire on 2008-08-21
Odd. I'm running th 32bit Hardy. The Hardy PPA version seems to run great. Maybe its a 64bit isues?

I've been running XBMC on my xboxes for years, so I'm thrilled to get it on my PC now :)

---

### Post by pelle@xburk on 2008-08-22
Thank you biriachan!

With a little hassle after adding those repositories, I managed to get it work in a resolution which was smaller than my screen, from which I then could change it to my resolution.

---

