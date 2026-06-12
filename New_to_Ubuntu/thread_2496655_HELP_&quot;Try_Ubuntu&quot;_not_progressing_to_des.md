---
title: "HELP: &quot;Try Ubuntu&quot; not progressing to desktop"
date: 2024-04-06
forum: New to Ubuntu
---

### Post by ddoubleuc on 2024-04-06
Hi Gang,

UPDATE: big thanx for your support gang - issue resolved

ORIG POST

I installed Ubuntu 22.04 LTS using Rufus onto an 8GB Sandisk Cruzer Switch. During boot, a text string appears repeating same or similar message but it's so fast all I discern amongst the text is error and possible abort. It then progresses to the select language screen then, when I Select "Try Ubuntu", the screen goes black and after 1 minute still no activity. I'm also not able to use any keyboard command or mouse to withdraw from the install so I close the PC down and restart. Is it my USB drive is too slow to run Ubuntu this way or? 

Thanks for considering

---

### Post by Rubi1200 on 2024-04-06
What make and model PC? What are the specs. especially RAM and graphics card?

---

### Post by ddoubleuc on 2024-04-07
Thanx for your time Rubi and, as requested:

Acer Predator PH315-54 Helios 300 > CPU: 8-core 11th Gen Intel Core i7-11800H MHz > RAM 16gb > per inxi -G ... Graphics Microsoft driver: dxgkrnl v: 2.0.2 Display: wayland server: Microsoft Corporation X.org driver: gpu: dxgkrnl,dxgkrnl OpenGL: renderer: D3D12 (Intel UHD Graphics) v: 4.1 Mesa 23.2.1-1ubuntu3.1~22.04.2.

I hope this assists and, if u want any other specs, I'll try to find appropriate inxi options to draw them.

---

### Post by ajgreeny on 2024-04-07
Did you check the ISO file used to create the live USB is a good download?

If not either download it again or carry out the advised check of its shasum which you can do from Windows.

---

### Post by ddoubleuc on 2024-04-07
thanx for touching base ajgreeny … no I didn’t … I’ll run the check as suggested … thanx again

---

### Post by tea for one on 2024-04-07
> **ddoubleuc said:**
> Acer Predator PH315-54 Helios 300 
Graphics Microsoft driver: dxgkrnl 
Does your PC have Nvidia GPU?

Verify your ISO (as suggested by ajgreeny)
Boot your USB and select "Try Ubuntu (safe graphics)"

---

### Post by MAFoElffen on 2024-04-07
Your laptop's main GPU is NVIDIA® GeForce RTX&#8482; 3060 with 6 GB dedicated memory...

Use the Safe graphics option... Or:
At the initial Grub Menu, Press the <E> key to get into an edit mode > <Arrow-Down> to the line that starts with the word "linux" > <Arrow-Right> until the cursor is passed the words "quiet splash" > Add the word "nomodeset" without those quotation marks. > Press the keys <Cntrl><X> to boot.

Remember that process for your machine. If you do install Natively on your hardware, you will need to rember how to do that on the first reboot, to get your graphics working until you install your NVidia Drivers. That is, if your forget to check the "Install 3rd Party drivers..." checkbox during the install. Or if for some reason, it doesn't install it with that option checked. It's a 3rd Party licensing thing.

---

### Post by ddoubleuc on 2024-04-07
Hi T41 ... thanx for assisting ... "Try Ubuntu (safe graphics)" mode enabled access

---

### Post by ddoubleuc on 2024-04-07
Thanx MAFoE ... "Try Ubuntu (safe graphics)" mode enabled access

---

