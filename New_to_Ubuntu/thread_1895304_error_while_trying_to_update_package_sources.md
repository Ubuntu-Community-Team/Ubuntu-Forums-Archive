---
title: "error while trying to update package sources"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by kanjiline on 2011-12-14
The following error message is given when I try to update package sources:
```

W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch http://ppa.launchpad.net/shawn-p-huang/dev/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/shawn-p-huang/dev/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/shawn-p-huang/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/shawn-p-huang/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```What to do?

---

### Post by matt_symes on 2011-12-14
Hi

Open a terminal and type (or copy and paste; case is important).

```
grep -lZ "shawn-p-huang" /etc/apt/sources.list.d/* | xargs -0 sudo rm
```That is a small L after grep and a zero after xargs. Enter your password. It will not be echoed to the screen.

Then copy and paste

```
sudo sed -i 's/^deb cdrom*/#deb cdrom/' /etc/apt/sources.list
```Lastly

```
sudo apt-get update
```Kind regards

---

### Post by mikewhatever on 2011-12-14
There is the cdrom and a PPA. Just remove the two from the sources list, and that should be it.

---

### Post by kanjiline on 2011-12-14
Hello Matt, I copy-pasted as you suggested and the result was a bunch of lines appeared in Terminal, some starting "OK" and others "Ign". Hopefully this will have sorted out the problem.

Mike, thank you for your reply but I am afraid that I did not understand what I was supposed to do.

Thank you both for being so quick to help!

---

### Post by matt_symes on 2011-12-14
Hi

If you got no errors like in your post #1 then you're good to go.

Kind regards

---

### Post by kanjiline on 2012-01-25
Somewhat related to my original question, I have been having a problem with ibus 1.3.99. due to its not accepting umlauts as input for pinyin characters. The developer has a newer version available for download -- ibus 1.4.0 -- which I've downloaded (it's a tar.gz archive). However, I am unsure what to do next.

In Windows I would just doubleclick a setup.exe and let the Installer do the rest. In Ubuntu I am clueless  :confused:

---

