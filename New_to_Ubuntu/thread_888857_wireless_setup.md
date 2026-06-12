---
title: "wireless setup"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by richie3418 on 2008-08-13
I am completely new to Ubuntu. I have been fooling around windows and still learning. I wanted something different so here I am. I installed Ubuntu 7.10 on a Inspiron 1150 with Intel-Celeron 2.60 ghz, 512 mb memory and 24X CD-RW/DVD. The installation went great as I had it take over the whole hard drive. It recognized the hard wire ethernet from my Hughes modem but when I tried to use the wireless N adapter  nothing happened. I tried the troubleshooting for 7.10 and couldn't find the device manager it said was supposed to be at system-administration-devise manager. Is it possible that it wasn't installed from the cd? I imagine I will find more things to puzzle me but right now I would appreciate any input on the missing device manager.

---

### Post by reya276 on 2008-08-13
Did the system do all the updates after the install? Meaning did it download all the updates via your ethernet connection(not wireless) if so you can see if there are any Hardware restricted drivers by going to System>Administration>Hardware Drivers.This is in ubuntu 8.04 so it might be different in 7.10 but it should be in the same path System>Administration>..... But there it should tell you if you have any drivers that are available that are not being used such as your Wireless N. If you do see it, selected and then the system will download some files and then ask you to restart, do so and then test it.

Now if it does not find it, get the name of Winless N adapter/Model number so that we can check if there are any drivers available. One way you can find out is by opening a terminal window Applications>Accessories>Terminal. In the terminal window type dmesg and copy all of the text it outputs and paste it here [http://www.pastebin.us/](http://www.pastebin.us/). Post the return link on this post so we can look at it. Don't worry this is not going to give out any personal information stored on your PC just the devices connected inside your PC.

---

### Post by reya276 on 2008-08-13
You can also visit #ubuntu-us-fl on IRC chat and we can help you there as well or the main #ubuntu channel on IRC.

---

### Post by cozmicharlie on 2008-08-13
Any particular reason you installed 7.10 vs 8.04?  

The device manager should be under System>Administration>Network.  You should also have a Network Manager icon in your panel.

---

### Post by richie3418 on 2008-08-13
The wireless adapter is a Belkin N model #FSD8053
After install I downloaded and installed all the updates and the restricted drivers had one and that was for a phone modem which I enabled.
Also I copied and sent all the information from the terminal when I typed dmesg.
I am going to be away until thursday night or friday.
Thank You

---

### Post by richie3418 on 2008-08-13
I will have to try this friday
Thank You

---

### Post by richie3418 on 2008-08-13
I tried twice to upgrade to 8.04 but it got locked up close to the end of the install. I didn't write down the exact spot but I think it  was when it tried to connect with the modem. Anyway I ordered a CD because of a limit on this satelite internet FAP I only have a 375 mb threshold in a 24 hr period hazards of living in the boonies.
Thank You

---

