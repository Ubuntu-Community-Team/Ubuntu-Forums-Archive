---
title: "Stuck on Unity 2d!"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-09-29
How can I get out of Unity 2D and into plain Unity? Help Please!

---

### Post by Myki on 2012-09-29
When you first boot, you should arrive at a log in screen. 

Example (image via Google search) 

[IMG]http://imageshack.us/a/img580/4505/lightdmunitygreeter.png[/IMG]

See the Ubuntu icon? That's what you want to click to get back to your Unity 3D experience.

edit: If you already know this, but just a matter of Unity 3D not loading or something, simply reset it to defaults.

In the terminal, type the following: unity --reset

That's it.

---

### Post by TheMTtakeover on 2012-09-29
> **Myki said:**
> When you first boot, you should arrive at a log in screen. 

Example (image via Google search) 

[IMG]http://imageshack.us/a/img580/4505/lightdmunitygreeter.png[/IMG]

See the Ubuntu icon? That's what you want to click to get back to your Unity 3D experience.

edit: If you already know this, but just a matter of Unity 3D not loading or something, simply reset it to defaults.

In the terminal, type the following: unity --reset

That's it.

I tried doing unity --reset. I guess I should also mention that It has been stuck in 2D since the start on this computer. But I know I have the specs to handle it. My last dell could handle it fine and this one is a much faster/better machine.

---

### Post by newb85 on 2012-09-29
What graphics card and drivers are you using?

---

### Post by Frogs Hair on 2012-09-29
Check for 3D support with this command.```
/usr/lib/nux/unity_support_test -p
``` 

Graphics card/chip information.```
lspci
```

---

### Post by grahammechanical on 2012-09-29
You do not state which version of Ubuntu you are using. If it is 11.10 or 12.04 then you will only get Unity 2D until you install a proprietary driver using Additional Drivers.

I mention this because you say:

> It has been stuck in 2D since the start on this computer.

I think that with 12.04 if you tick to install third party software during the install then a proprietary video driver is installed and you get Unity (3D) from the beginning.

I am testing 12.10 and I get Unity 3D with both the Nvidia driver and the Nouveau driver (open source). So, that is an improvement and there is a tab in Software Sources  for Additional Drivers. So, on 12.10 if you do not install the proprietary driver as third party software you go to Software Sources to install it afterwards.

Regards.

---

### Post by deadflowr on 2012-09-29
Here's your other post about windows snapping I believe the issue of Unity2d was brought up.

[http://ubuntuforums.org/showthread.php?t=2063638]("http://ubuntuforums.org/showthread.php?t=2063638")

Hopefully someone with better knowledge on Nvidia cards can give you a clearer answer/workaround to get it to run properly.

---

### Post by TheMTtakeover on 2012-09-29
> **Frogs Hair said:**
> Check for 3D support with this command.```
/usr/lib/nux/unity_support_test -p
``` 

Graphics card/chip information.```
lspci
```

The first ones results are:

```
Error: GLX is not available on the system
```

The second one outputs:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

---

### Post by TheMTtakeover on 2012-09-29
> **grahammechanical said:**
> You do not state which version of Ubuntu you are using. If it is 11.10 or 12.04 then you will only get Unity 2D until you install a proprietary driver using Additional Drivers.

I mention this because you say:



I think that with 12.04 if you tick to install third party software during the install then a proprietary video driver is installed and you get Unity (3D) from the beginning.

I am testing 12.10 and I get Unity 3D with both the Nvidia driver and the Nouveau driver (open source). So, that is an improvement and there is a tab in Software Sources  for Additional Drivers. So, on 12.10 if you do not install the proprietary driver as third party software you go to Software Sources to install it afterwards.

Regards.

My apologies. I am using Ubuntu 12.04. I did mark that tick, and when I check under additional drivers is says, "There is no proprietary drivers are in use on this system."

I tried to download a driver for my graphics card following instruction online from the bumblebee project but it kept bringing up errors.

---

### Post by TheMTtakeover on 2012-09-29
> **deadflowr said:**
> Here's your other post about windows snapping I believe the issue of Unity2d was brought up.

[http://ubuntuforums.org/showthread.php?t=2063638]("http://ubuntuforums.org/showthread.php?t=2063638")

Hopefully someone with better knowledge on Nvidia cards can give you a clearer answer/workaround to get it to run properly.

Yeah, thank you. I hope it isn't a violation to make a new thread. I just thought since we figured out why the windows weren't working I would open a new thread for the problem.

---

### Post by deadflowr on 2012-09-29
See if mips advice in this thread helps:

[http://ubuntuforums.org/showthread.php?t=1972287]("http://ubuntuforums.org/showthread.php?t=1972287")

For the record, I don't see a problem with starting a new thread. The first thread was answered, so now solving the problem discovered in the first thread should be paramount. I think keeping this in the first thread would probably cause confusion between posts about drivers, and compiz issues. I think is was wise, if a mod or admin thinks otherwise, they'd probably merge em, or something.

---

### Post by Frogs Hair on 2012-09-29
> The first ones results are:

Code:
Error: GLX is not available on the system

It looks like you can't run Unity  3D . Open additional drivers and see if there are any drivers available. I don't know if the link in the last post will help since you have Intel graphics and not Nvidia but you could look into it further.

---

