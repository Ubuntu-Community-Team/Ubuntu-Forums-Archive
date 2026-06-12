---
title: "Ubuntu Problems."
date: 2015-01-29
forum: New to Ubuntu
---

### Post by Ahmed_Elhalawani on 2015-01-29
Hello Ubuntu forums, I wished to join all the glory that is Linux by installing Ubuntu. I was using Windows 7 and burnt Ubuntu onto a disk then installed said disk. Installing went smoothly with little to no problems at all. I decided to dual-boot Ubuntu and Windows 7. Upon arrival to desktop my PC started to show visual artifacts, I ignored but then I had realized my PSU was overheated and the PC manually shut down. Upon booting again, this happened once again with Ubuntu. Then, I tried booting from Windows 7 and the PC is working fine, (I'm typing this from the PC.) I believe there is some type of compatibility error with my PSU and Ubuntu. I don't know my PSU, This current PC is a [HP Pavilion p6320y]("http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01969880-27") An oldish PC from 2009, The CPU is an  AMD Phenom II X4 820 If any of you have any advice that would be appreciated. Thank you and I look forward to joining Ubuntu

---

### Post by nerdtron on 2015-01-29
Probably Ubuntu is a bit heavier on heavier on resources on your older laptop. But have you cleaned the fans and exhaust grill of your laptop? Better airflow means lower temps and a happy system.

Also, you can try other "lighter" Ubuntu flavors like Xubuntu. 

**Note that if you decided to try install Xubuntu do not choose the option "Replace Ubuntu" because this may cause your hard drive to be wiped cleaned. If you want to install Xubuntu and replace Ubuntu, choose the "Something Else" option on the installer.
You probably don't know how to proceed here but post your screenshot in this forum and we'll help. This method will be safer than "Replacing Ubuntu".

---

### Post by mastablasta on 2015-01-30
you can install psensor to monitor the temperature: [http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/)
what kind of GPU do you have? did you install any additional drivers? : [http://askubuntu.com/questions/47506/how-do-i-install-additional-drivers](http://askubuntu.com/questions/47506/how-do-i-install-additional-drivers)
if not, did you enable any power management features? what is actually overheating the CPU or the GPU? is the CPU doing anything intensive while in Ubuntu?


note that default Ubutnu uses 3D hardware rendering to draw the desktop. this is likely similar to windows 7 but methods and scope could be different.

---

### Post by Impavidus on 2015-01-30
The PSU? That would be a first for me. Usually it's the graphics card, which is also indicated by your visual artefacts. So +1 to mastablasta.

---

### Post by Ahmed_Elhalawani on 2015-01-30
It's a generic 300w psu, ([http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01969880-27](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01969880-27)) I thought it would be the problem, it always runs loud and generates a lot of heat, Also this Pc
 has no GPU.

---

### Post by deadflowr on 2015-01-30
> **Ahmed_Elhalawani said:**
> It's a generic 300w psu, ([http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01969880-27](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01969880-27)) I thought it would be the problem, it always runs loud and generates a lot of heat, [B]Also this Pc
 has no GPU[/B].

It sure should.
You might be thinking dedicated card(which is where you'd see a card attached to a pcie/apg port or something) and not integrated(where the gpu is actually built in the board/cpu), which is probably what it is.

Anyway, if it's connected in anyway to a monitor is has a gpu.

Fer what it's worth though, your card as shown in the link is an nvidia geforce 9100.
you might see if it's a bad driver, or if a better one would suffice.
Unfortunately I do not know which nvidia driver would work best.
I think the nvidia-304 driver should work fine, but again not sure...

My sad experience with integrated cards is that they suffer from wear and tear faster than dedicated cards.
Simply because they share resources with the system, that a dedicated card does not.

---

### Post by Ahmed_Elhalawani on 2015-01-30
This was a kinda old dead computer I was trying to bring back to life. I don't really wish to invest into a new GPU for this PC. I kinda just wanted to mess with Ubuntu on a separate PC in case I screw up.
I can't even run Ubuntu for 2 minutes without PC manually shutting off from overheating so I can't really install the GPU drivers. 

Perhaps I could try [COLOR=#000000] Xubuntu. I also tried lower the Voltage of the CPU down to .6v and to 2.5 Ghz. It still will Crash almost instantly. 

Anyway, Thanks for helping  [/COLOR]

---

