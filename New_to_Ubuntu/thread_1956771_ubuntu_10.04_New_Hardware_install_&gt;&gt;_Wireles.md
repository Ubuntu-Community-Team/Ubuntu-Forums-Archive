---
title: "ubuntu 10.04 New Hardware install &gt;&gt; Wireless internet won't connect"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by xken24 on 2012-04-11
Hey all,

I'm new to the forum as well as new to the ubuntu (linux) operating system. I've just gotten my machine up and running and I've chosen to install 10.04 off the ubuntu website download boot disk. 

My hardware comes with a wired internet Ethernet connection, however I am connecting wireless to my wireless hub via airport express. My wireless card is taken off an older PC but it's the Linksys 802.11 WMP11 v4 PCI chip. It should work, but I'm experiencing some difficulties with a driver to get the PCI chip up and running. 

So far I've executed the 'lshw -C network' command and the terminal seems to recognize the hardware. There isn't really anything there in terms of a driver installed and it doesn't seem to be working. 

I looked up a site on the web that links this download [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) to being a sufficient driver. I downloaded the .zip file and attempted to extract it into the lib folder as told. The OS is telling me I don't have access to extract the file to the folder! 

I don't know what to do, all this hardware and I haven't even begun to search for drivers on my video card yet. 

Anyone know?

---

### Post by anewguy on 2012-04-11
Please post back the output of:

lspci | grep Ethernet

BTW, that's not a 1 or an I, but the piping symbol.  On both of my keyboards it's on the "\" key as the shifted symbol.


Dave ;)

---

