---
title: "Temperature"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by Merisi on 2011-09-23
As much as I'm enjoying Ubuntu, I can't help but notice my pc (it's a desktop) has been getting a lot hotter and I've read that other people have experienced the same issue.  Can anyone tell me how I can lower the temperature and reduce stress on my pc and also why Ubuntu seems to create higher temperatures.

---

### Post by kaldor on 2011-09-23
Which graphics card do you have? If you have an NVIDIA or AMD (ATI) card, you should install the Proprietary driver to fix heat problems. Check the Additional Drivers (Jockey) program for this.

By default Ubuntu uses the open source drivers for NVIDIA and AMD cards. These cards lack some power management abilities which cause heat issues.

---

### Post by aura7 on 2011-09-23
install [B][https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

[/B]and check your temp[B].

compare it with windows ..... there you have core temp
[/B]

---

### Post by Merisi on 2011-09-23
> **kaldor said:**
> Which graphics card do you have? If you have an NVIDIA or AMD (ATI) card, you should install the Proprietary driver to fix heat problems. Check the Additional Drivers (Jockey) program for this.

By default Ubuntu uses the open source drivers for NVIDIA and AMD cards. These cards lack some power management abilities which cause heat issues.

I am using an NVIDIA and I have two options with jockey: version current which I opted for and version 173 which is unactivated.

---

### Post by kaldor on 2011-09-23
> **Merisi said:**
> I am using an NVIDIA and I have two options with jockey: version current which I opted for and version 173 which is unactivated.

So you were already using the Current driver?

---

### Post by Merisi on 2011-09-23
> **kaldor said:**
> So you were already using the Current driver?

Yes but would that need to be updated through update manager as I have the default setting for that which doesn't seem to include some third parties.

---

### Post by Blasphemist on 2011-09-23
I can't say that I agree about the video cards. I do have to edit the kernel boot line in Grub2 to get my fan to run well on this Satellite laptop. acpi_osi=Linux [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by kaldor on 2011-09-23
> **Merisi said:**
> Yes but would that need to be updated through update manager as I have the default setting for that which doesn't seem to include some third parties.

I doubt that would help at all. In many cases, heat issues are caused by the open source drivers. Since you were already using the current proprietary driver, that doesn't apply to you. 

It could just be that Ubuntu runs hotter than Windows in your situation.

---

### Post by grahammechanical on 2011-09-23
I find that xsensors works very well. It has a GUI that shows real time CPU and motherboard temperatures as well as fan speeds. If you are using an Nvidia driver then you also get the Nvidia X server Settings Utility. That has a section for thermal settings that will show you the graphic card temperature if that is possible.

Make sure the fans are working. Keep the vents unblocked. Dust will block up vents and trap heat in the motherboard.

Oh, at the moment my CPU temperature is 44 degrees and the motherboard is 36 degrees. And the CPU fan is doing 937 rpm and the two chassis fans 1028 and 1205 rpm. The graphic card temperature is 44 degrees (in the green).

I am using Ubuntu and the Nvidia driver and I do not have desktop temperature heat stress.



Regards.

---

### Post by oldsoundguy on 2011-09-23
Check your fans and open the box up and use canned air and blow the dust bunnies and cat and dog hair out.

I am running a 3.06 Hyperthreaded (a real heat monster) and it runs 24/7 and the processor/memory is in constant use via using BOINC items running in the background. My constant cpu temp is 46C according to the applet. But I added a large heat pipe cooler to the CPU, an added fan on the NVidia card and an extra exhaust case fan (coolermaster all the way).

---

### Post by Merisi on 2011-09-23
> **grahammechanical said:**
> I find that xsensors works very well. It has a GUI that shows real time CPU and motherboard temperatures as well as fan speeds. If you are using an Nvidia driver then you also get the Nvidia X server Settings Utility. That has a section for thermal settings that will show you the graphic card temperature if that is possible.

Make sure the fans are working. Keep the vents unblocked. Dust will block up vents and trap heat in the motherboard.

Regards.

I literally just checked the temperature and it's 65c.  Fans are working ok and it won't be dust as my pc is only a few months old.

---

### Post by Merisi on 2011-09-23
> **oldsoundguy said:**
> Check your fans and open the box up and use canned air and blow the dust bunnies and cat and dog hair out.

I am running a 3.06 Hyperthreaded (a real heat monster) and it runs 24/7 and the processor/memory is in constant use via using BOINC items running in the background. My constant cpu temp is 46C according to the applet. But I added a large heat pipe cooler to the CPU, an added fan on the NVidia card and an extra exhaust case fan (coolermaster all the way).

I was hoping I wouldn't have to resort to opening my pc and adding more fans.  The hard drive seems okay, it's just the gpu that is getting fried.

---

### Post by Blasphemist on 2011-09-23
Which video card do have and what driver showed as in use? Use this if you need for determining your card.
```
lspci -k
```
That should show the card and driver in use as in my example here.
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Toshiba America Info Systems Device ff10
	Kernel driver in use: i915
	Kernel modules: i915


---

### Post by wildmanne39 on 2011-09-23
Hi, I have used a nvidia card in a desktop and laptop for several years, and the desktop has never run hot, however the temperature does increase by 20 degree's when I watch movies on hulu in full screen mode but it is still within the temperature range for my card.

I have an older card the 6150 and I use the 173 driver it work's better for my card.

I can tell you that even after a few months a computer can get dirty inside, I am not saying that is the problem but it happens, I clean my computer at least every 6 months.

Have you research what the temperature range of your card is? 

You may just think it is to hot comparing it to windows temp but temperature information is not always correct, so I suggest to find out the range that is acceptable according to the manufacturer.
Thank you

---

### Post by Merisi on 2011-09-24
> **wildmanne39 said:**
> Hi, I have used a nvidia card in a desktop and laptop for several years, and the desktop has never run hot, however the temperature does increase by 20 degree's when I watch movies on hulu in full screen mode but it is still within the temperature range for my card.

I have an older card the 6150 and I use the 173 driver it work's better for my card.

I can tell you that even after a few months a computer can get dirty inside, I am not saying that is the problem but it happens, I clean my computer at least every 6 months.

Have you research what the temperature range of your card is? 

You may just think it is to hot comparing it to windows temp but temperature information is not always correct, so I suggest to find out the range that is acceptable according to the manufacturer.
Thank you

I have the NVIDIA GTS 240 which appears to be notorious for heat however it can operate to almost 100c so I am well under the limit.

---

### Post by wildmanne39 on 2011-09-24
Hi, that is a newer card then mine, and as long as you are well under the limit I would not worry about it then, but that is just my opinion.
Thank you

---

### Post by nrundy on 2011-09-24
@Merisi,

The heat/power issue affects all graphics drivers, even the integrated Intel ones on the Sandy Bridge CPUs. The fault lies in the Linux Kernel. Unfortunately not enough is being done to address power. The last several Kernel releases have all introduced major power regressions. The situation is only getting worse with the new CPUs (e.g., Sandy Bridge with kernel 3.0 and 3.1).

There is no real fix at the moment. I'd suggest filing bug reports with Linux Kernel folks and expressing your desire for them to iron out these power bugs.

A good place to read up on the issue is phoronix.com. But you can also find numerous bug reports from users on all the linux distro sites.

It is a huge disappointment because even though I prefer to use Linux, these power/heat issues have forced me to switch to Windows on laptops/netbooks because Windows gets much better battery-life and lower heat than Linux. I don't think there's much Canonical/Ubuntu can do about it though. The Linux-Kernel people need to fix it.

---

### Post by Merisi on 2011-09-24
> **nrundy said:**
> @Merisi,

The heat/power issue affects all graphics drivers, even the integrated Intel ones on the Sandy Bridge CPUs. The fault lies in the Linux Kernel. Unfortunately not enough is being done to address power. The last several Kernel releases have all introduced major power regressions. The situation is only getting worse with the new CPUs (e.g., Sandy Bridge with kernel 3.0 and 3.1).

There is no real fix at the moment. I'd suggest filing bug reports with Linux Kernel folks and expressing your desire for them to iron out these power bugs.

A good place to read up on the issue is phoronix.com. But you can also find numerous bug reports from users on all the linux distro sites.

It is a huge disappointment because even though I prefer to use Linux, these power/heat issues have forced me to switch to Windows on laptops/netbooks because Windows gets much better battery-life and lower heat than Linux. I don't think there's much Canonical/Ubuntu can do about it though. The Linux-Kernel people need to fix it.

Thank you for your honesty with this answer.  I think it's a shame too because it means it will put a lot of people off Linux.  I'm going to stick to with Ubuntu because I enjoy it so much and hopefully my gpu will handle the added heat.

---

