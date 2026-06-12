---
title: "[SOLVED] Sony nwz-s61x series connection software"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by rmx on 2008-07-21
Hello,

I've read on this forum that people use to connect to Sony nwz-s61x with amarok.

However, my ubuntu (8.04) just don't recognize the device (I mean not even like a pen).

Anyone have a clue?

thank,

RMX

---

### Post by rktesser on 2008-07-22
I have one of these. There's a bug in some component of Ubuntu which causes ito not to be mounted automatically as a pen drive would. However you can use it either with Amarok or Rhythmbox, using the MTP protocol.

With rhythmbox you just need to plug the device when the software is running and it will be recognized automatically. To transfer music to the device you just need to drag them from your libray to the device icon in the left of the window.


 In Amarok you need to open the configuration dialog and add a new media device (MTP device). Then you must click the "Devices" tab in the left of the Amarok window, be sure that the mtp device is selected in the drop-down menu. and the press the connect button. The music in the device is displayed and can be transfered to your library or removed from the device. To transfer music to the device you must select it, click whit the right button and select from the menu the option to transfer them to the media device. to finalize the process you must go back to the device tab and click in the transfer button at the top. At the end you must press the disconnect button.

I can't give you the exact names of the commands and options because mys system is not in English, sorry.

---

### Post by rmx on 2008-07-23
Thank you very much.

with your post I found that MusicBox has a plugin "MTP device" that needed to be on.:)

Rui

---

