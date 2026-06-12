---
title: "Remote desktop"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by pmohankumar on 2013-01-28
Hi,
In my network, a pc with ip 10.0.1.132. I could ping that 1.132 pc from my pc but i cannot connect through remote desktop app. remote desktop enabled in 1.132 pc and also i could connect my pc from 1.132 pc through remote desktop.
Pls help me.

---

### Post by GordThompson on 2013-01-28
Gnome Desktop Sharing uses the VNC protocol. Are you using a VNC-capable client (sometimes called a "VNC Viewer") when you try to connect to the 1.132 machine?

Also, it would be helpful if you were more specific about the the machines in question. Are they both running Ubuntu? What version(s)? What client are you using when you try connecting to the 1.132 machine?

---

### Post by dolphin194 on 2013-01-28
If you're using Windows to connect, as said above, the protocol used for the remote desktop in Ubuntu is not the same as in Windows, therefore you cannot connect with the built-in remote desktop client for Windows. 

If you are using Ubuntu to connect, make sure you tell the Remote Desktop client to use the VNC protocol, not the RDP one.

---

