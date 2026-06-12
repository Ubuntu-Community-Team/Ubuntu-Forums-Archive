---
title: "Strange snapping sound and Screen dims"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by SVWander on 2008-06-29
I am having a strange problem with my Dell 1200 laptop. At first I thought it might be a problem with the AC jack. When I move the laptop sometimes (but not always) I can here a snapping sound and at the same time the screen dims. Last night I was about to take this computer apart and see if there was a loose connection in the area around the AC jack. But then I decided to check to see if it was a OS problem so I took out the Ubuntu hard drive and installed the XP HD. It took 10 minutes booting up and with the CPU temperature hovering at 130. I am even bouncing this laptop on my lap but no snapping sound . . . no screen dimming. Does anyone have an idea what could be going on with Ubuntu?
Tim

---

### Post by phidia on 2008-06-29
What video card does your laptop have and did you enable the driver for that card in ubuntu?

---

### Post by silkstone on 2008-06-29
Double post

---

### Post by silkstone on 2008-06-29
A CPU temp of 130C is way too high - I'm surprised it didn't burn out. If it's reaching that temperature it may be reducing speed due to overload. It doesn't sound like an OS issue since you got that temp with XP - more likely a hardware problem such as a defective fan.

FYI I run Hardy on an Asus laptop (Intel dual core and Nvidia graphics card), and the CPU temp idles in the mid-30s and never rises above about 45C.

Edit/ OK - apologies - I guess you mean 130F not 130C. :)

---

### Post by SVWander on 2008-06-29
> **phidia said:**
> What video card does your laptop have and did you enable the driver for that card in ubuntu?

Well, I believe the Dell 1200 uses integrated video and at the Dell site I picked up this bit of information:  Intel Graphics Video
I will have to put the Ubuntu hard drive in to give you more information. This computer has run excellently under Ubuntu for more than a year. It only started this within the last couple of months. I am running 8.04 with the latest updates. Do you think reinstalling the system would help solve the problem? The restricted drivers are enabled in Ubuntu for the wireless card. And there might be another restricted driver installed but I don't remember which.

Tim

---

### Post by SVWander on 2008-06-29
> **silkstone said:**
> A CPU temp of 130C is way too high - I'm surprised it didn't burn out. If it's reaching that temperature it may be reducing speed due to overload. It doesn't sound like an OS issue since you got that temp with XP - more likely a hardware problem such as a defective fan.

FYI I run Hardy on an Asus laptop (Intel dual core and Nvidia graphics card), and the CPU temp idles in the mid-30s and never rises above about 45C.

Edit/ OK - apologies - I guess you mean 130F not 130C. :)

This machine has always run hot as fire. The problem is with Ubuntu and not XP. In Ubuntu using gkrellm with the Dell 18K plug in. With that the temperature runs 50 to 55C or right now about 127 degrees. It was only with Ubuntu and Gkrellm that I learned the real temperature and downloaded gkrellm for windows to handle the fans in XP. I use the standard temp control in the windows gkellm for windows program. So it is not a heat issue since the computer runs cooler in Ubuntu than it does in XP (where the snapping sound and dimming does not occur).

To get this Dell to run at 40C the fans have to run flat out all the time.

However, thank you so much for your help. Next laptop I own I want it to run COOLER! It is bloody hot in South Texas today and this machine only makes it hotter. 

Tim

Is there a way for me to edit out the double post?

---

### Post by silkstone on 2008-06-29
I'm wondering if the noises are the graphics card/processor complaining and a thermal cut-out tripping on the GPU. Are you reading GPU temps as well as CPU?

---

### Post by SVWander on 2008-06-29
> **silkstone said:**
> I'm wondering if the noises are the graphics card/processor complaining and a thermal cut-out tripping on the GPU. Are you reading GPU temps as well as CPU?

I have never really been able to figure out what temperatures the senors are reading.

GKreIIM in the configuration file talks about thermal_zone/THM it is enabled.
 
And the i8krellm is a GKreLLM interface for the Dell Inspiron laptops.

The computer does not trip a cut-out in XP which runs far hotter. However if the trip points are buried in some Ubuntu configuration file that might be it. But I would need to know how to access the file and have the knowledge to correctly set it up.

This afternoon I have been using the laptop in Ubuntu without a problem. So my first reaction, that it is a problem with the motherboard, might be the answer. I just don't know. This is a great . . . very cheap Laptop . . . I would hate to be doing something that might damage it.

Tim

---

### Post by silkstone on 2008-06-29
I installed lm-sensors and sensors-applet which I added to the top panel. You can configure what is shown in the panel, but I have the CPU and GPU temps (can also have core temps etc).

I've not figured out how to set up lm-sensors to display fan speeds etc, but at least it tells me if I need to worry. :)

Sorry I can't be of more help. I'm a great fan of Ubuntu but mainly as a user rather than a tweaker, and there's a huge amount I don't know about.

---

### Post by SVWander on 2008-06-29
> **silkstone said:**
> I installed lm-sensors and sensors-applet which I added to the top panel. You can configure what is shown in the panel, but I have the CPU and GPU temps (can also have core temps etc).

I've not figured out how to set up lm-sensors to display fan speeds etc, but at least it tells me if I need to worry. :)

Sorry I can't be of more help. I'm a great fan of Ubuntu but mainly as a user rather than a tweaker, and there's a huge amount I don't know about.


Well, thank you so much for trying! I am a huge fan of Ubuntu also. This machine, which is really underpowered, can zip through most work in Ubuntu and boots in a minute vs XP five minutes (or more with Norton installed). I might try to just move /home to my file server and reinstall. I have chilled this machine down to 118 degrees but a minute ago (without any movement of the laptop) that snap or popping sound followed by a readjustment of the screen. 
Again, thank you for your help.
Tim

---

### Post by SVWander on 2008-07-03
The problem was in my power adapter cord or adapter itself. The reason for the snapping sound was simply a sound setting in System/Power Management under the general heading I simply unclicked the sound notification. So the problem is solved.

---

