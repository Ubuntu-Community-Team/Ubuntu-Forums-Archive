---
title: "Laptop compatibility issue"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by zaibi007 on 2012-11-11
hi Friends....
i've  Toshiba Satellite** L-500 T-21** with
[B]Intel core i3 @2.13 GHZ M330
Ram 6GB
Hd 320GB
Ati Mobility Readon 4500 series[/B]

[SIZE="2"][FONT="Arial Black"]Problem:[/FONT][/SIZE]
i've tried Ubuntu twice in my machine, once X64 then X32. it has win-7 before my tries and after my tires contains the same.
Problem is that, during installation my machine became overheated and system halted during installation.
by using cooling pad, i successfully installed the OS but then it just drain my battery just in 30 Mins :(:o 4400mAh battery just in 30 minutes.....
overheating disturbed me as well after installation too... so reluctantly i just removed the OS and got back Win7 X32...

i installed Ubuntu with Ext4 in main drive and other drives were not chnged. they were on the same file system as were on win7 i.e NTFS
later on in my 2nd try of ubuntu 12.4 X32, i changed the whole hd's partitions into Ext4 and installed the Os but the same problem existed...

plz guide me what to do to have Ubuntu in my lappy without any problem

---

### Post by NikTh on 2012-11-11
Hi , 
as you have now the Win7 OS , search and find if any BIOS upgrade is available. **Search Only** in manufacturer's page (not unofficial). If a BIOS upgrade is available then proceed to upgrade. 

Problems as you described , are probably  due to ACPI + Kernel incompatibility. BIOS upgrade maybe solve battery's problem. 

The other problem , with temperature , is probably due to open source ATI driver radeon. Some "manual hacking" needed there to drop down the temperatures , of you can install the fglrx (closed source) driver and see how is going. 

Thanks

---

### Post by zaibi007 on 2012-11-12
> **NikTh said:**
> Hi , 
as you have now the Win7 OS , search and find if any BIOS upgrade is available. **Search Only** in manufacturer's page (not unofficial). If a BIOS upgrade is available then proceed to upgrade. 

Problems as you described , are probably  due to ACPI + Kernel incompatibility. BIOS upgrade maybe solve battery's problem. 

The other problem , with temperature , is probably due to open source ATI driver radeon. Some "manual hacking" needed there to drop down the temperatures , of you can install the fglrx (closed source) driver and see how is going. 

Thanks
thanks for your suggestions...

yupz.. there were bios upgrade and my machine was running **@updated bios **before attempted UBUNTU....

after that no new update is available...
the all information i can get abut the current bios is that its windows based OS Independent Bios from Toshiba. so OS Independence tag doesn't means that any Os can be installed on Machine..??? I've no idea about that.
now should i believe that my machine's bios firmware and Kernel is not compatible with **LINUX**...???

if bios problem solved, if it exists, then **ATI Readon's kernal** shall not be any issue.. it'll be solved later on as it is the secondary matter.

---

### Post by Mark Phelps on 2012-11-12
BIOS's are not Windows-based any more than they are Linux-based.  BIOS is independent of any operating system.  What IS Windows-based or Linux-based can be the TOOL that is used to update the BIOS.

Most PCs still run a version of Windows, so laptop manufacturers usually provide BIOS updates using Windows-only utilities.

Unlike others, I generally advise AGAINST BIOS updates.  These are done to address very specific issues (like adding a new processor model to an existing line for a motherboard).  Any mistakes encountered or caused during a failed BIOS update leaves you with an "electric brick".

Overheating is, unfortunately, a common problem with today's laptops running Linux versions because these PC's are built to run using Windows drivers that automatically throttle back the processors to keep down the heat levels.  Linux nearly always does NOT have these drivers, so the processors run a higher levels, generating more heat.

While it's possible, it's very unlikely, that a BIOS update is going to "fix" the overheating problem -- because as originally built and shipped, the laptop does not have an overheating "problem".  That problem only appears when you replace the original Windows OS that came on the laptop with something else.

---

### Post by zaibi007 on 2012-11-13
> **Mark Phelps said:**
> BIOS's are not Windows-based any more than they are Linux-based.  BIOS is independent of any operating system.  What IS Windows-based or Linux-based can be the TOOL that is used to update the BIOS.

Most PCs still run a version of Windows, so laptop manufacturers usually provide BIOS updates using Windows-only utilities.

Unlike others, I generally advise AGAINST BIOS updates.  These are done to address very specific issues (like adding a new processor model to an existing line for a motherboard).  Any mistakes encountered or caused during a failed BIOS update leaves you with an "electric brick".

Overheating is, unfortunately, a common problem with today's laptops running Linux versions because these PC's are built to run using Windows drivers that automatically throttle back the processors to keep down the heat levels.  Linux nearly always does NOT have these drivers, so the processors run a higher levels, generating more heat.

While it's possible, it's very unlikely, that a BIOS update is going to "fix" the overheating problem -- because as originally built and shipped, the laptop does not have an overheating "problem".  That problem only appears when you replace the original Windows OS that came on the laptop with something else.

HmmmmMMmm Got your point dear....

so is there any fix to reduce heat in laptop while running Linux. should i go for the Linux specific drivers available either at Intel's Website or Toshiba's Website or at AMD's Website as my lappy's Graphic card is of AMD, ATI Mobility Readon

---

### Post by Linuxisfast on 2012-11-13
The first thing you would do is install the proprietary catalyst driver for your amd card via hardware drivers, this will solve your heat issue.

---

### Post by gbrowning on 2012-11-13
I agree with Markphelps and with Linuxisfast, the BIOS is not a problem. You are probably using the Unity desktop.  Go to system settings (the gear/wrench icon) then click on "additional drivers" under Hardware.  Let the system try to find additional drivers for you.  It will likely find the ATI/AMD FGLRX drivers.  There are two, install them one at a time.  Often the second driver will not install.  That's OK.

---

### Post by sammiev on 2012-11-13
I have much the same laptop but my video card is Intel. I would look at your video card. What are your temps?

---

### Post by gbrowning on 2012-11-13
This list is  a bit heavy for someone new to Linux.  I lifted it from a 2009 post by Knifemonk regarding energy efficient Ubuntu machines.  I cannot endorse these packages but would definitely explore them if I were on a laptop and having battery life problems.

[I]cpufreqd
 fully configurable daemon for dynamic frequency and voltage scaling

 cpufrequtils
 tools to switch between frequency modes, availability depends on your kernel: conservative, ondemand, or performance modes exist.

 cpudyn
 It saves battery, lowers temperature, and can put the computer disks in standby mode if a given period has passed without any I/O operation.

 powertop
 finds the software component(s) that make your {system} use more power than necessary while it is idle. - (this one is really smart)

 upower
 an abstraction of the power controls present in HAL which are now officially obsolete... not yet fully implemented(?).

 cpulimit
 limits the cpu usage of a process, good when something is causing an overload or simply to reduce the load.

 procmeter3
 my fav system monitor- temp, load, usage, in, out, average, etc. cpu, gpu, hdd, network. if it gives a reading, this little beastie will pick it up and give you the facts.

 pm-utils
 suspend / hibernate... this is what you want to know about for these functions.

 bum / rcconf
 these let you disable the things that lurk in the background eating power and resources.[/I]

---

