---
title: "Home theatre hdmi"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by anderskitson on 2008-06-26
I installed Ubuntu hardy heron, on my computer hooked up to my tv. It installed fine and surprisingly, there was no problem with resolution it fit my screen full, which I could never get work with the integrated graphics card, in vista. I enabled the restricted drivers and on reboot, I lost my screen. It is an msi board with an ati card built in, via hdmi. I will post the exact specs when I get home, but has anyone got around this problem with ati and hdmi. I would like to have the compiz effects, because its much prettier on a home theater, and I hate windows. If anyone could even recommend a fairly inexpensive graphics card that would solve my problem. (preferably hdmi, that will actually send sound in linux) Also the sound doesn't work, but I looked this up a while ago, and there didn't seem to be any linux support for sound blaster, I think thats what it was, its optical out any how. If any one has any suggestions that would be great.

---

### Post by ZabiGG on 2008-06-27
Hi,

The only way I managed to get mine working through my ATI HD2600Pro card was with the restricted driver. 

There's a complete how-to here:

regular binary driver: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If that doesn't work, you might also want to check out the EnvyNG installer (after you uninstall all fglrx drivers first).

You should read thye entire thread BEFORE you start installing and configuring so you'll know what you're getting into beforehand. A tip, though: if you have one, connect a monitor to your second output so you can install and view your display, so that you may reconfigure the TV after (mine didn't display anything during installation until reboot, so the monitor was quite useful)

Hope this helps,

Z.

---

