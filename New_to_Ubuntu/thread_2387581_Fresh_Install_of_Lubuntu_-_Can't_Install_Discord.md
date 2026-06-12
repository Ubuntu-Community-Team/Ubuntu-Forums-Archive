---
title: "Fresh Install of Lubuntu - Can't Install Discord"
date: 2018-03-20
forum: New to Ubuntu
---

### Post by zzypr on 2018-03-20
So I downloaded the .deb file for Discord and entered the command sudo apt install "filename.deb" and was met with this output: 
 
 The following packages have unmet dependencies: discord:amd64 : Depends: libc6:amd64 but it is not installable
                 Depends: libasound2:amd64 but it is not installable
                 Depends: libatomic1:amd64 but it is not installable
                 Depends: libgconf-2-4:amd64 but it is not installable
                 Depends: libnotify4:amd64 but it is not installable
                 Depends: libnspr4:amd64 but it is not installable
                 Depends: libnss3:amd64 but it is not installable
                 Depends: libstdc++6:amd64 but it is not installable
                 Depends: libxss1:amd64 but it is not installable
                 Depends: libxtst6:amd64 but it is not installable
                 Depends: libappindicator1:amd64 but it is not installable
                 Depends: libc++1:amd64 but it is not installable 
E: Unable to correct problems, you have held broken packages.

Is there any fix to this? What do you guys recommend? Thanks for the input

---

### Post by again? on 2018-03-20
What release are you using?
```
lsb_release -a
```

---

### Post by zzypr on 2018-03-20
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful

---

### Post by again? on 2018-03-20
Did you use dpkg to install?
output for 
```
apt policy discord libc6
arch
```

---

### Post by tsimonq2 on 2018-04-19
Which deb did you download?

It's likely that the deb you downloaded is incompatible with the version of Lubuntu you are running.

---

### Post by thenailedone on 2018-04-19
On an aside and not directly related to the issue (perhaps) I tend to prefer gdebi to install any downloaded apps (but as has been mentioned in a prior post you can use dpkg to install the file). You couldn't use apt in the past to install an offline deb file but that might have changed.

You can try ```
sudo dpkg -i <file.name>
```
or, install gdebi with ```
sudo apt install gdebi
``` and then either run ```
sudo gdebi <file.name>
``` or simply double click the file in your file browser.

---

### Post by logix2 on 2018-04-20
This line tells you what's going on:
```
E: Unable to correct problems, you have held broken packages.
```
You need to fix whatever issue your Ubuntu system has before installing this. Try to run this and see if it fixes it:
```
sudo apt-get update
sudo apt-get install -f
```

---

