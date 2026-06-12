---
title: "Updating Ubuntu?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by TrezenChath on 2008-05-12
I'm trying to install Wine so that I can play WoW, but I'm getting this error

> The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.14) but 1.0.13-1ubuntu5 is to be installed
        Depends: libgphoto2-2 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
        Depends: libgphoto2-port0 (>= 2.4.0) but 2.3.0-0ubuntu4 is to be installed
        Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.13.24ubuntu6 is to be installed
E: Broken packages

Do I need to update Ubuntu or something? If so how? I'm so out of my depth here, any help would be great.

I'm using Ubuntu 7.04 Feisty Fawn, in case you needed to know.

---

### Post by Jimmey on 2008-05-12
How are you trying to install wine? Are you using the wine repositories, or the universe ones?

---

### Post by TrezenChath on 2008-05-12
Bump of fail

---

### Post by TrezenChath on 2008-05-12
I used the commands shown in this thread [http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644) I dont know which that would be, honestly

---

### Post by muteXe on 2008-05-12
I'd get wine from the repositories, like that fellow says in the last line of his post under his number 7.

---

### Post by john91 on 2008-05-12
I think you simply have some other packages that you need to install.  wine depends on several other packages from the repos (regardless of where you get wine from).  taking a look at your original post, it looks like you need to run something along the lines of:

```
sudo apt-get install libasound2 libgphoto2-2 libgphoto2-port0 libldap-2.4-2 dpkg
```

also, if you're going to install wine from source, make sure you have the right dependencies installed to build from source.

---

### Post by TrezenChath on 2008-05-12
I used that command and got

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2 is already the newest version.
libgphoto2-2 is already the newest version.
libgphoto2-port0 is already the newest version.
Package libldap-2.4-2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libldap-2.4-2 has no installation candidate

As for building it from source, I really didnt mean to do it the hard way, I just dont know what I'm doing. I only just installed Ubuntu tonight, and am still learning the ropes so to speak. Easy one click solutions is the only thing I miss from Windows.

---

### Post by philinux on 2008-05-12
Just use, System Admin> Synaptic Package manager. 

Click on any app. Then type w i n e and it will take you straight to wine. Click it and mark it for install. Then click apply at the top menu.

---

### Post by TrezenChath on 2008-05-12
Doing it from Synaptic doesnt change anything. I still get an error message:

> wine:
  Depends: libasound2 (>1.0.14) but 1.0.13-1ubuntu5 is to be installed
  Depends: libgphoto2-2 (>=2.4.0) but 2.3.0-0ubuntu4 is to be installed
  Depends: libgphoto2-port0 (>=2.4.0) but 2.3.0-0ubuntu4 is to be installed
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.13.24ubuntu6 is to be installed

---

### Post by TrezenChath on 2008-05-12
Never mind, I figured it out. The default installation version was set to Hardy and I needed to force install the Feisty version. Thanks for all the help anyways, guys.

---

