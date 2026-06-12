---
title: "how to install lubuntu restricted extras"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by DragonGirl123 on 2013-05-11
Hello everyone.When i go to the lubuntu software center i dont find lubuntu restricted extras.Where to install it?

---

### Post by oldos2er on 2013-05-11
Try running ```
sudo apt-get update && sudo apt-get install lubuntu-restricted-extras
```

---

### Post by DragonGirl123 on 2013-05-11
it installed a lot of stuff but also i got an error dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. what to do? :(

---

### Post by oldos2er on 2013-05-11
Run ```
sudo dpkg --configure -a
``` as it's telling you. If you're stuck at the EULA for the Microsoft core fonts package, use the Tab key or arrow keys to highlight "Ok", then press Enter.

---

### Post by DragonGirl123 on 2013-05-11
ok it downloaded something i belive and i used the configure terminal thingy also. Is there anyway i can check if they installed correctly?

---

### Post by oldos2er on 2013-05-11
```
dpkg -s lubuntu-restricted-extras
``` look at the Status: line. There may be a way to do this with Software Center, but I don't know what that might be.

---

### Post by DragonGirl123 on 2013-05-11
i got this dpkg-query: package 'lubuntu-restricted-extras' is not installed and no information is availableUse dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

---

### Post by oldos2er on 2013-05-11
Can you run the command in post #2 again, and copy and paste all the text output here?

---

### Post by DragonGirl123 on 2013-05-11
I did everything again.It seems to me that it is ok now ,but still here is the response i got from terminal.Package: lubuntu-restricted-extrasStatus: install ok installed
Priority: optional
Section: metapackages
Installed-Size: 30
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Architecture: amd64
Source: ubuntu-restricted-extras
Version: 57
Depends: lubuntu-restricted-addons
Recommends: ttf-mscorefonts-installer, unrar, libavcodec-extra-53
Description: Commonly used restricted packages for Lubuntu
 This package depends on some commonly used packages in the Lubuntu
 multiverse repository.
 .
 Installing this package will pull in support for Microsoft fonts, Flash plugin,
 DVD playback, LAME (to create compressed audio files) and patent codecs for
 Chromium.
 .
 Please note that this does not install libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
 .
 Please also note that packages from multiverse are restricted by copyright
 or legal issues in some countries. See
 [http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)
 for more information.
Is it installed?

---

### Post by oldos2er on 2013-05-11
> Status: install ok installed

Looks good to me.

---

### Post by DragonGirl123 on 2013-05-11
yay ,thanks for your help :D

---

### Post by oldos2er on 2013-05-11
You're welcome.

---

