---
title: "trouble installing ffmpeg on lucid - Couldn't find package libva-dev"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by randall4 on 2014-02-22
I have a EC2 instance (made with turnkeylinux but that is probably not an issue) running 

Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid


and trying to install ffmpeg using [https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) after issuing the first block to install dependencies I get 
E: Couldn't find package libva-dev

Can someone please help?  I'm fairly new to Ubuntu administrative

thank you in advance.

---

### Post by Bashing-om on 2014-02-22
randall4; Hi !

Release 10.04 for the desktop has reached End Of Life and is no longer supported. As such, the repository is no longer.
May I highly suggest that you upgrade/install a current version ? The current Long Term Support release is version 12.04 and the latest release is version 13.10.
An on-line upgrade is not recommended in this instance, too much has changed since version 10.04.
For ubuntu:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

And for older hardware:
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT][INDENT]we are here to 
[INDENT][INDENT][INDENT]help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by randall4 on 2014-02-22
thanks....

---

### Post by Bashing-om on 2014-02-22
randall4;

No problem, let us know how it goes.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by coldcritter64 on 2014-02-22
I fully agree with Bashing-om regarding using an up to date release (better support). 

It is however possible to change repositories from archive.ubuntu.com to old-releases.ubuntu.com to continue with Lucid (though not a particularly wise idea wrt security etc).

For libva-dev, I could download it from here...[http://www.ubuntuupdates.org/package/lucidbleed/lucid/main/base/libva-dev](http://www.ubuntuupdates.org/package/lucidbleed/lucid/main/base/libva-dev)

Despite this information, please consider using 12.04 or later; Or if you don't like unity, install 12.04 and gnome-fallback for the older style interface. There is also lubuntu and xubuntu to consider if you are on older hardware (with their 12.04 releases or later)

---

### Post by FakeOutdoorsman on 2014-02-23
> **randall4 said:**
> ...and trying to install ffmpeg using [https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) after issuing the first block to install dependencies I get 
```
E: Couldn't find package libva-dev
```

Can someone please help?

See the note immediately below the box with the install command: **Lucid lacks the package libva-dev. This can be ignored.**

---

