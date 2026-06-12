---
title: "Unable to boot"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by sezhiana on 2013-04-05
Hi,

I am having this problem for a few months now. I have Dell D630 laptop and I installed 10.04 I think and then slowly upgraded to 12.10. I started having problems like freezing. I had installed in my wife's Sony NR110E Ubuntu (currently 12.04) in dual boot with XP. I do not have any problems in this laptop.

I thought 12.10 was the issue in my Dell and installed 12.04 back. Things were OK for a while and again this problem started and I was unable to boot. No video nothing. I connected it to an external monitor. I disconnected it but nothing happened. Then I connected it back and I could do Fn+F8 to get the display on the external monitor.

Then I installed Zorin. It was ok for a few days and then the problem started again. So I cleaned everything and installed Zorin afresh. Same story. Right now I could not even boot with the Live CD (Both Zorin and 12.04).

I think the graphics card is NVidia.

I need some help here.

Thanks

Sezhian

---

### Post by DuckHook on 2013-04-05
You've given a good description of your progressively worsening problems. I suspect that it is hardware. If you were able to run LiveCD before but not now, and the problem seems to have worsened with time, then this usually indicates that either your motherboard is going, or your video card. The D630 should be able to run modern flavours of Ubuntu with no problem, so it is not a case of your HW being under-powered.

Do you still have the Dell HW diagnostics CDs? If so, you may wish to give those a try and run a complete set of HW diagnostics.

---

### Post by sezhiana on 2013-04-05
Thanks for your reply.

I do not have the CDs.

Three days back I installed Zorin and it working fine for two days and then it suddenly froze and after that I am unable to boot except for once. At times I get to what looks like a command line when I boot. I dont know what to do at that point.

Thanks again.

---

### Post by DuckHook on 2013-04-05
You can download them on the Dell site. Easy to Google. You will have to burn them from your Wife's laptop, but this can be done easily. Site is [here]("http://www.dell.com/support/drivers/us/en/04/Product/latitude-d630").

---

### Post by sezhiana on 2013-04-07
i downloaded the .exe file as an ISO image and booted my system with the disc in my cd drive. Nothing happened. How do I run it? I tried with wine - it opens the folder.

The system works on and off - there is flick suddenly and the system freezes. One time I was hearing the audio for more than an hour but system froze. I had to do a hard reboot.

Thanks.

Sezhian A

---

### Post by Ernesto M EF on 2013-04-07
The new Ubuntus are jokes really.. i myself have had so many issues with my 12.04 LTS i did an update to it and when it was done i rebooted my system for it to take effect and random issues were just.. exploded everywere freezing, unexpected applications being opened "System Settings.. or the icon with the tools in Ubuntu" that was unable to close at all it didnt let me use any other application if i closed it it reopened, no audio, no right click and even complete instability with horrible i mean HORRIBLE multitasking that would freeze one application for god knows how long "That has not been fixed at all". So in the end of the day i gave up i mean really i was just being retarded trying to fix this nightmare that has no true stability and my PC has enough memory to support at least 5 windows opened in my Windows Multi tasking is no issue in Ubuntu its a hard reboot.

---

### Post by sezhiana on 2013-04-08
I don't agree with you. I have Ubuntu 12.04 installed on my other machine (Sony) and I don't have any problems with it. It is only this m/c (Dell) and that too only recently. I really like Ubuntu but new to it and don't have time to fully learn it. Thanks.

---

### Post by grahammechanical on 2013-04-08
Do you have another OS on this Dell laptop? Do these issues arise in that OS? Is there a page in the BIOS that monitors temperatures and stuff like that? If so let the machine run for a bit with the BIOS open and check temperature settings.

I have installed Psensor which sits as an icon in the top panel (app indicator) and one click on the icon and I can see various temperature readings as well as fan speeds and CPU speeds. Over-heating due to blocked air flows should not be discounted. Battery/power supply issues and failing memory chips.

Regards.

---

### Post by DuckHook on 2013-04-08
It's been ages since I've used Dell diagnostics, so this is all from foggy memory, but as I recall, you have to run the .exe file on a Windows machine for it to self-extract. This produces an iso file that can then be burned to a cd which, in turn, produces a bootable CD that can be used to diagnose.

When you first posted, I got the impression that your laptop simply would not boot at all. But from your latest postings, it it is now clear that it will sometimes boot, sometimes not. If this is its behaviour, then you almost certainly have a HW problem.

I am asking again (please provide info) does it boot from Ubuntu LiveDVD?

Do you hear the laptop fan come on?
Does computer run hot to the touch?

In addition to what grahammechanical recommends, the next time the computer manages to boot, do:```
sudo apt-get install lm-sensors
```Answer "yes" to all of its installation questions. Then do:```
watch sensors
```which will give you a running readout of your core temperatures. If you are using the open source video driver, it will also give you GPU info. Fan speeds may or may not appear depending on your system and BIOS. <CTRL>+<c> to quit.

If core is idling higher than 70* or GPU is higher than 90*, then you have a temperature problem. Either a bad fan or clogged intakes.

---

### Post by sezhiana on 2013-04-08
Thanks to both grahammechanical and duckHook.

I installed the lm-sensors and it only displays "temp1" which right now varies from 46.5`C to 51.5`C. I can hear the laptop fan come on. Some times the sound goes up and down. The m/c is not hot to touch.

Till two days back it was not booting even from live CD (Zorin / Ubuntu 12.04) at best it was going to a command line only on the external monitor. By accident I found that pressing F2 immediately after pressing the power button brings the Dell logo and the laptop boots normally. I have not tried otherwise as I was afraid that the m/c might go back to its old ways.

Even now suddenly there is a flicker on the screen and the m/c will freeze.

I made the bootable CD from my dual boot laptop (XP/12.04) but it does not seem to do anything because default booting is CD drive first and then internal HDD. The down load from Dell website was for an XP OS. I don't know if it makes any difference as my current OS is Zorin.

I am posting this from the Dell laptop (Zorin OS).

Thanks.

---

### Post by DuckHook on 2013-04-09
Temp seems okay. The only other thing I can suggest at this point is to look at your logs to see if anything unusual is being registered. Especially syslog and bootlog. I've never used Zorin and don't know anything about it, but since it is Ubuntu-based, then both logs should be at /var/log/. You will have to use a text editor to look at both. dmesg is also worth looking at but can be seen just typing *dmesg* into a terminal.

Are you using proprietary video drivers? I believe the D630 uses an nVidia chipset, but again, I know nothing about Zorin, so no idea if they install proprietary nVidia drivers or use the open source nouveau. You might try changing video drivers to see if that helps.

To diagnose possible HW problems, I've used UBCD (Ultimate Boot CD) available [here]("http://www.ultimatebootcd.com/").

---

### Post by sezhiana on 2013-04-09
It happened again tonight. Suddenly the screen started to flicker and then the system froze. After trying shut down/reboot several times, I could come back on. My F2 trick did not work the first few times. One of the times it booted into Zorin, I got the desktop background on the external monitor. It was flickering every few seconds and nothing else happened and i realized that the system was frozen. Temperature is normal 52`C.

Thanks.

---

### Post by sezhiana on 2013-04-10
The problem happened again yesterday. It seems that finally I have run out of luck. Pressing F2 before Dell logo shows up, brings up Dell logo and then I get a blinking cursor. The same thing happens even if I press F2 (BIOS) or F12 boot menu. I tried with LIVE CDs of Zorin as well as 12.04. All i get is the blinking cursor.
 
I will try the UBCD to see if it helps.

Thanks.

---

### Post by DuckHook on 2013-04-11
If you cannot bring up the system BIOS, then you have a hardware problem that neither this forum nor any software can help with. The D630 is not worth fixing in my view, but the parts may be salvageable for any other D630 you may have. Good Luck!

---

### Post by sezhiana on 2013-04-11
It came back up again without the LIVE CD. Hopefully it will come back up this evening.

Now I have the UBCD made. How do I use this?

Thanks.

---

### Post by DuckHook on 2013-04-12
If you have downloaded UBCD, you will know that it is a collection of diagnostic utilities so extensive that it is impossible to give you instructions on a help forum. The UBCD site is a good one and provides not only a [FAQ]("http://www.ultimatebootcd.com/faq.html"), but [tutorials]("http://www.ultimatebootcd.com/tutorials.html") to deal with the most common tools. Please use the instructions provided on the UBCD site.

I am 99% sure that you are wasting your time on this one. In my experience, intermittent and deteriorating ability to boot is the sign of borked hardware, likely your video chip or your motherboard. Software issues tend to be all or nothing affairs: so if your problem is, say, a video driver, then it would simply give you a black screen (or whatever wonky result) each and every time. We've reached the point where I'm afraid there is no further advice I can offer you beyond what has already been offered in above threads.

[http://wiki.ultimatebootcd.com/index.php?title=Main_Page](http://wiki.ultimatebootcd.com/index.php?title=Main_Page)

---

