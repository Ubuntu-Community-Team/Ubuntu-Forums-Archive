---
title: "Ultimate Edition"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by at2smithjason on 2008-08-31
I was stumbling around the internet and I came across Ultimate Ubuntu 1.7 through 1.9.  I started to download the 1.9 edition, but I stopped and thought that it might be wise if I came here and asked if there are people that are using it.  Right now I have 8.04.1 Herdy Heron.  I wanted to try the Ultimate.  Any feedback on this would help me.  Thanks guys and gals.

---

### Post by jerome1232 on 2008-08-31
It just looks like Ubuntu with alot of pre-installed themes, games and apps. Mostly themes.

---

### Post by Bruce M. on 2008-08-31
> **at2smithjason said:**
> Any feedback on this would help me.  Thanks guys and gals.

OK, some feedback ...

Lets see, it is Ubuntu Edgy Eft ... you have Hard Heron.

Going back three version of Ubuntu to get these files:

[LIST]
[*]New theme / splash screen / wallpaper
[*]VCD Gear debian style
[*]Subversion & build tools
[*]Wireless Internet integration
[*]Bluetooth integration
[*]PPP integration
[*]Networking tools
[*]35 Additional fonts
[*]Tons more themes
[*]Repository driven Beryl
[*]New sounds theme
[*]Integrated Custom repository support
[*]All current Updates 158 at time of posting
[*]IPod support
[*]Beagle
[*]Gramps - Genealogy software (thanks poweruser2600)
[*]Legends - Video Game
[*]Kapote - Instant Messenger
[*]Integrated codecs (the good the bad & the ugly)
[*]Mplayer, VLC, Songbird & Amarok players with mp3 support
[*]Mencoder, K9Copy, DeVeDE, DVD Shrink - dvd copying software.
[*]Integrated Nvidia drivers (will work with other cards)
[*]Automatix 2 & Automatix Bleeder (in case you want additional software)
[*]Gaim beta 5 & plugins
[*]GFTP - FTP ClientNew theme / splash screen / wallpaper
[*]VCD Gear debian style
[*]Subversion & build tools
[*]Wireless Internet integration
[*]Bluetooth integration
[*]PPP integration
[*]Networking tools
[*]35 Additional fonts
[*]Tons more themes
[*]Repository driven Beryl
[*]New sounds theme
[*]Integrated Custom repository support
[*]All current Updates 158 at time of posting
[*]IPod support
[*]Beagle
[*]Gramps - Genealogy software (thanks poweruser2600)
[*]Legends - Video Game
[*]Kapote - Instant Messenger
[*]Integrated codecs (the good the bad & the ugly)
[*]Mplayer, VLC, Songbird & Amarok players with mp3 support
[*]Mencoder, K9Copy, DeVeDE, DVD Shrink - dvd copying software.
[*]Integrated Nvidia drivers (will work with other cards)
[*]Automatix 2 & Automatix Bleeder (in case you want additional software)
[*]Gaim beta 5 & plugins
[*]GFTP - FTP Client
[*]KVIrc - IRC Client
[*]Additional Themes, icons, cursors & logins
[*]XSnow
[*]Samba
[*]NFS
[*]EasyTag - MP3 Tag Editor
[*]GDesklets
[*]Inkscape - 2D vector drawing
[*]Screem - HTML Editor
[*]Gambas - Programing environment
[*]QEMU & Kqemu Accelerator - Emulation
[*]Screem - HTML Editor
[*]Avidemux - Avi (divx /xvid) editor
[*]GDesklets - Eyecandy & info
[*]NTFS read / write support
[*]Lamp - web server (Apache2, mysql, PHP5)
[*]phpmyadmin
[*]Azureus - P2P software
[*]MS core Font's and extra fonts
[*]Wine - Windows emulation (always newest version - through repo)
[*]Alien - Allows installation of foriegn packages (RPM, suse etc)
[*]Gobby Team programing software
[*]Ksnapshot - Screen capture software
[*]Google Picasa - Graphic editing software
[*]Frostwire Pro - P2P software
[*]Kolourpaint - Graphic editing software
[*]Qcad - Autocad wannabe
[*]Archive Suite - virtually any archive can be handled.
[*]Ajunta IDE - Programing environment
[*]Bluefish - HTML Editor
[*]Glade - Interface designer
[*]Gtranslator
[*]Bit Tornado - P2P Software
[*]Amule - P2P software
[*]Kino - Flick editor
[*]Audacity - Sound editor
[*]Debian Menu (pdmenu)
[*]Dvdrip - Dvd ripping software
[*]Democracy Player
[*]Listen Media Manager
[*]Steamripper
[*]Ilinux (banshee)
[*]Gnucash - Financial software
[*]Aria - Download manager
[*]Build Essentials and make utility's
[*]Quanta Plus and extras - HTML Editor
[*]Graveman - burning software
[*]New Grub splash screen and animated "very pretty" boot up screen
[*]Bum - Boot-up manager
[*]Sum - Startup manager (newer improved version gtk and terminal based)
[*]Istanbul - Live screen capture
[*]Ghex - Hex editor
[*]Gourmet - Recipe manager
[*]Isomaster - CD / DVD ISO editor
[*]GPHPEdit - PHP Editor
[*]Kino - Clip editor
[*]Aria - Download manager
[*]Democracy - Movie streamer
[*]ClamAV - Anti-virus software
[*]Listen - Media manager
[*]DVD|RIP - Dvd ripping software
[*]Lifrea - RSS feed reader
[*]Brasero - Disc burning tool
[*]X-Chat - IRC Client
[*]QDVDAuthor - DVD authoring software
[/LIST]

Some of which are built in to HH, and some I'll bet you don't really want or need.

Personally I would check the list out and if it looks interesting, get it from Synaptic Package Manager.

You'd end up with you're own personalized "Ultimate Edition" based on the latest version of Ubuntu and without a bunch of programs you don't want.

What you can do now is create a file: **myinstall.sh** that will automatically install all your favorite programs whenever you do a clean install of Ubuntu, like when v8.10 comes out for example:

a sample **myinstall.sh**
```
#!/bin/bash

sudo aptitude install buoh mozilla-mplayer mozilla-plugin-vlc jpilot jpilot-backup jpilot-plugins jppy jppy-jpilot-plugins conky curl lm-sensors ntp ntp-doc gparted thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman homebank aspell-en aspell-es ispell escputil bluefish weblint-perl libxml2-utils vlc preload gimp-help-en nvidia-settings -y
```
Make that executable, back it up to a floppy, and run it when you want.

That's my feedback.  :)

Have a nice day.
Bruce

---

### Post by lovinglinux on 2008-08-31
> **Bruce M. said:**
> What you can do now is create a file: **myinstall.sh** that will automatically install all your favorite programs whenever you do a clean install of Ubuntu, like when v8.10 comes out for example:

a sample **myinstall.sh**
```
#!/bin/bash

sudo aptitude install buoh mozilla-mplayer mozilla-plugin-vlc jpilot jpilot-backup jpilot-plugins jppy jppy-jpilot-plugins conky curl lm-sensors ntp ntp-doc gparted thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman homebank aspell-en aspell-es ispell escputil bluefish weblint-perl libxml2-utils vlc preload gimp-help-en nvidia-settings -y
```

Make that executable, back it up to a floppy, and run it when you want.

Wouldn't be easier to generate the script using Synaptic?

---

### Post by Bruce M. on 2008-08-31
> **lovinglinux said:**
> Wouldn't be easier to generate the script using Synaptic?

I simply included the script as an option for future use.

It has nothing to do with at2smithjason's question though, and I don't want to hijack his thread.

Have a nice day.
Bruce

---

### Post by bobpur on 2008-08-31
I tried the 1.7 version. For the most part, I felt that Ultimate Ubuntu was a venture to see if everything could be installed in Ubuntu and still work. You will do better with a straight Ubuntu install with what you want installed (and working).

---

### Post by fedex1993 on 2008-09-01
i tried ubuntu ultimate edition ecept that it was totally slow and i did not liek it at all. It is for someone who wants everything pretty much.

---

### Post by empty_spaces on 2008-09-01
I am posting this from my laptop running Ultimate Edition 1.8 and I like it. It does include a lot of software, which works for me, but might not be to everyone's liking. It runs just as fast and smooth as plain ubuntu and comes with a really nice dark glossy theme by default.

---

