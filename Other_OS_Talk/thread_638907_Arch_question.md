---
title: "Arch question"
date: 2007-12-12
forum: Other OS Talk
---

### Post by Tala Shazi on 2007-12-12
I finally got around to installing Arch, opted for a xfce4 (good choice).  I have one question though, I installed abiword-plugins, and pacman said it was dependent on some things-- the entire installation was close to 30 MB.  I thought that was heavy, but I installed it, regretfully.

I wasn't too impressed with abi's plugins.  So I did 'pacman -R abiword-plugins,' but it only got rid of the plugins and not the other dependencies I had no use for.  I got rid of the larger files that I'm fimiliar with, but it's too difficult for me to go any further.  Is there a toggle menu for pacman?

Also, how do I find the weight of what I have installed so far, instead of a 'pacman -Q,' which does not display the size of those files?

---

### Post by miggols99 on 2007-12-12
If you want to get rid of dependencies installed, just do
```

pacman -Rs package-name

```

---

### Post by Rumor on 2007-12-12
pacman -Qi package_name is what you are seeking, I think as it gives you the dependencies and installed size of the package. For example, here is the output for xchat on my system:

```
pacman -Qi xchat
Name           : xchat
Version        : 2.8.4-1
URL            : http://www.xchat.org/
License        : GPL  
Groups         : None
Provides       : None
Depends On     : gtk2>= 2.10.9  openssl>=0.9.8b  dbus-glib>=0.7.2  
Removes        : None
Required By    : None
Conflicts With : None
Installed Size : 6009.06 K
Packager       : Eric Belanger < eric@archlinux.org>
Architecture   : i686
Build Date     : Thu Jul  5 00:43:59 2007 UTC
Build Type     : Unknown
Install Date   : Wed Dec 12 17:28:35 2007 UTC
Install Reason : Explicitly installed
Install Script : No
Description    : A GTK+ based IRC client

```

---

