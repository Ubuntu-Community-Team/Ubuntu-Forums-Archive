---
title: "neither wireless nor ethernet after 8.04 installed on asus 901"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by aspergerian on 2008-08-21
8.04 is installed and running via a USB boot drive. While 8.04 was running from the USB boot drive, ethernet did not work and wireless worked. After completing the 8.04 install onto the ASUS and after booting, disconnecting battern, rebooting - each without the USB boot drive, neither the ethernet nor the wireless works. 

One ubuntu help lists wireless and ethernet as "don't work".
[http://www.ubuntu-eee.com/index.php5?title=EeePC_901](http://www.ubuntu-eee.com/index.php5?title=EeePC_901)
Ironically, subsequent paragraphs of the aforementioned help-page are based upon direct downloads, which is a non-solution in circumstances wherein neither ethernet nor wireless works. I've read numerous posts but haven't a clue as to how to proceed.

Thank you.

---

### Post by pytheas22 on 2008-08-21
First of all, open a terminal (Applications>Accessories) and run these commands.  They might fix the ethernet (but don't get your hopes up):
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

Wait a few seconds and see if the ethernet works.

If that doesn't help, please run these commands:
```

lshw -C Network
lspci -nn
lsusb
uname -m
```

Then please copy-and-paste the output into a text file (Applications>Accessories>Text Editor) and transfer that file to a computer that has Internet.  From there, please copy-and-paste the output here.

(To copy-paste from terminal, highlight the text, right-click in the terminal windows and select "copy," then paste with control-v.)

With that information we can figure out what's wrong and get you online.

---

