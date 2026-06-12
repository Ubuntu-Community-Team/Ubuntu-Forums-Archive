---
title: "Windows and Ubuntu on same router"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by chimchim on 2008-05-02
I have a PC with Ubuntu 8.04 installed which works fine independently. I also have a PC with Windows XP which works fine independently, they will even work OK for the first time they are connected to the same router (NOT wifi). However, when the Ubuntu PC is switched off its BIOS settings become corrupted and it will not reboot without I reset the BIOS. The Windows PC does not have this problem. Usually it is the BIOS system time setting only which is corrupted but it is not unusual for the whole setup to be corrupted and set to default.
On the Ubuntu PC the BIOS system time is set to GMT and the time zone to GMT+2. On the Windows PC the BIOS system time is set to GMT+2.
I had the same problem with Ubuntu 7.10 and have spent hours searching for a solution. I am now running on empty and would appreciate some help.
Thankyou for reading.

---

### Post by yamawho on 2008-05-02
Man ... I never heard of such a thing  :confused:

I have 12 systems running on my wired router and 2 laptops on wireless without issues ...

Most run XP but also running Xandros, Mandriva, Ubuntu, Linix Mint, Mepis and FreeNAS.

---

### Post by y-aji on 2008-05-02
Let me make sure I understand.  Your Linux PC bios corrupts when it is plugged into the router with the windows system?

---

### Post by chimchim on 2008-05-02
Hi yamawho.  You have now!

Hi y-aji.  No. The BIOS gets corrupted when I switch off the Linux PC. The next time I switch it on I have to reset the BIOS.

---

### Post by eriqjaffe on 2008-05-02
If the BIOS is having troubles, it may be as simple as replacing the CMOS battery.

---

### Post by chimchim on 2008-05-02
Hi eriqjaffe

I have replaced the battery (although it was not necessary), I have replaced the MB and flashed the latest bios. I have run memtest for 8 passes with no errors and even changed the OS. I am convinced this is not a hardware problem. Both these PCs work fine independently, only when both are accessing the router does the problem occur.
Thanks for responding.

---

### Post by Fatal Equinox on 2008-05-02
would it be hard for you to run one of them  off wifi to verify that it is infact a router issue?

---

### Post by mlentink on 2008-05-02
So....
How about replacing your router?

Although frankly, I've never heard about an OS being able to reset a BIOS upon reboot before. I'm 99.99% convinced Ubuntu will not do that for you.

---

### Post by jimv on 2008-05-02
Just for kicks, see if turning off the Windows Time service on the XP box helps.

Go to Start>Run and type in Services.MSC
Scroll down until you see Windows Time, right-click on it and click Stop
Right-click Windows Time again and click Properties
Set Startup Type to Disabled
Click ok


Now wait and see if the issue with the Linux box keeps happening.  It could be that your XP box is running an NTP server that is somehow screwing things up.

---

### Post by chimchim on 2008-05-03
Hi Guys, Thanks for your interest.

1. I am not set up for wireless and am reluctant to go that route just for a test. Sorry!

2. As for replacing the router - it would be cheaper to install windows:)

3. I am trying the Time Service suggestion. I need to run the setup for at least 24 hours (to include a date change) but will let you know what happens. 

When I installed Ubuntu it picked up the router connection automatically (no input from me) and I am now wondering if I should have configured something????

---

### Post by mlentink on 2008-05-03
> **chimchim said:**
> 2. As for replacing the router - it would be cheaper to install windows:)
Fine. Suit yourself...
> **chimchim said:**
> When I installed Ubuntu it picked up the router connection automatically (no input from me) and I am now wondering if I should have configured something????
I'm unsure what you mean by this. Why would Ubuntu NOT pick up the router connection automatically? Is this router not set up to serve DHCP requests? If that's the case, which computer in your lan does? Or have you manually configured all boxes in the lan for fixed IP?

---

### Post by y-aji on 2008-05-03
Something you could try..

This probably isn't it, but it is possible windows is doing something with pxe network boot on the linux machine.. Again, this is very unlikely, but you never know.  See if you can disable pxe boot in the startup options.  This would be more likely to be occurring if you had some kind of server.  But, I have seen stranger in regards to pxe boot.

Just go into your bios, and see if network boot is one of the options under startup list.  If so, see if you can move it down, change the priority, etc.

---

### Post by kestrel1 on 2008-05-03
Disconnect the Linux box from the router. If it looses the BIOS settings, there must be a hardware problem. Make sure that the CMOS chip is fully pushed in to it's socket on the mobo, make sure that the CMOS reset jumper is not set incorrectly (not very likely as most mobo's wouldn't even boot)
Is it only the time settings that are lost? or are other settings lost?
You could have a faulty mobo. Have you actually checked the voltage of the CMOS battery with a volt meter? It could be that there is a fault on the mobo that is draining the battery very quickly.
Loss of BIOS settings is normally down to the battery or the hardware, but there is also the possibility that you have managed to catch a BIOS virus (not that likely, but possible)

---

### Post by jimv on 2008-05-03
Naw, you shouldn't have to configure anything.  A wireless router is pretty much just a network bridge with a DHCP server built in.

---

### Post by chimchim on 2008-05-05
Hi Guys
I tried to boot up my Linux PC this morning and got "Please enter setup to recover BIOS setting" Date/time was corrupted and all custom settings were at default.
I have had this problem since last November with Ubuntu 7.10. Since then I have replaced router, MB, RAM and OS (Ubuntu 8.04). I have spent hours searching websites and forums for a solution, I have even bought a couple of Ubuntu Linux books hoping they would help.
After six months and with no end in sight I am admitting defeat and reinstalling Windows:sad:
I realise that it is not easy to diagnose problems remotely and appreciate your interest and your time. My thanks for your efforts.
Have a nice day.

---

### Post by mlentink on 2008-05-05
Chimchim, you're only two days and six posts into this forum. 
Sorry to see you give up.

---

### Post by kestrel1 on 2008-05-05
If you have lost the date/time & settings in your BIOS, using another OS will not help. It is a hardware problem & the most likely thing is the CMOS battery. If however you have changed the battery & you are sure that the new battery is okay, you need to be looking at your motherboard. An OS will not affect your BIOS in this way.

---

### Post by fahadsadah on 2008-05-05
Perhaps your router is giving your computer a power surge?

---

### Post by chimchim on 2008-05-05
Hi Guys
Just thought I would check back.
Hi Kestrel, Having changed the battery twice, tried two MBs (and flashed the latest BIOSs). Which part of the MB should I be looking at?

Hi mlentink. You are probably not as sorry as I am, but I did raise this concern on these forums last January. Mistakenly, I thought it had been fixed. Two days after I marked it as solved it reoccured and I have been struggling with it ever since. I think I have given it my best shot! 

Hi fahadsadah, Interesting theory but as an electronics engineer it does give me a problem. How do you propose I check it?

Thanks again for all your interest but I really have given up on Linux. Maybe I will look at it again in 4-5 years time.

Have a nice day

---

### Post by kestrel1 on 2008-05-05
Hmmmm, If you have tried different MB's then looking somewhere else. Are you using the same RAM? Have you swapped out the PSU?
PSU's can cause some very strange things to happen. I have never seen an OS cause this issue or a router come to that.
If you are able to swap out the PSU I would give that a go.
It is a shame that you are giving up on Linux, I really do not think that this is the cause of your problem.
If I am wrong though :confused:

---

### Post by kwacka on 2008-05-05
Could you let us know how it works under Windows?

I really am intrigued as to how an operating system can have an effect on something that happens before it is booted.

---

### Post by kestrel1 on 2008-05-05
Same here:lolflag:

---

### Post by mlentink on 2008-05-06
> **chimchim said:**
> Hi Guys
Hi mlentink. You are probably not as sorry as I am, but I did raise this concern on these forums last January. Mistakenly, I thought it had been fixed. Two days after I marked it as solved it reoccured and I have been struggling with it ever since. I think I have given it my best shot! 


I'm sorry, I had not seen that. Pity it didn't work out. Good luck!

---

