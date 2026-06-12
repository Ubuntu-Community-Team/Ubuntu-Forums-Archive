---
title: "[SOLVED] Help with using my S-video with ubuntu"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by sdiaz411 on 2008-05-12
I am very new to Linux, My brother had installed ubuntu on my desk top PC. The PC is a Hewitt packer, OS windows xp on a separate hard drive. Mb ram is 512, video card is 64 MB Nvidia Gforce MX 4000 PCI card. Also I have an Intel on-board video card, which is not the primary video under bios. I am trying to use my 42 inch, plasma television with my S-video Nvidia Gforce MX 4000 PCI card. When I boot the PC with ubuntu, I see the loading of the ubuntu, but when it comes to signing in with user name, there is nothing on the screen. So i know the system boots but I don't think that the driver for the S-Video is there. Does anyone have any information for me, remember I am a big noob. What I want to do is be able to use my plasma TV with my PC so I can start learning to use ubuntu. Please someone help me. thank you. If i am missing any information please let me know.

I am using ubuntu 8.04 version. also if there is a site that can help me to learn how to use Linux better, please help me out, thank you.

---

### Post by nemesisau on 2008-05-13
You'll need to have a regular monitor plugged in to start with for this, I'm guessing...

Open System>Administration>Hardware Drivers and check that you're using the newest nvidia drivers. If there's a green dot and a tick, then you are. You can open Synaptic and search for "nvidia-settings".  A new shortcut will appear in Admin. with the nvidia logo, you can change screens etc from there, similar to the windows desktop config screens.

If you aren't running the latest, still open Synaptic and search for "nvidia-glx-new" first.

Hope it helps.

---

### Post by Cadmus on 2008-05-13
One small niggle I had with the nvidia setting sprograms is when I tried to edit the setting for both screens at once (rather than seting up one, comitting it, then seting up the nex) it segfaulted.

---

### Post by sdiaz411 on 2008-05-13
Well OK i had opened the synaptic package manager, and i had searched for "nvidia-glx-new" and "nvidia-settings" and there are no packages is says. also when i go to hardware drivers and under the device driver, under that it says "nvidia" and to the right it is enabled but the status says (with a red circle in front) Not in use. also when i put the mouse over the word "nvidia" it gives me a description saying, "This driver is necessary to support the hardware, there is no free/open alternative. If this driver is not enabled, the hardware will not function."

so i must not have the updated driver for my card. i believe that we had found an update it is called "NVIDIA-Linux-x86-1.0-9755-pkg1.run" and we went to the terminal and tried running it but kept saying the command was not found. I am very new to this and i really want to learn how to use linux. i have looked around for this information but there isn't really any step by step information. seems like everyone writes as if i am suppose to know it. also i have been trying to look for places to where i can learn how to use ubuntu better, any ideas... thanks for the help.

---

### Post by philinux on 2008-05-13
Have you got all your sources ticked, and installed ubuntu-restricted-extras

---

