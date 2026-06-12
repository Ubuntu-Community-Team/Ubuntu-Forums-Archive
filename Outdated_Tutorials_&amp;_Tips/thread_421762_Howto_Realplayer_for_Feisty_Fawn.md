---
title: "Howto: Realplayer for Feisty Fawn"
date: 2007-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2007-04-24
I have built a .deb package using Feisty dependences for Realplayer 10 with pbuilder.

[LIST=1]
[*]Download the [Realplayer .deb.package]("http://mikesplanet.net/feisty/realplay/realplay_10.0.8-0ubuntu3_i386.deb")
[*]Install with gdebi or ```
sudo dpkg -i realplay_10.0.8-0ubuntu3_i386.deb
```
[/LIST]

Full sources can be found at [http://mikesplanet.net/feisty/realplay/]("http://mikesplanet.net/feisty/realplay/")

Please let me know if you have any problems with this package.

---

### Post by milad on 2007-04-26
The link is broken

---

### Post by DC@DR on 2007-04-26
Why would we need the .deb file when we can get the .bin file from [http://www.real.com/linux](http://www.real.com/linux) ?

---

### Post by TheMono on 2007-04-26
Why would you use a .bin rather than a .deb? Much easier to remove a .deb, means nothing can interfere with dpkg because dpkg is kept aware, etc. Far better to keep everything under one package system.

---

### Post by Flavian on 2007-04-26
Thanks a lot! Works flawlessly :)
Just a thought: Change the first link and the command line, because you may have happened to rename the files, so they are not accessible through the first link anymore + the command wouldn't work since the files now have a different name :)

---

### Post by Cerberus 81 on 2007-04-26
Nuts... doesn't work for 64-bit.

---

### Post by docomo on 2007-04-30
I can't install.

```
sudo dpkg -i realplay_10.0.8-0ubuntu3~feisty3rdparty_i386.deb 
Selecting previously deselected package realplay.
(Reading database ... 223182 files and directories currently installed.)
Unpacking realplay (from realplay_10.0.8-0ubuntu3~feisty3rdparty_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing realplay_10.0.8-0ubuntu3~feisty3rdparty_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/realplay-10.0.8/plugins/mp4fformat.so')
Errors were encountered while processing:
 realplay_10.0.8-0ubuntu3~feisty3rdparty_i386.deb
```

Update: I used the old package from Edgy instead which works for me:

[http://archive.canonical.com/ubuntu/pool/main/r/realplay/realplay_10.0.8-0ubuntu3_i386.deb](http://archive.canonical.com/ubuntu/pool/main/r/realplay/realplay_10.0.8-0ubuntu3_i386.deb)

---

### Post by galleonway on 2007-04-30
Same problem here as docomo.

---

### Post by greenstar on 2007-05-12
> **Mike said:**
> I have built a .deb package using Feisty dependences for Realplayer 10 with pbuilder.[LIST=1]
[*]Download the [Realplayer .deb.package]("http://mikesplanet.net/feisty/realplay/realplay_10.0.8-0ubuntu3_i386.deb")[/LIST]This link is broken, doesn't work when clicked or right-clicked.

> **Mike said:**
>  Full sources can be found at [http://mikesplanet.net/feisty/realplay/](http://mikesplanet.net/feisty/realplay/) 

Please let me know if you have any problems with this package.

I found that following this link took me to the actual directory that contains the file, where I had no problem downloading it.

Greenstar

---

### Post by aysiu on 2008-03-24
I moved this to Outdated T&T, since the link appears to be dead.

---

