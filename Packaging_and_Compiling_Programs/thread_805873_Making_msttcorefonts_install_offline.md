---
title: "Making msttcorefonts install offline"
date: 2008-05-24
forum: Packaging and Compiling Programs
---

### Post by cutout33 on 2008-05-24
Hello All.

Am trying to workaround msttcorefonts package and make install offline...
is this possible, if yes then how???

Thanks in advance.:)

---

### Post by kostkon on 2008-05-24
You can use [*APTonCD*]("http://aptoncd.sourceforge.net/") to download the package from an *Ubuntu* machine or [*Wubdepends*]("http://wubdepends.sourceforge.net/") to do it from a *Windows* one.

---

### Post by cutout33 on 2008-05-24
OK thanks this is I know but it doesn't work when you try to install it becase it needs to connect to the internet for configuration or something...
The idea is how to prevent it from connecting to internet???

---

### Post by narcisgarcia on 2011-02-04
Somebody has packaged a "msttcorefonts-offline", downloadable here:

[http://imaginux.com/repos/](http://imaginux.com/repos/)

---

### Post by gmargo on 2011-02-04
How to prevent the corefonts installer from downloading from the net:

1. Download the fonts manually and save them somewhere. Source: [http://sourceforge.net/projects/corefonts/files/the%20fonts/final/](http://sourceforge.net/projects/corefonts/files/the%20fonts/final/)

2. Run aptitude (or apt-get) with special option.  You will be prompted for the directory containing the downloaded fonts.
```

$ sudo aptitude -V -o DPkg::Pre-Install-Pkgs::="dpkg-preconfigure --apt --priority=low;" install ttf-mscorefonts-installer

```

---

