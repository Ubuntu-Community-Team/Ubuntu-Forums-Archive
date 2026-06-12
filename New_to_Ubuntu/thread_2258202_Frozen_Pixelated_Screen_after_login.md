---
title: "Frozen Pixelated Screen after login"
date: 2014-12-25
forum: New to Ubuntu
---

### Post by Taqi_Anwar on 2014-12-25
Hi, I am new to linux. So, I decided to go with ubuntu. I have installed it on my eMachine El1331G. When I tried the Try Ubuntu option, there was a pixelated screen and nothing  else. So, I just went ahead and installed it thinking it'll be different, After the installation Ubuntu booted perfectly and took me to login screen, but after I logged in there it was again. The same pixelated screen, I have tried to wait it out but it's just frozen, if you can give me any insight on how to fix this issue; it'll be really helpful. I have attached a picture of how the screen looks.

---

### Post by Frogs Hair on 2014-12-25
Hello and Welcome 

Please post some hardware information such as , cpu , memory, and graphics since there are different configurations for that computer. Generally if the live session fails it's not a good to proceed with the installation.

---

### Post by Taqi_Anwar on 2014-12-27
It's an AMD Athlon 2850e (1.8 GHz) cpu, runs 3 gb of ram and has NVIDIA GeForce 6150 Se n430 integrated graphics. I know I shouldn't have gone forward with the installation, but that was bad on my part. I was able to install and run ubuntu by pressing F3 on ubuntu boot, but the screen resolution appears to fixed and too small.

---

### Post by Jonathan Precise on 2014-12-27
Hello Taqi_Anwar, welcome to the forums!

1)Can you switch to a virtual terminal, e.g. pressing CTRL-ALT-F1, CTRL-ALT-F2... CTRL-ALT-F6?

2) If so, you might have luck installing proprietary drivers. I'm not too familiar with this, so wait for someone else to post how.
-OR-
2) Maybe a bad download? [SIZE=1]Who knows.[/SIZE]. Try downloading ubuntu again by going to a virtual console, assuming you can (if not, go to the last "2"), and typing (asuming 64-bit):
```

wget http://releases.ubuntu.com/14.10/ubuntu-14.10-desktop-amd64.iso || until wget -c http://releases.ubuntu.com/14.10/ubuntu-14.10-desktop-amd64.iso ; do : ; done
md5sum ubuntu-14.10-desktop-amd64.iso
```
Make sure the md5sum of the ISO is equivalent to:
```
08494b448aa5b1de963731c21344f803
```
-OR-
2) 32-bit: ```
wget http://releases.ubuntu.com/14.10/ubuntu-14.10-desktop-i386.iso || until wget -c http://releases.ubuntu.com/14.10/ubuntu-14.10-desktop-i386.iso ; do : ; done
md5sum ubuntu-14.10-desktop-i386.iso
```
Make sure the md5sum is equivalent to: ```
4a3c4b8421af51c29c84fb6f4b3fe109
```
-OR-
2) No luck? Download the corresponding ubuntu ISO on a working PC, and md5sum. See [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM").

-Jonathan

---

