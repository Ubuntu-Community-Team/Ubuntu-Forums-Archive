---
title: "broken packages"
date: 2018-04-27
forum: New to Ubuntu
---

### Post by newblank25 on 2018-04-27
I discovered i have broken packages. how do you repair that problem. I got this message.You might want torun 'apt --fix-broken install' to correct these.
The followingpackages have unmet dependencies:
 libsnmp30:i386 :Depends: libperl5.26:i386 (>= 5.26.0~rc1) but it is not installed
E: Unmetdependencies. Try 'apt --fix-broken install' with no packages (orspecify a solution).

 I typed sudo apt --fix broken install libsnmp30:i386 the result was this 
sudo apt -- fix broken install libperl5.26:i386 E: Invalid operation fix
What am i doing wrong? any help would be appreciated.

---

### Post by newblank25 on 2018-04-27
went to google. found what commands to use. this was my result
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libsnmp30:i386:
 libsnmp30:i386 depends on libperl5.26 (>= 5.26.0~rc1); however:
  Package libperl5.26:i386 is not installed.


dpkg: error processing package libsnmp30:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libhpmud0:i386:
 libhpmud0:i386 depends on libsnmp30 (>= 5.7.3+dfsg-1.8ubuntu3~dfsg); however:
  Package libsnmp30:i386 is not configured yet.


dpkg: error processing package libhpmud0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsane-hpaio:i386:
 libsane-hpaio:i386 depends on libhpmud0; however:
  Package libhpmud0:i386 is not configured yet.


dpkg: error processing package libsane-hpaio:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsnmp30:i386
 libhpmud0:i386
 libsane-hpaio:i386
michael@michael-p7-1456c:~$ sudo apt-get update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release              
Reading package lists... Done         so what is wrong?

---

### Post by oldrocker99 on 2018-04-27
Try this instead:
```
sudo apt -f install
```

That should pull in all the dependencies that the program needs and should (should) install the program OK.

---

### Post by Impavidus on 2018-04-28
When it says "You might want to run 'apt --fix-broken install' to correct these,' you should run```
sudo apt --fix-broken install
```and not```
sudo apt -- fix broken install [package]
```See the different spaces? When using --fix-broken, you only have to provide a package name if you want to specify an exact solution, but usually apt is smart enough to find the solution automatically. And -f, as suggested by oldrocker99, is just short for --fix-broken.

---

### Post by mörgæs on 2018-04-28
To prevent errors like this: Don't write commands. It's that simple. 

When you see a command which might be useful copy and paste it to the prompt.

---

