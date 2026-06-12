---
title: "KZenExplorer Package for Creative MP3 players"
date: 2005-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by mstralka on 2005-06-17
I just bought a Creative Zen Micro and wanted to get it working well in Kubuntu.  I tried gnomad2 but it didn't match well with KDE and didn't seem to be very powerful.  So I found [http://kzenexplorer.sourceforge.net](http://kzenexplorer.sourceforge.net), which seems to be more polished and advanced.  Unfortunately it didn't appear in synaptic so I had to build it from scratch.  

The build process wasn't too bad.  Running ./configure gave friendly error messages when it couldn't find a dependency and I just had to use synaptic and google to track them down.  

After tracking down and installing a ton of required development libraries, I installed it with [http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/) and it built and installed the .deb package for me.  

I'm providing the package here, although I have no idea if there is a better way to provide this file, nor can I guarantee it will work for anyone else.  I hope this helps some of you out there.

Mark

---

### Post by spacemonkey on 2005-06-18
I tried to compile from source, but I'm running gnome, with just enough KDE installed to run KDE programs, and I couldn't compile.  configure gave me an error.  But your .deb package worked great for me.  So far I like it a lot better than gnomad2.  Smart playlists and syncing seems nice.  Thanks for the tip.

Oh, also, I'm using a Dell DJ20, so far everything works normally.

EDIT:  Well I spoke to soon, I can't seem to figure out how to get syncing to work, nor can I figure out how to transfer individual tracks to the jukebox.  The playlists work fine, but other than that....I'm lost.

---

### Post by mstralka on 2005-06-18
I found out that gnomad2 doesn't have synchronization.  I'm trying to build nomadsync but it's not easy.  If anyone has built a .deb of  nomadsync please post it.

EDIT:
I successfully built nomadsync as a .deb with checkinstall and it works!! I can now auto-sync to my Zen Micro!
See attached

---

### Post by spacemonkey on 2005-06-18
I'll have to give that a shot, but I was referring to the sync button in KZenExplorer.  It doesn't seem to do anything for me.

EDIT:
nomadsync worked great.  I didn't even try to compile it, I just used your package, and it ran just fine.  I really like the program, finally, an easy way to update track info without having to remove and re-add the entire track.  I also really like how it tells you exactly what it's going to do before it does it, unlike MusicMatch, which always gave me problems when syncing.

Thanks for the tips.

---

### Post by hammett111 on 2005-06-18
I assessed your package on AMD64 and unfortunately it doesn't work. The installation proceeds perfectly, with desktop links and all, however the terminal output shows this >>

quentin@andromeda:/usr/bin$ kzenexplorer
kzenexplorer: error while loading shared libraries: libkutils.so.1: cannot open shared object file: No such file or directory

I am in the process of finishing a Kubuntu HOW TO, and this would be a welcome edition. libkutils.so.1, actually symlinks to libkutils.so.1.2 in /usr/libs, where both reside. Symlinking to libkutils.so.1 does not work, neither does symlinking to libkutils.so.1.2 with symlinks named libkutils.so.1. I was going to extract a redhat AMD64 version of kzenexplorer and recompile it for Kubuntu, but as with all good things, they take time.

Any hints on the libkutils problem though?
Cheers

OH BTW >> Can't uninstall your package, its not showing up in kynaptic/synaptic and dpkg -r "program" only works with debs recognized on the system.

---

### Post by mstralka on 2005-06-18
Sorry, but I don't know all that much about building packages - I just followed the directions in the INSTALL file from  [http://kzenexplorer.sf.net](http://kzenexplorer.sf.net) and used checkinstall to make a package.  

About it not working on AMD64, I think it probably has to be rebuilt from scratch for a different processor type. and I didn't have problems with libkutils.  I can uninstall it in Synaptic on my system.

---

### Post by hammett111 on 2005-06-18
Any hints on where the pointer is that links the kzenexplorer executable to libkutils.so.1?

Doing an AMD64 repackage today, will post the working .deb on the forums.

---

### Post by hammett111 on 2005-06-18
Hey can you give me some info, can you tell me where on your system libkutils.so.1 is stored.

And are they in the 32bit or 64bit libs

Cheers

---

### Post by mstralka on 2005-06-18
On my system it's in /usr/lib

```

/usr/lib/libkutils.so.1.2.0
/usr/lib/libkutils.so.1
/usr/lib/libkutils.so

```

---

### Post by hammett111 on 2005-06-18
Are yours 32 or 64 bit libs?

---

### Post by xalphas on 2005-06-19
[QUOTE=mstralka]On my system it's in /usr/lib

```

/usr/lib/libkutils.so.1.2.0
/usr/lib/libkutils.so.1
/usr/lib/libkutils.so

```[/QUOTE]

I've tried your .deb thx.. But didn't work cause only gnome here. It needs exact kde libs. So for only gnome users can't use this package. 

Thx for sharing

---

### Post by mstralka on 2005-06-19
[QUOTE=hammett111]Are yours 32 or 64 bit libs?[/QUOTE]

32 bit libs

---

### Post by hammett111 on 2005-07-06
I tossed it and built gnomad. It works cool. I wish amarok would do a zen plugin, then it would cream everyone

---

### Post by steffen on 2005-07-07
I've tried both the KZenexplorer and the Nomadsync. Both gives me this error:
> nomadsync: error while loading shared libraries: libnjb.so.4: cannot open shared object file: No such file or directory

Anyone know why?

I have all KDE libs installed, and running Amarok and K3B smoothly.

---

### Post by steffen on 2005-07-07
This posting gave a few hints: [http://ubuntuforums.org/showthread.php?t=2700&page=2&pp=20](http://ubuntuforums.org/showthread.php?t=2700&page=2&pp=20)

I installed the compiled package from this forum.

However, when I run:
> sudo echo /usr/local/lib >> /etc/ld.so.conf
I get > bash: /etc/ld.so.conf: Ikke tilgang (Not allowed)


Why not?

---

