---
title: "Weird colors at VNC after changing nvidia driver"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by inter5tella on 2013-04-27
Hello community,

i've installed latest Ubuntu Gnome 13.04 x64 release and successfully installed x11vnc with autostart etc. .
Works really nice so far but only a lil' bit slow. I've readed that a propri installed nvidia-driver can accelerate the transfer over LAN.
First i tried the including driver system from "software&updates>additional drivers" (sorry, don't know exact name, 'coz i use german) und used latest one 310.
After reboot i noticed some blue color glitches, but moving mouse around will stop this (see pics below). The glitch comes after i've marked an object or open a drop-down menu. The Application-overview is most affected by this issue.
A rollback to default nouveau-driver cleans it all out, but the performance lags... 

Already tried the drivers from the ppa's from x-wat and xorg-edge and tried other vnc-viewers but without any changes.

Sry, if this forum is not for help with x11vnc, but maybe someone knows this....and sorry for my bad english.


thanks

---

### Post by khelben1979 on 2013-04-28
I'm curious on what nVidia chipset that you got installed. 

You can share that by typing lspci from a text console, just copy the text contents over here. My thought is that the nVidia drivers you're using, that they support your graphics badly. On the nVidia webpage you can check if the chipset really is supported by typing in your chipset model on the dialog boxes. I would not recommend you to directly install from there, since the nVidia graphics driver will break your graphics each time a new kernel upgrade occurs.

So in short, take a look at the nVidia webpage, check if your nVidia graphics chipset is officially supported.

---

### Post by inter5tella on 2013-04-28
Sorry, forgot to say that the video output from the remote machine works perfect. There are no such issues if i plug in any display.
These color problems only appear while i use vnc to this machine.

---

### Post by khelben1979 on 2013-04-28
I see. Then the choice you got would be to replace your VNC client to try and solve this issue, if it's of high priority to get done. There are several VNC clients available to try out and you should see them available in Ubuntu Software center.

I've used VNC clients myself (on MS Windows as well), and I never thought it was possible to solve these issues myself.. :) But good luck on that!

---

