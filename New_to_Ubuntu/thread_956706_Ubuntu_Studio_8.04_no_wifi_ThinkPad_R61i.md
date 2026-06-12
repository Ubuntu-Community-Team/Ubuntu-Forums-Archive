---
title: "Ubuntu Studio 8.04 no wifi? ThinkPad R61i"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by alphabyte on 2008-10-23
I just did a full install of Ubuntu Studio 8.04 on my Lenovo R61i. It boots fine and everything looks great. However, my network seems to not be available (no network icon in the upper right corner). When I ran "lshw -C network" I see that my wifi is "DISABLED". What do I do? I went through the System>Admin>Network but it didn't help me at all. Any help would be greatly appreciated... I'm sure I'm missing something small and dumb. The wifi card is an Intel PRO/Wireless interface.

-Alphabyte

---

### Post by Fire_Chief on 2008-10-23
Are you using NetworkManager to control network connections? It should look like two screens in the top panel near the time/date and volume control display. If you right click on it, you should see two check boxes for Enable Networking and Enable Wireless. Be sure both are checked. Then you should be able to left click and select a visible wireless network to connect to.

If you don't see NetworkManager, you can type```
sudo NetworkManager
``` in a terminal and it should put the dual screen icon in the panel.

Cheers!

---

### Post by alphabyte on 2008-10-23
the network manager is not in the upper corner, and when I typed the command is came back with "command not found" I'm not sure I have it some how....

---

### Post by prshah on 2008-10-23
> **alphabyte said:**
> (no network icon in the upper right corner). 

Press Alt+F2, then give the command ```
nm-applet
```, that should give you the network manager; post back if you still have problems.

---

### Post by alphabyte on 2008-10-23
It looks like the network manager is not installed... wonder how/why that happened? I gotta find an ethernet cable now so I can install it and turn on my wifi? What happened?

---

### Post by alphabyte on 2008-10-23
ok so it seems that ubuntu studio doesn't come with network manager when you install it off of an official ubuntu studio cd? How in the world was this left out? lol and how do I go about fixing it?

-alphabyte

---

### Post by alphabyte on 2008-10-23
The problem, as far as I can see it, is that ubuntu studio does not install network manager for some dumb reason and is default with the wifi card disabled. How do I enable the card?

---

### Post by prshah on 2008-10-23
> **alphabyte said:**
> The problem, as far as I can see it, is that ubuntu studio does not install network manager for some dumb reason and is default with the wifi card disabled. How do I enable the card?

See [[SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless]("http://ubuntuforums.org/showpost.php?p=4723545&postcount=1") for a step-by-step on how to activate wireless networking from the command line.

Have you tried toggling the wireless network switch (if you have one?)

---

### Post by Waelwulf on 2009-02-02
I just installed Ubuntu Studio today and I also have no NetworkManager. How does this get left out?

---

