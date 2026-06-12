---
title: "Need a good distro for this old comp"
date: 2007-01-01
forum: Other OS Talk
---

### Post by Zanwar000 on 2007-01-01
I want a good lightweight distro like Zenwalk linux in that it is good for multimedia and programming, as I won't use it to connect to the internet. 

96MB RAM.
7GB of space on the partition I am installing it to
Pentium II
Intel MMX

Thanks for any help.

---

### Post by meng on 2007-01-01
I think Zenwalk would be okay, also Xubuntu as it is also Xfce based. If you wanted it to be even faster, use something even more lightweight like fluxbox or icewm. Damn Small, Feather, Puppy Linux are reasonable options.

---

### Post by RAV TUX on 2007-01-02
I suggest [GeeXboX]("http://geexbox.org/en/index.html")


[Built-in Packages]("http://geexbox.org/en/packages.html")


> **What is GeeXboX ?**

                    GeeXboX is a free embedded Linux distribution which aims at         turning your computer into a so called HTPC (Home Theater PC)         or Media Center. Being a standalone LiveCD-based distribution,         it's a ready to boot operating system than works on any         Pentium-class x86 computer or PowerPC Macintosh, implying no software         requirement. You can even use it on a diskless computer, the         whole system being loaded in RAM.         
            
        Despite his tiny ISO image size, the distribution comes with a         complete and automatic hardware detection, not requiring any         driver to be added. It supports playback of nearly any kind of         audio/video and image files and all known codecs and         containers are shipped in, allowing playing them through         various physical supports, either being CD, DVD, HDD, LAN or         Internet.         
            
        GeeXboX also comes with a complete toolchain that allows         developers adding easily extra packages and features but that         might also be used to give birth to many dedicated embedded         Linux systems.       
           **                                         GeeXboX 2.x technological preview:         what a surprise !           (12/31/2006)         **

                    Xmas passed away and no new GeeXboX release came out this         year. It's a bit sad but we were focusing on next generation         architecture which delayed a bit the 1.x serie development.         You may however expect some 1.1 release any time soon, with         it's usual set of improvements. Time has come now to let you         discover our very first technological preview of GeeXboX 2.x         series.
        
        Some of you may have heard about MPUI years ago, or         OMC/libplayer a bit earlier this year but both approaches went         down. The decision has been taken to make use of Freevo 2.0         (still work in progress, but so is GeeXboX 2.x) and Kaa, its         multimedia framework as our new UI reference. As a consequence,         many new packages had to be added (such as Python) to our         distribution. In a near future, GeeXboX and Freevo projects         will be more tighten than ever, and we should be the official         Freevo LiveCD, still keeping in mind our embedded and         easy-to-setup approach. Unfortunately, ISO grew up radically         (it is now 20 MB) and so does RAM usage (at least 128MB is now         mandatory). But, as a development version, don't take it too         seriously, it'll still change 'till the final release. If you         want to have a try at this technological preview, just grab the              [               **GeeXboX 2.x 2006-12-31**             ]("http://www.geexbox.org/%7Eben/v2/geexbox-sherkhan-20061231-en.i386.iso")    ISO and burn it to a         CD or try it through VMware or so. Don't look for a generator         or try to install it on disk, it is not yet meant for. Don't         expect it either to be fully functional, it's still full of         bugs and isn't meant to replace the official 1.x serie anytime         soon. Right now, it can be controlled through keyboard only         (arrow keys and Enter/Escape) but should already be able to         let you watch some videos, play audio files or view various         pictures. Well, that's said, here are some screenshots, just         for you to know what to expect from 2007 ;-)
        
                    [         [IMG]http://geexbox.org/img/freevo-scr-menu-thumb.png[/IMG]       ]("http://geexbox.org/img/freevo-scr-menu.png")       [         [IMG]http://geexbox.org/img/freevo-scr-video-thumb.png[/IMG]       ]("http://geexbox.org/img/freevo-scr-video.png")       [         [IMG]http://geexbox.org/img/freevo-scr-audio-thumb.png[/IMG]       ]("http://geexbox.org/img/freevo-scr-audio.png")       [         [IMG]http://geexbox.org/img/freevo-scr-image-thumb.png[/IMG]       ]("http://geexbox.org/img/freevo-scr-image.png")     
            
        Happy new year from all the GeeXboX team members ...       
           **                                         GeeXboX 1.0: 'As foretold by Nostradamus' edition (posted by Ben)           (06/22/2006)         **

            Here we finally are ... after more than 3 years of perpetual development, GeeXboX finally reaches its so long awaited 1.0 release. Many of you were waiting for it and this is probably the best edition of GeeXboX that you've ever had. We've spent so much time in the last few months to fix all the bugs that we can, so that you'll be forced to enjoy it ;-) At the time Aurel and myself started working on GeeXboX, none of us would have expected our software to become that famous. I'm really glad that this version finally came out and I really really want to thank from the depths of my heart all the people of our development team who are getting involved in GeeXboX everyday. None of this would ever have been possible without the work you've all done on it. I'd also like to thank all users that trusted us and are now using our software in a daily manner. You are the ones who made it possible. So for now, I hope you'll all enjoy our 1.0 release, we all did our very best on it, and we're on the road to 2.0.
      
So, what can you expect from this final 1.0 release ? Well, so many things have changed, been added or simply fixed. The most noticeable thing probably is the support for DVD menus, this feature that had been requested so many times by so many people and that was unfortunately missing from MPlayer is now part of GeeXboX. A lot of work also has been done for playing back network streams from SHOUTcast WebRadios, WebTVs or even RTP/RTSP streaming so that you should now be able to easily watch any kind of network or broadcasted stream from your GeeXboX media center. The overall hardware support for various DVB cards, sound cards and video display adapters has also been improved. You're now also able to see all metadata information and properties (like Codecs, resolution or ID3 tags) from your multimedia files. The easiest way to tell you the changes is probably for you to read the concise version of our changelog.
      
**Detailed Changelog (relative to 0.98.7 release) :**             

**System:**             
- Updated linux to version 2.6.16.17.
- Updated BusyBox to 1.1.3.
- Updated uClibc to 2006.05.05 snapshot.
- Updated udev to version 0.92.

**Toolchain:**             
- Introduced GCC 4.1.1 as the new compiler.
- Support for C++ in the toolchain.
- All packages are now built with big files support flag.
- Added support for non-free binary firmwares at sources build.

**Player:**             
- Updated MPlayer to 1.0pre8.
- DVD Navigation Menus support.
- SHOUTcast and Netstream support (with content filtering on adult/subscription-only streams).
- Support for LIVE555 library (RTP/RTSP/SIP streaming) which provides FreeboxTV support for French people using the Free ISP.
- Use mp3-lib instead of FFMpeg to avoid audible glitches while seeking.
- Fix MPlayer's bug which prevents AVI files with ODML index (99% of XviD files) to be read when idx=yes (default).
- Fix sound/subtitles issues while playing MPEG-TS streams.
- Support for multichannel AAC in MOV files.
- Playback of IFO files (DVD disc ripped on HDD for example) now works as expected.
- Set minimal cache size (5% of cache) to start playback of file very quickly.
- Fix TV channel OSD name generation with spaces in their name.
- Allows RTSP client's port forcing (for FreeboxTV users in router mode for example).
- Added support for DVD-RAM MPEG files.

**Menu:**             
- Brand new menu item selection display (now with alpha layer).
- Added new menu that displays streams A/V properties.
- Allows metadata retrieval from MP3/OGG/FLAC audio files.
- Properties menu auto-opens and updates on audio-only media.
- Prevent user from browsing (and getting lost) in /
- Display NIC's MAC address into information menu.
- Display CDROM size.
- Fixed display of disks partition size and freespace.
- Added release number information.

**Audio:**             
- Update ALSA library and utilities to version v1.0.11.
- Added a lot of fixes for audio playback.

**Video:**             
- Added support for different resolutions to be used through generator.
- Support for VESA with Intel i865, i910 and i915 chipsets.

**Drivers:**             
- Added support for Serial ATA CDROM drives.
- Added support for ATAPI/IDE ZIP/LS120 drives.
- Added support for PcCard (32bits CardBus only, not 16bits PCMCIA).
- Added LCD displays support through LCD4Linux.
- Added support for most of the Gigabit NICs.
- Fix support of Nova DVB-S+ card.
- Updated LIRC to v0.8.0.
- Updated rt2400/rt2500 drivers to CVS 05.09.2006.
- Fix em8300 driver and firmware loading issues.

**Networking:**             
- Updated djmount to version 0.53 (files are no more represented as playlist).
- Fixed bftpd FTP server write access error.
- Updated bftpd to version 1.4, and included fix for file transfers greater than 2GB.
- Update wireless tools to version 28.

**Generator:**             
- Updated generator tools for MacOS X (support for MacIntel x86 OSX 10.4).
- Allow you to choose between multiple themes.
- Option for DVD Navigation menus to select it as a default or not.
- Option for autoplay to select it as a default or not.
- Option for SHOUTcast (radio and tv netstreams).
- Tab for video settings configuration (resolution, color depth and boot splash)
- Tab for support of LCD displays.

**Miscellaneous:**             
- Fixed zoomed scrolling in FBI image viewer.
- Support for Microsoft Media Center Edition USB, StreamZap, Twinhan DTV, Toshiba VT76F and ATI Remote Wonder II remotes.
- Implemented full Digimatrix hardware support (apart from panel buttons).
- Allow multiple resolutions in themes.
- Support for VMware and QEMU (usefull for test purpose).

      GeeXboX 1.0 is available [here]("http://geexbox.org/en/downloads.html") and right now!       
                                   
                                **Styles**
[LIST]
[*]             [DeepBlue]("http://geexbox.org/en/index.html#")
[*]             [Console]("http://geexbox.org/en/index.html#")[/LIST]       © 2002 - 2007, GeeXboX Team :
 [http://geexbox.org/en/index.html](http://geexbox.org/en/index.html)

---

### Post by RAV TUX on 2007-01-02
> **Downloads ...**

           **                                         GeeXboX ISO**

                                                    [IMG]http://geexbox.org/img/dl-trans.png[/IMG]               
                GeeXboX ISOs are ready-to-burn disc images containing the bootable GeeXboX Operating System for multimedia entertainment. Pre-made ISO images are currently available in English or French for both i386 (PC) and PowerPC (Macinstosh) computers. Other languages are available with the ISO generator. The installer software is included in the ISO. 
             
                                   **GeeXboX 1.0 English Edition for i386 (PC)**                 English ISO for i386 (PC) computers is available from the following locations :
                  **Size:** 6.8 MB - **md5sum:** b72c0bc20ec3dacf058e9f4e9e9b9eff - **sha1sum:** cc6d8cd7e448e4dd482e78768f77bbe258474c73
                        [GeeXboX.org, Dublin (Ireland, HTTP)]("http://www1.geexbox.org/releases/1.0/geexbox-1.0-en.i386.iso")                     
                                              [Free / ProXad.net, Paris (France, FTP)]("ftp://ftp.proxad.net/pub/Distributions_Linux/GeeXboX/releases/1.0/geexbox-1.0-en.i386.iso")                     
                                              [Zyrianes.net, Paris (France, HTTP)]("http://www2.geexbox.org/releases/1.0/geexbox-1.0-en.i386.iso")                     
                                              [RelouFR Networks, Paris (France, HTTP)]("http://geexbox.reloumirrors.net/releases/1.0/geexbox-1.0-en.i386.iso")                     
                                              [Mirrorgeek.com, Austin (Texas, USA, HTTP)]("http://geexbox.mirrorgeek.com/releases/1.0/geexbox-1.0-en.i386.iso")                     
                                              [German Service Network, Oberhausen (Germany, HTTP)]("http://mirror.gsnw.org/geexbox.org/releases/1.0/geexbox-1.0-en.i386.iso")                     
                   
                   
                                **GeeXboX 1.0 French Edition for i386 (PC)**                 French ISO for i386 (PC) computers is available from the following locations :
                  **Size:** 6.8 MB - **md5sum:** c103ee461f37a448c89ebc8aeb8d5839 - **sha1sum:** 362e2ab0ccb3eee83b28a2531eabccdd055094be
 [ GeeXboX.org, Dublin (Ireland, HTTP)]("http://www1.geexbox.org/releases/1.0/geexbox-1.0-fr.i386.iso")                     
                                              [Free / ProXad.net, Paris (France, FTP)]("ftp://ftp.proxad.net/pub/Distributions_Linux/GeeXboX/releases/1.0/geexbox-1.0-fr.i386.iso")                     
                                              [Zyrianes.net, Paris (France, HTTP)]("http://www2.geexbox.org/releases/1.0/geexbox-1.0-fr.i386.iso")                     
                                              [RelouFR Networks, Paris (France, HTTP)]("http://geexbox.reloumirrors.net/releases/1.0/geexbox-1.0-fr.i386.iso")                     
                                              [Mirrorgeek.com, Austin (Texas, USA, HTTP)]("http://geexbox.mirrorgeek.com/releases/1.0/geexbox-1.0-fr.i386.iso")                     
                                              [German Service Network, Oberhausen (Germany, HTTP)]("http://mirror.gsnw.org/geexbox.org/releases/1.0/geexbox-1.0-fr.i386.iso")

                                **GeeXboX 1.0 English Edition for PowerPC**                 English ISO for PowerPC computers is available from the following locations :
                  **Size:** 11.6 MB - **md5sum:** ed9845e6893866e8eb778d86e099381e - **sha1sum:** 666b259410e026edbde57fe1c8ccf7e7fb4e51ba
                        [GeeXboX.org, Dublin (Ireland, HTTP)]("http://www1.geexbox.org/releases/1.0/geexbox-1.0-en.ppc.iso")                     
                                              [Free / ProXad.net, Paris (France, FTP)]("ftp://ftp.proxad.net/pub/Distributions_Linux/GeeXboX/releases/1.0/geexbox-1.0-en.ppc.iso")                     
                                              [Zyrianes.net, Paris (France, HTTP)]("http://www2.geexbox.org/releases/1.0/geexbox-1.0-en.ppc.iso")                     
                                              [RelouFR Networks, Paris (France, HTTP)]("http://geexbox.reloumirrors.net/releases/1.0/geexbox-1.0-en.ppc.iso")                     
                                              [Mirrorgeek.com, Austin (Texas, USA, HTTP)]("http://geexbox.mirrorgeek.com/releases/1.0/geexbox-1.0-en.ppc.iso")                     
                                              [German Service Network, Oberhausen (Germany, HTTP)]("http://mirror.gsnw.org/geexbox.org/releases/1.0/geexbox-1.0-en.ppc.iso")                     
                     
                                **GeeXboX 1.0 French Edition for PowerPC**

[http://geexbox.org/en/downloads.html](http://geexbox.org/en/downloads.html)                 French ISO for PowerPC computers is available from the following locations :
                  **Size:** 11.6 MB - **md5sum:** 3b570cb18691880c558c54fe6fc4e881 - **sha1sum:** de118e7820e9135ca6e34655254544292bd450d6
                        [GeeXboX.org, Dublin (Ireland, HTTP)]("http://www1.geexbox.org/releases/1.0/geexbox-1.0-fr.ppc.iso")                     
                                              [Free / ProXad.net, Paris (France, FTP)]("ftp://ftp.proxad.net/pub/Distributions_Linux/GeeXboX/releases/1.0/geexbox-1.0-fr.ppc.iso")                     
                                              [Zyrianes.net, Paris (France, HTTP)]("http://www2.geexbox.org/releases/1.0/geexbox-1.0-fr.ppc.iso")                     
                                              [RelouFR Networks, Paris (France, HTTP)]("http://geexbox.reloumirrors.net/releases/1.0/geexbox-1.0-fr.ppc.iso")                     
                                              [Mirrorgeek.com, Austin (Texas, USA, HTTP)]("http://geexbox.mirrorgeek.com/releases/1.0/geexbox-1.0-fr.ppc.iso")                     
                                              [German Service Network, Oberhausen (Germany, HTTP) ]("http://mirror.gsnw.org/geexbox.org/releases/1.0/geexbox-1.0-fr.ppc.iso")[U]
[http://geexbox.org/en/downloads.html](http://geexbox.org/en/downloads.html)

[/U]

---

### Post by K.Mandla on 2007-01-02
I've been using Openbox on Ubuntu 6.10 on a P2-300 for my mom to surf the Internet with. It's a little sluggish; something lighter than Ubuntu would do better.

[SLAX]("http://www.slax.org/") might interest you. Or maybe [Fluxbuntu]("http://www.fluxbuntu.org"), which is coming along nicely.

---

### Post by fakie_flip on 2007-04-15
How about Damn Small Linux or DSL-n? There is also Feather Linux.

---

### Post by darksong on 2007-04-15
I got Debian running well on an old PC similar to yours. It had 128mb of ram though but an old crix prosessor.

I had gnome running at a very reasonable speed, it was prefectly usable. I would give debian a try =)

---

### Post by energiya on 2007-04-18
You could try Zenwalk. It's XFCE based and really fast. You can then install openbox or whatever.

---

### Post by fakie_flip on 2007-04-18
Damn Small Linux is made to run on old computers with little resources. Most of the time I was running it, it was only consuming 35 mb of ram. If you have 128 mb of ram, then you can use the toram boot option which loads the entire os into memory and makes it super fast. It's able to load itself into memory because it's Damn Small. I also heard good things about Feather Linux running on older PCs, and you may like DSL-n better than DSL. Fluxbuntu is also worth looking into, but if you prefer XFCE over Fluxbox, then use Xubuntu.

---

### Post by peterthewolf on 2008-12-06
Suggest Debris Linux which is based on hardy repos.

---

### Post by Bungo Pony on 2008-12-06
This thread is old, and I didn't like GeexBox

---

### Post by wecaoniddmabb789 on 2008-12-08
i always saw a guy selling [runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php) .but dont know if my account will be banned when i bought?

---

