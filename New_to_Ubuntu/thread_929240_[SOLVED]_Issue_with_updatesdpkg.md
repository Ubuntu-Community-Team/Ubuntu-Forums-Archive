---
title: "[SOLVED] Issue with updates/dpkg"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-09-24
So I was browsing the forums, and I saw in a lower post that if you were having issues with videos, that this would help

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

I did that and I got a screen in the terminal with suns license terms, but no way to get out of the screen, so i quit terminal.  At that point I saw there were updates available, so I clicked on it, and when trying DL updates, it said that i had to run a dpkg command, so i did, and then the updates, worked.  The problem is that it said i had a broken package, and i needed to run the broken command.  Terminal doesnt accept man broken, how do I find this?  also when i try to run that same command that I pasted above, it starts, but stops at resolving medibuntu.com,  any input for either of these issues??

---

### Post by Crafty Kisses on 2008-09-24
Try running the following commands:
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
```
That should solve the issue.

---

### Post by rideburton56 on 2008-09-24
Thanks!

Question... What did those 3 commands exactly do??

---

### Post by alzie on 2008-09-24
The license issue is that mediabuntu contains Sun java rather than open source java.

---

