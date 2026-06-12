---
title: "Building Nvu from source"
date: 2005-07-06
forum: Programming Talk
---

### Post by Dogmeat on 2005-07-06
Hi, I'm trying to build Nvu from source, as it currently doesn't support SFTP. After struggling a few days trying to configure a SSH FTP tunnel (I must have tried everything but the correct way of doing things), I gave up and thought implementing SFTP support in Nvu myself would be easier :razz: 

So I tried to compile its source, but I'm having a few problems to which I haven't found a solution anywhere.

The first one was xprintutils complaining /usr/include/X11/extensions/Print.h didn't exist. This one I solved by disabling xprint (couldn't find its dev package). Now it's complaining it can't find Xrender.h on the same folder, and I can't disable this one.

My guess is I'm missing a X11 extensions dev package or something. Does anyone know what is it called? Also if you managed to compile Nvu from source please tell me what else I need, thanks!

---

### Post by gil-galad on 2005-07-06
If you go to this [site](http://packages.ubuntu.com/) you can find out what packages have what files.  

By searching for Print.h, I think libxp-dev is what you are looking for.
Xrender.h = libxrender-dev

---

### Post by Dogmeat on 2005-07-06
I didn't know about that site, :grin: i bet that it will make all my i-wonder-what-that-file's-package-is-when-there's-no-INSTALL-file kind of woes extinct! Thanks a lot  :)

---

### Post by Dogmeat on 2005-07-06
... or so I thought! That's odd, I had libxrender-dev and it has no Xrender.h  :-?! Only render.h ... i tried creating a symlink but xft.h complains:

```
In file included from nsDeviceContextGTK.cpp:78:
/usr/X11R6/include/X11/Xft/Xft.h:76: error: 'XRenderColor' is used as a type,
   but is not defined as a type.
```

When i try getting libxrender-dev ubuntu says its the latest version, but it doesn't have Xrender.h like Ubuntu Packages says... what's going on?

---

### Post by gil-galad on 2005-07-06
Strange.  I have Xrender.h installed, and its from libxrender-dev.  

/usr/X11R6/include/X11/extensions/Xrender.h

 :-?

---

### Post by Dogmeat on 2005-07-06
I don't. I read around a bit and I guess its needed for XFree86 fonts or something. Are you using XFree86? I'm using Xorg, maybe thats where the problem is? I had that library installed automatically by Ubuntu because a lot of stuff depends on it, and I can't remove and reinstall it without breaking lots of things. I disabled XFT but now I get this error:

```
../../dist/lib/libneckobase_s.a: member ../../dist/lib/libneckobase_s.a(nsURLHelper.o) in archive is not an object
collect2: ld returned 1 exit status

```

Come on surely someone must have built NVU from source successfully ??  ](*,)  ](*,)  ](*,)

---

### Post by lamborghiniwang on 2007-01-30
Was anyone able to add sftp feature to Nvu? The web server I'm using only supports sftp.:(

---

