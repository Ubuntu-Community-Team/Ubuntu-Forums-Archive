---
title: "can i install wine to a different directory????"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by stinger30au on 2008-06-30
Im having some dramas trying to get a program to run in wine. id like to leave all my wine stuff how it currently is and install a new version from the winehq site but in to a different directory if possible and run it and see if that helps.

anyone know how this may be achieved?

---

### Post by Marshal0505 on 2008-06-30
> **stinger30au said:**
> Im having some dramas trying to get a program to run in wine. id like to leave all my wine stuff how it currently is and install a new version from the winehq site but in to a different directory if possible and run it and see if that helps.

anyone know how this may be achieved?

No need to 'reinstall' wine. Let it make a new directory as described here:

WINEPREFIXCREATE - When you first run "winecfg", it runs WINEPREFIXCREATE to create a default .wine directory, but you can use it to create a separate directory for running custom Wine configurations. I have found this useful for running games that require OSS for sound when I prefer to use ALSA. Having a separate directory for those games allows me to run them without having to run "winecfg" first to change my sound settings.

For your convenience i copied this from [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=497332](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=497332)

---

### Post by stinger30au on 2008-06-30
thanks for the info

---

