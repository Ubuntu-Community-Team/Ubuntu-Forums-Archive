---
title: "new router wi-fi connection"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by nelgold on 2013-12-10
hi all,
this is a case of fools rush in where angels fear to tread:
I have installed a new router on my main machine (winxp) and thought to upgrade the netgear usb wifi dongle on my second pc (ubuntu 12.04) to a linksys ae1200 dongle - no, I didn't check first to see if it was linux compatible, anyway I tried to install ndiswrapper (downloaded from the internet, didn't realize that it could be done through the "software center" also tried installing the linksys driver - and now I'm in a great old mess, wifi code screen popping up every minute which I can't close, also I'm not able to connect to the internet for more than about one minute.  can anyone guide me through the process of uninstalling the ndiswrapper and the linksys driver?
in hope that I can be saved.
thank you in advance:confused::(

---

### Post by codenine75a on 2013-12-10
I have a wifi dongle set up on my machine too.  If you disabled the internal NIC and are going to use an external wifi dongle blacklist the internal wifi driver @ /etc/modprobe.d/blacklist.conf  You need to find the driver with the 'lsmod' command.  'sudo lsmod | more' and guess which one it is and add that to the blacklist configuration file.  There is a quick way to restart the services but I just reboot.

---

### Post by kulen19 on 2013-12-10
If I understand you correctly, you installed ndiswrapper from source?  You then have to unpack the contents of the tarball again, and run  "./configure" (with the same parameters as you used when installed it).  Then you can run "make uninstall". A better option, for the next time  you decide to install something from source, is to make use of the  CheckInstall-program. Then you can run this code:

```

./configure
make
sudo checkinstall --type=debian --install=yes
```

After this you can uninstall it with for example synaptic; much easier :)
I'm not quite sure concerning the linksys driver.

---

