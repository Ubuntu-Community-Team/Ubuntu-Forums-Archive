---
title: "Laptop thinkbook 15 g2 Itl boots forever and black screen after Ubuntu 20.04 install"
date: 2021-12-27
forum: New to Ubuntu
---

### Post by krasimalchev on 2021-12-27
I have bought laptop thinkbook 15 g2 Itl with 40 GB ram, Intel core I7, Intel iris xe, and ssd 1 TB. I have connected it to an external monitor Dell Ultrasharp U2422HE and installed Ubuntu 20.04. 3 LTS desktop from a USB stick. After restart at the end of the installation the laptop didn't switch on the display and only CAPSLK, NUMLK, and ESC (funclock) buttons are enlighten on the laptop. After some seconds only ESC button stays enlightened and then the laptop is automatically restarted. And this continues until I press the power button long to switch off the laptop. I tried to press the Novo button but the display is still off and the laptop again restarts. I have tried any function buttons combinations without success.

 

Can you please help me sove this issue?

---

### Post by oldfred on 2021-12-27
Does 20.04.3 boot in live mode? If not try 21.10.
We typically recommend LTS versions, but new hardware may need newer version.
Often very new hardware like yours needs the very newest kernel, drivers and then latest distribution to include those. Or even a ppa to add even new kernels that are not yet in a distribution.

If you press escape right after Lenovo screen, but before grub menu would normally show, do you get a grub menu? 
May have to try several times as timing is tricky. And if you have UEFI fast boot on, you may not have any time at all.
And then can you boot recovery mode, second line or from sub-menu?

It may be boot issue, but often black screen is after boot and then a video issue. Do you just have Xe or nVidia also?
If grub does not have Windows in menu, so it thinks it is a single boot, it will not show menu by default.

Supposedlyl it should work. But may need settings in UEFI or boot parameters in grub.
[https://ubuntu.com/certified/202008-28154](https://ubuntu.com/certified/202008-28154)

---

### Post by grahammechanical on 2021-12-27
Did you install Ubuntu with the external monitor connected or disconnected? Does  Ubuntu load with the external monitor disconnected. I think that it is best to get Ubuntu working on a laptop's built in  hardware and then connect external components such as external monitors.

Regards

---

### Post by tea for one on 2021-12-27
> **krasimalchev said:**
> I have connected it to an external monitor Dell Ultrasharp U2422HE and installed Ubuntu 20.04. 3 LTS desktop from a USB stick. After restart at the end of the installation the laptop didn't switch on the display 

Which display?
External monitor or laptop display?

Good advice from [COLOR="#0000FF"]grahammechanical[/COLOR] - Concentrate on the laptop first and then consider the external monitor.

More sound advice from [COLOR="#0000FF"]oldfred[/COLOR] - New hardware may need a more recent kernel.

You could run the recently created utility, designed to provide relevant system information so that forum members can offer suitable advice.

[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

---

