---
title: "Dont know how to install Skype or other 3rd arty software"
date: 2017-10-08
forum: New to Ubuntu
---

### Post by steve482 on 2017-10-08
I am new to Ubuntu 1.16.04-3
Canonical 
I tries to get list of Canonical partners but nothing ever appeared.
Please advise. Might I be missing something?
TIA

---

### Post by kostkon on 2017-10-08
Is your Ubuntu installation 64bit? What's the output of:
```
uname -p
```

If yes, you need to download it from [Skype's own download page]("https://www.skype.com/en/download-skype/skype-for-linux/"). Click on the *Download Skype for Linux DEB* to download the .deb file, then open your Downloads folder and double-click on the skypeforlinux.deb file to install it.

---

### Post by inerstellar-cowboy on 2017-10-17
Skype has a very good port for linux imo.

Deb files are the easiest method of installation, along with command line...

I am a novice user myself...

---

### Post by Autodave on 2017-10-17
Yes: .deb files are the easiest. Go to the Software Center and get *gdebi* to use. Gdebi will install the .deb files for you and will also take care of any dependencies that you will need.

---

