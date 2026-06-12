---
title: "Static Ip"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by DestroyMicroshaft on 2008-05-13
Can someone tell me in simple terms how to set up a static ip address in ubuntu using the networking tool in system>>administration>>network?
Ive looked everywhere and i dont know what im doing wrong?
Im on a wired connection with lynksys router, which has a default ip of 192.198.1.1

---

### Post by Zalbor on 2008-05-13
system>>administration>>network, wired connection (or wireless, depending on which you use), disable roaming mode, configuration: static IP, enter your settings. Does that not work?

---

### Post by DestroyMicroshaft on 2008-05-13
Hey thanks for a quick reply. I select static ip, i put in
ip address 192.168.1.140
subnet mask 255.255.255.0
default gateway 192.168.1.1
and I get nothing.

---

### Post by Het Irv on 2008-05-13
Click on your wired connection, and click properties on the right. ( You may need to unlock it)

Goto the drop down box and click Staic IP address, you should then be allowed to change the settings.

You may need to reset the router to force it to take the settings

---

### Post by DestroyMicroshaft on 2008-05-13
Resetting my router to factory settings did it, thanx everyone!

---

