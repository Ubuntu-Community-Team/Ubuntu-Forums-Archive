---
title: "[SOLVED] Package Manager error"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by slwelch33 on 2008-07-04
Brand new to Ubuntu after a disastrous foray into Fedora Core 9.
Having a problem with the Package Updater.
I installed KDE and somewhere in the processes, Package Manager got broken.
Here is the error I get when I try to open Synaptic Package Manager:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

---

### Post by hyper_ch on 2008-07-04
what do you get when you run this from the command line:
```

sudo apt-get update

```

---

### Post by slwelch33 on 2008-07-04
here is the results:
```

```Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by slwelch33 on 2008-07-04
BTW, this is a "Brand New" installation of 8.04.01, done this morning.

---

### Post by hyper_ch on 2008-07-04
change the us to some other country... you can do that in synaptic somewhere in the settings... you'll find it... then try again.

---

### Post by slwelch33 on 2008-07-04
Not quite sure how to do that, when I get the error from package manager, it displays the error and when I click the button, it closes - is there a config file somewhere that I can change the file?

---

### Post by slwelch33 on 2008-07-04
GOT IT! It was the Software Sources - changed and then changed back.
Working now. Thanks for your help!

---

### Post by unutbu on 2008-07-04
Why does this error happen? Is there something wrong with us.archive.ubuntu.com?

---

### Post by slwelch33 on 2008-07-04
I have absolutely no idea why this happened.
I had installed the KDE desktop and after switching to KDE, was attempting to install some other misc packages (do not remember what) when something failed and from then on, nothing regarding package updating or software management would work.
Per hyper_ch suggestion, I changed the Software Sources to something in the UK, let it download, then changed it back to US, downloaded and everything appears to be OK now.

---

### Post by hyper_ch on 2008-07-04
use the thread tools to mark this as solved ;)

---

