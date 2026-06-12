---
title: "Wired connection drops every few minutes"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by chillpenguin99 on 2012-11-12
I just installed ubuntu 12.10 64-bit along side windows 7 on my desktop pc. It was custom built by me a few years ago. If more info is needed on my hardware i can supply it. I really want to move to linux completely because I love the idea of opensource and linux seems more secure and has more customization  as well. However, my internet connection drops every few minutes or so and it takes a few seconds to a few minutes to start to work again. I am connected with an Ethernet cable directly into the gateway. Note that my windows 7 connection works flawlessly using the exact same hardware. I am an absolute linux noob so i have no idea what to do. I don't really know how to install new drivers. So if i must install Ethernet drivers i will need help. What should i do? Do i need new drivers? Is there some settings i just need to change in firefox? Maybe some settings in the ubuntu menus? I am lost. Thanks for the help!

---

### Post by audiomick on 2012-11-12
Ok, I am not going to be able to help much but:

You should not need to install any drivers for a wired Ethernet connection. That generally just works, and has done for a long long time.


You should post your hardware specs here. People are more likely to be able to help if they know what you are dealing with. Maybe you could post the output of the command

```
sudo lshw
```

here. Use the code tags. That is the # icon at the top of the post window. Perhaps the type of router  or how your are connected to the internet as well. There a so many variations on that theme that a bit of concrete info can go a long way.

---

### Post by chillpenguin99 on 2012-11-12
Now i have no idea what is going on. I booted into ubuntu and was greeted by a login screen on only 1 of my 2 screens. I believe it usually appears on both of my screens. So that was weird. Then i typed in my name and password and the desktop was only appearing on that 1 screen. My other screen was black. Also the resolution must not have been right because the desktop screen wasn't filling up my entire monitor. There were no options it was just a plain desktop. There was no taskbar or anything to click on. And i could not move my mouse over to the next screen (even though the screen was black i thought maybe my mouse would be able to move over onto it, but it was stopped at the edge of the screen as if i only had 1 monitor). So basically i didn't even get the chance to type in the command you wanted me to type. What do i do now?

Also you said ethernet drivers should work right away but just to let you know my ethernet did not work at all on my windows 7 install until i installed new ones... Just saying...

---

### Post by chillpenguin99 on 2012-11-12
Btw my hardware is: 
processor: intel core i5 750
video card: NVIDIA GTX 460
motherboard: Gigabyte P55-USB3 
4 GB ram

---

### Post by coldcritter64 on 2012-11-12
Please post the output of the command audiomick posted (sudo lshw). It will give helpers a lot more technical info to work with. Likely including make/model of the networking hardware etc. and in some cases will directly indicate the source of a problem to experienced eyes here.

---

### Post by chillpenguin99 on 2012-11-12
I don't know how to get to the terminal i have a blank desktop with nothing to click on.

---

### Post by audiomick on 2012-11-13
> **chillpenguin99 said:**
> Now i have no idea what is going on. I booted into ubuntu and was greeted by a login screen on only 1 of my 2 screens. I believe it usually appears on both of my screens. So that was weird. Then i typed in my name and password and the desktop was only appearing on that 1 screen. My other screen was black. Also the resolution must not have been right because the desktop screen wasn't filling up my entire monitor. 
This is, on a new install, not a necessarily a problem, or have you already had the second screen running on this install? My first thought would be that the screen configuration has just not been set up

> There were no options it was just a plain desktop. There was no taskbar or anything to click on.

With 12.04 you will have the Unity desktop. Was the bar down the left side not there? It is possible that the GUI isn't being started properly or is broken. Have you tried re-booting? Is the problem consisten? 
As far as the mouse not moving over, as I have already said, the graphics card is only seeing one screen as if the configuration is not set up.

I see you have an nVidia graphics card. Had you installed the proprietary nVidia drivers?

This is a separate problem to the one with your Ethernet. You might get quicker help on the graphics problem, if it persists, by starting a new thread with a title referring to that problem. If you do that, you should perhaps put a link in here to the new thread so that people who might try to help can stay on top of where you are up to.


> Also you said ethernet drivers should work right away but just to let you know my ethernet did not work at all on my windows 7 install until i installed new ones... Just saying...

I don't think that is relevant. The way drivers are handled, and the drivers themselves, are completely different between Windows and Linux. I understand your logic, but in fact it is a bit like comparing apples with pears.

---

