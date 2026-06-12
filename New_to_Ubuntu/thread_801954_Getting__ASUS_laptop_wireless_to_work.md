---
title: "Getting  ASUS laptop wireless to work"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by tomlaber on 2008-05-21
Hi all,
I am desperate to make the Ubuntu leap but I cannot get networking going on my asus a6jc laptop which uses intel pro wireless abg 3945. The wireless light will not come up and I can't see any connections. The laptop works perfectly when plugged into a lan.
I have read every article I have found but I really don't understand the threads. I am a complete newb when it comes to Linux but am OK with Windows and DOS.
Please can anyone suggest how I can turn the wireless on. I have downloaded the intel drivers (i think they are drivers?) ipw3945d_1.7.22-4.diff.gz but don't know how to install them.

I pledge to name my first born after the user that can get me going.

Cheers

---

### Post by kilroy423 on 2008-05-21
I have an HP Pavilion dv 8300 with the intel pro wireless 3945 and I was able to get my wireless working using ndiswrapper.  I downloaded the driver from HP and then loaded them with ndiswrapper.  

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

here is a thread that talks about the light issue, hope this helps

[http://ubuntuforums.org/showthread.php?t=781472&highlight=intel+3945&page=2](http://ubuntuforums.org/showthread.php?t=781472&highlight=intel+3945&page=2)

Kilroy

---

### Post by Xiong Chiamiov on 2008-05-21
If it isn't [recognized out-of-the-box]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel?highlight=%28wireless%29"), you might be able to get it going with some drivers [specifically for it]("http://ipw3945.sourceforge.net/").  And, if all else fails, [Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

/crosses fingers for baby named after my pseudonym

---

### Post by carlolovearianne on 2008-05-21
Try this:

Copy and paste in the terminal:

```
sudo update usbids 
sudo update pciids
```

And then copy and paste this as well:

```
sudo apt-get install build-essential
```

And finally this:

```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
tar xfz madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make
sudo make install
sudo modprobe ath_pci
sudo reboot
```


You may have to restart your computer at least twice to get it working.

Good luck.

---

