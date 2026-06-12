---
title: "DLNA Client"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-08-24
As many of you may or not know many new Televisions and Blu-Ray DVD players, as well as a whole raft of other set-top devices have a built-in [DLNA]("http://www.dlna.org/digital_living/how_it_works/") client. Mediatomb, a dlna server, has been available for several releases, but I've never had much luck with it, as it keeps segfaulting on me. One of the new packages available for Oneiric only is minidlna, an easy to setup dlna server. I took less than 5 minutes to set it up, but now comes the problem. The only two clients I've found are Totem, and XBMC. I can get XBMC to work with the server, but the plugin needed for Totem never shows up in the plugin registry. The problem with XBMC is that I have to log out, then log into an XBMC session, this can be a bit of a hassle when setting up the directory structure, so I wanted to use Totem for my experimentation.

 I've installed python-coherence and totem-plugins-extra, but no joy. Has anyone else tried this yet? 

This system is a bit of a mess as far as the installation goes, so I'm going to install the plugin on another system to see if it works there, before I create a bug report.

---

### Post by cariboo on 2011-08-24
Updating my own thread, Tony Mugan, had already reported the problem. Bug #[lpbug]827382[/lpbug].

---

### Post by meborc on 2011-08-25
I have used minidlna since I got my nice 50'' plasma :)

It used to work fine in 10.10 and 11.04 (I used the sourceforge files for minidlna) but in 11.10 (the repo version) even with the same exact configuration file, the TV does not find any files on my computer. It sees that minidlna is working and it recognizes the device, but not the files.

So I expect there is a regression in minidlna itself :(

---

### Post by SevenMachines on 2011-08-25
The coherence stuff in the totem packaging is disabled, I'm guessing because trying to build totem with it enabled gives
```
configure:20181: WARNING: the coherence_upnp plugin uses PyGTK and conflicts with the new pygobject bindings (disabling plugin)

```So its not built

---

### Post by ronacc on 2011-08-25
> **meborc said:**
> I have used minidlna since I got my nice 50'' plasma :)

It used to work fine in 10.10 and 11.04 (I used the sourceforge files for minidlna) but in 11.10 (the repo version) even with the same exact configuration file, the TV does not find any files on my computer. It sees that minidlna is working and it recognizes the device, but not the files.

So I expect there is a regression in minidlna itself :(

as much as I love linux ,after 2 years of fighting twinview I gave up and bought a mac mini ( my first apple ) for that job , it just worked .

---

### Post by seeker5528 on 2011-08-29
> **meborc said:**
> It used to work fine in 10.10 and 11.04 (I used the sourceforge files for minidlna) but in 11.10 (the repo version) even with the same exact configuration file, the TV does not find any files on my computer. It sees that minidlna is working and it recognizes the device, but not the files.

I see the same thing in Debian attempting to use VLC as the client, VLC sees the stuff MythTV is sharing. VLC only seems to show the UPnP option on the playlist view.

Tried using Rygel, but VLC doesn't see it. I think another machine in my house with Windows 7 sees Rygel, when I view the network on the windows machine I see something from my machine broadcasting it's availability, which when clicked opens Windows media player and I can play music.

Later, Seeker

---

### Post by xeizo on 2011-08-29
Minidlna works fine here, in latest Oneiric, my Sony blu-ray player play everything wireless except FLAC and very large movie files( >~2GB in size).

My other computers with XBMC plays everything, including FLAC and very large movie files.

XBMC seems to be the best dlna client as far as I've found out.

---

### Post by vassie on 2011-09-08
> **meborc said:**
> I have used minidlna since I got my nice 50'' plasma :)

It used to work fine in 10.10 and 11.04 (I used the sourceforge files for minidlna) but in 11.10 (the repo version) even with the same exact configuration file, the TV does not find any files on my computer. It sees that minidlna is working and it recognizes the device, but not the files.

So I expect there is a regression in minidlna itself :(

I have the same problem, I'm guessing that the minidlna process is running as a user that does not have access to my home directory

Using the sourceforge version works perfectly, however I'd rather use the repo version as it also downloads all the codec dependencies

Ben

---

