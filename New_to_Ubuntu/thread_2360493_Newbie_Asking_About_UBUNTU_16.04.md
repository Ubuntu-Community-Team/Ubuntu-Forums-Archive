---
title: "Newbie Asking About UBUNTU 16.04"
date: 2017-05-05
forum: New to Ubuntu
---

### Post by dzanity on 2017-05-05
Hello guys,
Im new with Ubuntu. My first linux OS was Kali.
And i want to ask some questions here:

Last night i installed Ubuntu 16.04 LTS as the only OS for my laptop, after installation, my laptop didnt want to auto reboot it is says (something i forgot lol).
Then i try to hard shutdown, and it is working fine. After that i tried to update from ubuntu software which is located in my desktop launcher.
And then today, ive got 3 times freezing (cant operate mouse and keyboard) the only thing works is just hard shut down. I dunno why.
First time i thought it is just coincidence but 3 times makes me wonder why? Can someone explain to me what happen? Ive read in another article, they said that maybe it is a kernel bug. But im not sure... Or maybe is it the graphic card compatibility? Because ive read that ubuntu doesnt work alongside with radeon.

Im thinking about to reinstall ubuntu again from fresh, but tell me what things first to do after installation? Do i have to update it from ubuntu software or how?
My machine spec:
Lenovo V310
8GB RAM
Core i5 7th Gen
AMD Radeon GPU

Sorry for my bad english, and for my newbie question. Hope someone can help me, so i can keep learning with this OS. Thx...

---

### Post by howefield on 2017-05-05
Would be good to know the full hardware specifications of the machine that you are using ?

---

### Post by dzanity on 2017-05-05
> **howefield said:**
> Would be good to know the full hardware specifications of the machine that you are using ?

Lenovo V310
8GB RAM
Core i5 7th Gen
AMD Radeon GPU

Is that enuff sir? :D

---

### Post by mastablasta on 2017-05-05
which amd radeon? what chip? does the PC also have intel GPU?

you read wrong that Ubutnu doesn't work with Radeon. in fact the linux drivers from AMD were made for Ubutnu first then for other distros. they worked with cannonical on patches etc. 


[LIST]
[*]check the os image after download and before install.
[*]you may need to install additional drivers (amdgpu pro or whatever they are called now). you likely have dual GPU aka hybrid graphics (intel and AMD). make sure you set it all up correctly after install.
[*]when there is an error it is good to know what it was. it might be in a log or you could always take a screenshot and post that.
[/LIST]

---

### Post by dzanity on 2017-05-05
> **mastablasta said:**
> which amd radeon? what chip? does the PC also have intel GPU?

you read wrong that Ubutnu doesn't work with Radeon. in fact the linux drivers from AMD were made for Ubutnu first then for other distros. they worked with cannonical on patches etc. 


[LIST]
[*]check the os image after download and before install. 
[*]you may need to install additional drivers (amdgpu pro or whatever they are called now). you likely have dual GPU aka hybrid graphics (intel and AMD). make sure you set it all up correctly after install. 
[*]when there is an error it is good to know what it was. it might be in a log or you could always take a screenshot and post that. 
[/LIST]


Yes, it is with intel GPU. And it is AMD Radeon R5 M430 2GB DDR3.
Hmm, maybe its missunderstanding, what i mean is, AMD not support yet for 16.04. CMIIW.
From some article in omgubuntu:
"Those of you on Radeon device should be aware that the standard AMD driver is** NOT SUPPORTED**  in 16.04 at this time. A future point release is expected to bring  support for the new AMDGPU driver. Expect a regression in system  performance if you upgrade."

Then, Where can i see the log when error?

---

### Post by mastablasta on 2017-05-05
logs are in /var/log

but also there should be a log viewer installed.

the radeon - that was with 16.04, the point releases then get new kernel and are known as hardware enablement (HWE) stack. more on this topic:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) 

as for the driver:
Radeon: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

edit: short explanation - Radeon is opensource and is used on older AMD chips. it is the only avaialble driver after the closed source fglrx was retired. AMDGPU is opensource driver for chips with new architecture, while AMDGPU-PRO is a hybird driver (part opensoruce, part closed source) and is again aimed at the very latest chips.

and amdgpu with hybrid graphics: [https://askubuntu.com/questions/760879/amdgpu-with-hybrid-graphics-16-04](https://askubuntu.com/questions/760879/amdgpu-with-hybrid-graphics-16-04)

intel has opensource drivers available in kernel.

it would be good for you to use the latest point verison of 16.04 or maybe even checkout 17.04, although 16.04 should get same kernel as 17.04 soon if it hasn't already.

---

### Post by dzanity on 2017-05-05
> **mastablasta said:**
> logs are in /var/log

but also there should be a log viewer installed.

the radeon - that was with 16.04, the point releases then get new kernel and are known as hardware enablement (HWE) stack. more on this topic:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) 

as for the driver:
Radeon: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

edit: short explanation - Radeon is opensource and is used on older AMD chips. it is the only avaialble driver after the closed source fglrx was retired. AMDGPU is opensource driver for chips with new architecture, while AMDGPU-PRO is a hybird driver (part opensoruce, part closed source) and is again aimed at the very latest chips.

and amdgpu with hybrid graphics: [https://askubuntu.com/questions/760879/amdgpu-with-hybrid-graphics-16-04](https://askubuntu.com/questions/760879/amdgpu-with-hybrid-graphics-16-04)

intel has opensource drivers available in kernel.

it would be good for you to use the latest point verison of 16.04 or maybe even checkout 17.04, although 16.04 should get same kernel as 17.04 soon if it hasn't already.

Thx for all your info. I really apreciate that...
Last night i reinstall again my ubuntu, because i really wonder why its freezing again, 5 times total in a day. LOL
Then, i know something, when i try to reinstall it again, i try not to choose install graphic, music components etc. And after install is done, nothings weird happen like i said before, it is automatically reboot after install, and work just normal up until now.
After that, i use apt-get update then install any package i need. So it is fix for now... :D

Btw thanx for all info, but i think i wont install gpu driver for this laptop, i dont want something weird happen again. lol

---

### Post by mastablasta on 2017-05-06
it means you are using Intel GPU only.

you coul dinstall the driver, but there should be a switch to enable hybrid mode. i don't knwo what the switch it. maybe someone with more experience with new drivers will come along and tell you. 

in the not so old days you would have installed the closed source driver and then basically initialise the hybrid mode and reboot.

---

