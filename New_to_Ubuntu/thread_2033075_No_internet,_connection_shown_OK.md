---
title: "No internet, connection shown OK"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by freshminted on 2012-07-25
Using 12.04 on my other system,  I have lost my internet connection (BT) while the network is shown to be connected.

How do I resolve this? Why did it suddenly happen when it worked fine before. NO other changes, additions or reductions were made to the system.
Thank you for your help

---

### Post by Grenage on 2012-07-25
Are your IP and other settings static, or dynamic?
Can you ping an external site by name ( google.com )?
Can you ping an external IP ( 8.8.8.8 )?

---

### Post by Bufeu on 2012-07-25
Have you routed the traffic? Use *man route* to learn more about the command *route*.

---

### Post by mapes12 on 2012-07-25
If your BT Broadband was previously working with 12.04 then it sounds to me as if a simple router reset is all that's required. Unplug the power from the back of the BT Broadband Hub, leave it for about 10 seconds or so, then plug it back in again. If you have any powered switches on your home network do the same to them as well. Let the lights settle down then check to see if your Ubu connection is working. Once you've rest the BT Broadband Hub you may have to restart Ubu on your PC for the DHCP servcie to reconfigure itself.

It happens to me to.........:)

---

### Post by freshminted on 2012-07-25
Further to my appeal for help: we discovered that the router required a reset. Problem solved - so to those who thought about it, my thanks and I hope that the solution (switching the router off for 10 minutes and then re-starting it, may help someone as daft as me.

---

