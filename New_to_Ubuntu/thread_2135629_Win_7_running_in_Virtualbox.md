---
title: "Win 7 running in Virtualbox"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by dlrose on 2013-04-14
I have set up a virtualbox running win7 and it is running fine. I do have a scaling issue gettijng it to scale properly. I have a System76 with Ubuntu 12.10 w/16Gb mem (4Gb for thr virtualbox) a 500 Gb HDD (200Gb for Virtualbox) set the video mem to 64Mb.

The display for the win7 is streched horizontal and doesn't fit the 1920X1080 screen on the laptop.

Does any one have any sugestions ?

Thanks

Darrell

---

### Post by DuckHook on 2013-04-14
Installing VirtualBox Guest Additions should solve that problem. Available from the same repository that you downloaded Vbox from. If you don't want to taint your install with closed-source restricted software like Guest Additions, then you should still be able to get a more appropriate screen resolution by changing the resolution settings within Windows itself. I don't use Win7 so can't help you there. Your settings all look fine, but be sure to turn on 3D acceleration in your VM settings.

---

### Post by sp-1070 on 2013-04-15
Make the remote desktop/vnc work on the windows box, fire it up connect with it through ubuntu and there you have it.

---

### Post by Paqman on 2013-04-15
> **DuckHook said:**
> Installing VirtualBox Guest Additions should solve that problem.

+1 to this. If you haven't already install this. It'llgive you lots of useful stuff like graphics drivers and mouse sync.

---

### Post by dlrose on 2013-04-17
Thank you for the response. I did install the guest additions which helped several items, but didn't help with the screen sizing. Where do I make the changes for the remote desktop/vnc work on the virtualbox.

Thanks again

Darrell

---

### Post by DuckHook on 2013-04-17
If installed properly, guest additions should allow you to just drag on the frame (containing W7 running within) and resize it just like you would any other app. W7's menu bars, icons, etc should just realign to the new shape of the frame. If you make the shape of your frame equal to, say, 1280x1024, then W7 should dynamically adjust its display to 1280x1024(or whatever shape box you make). Is this not happening? If not, please open a terminal in Ubuntu while the W7 VM is up and running and do:```
lsmod | grep -i vbox
```and post the output back to this thread. Then, in W7, open device manager and see if it shows the vbox graphics driver as the video card. I can't give you more precise instructions for W7 because I don't use it. However, I believe that most Win OSes are similar in how to check what hardware is being detected.

---

