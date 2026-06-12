---
title: "Belkin Wireless G Plus MIMO USB Network Adapter"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by shoenigman on 2008-04-30
I have posted about not being able to configure this device before at [http://ubuntuforums.org/showthread.php?t=691186]("http://ubuntuforums.org/showthread.php?t=691186"). I was actually able to get this to get this device working properly through advice offered in the referenced post. 

However, since I updated to Ubuntu 8.04 (hardy) last week I have not been able to get on the Internet. When I type in the following command

```

ifconfig -a

```

there is no entry for WLAN0, just entires for 'eth2' and 'lo'. I have removed the USB device and plugged it back in, yet the system does not register the device. Does anyone have any advice as to how I can get this back up and working? Thanks in advance!

---

### Post by shoenigman on 2008-04-30
Just to reiterate, my wireless connection worked in Gutsy but now that I upgraded to Hardy it has stopped working. Does anyone know how to fix this issue? any responses would be greatly appreciated. Once again, thanks!

---

### Post by shoenigman on 2008-06-03
Does anyone have an answer on this yet? I still haven't been able to solve this. Thanks in advance!

---

### Post by shoenigman on 2008-07-15
I still have not gotten this to work. Does anybody have an answer? Thanks!

---

### Post by Happibun on 2008-08-06
:-k

Were you using Network Manager, or something else like Wicd in Gutsy? I had the same problem, though with a different card (My set up is with a Netgear router and #*%@ Broadcom Airforce one in my lappy). 

The install of Hardy wiped my wireless settings and I had to reconfigure Wicd and remove Network Manager all over again. 

I gather that Network Manager is needed when the OS is reinstalled, or upgraded, and so doing so mucks up the alternative wireless settings.
I hope this is of some use. [-o<

):P

---

