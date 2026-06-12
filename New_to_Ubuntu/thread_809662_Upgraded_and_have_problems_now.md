---
title: "Upgraded and have problems now"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Finlae on 2008-05-27
Ok, I upgraded last night to 8.04, and now I'm having problems with my laptop. It is a Compaq Preasrio F500, and I have lost the ability to use my wireless, my speakers have gone scratchy, it will lose the screen and not come back if I close it, and I can't hot swap USB tumbdrives or mice. All those things worked fine before, and I upgraded once, and they still worked. This recent update seems to have had problems though. Any advice? I think I can fix the Wireless card, but I haven't been successful yet. The rest is beyond me at this point. Thanks.

---

### Post by lswest on 2008-05-27
Can you post more information?

- Sound card 
check with: ```
lshw -C audio
```

- wireless card ```
lshw -C network
```

- graphics card ```
lshw -C Display
```

and anything else you may deem connected to this problem? (for example how you got wireless and such working before)

---

### Post by Finlae on 2008-05-27
My readout when I use lspci is:

VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)

Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

Before I used an NDISWrapper, but I haven't been successful with getting the NDISWrapper to work with Heron yet. I never had issues with the USB hotswapping, but now it only recognizes it if I have the USB device in when I boot up. If I don't have the device in, it won't accept it. And before Hardy Heron, I never had to worry about closing my laptop lid and losing my system. Also, I tested Hibernating and Suspending it, and those both darken the screen, and basically kill it. I think the speakers have lost their scratchy quality, but it is quieter than it used to be. What else do can I post to help?

---

### Post by stchman on 2008-05-27
> **Finlae said:**
> Ok, I upgraded last night to 8.04, and now I'm having problems with my laptop. It is a Compaq Preasrio F500, and I have lost the ability to use my wireless, my speakers have gone scratchy, it will lose the screen and not come back if I close it, and I can't hot swap USB tumbdrives or mice. All those things worked fine before, and I upgraded once, and they still worked. This recent update seems to have had problems though. Any advice? I think I can fix the Wireless card, but I haven't been successful yet. The rest is beyond me at this point. Thanks.

I have never been a big fan of the upgrade route.  What happened is that the upgrade gave you a new kernel.  You probably used ndiswrapper to get the Broadcom wireless working.

My advice is to do a clean install and install the ndiswrapper for Hardy.

---

### Post by Finlae on 2008-05-27
Would that help clear up the other issues as well?

---

### Post by lswest on 2008-05-27
> **Finlae said:**
> My readout when I use lspci is:

VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)

Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

Before I used an NDISWrapper, but I haven't been successful with getting the NDISWrapper to work with Heron yet. I never had issues with the USB hotswapping, but now it only recognizes it if I have the USB device in when I boot up. If I don't have the device in, it won't accept it. And before Hardy Heron, I never had to worry about closing my laptop lid and losing my system. Also, I tested Hibernating and Suspending it, and those both darken the screen, and basically kill it. I think the speakers have lost their scratchy quality, but it is quieter than it used to be. What else do can I post to help?

you're in luck about the broadcom card, same one i have and i wrote a quick how-to on it in a thread here: [http://ubuntuforums.org/showpost.php?p=4871609&postcount=5](http://ubuntuforums.org/showpost.php?p=4871609&postcount=5).  All the files you need are attached to that post.

The info i requested using lshw would be useful, as it will show what drivers are currently in use for each piece of hardware.  Also, the scratchy quality may be caused by pulseaudio, and there are some threads on the forums on replacing pulseaudio with alsa again in hardy (i haven't done it, so i don't know exaclty how).  I'd like to see what drivers are being used for your graphics card before i post some info on how i may solve it, if i even know how ;)

---

