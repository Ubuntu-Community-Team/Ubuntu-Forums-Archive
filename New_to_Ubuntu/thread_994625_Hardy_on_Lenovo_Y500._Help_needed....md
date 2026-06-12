---
title: "Hardy on Lenovo Y500. Help needed..."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by bobigeorge on 2008-11-26
Hello friends,

I have been trying to install Hardy on my friend's Lenovo Y500 Lap. I was able to install it successfully and I downloaded and installed about 280mb of updates. 

Then on the first reboot the touch pad and the keyboard freezed. After a lot of research I could fix the problem by adding locale=fr_FR i8042.reset to grubmenu. 

**But now I can't find nor use the wifi network which was working perfectly before**:(

Somebody please advice me on that.

Thanks in advance...

---

### Post by Michael.Godawski on 2008-11-27
Firstly: why not use the latest version of Ubuntu Intrepid 8.10?

Secondly: what do you mean by can't find? Is the network manager applet gone? Perhpaps you have just to add the notification area or the network monitor or both to the upper panel (right click > add to panel)

Thirdly: please post the result of these commands to clarify your current network status:
```
iwconfig
sudo iwlist scan
lspci
sudo lshw -C network
```

---

