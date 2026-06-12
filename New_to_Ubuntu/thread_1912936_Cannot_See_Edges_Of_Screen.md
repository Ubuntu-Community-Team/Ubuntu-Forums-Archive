---
title: "Cannot See Edges Of Screen"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by DLad24 on 2012-01-21
Hey Guys,
   I recently switched from Win XP to Ubuntu 11.10. After installation and booting Ubuntu for the first time, my screen looked like the attached file...
(sorry for bad quality i had to take a picture because screen shot did not show screen cutoff)
When i used Win XP i had the same problem, but it was fixed through the NVIDIA control panel (which i cannot find on Ubuntu) where i adjusted th size of the screen to fit my monitor 
Please Help me make the screen fit my TV!
P.S Im a noob to Ubuntu and barely know anything so a detailed explanation would be greatly appreciated
additional Info
I am using a Panasonic Viera 32" Plasma as a monitor 
I'm running Ubuntu 11.10
I have barely any knowledge of Ubuntu
Thanks!

---

### Post by MG&amp;TL on 2012-01-21
Right. You say you have an NVidia card. Have you installed the drivers for it? Click the top (black) button, then type additional drivers.

Once you've done that, click on the circuit board design, then install the driver.

See if that fixes anything, then you should also have an NVidia control panel.

---

### Post by DLad24 on 2012-01-22
i installed the driver like you said, but i did not get the NVIDIA Control Panel, only NVIDIA X server settings. Here i could not find the option of adjusting screen size. I tried to get the ION LE drivers off the website but encountered even more problems here. I tried to find the answer through multiple google searches, but to no avail. is there any way i can get the control panel another way?

---

### Post by bogan on 2012-01-22
Hi!, **DLad24**,

In the version of NVIDIA X Server Settings I have - v290.10 - there is an entry in the left sidebar, next to last in the list, that starts "DP0-" (name of Monitor) - if it detects it correctly.

Select that and there are options to set scaling method: Stretched; Centered; or Aspect ratio.

Have you tried that?

You may need to select 'Advanced' on the first screen.

Chao!, **bogan**.

---

### Post by DLad24 on 2012-01-22
Bogan,
         Just tried it, but it didnt work. Under GPU 0 - (ION LE) and DFP-0- (Panasonic-TV), there was a GPU scaling method. i tried all three settings, center aspect and stretch, but they did not change anything. any other ideas?

---

### Post by MG&amp;TL on 2012-01-22
Have you tried setting the resolution normally through the screen settings?

---

### Post by DLad24 on 2012-01-22
I tried all the resolution settings and even tried to set a panning radius. Neither of these options work... i even downloaded the newest driver off the nvidia website and tried that... this problem just seems like it doesnt want to go away...

---

### Post by blackrider99 on 2012-01-23
I just solved this same problem with an NVIDIA card.  In the NVIDIA X server find the overscan compensation slider and slide it until the screen resizes.  It works the same way the windows one did.

---

### Post by DLad24 on 2012-01-23
SOLVED THANK YOU SO MUCH!
i found the Overscan Compensation after 10 minutes of searching...
I adjusted it and now it fits perfectly Thank you so much!

---

