---
title: "snd_hda_intel 0000:00:1f.3: failed to add i915 component master (-19)"
date: 2015-11-06
forum: New to Ubuntu
---

### Post by juliancyh on 2015-11-06
[COLOR=#111111][FONT=Ubuntu]Questions:[/FONT][/COLOR]
[LIST=1]
[*]What is i915 component master?
[*]What are the outcome(s) of failing to add i915 component master?
[*]How do I resolve/remove this failure notice?
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Background Info:[/FONT][/COLOR]
[LIST]
[*]This failure notice at bootup and shutdone of Ubuntu 10.5.
[*]My built consist of ASUS Z170M-Plus mobo, NVidea graphic card Ubuntu 10.5 OS that uses linux kernel 4.2.0-16-generic and Nvidia binary driver 352.55.
[*]I am surprise that this failure notice appears as Ubuntu is operational and I can watch and hear videos and music.
[*]snd_hda_intel appears to be an intel audio driver in the linux kernel that communicates with the ALSA kernel core and z170M-Plus audio hardware controller. Pls correct me if I am wrong.
[*]0000:00:1f.3 is the PCIe slot of the built is audio device of the ASUS mobo.
[/LIST]
00:1f.3Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)	Subsystem:ASUSTeK Computer Inc. Device 86c7	Flags:bus master, fast devsel, latency 32, IRQ 125	Memoryat f7140000 (64-bit, non-prefetchable) [size=16K]	Memoryat f7120000 (64-bit, non-prefetchable) [size=64K]	Capabilities:[50] Power Management version 3	Capabilities:[60] MSI: Enable+ Count=1/1 Maskable- 64bit+Kerneldriver in use: snd_hda_intel

---

### Post by tgalati4 on 2015-11-06
i915 is the Intel video chipset.  Perhaps there is a link between the Intel sound chip and the Intel graphics chip (if you have one).  Is your on-board video chip turned off in BIOS?  Turn it on and see if the message goes away.  Perhaps it is used to synchronize sound and video.

---

### Post by juliancyh on 2015-11-06
[COLOR=#111111][FONT=Ubuntu]The boot failure notice disappeared from the bootup and shutdown screens after I executed the below commands and after the system rebooted.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo apt-get purge nvidia*[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo service lightdm stop[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I do not understand the logic for this occurrence. I think the Dynamic Kernel Module Support (DKMS) which rebuilt the kernel during the command sudo apt-get purge nvidia* had something to do with eliminating the failure notice "snd_hda_intel 0000:00:1f.3: failed to add i915 component master (-19)". Partial answer to question 3. However, I noticed the failure notice was still in dmesg. 

I then rebooted the system and went to view the UEFI to see if the video chip was turn on. Primay graphics was set to CPU Graphics. I changed it to Auto. Good news is that the failure notice no longer appears in dmesg and the bootup and shutdown screens.      

Thanks for your reply tgalati4.[/FONT][/COLOR]

---

### Post by matt_symes on 2015-11-06
Hi

> What are the outcome(s) of failing to add i915 component master?

If you revert your changes do you get sound out from your HDMI port ?

Kind regards

---

### Post by juliancyh on 2015-11-14
[SIZE=2][FONT=arial]Hi matt_symes, tgalati4,

Apologies for the late reply. 

From a week of reinstallations activities, I discovered the failure notice is caused by a setting in the ASUS UEFI. 
The failure notice appears when in Advance Mode of the [/FONT][/SIZE][FONT=arial]UEFI[/FONT][SIZE=2][FONT=arial], the tab ( "Advance" --> "Advance\Systems Agent (SA) Configuration" --> "Graphic Configuration" --> "iGPU Multi-Monitor" ) is set to "Disabled". 
However, when "iGPU Multi-Monitor" is "Enabled", dmesg shows:  
[/FONT][/SIZE][SIZE=2][FONT=arial]snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])[/FONT][/SIZE]
[SIZE=2][FONT=arial]snd_hda_intel 0000:01:00.1: Disabling MSI[/FONT][/SIZE]
[SIZE=2][FONT=arial]snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]At the same time, when "[COLOR=#111111]Primary Graphics" is set to "CPU Graphics", there is audio from ASUS mobo HDMI and Line-Out-Port.
However,  [/COLOR]when "[/FONT][/SIZE][SIZE=2][COLOR=#111111][FONT=Ubuntu][FONT=arial]Primary Graphics" is set to "Auto" or "PCIe", there is only audio from ASUS mobo Line-Out-Port. Audio from HDMIs of both mobo and NVIDIA graphic card are disabled.[/FONT][/FONT][/COLOR][/SIZE]

[FONT=Ubuntu][COLOR=#111111]The above occurrences  are  repeatable and should supersede my previous explanations/descriptions made my earlier post.

Does this means the "i915" (Intel Video Chip) is represented in ASUS UEFI as "[/COLOR][/FONT][FONT=arial]iGPU Multi-Monitor"?
 [/FONT][FONT=Ubuntu][COLOR=#111111]
Do you know if it is possible to activate audio from both NVidia graphic card HDMI and the mobo Line-Out-Port at the same time?   Should I post this as a separate post or continue from this post? 

Thanks.

[/COLOR][/FONT][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by tgalati4 on 2015-11-14
Is there a BIOS/UEFI update for your Asus?  Send an email to Asus describing your problem.  I presume that when Primary Graphics is set to Auto or PCIe that you want the nVidia HDMI sound to work.  It may be a problem with the proprietary nVidia driver.  The i915 error messages seem consistent with your UEFI settings, so unless your Intel sound isn't working, I wouldn't worry about it.

Perhaps a newer kernel will help, but 4.2 is pretty new.

Is this machine dual boot?  Does sound work as expected in Windows?

---

