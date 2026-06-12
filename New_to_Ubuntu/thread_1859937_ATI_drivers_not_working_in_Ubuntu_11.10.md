---
title: "ATI drivers not working in Ubuntu 11.10"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by RAJESHKSV on 2011-10-14
I am using Lenovo Thinkpad laptop with ATI Radeon HD 3400 Series graphic card. I installed Ubuntu 11.10 64 bit today and I found that compiz is not working.

1)Hence I installed proprietary drivers displayed on my system (through jockey) .Rebooted my system. Performance is better now but Still compiz is not working.

2)Then I tried the second driver available - 'post-release-updates' but couldn't install due to some error. Hence I opened synaptic and installed fglrx-updates and rebooted my system. Not much change and still compiz didnt work

3)Removed all these packages and downloaded the latest driver from ATI [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English) and installed it and rebooted my system. This is worse as I dnt get even launcher or dash this time - I guess I am forcefully logged in to Ubuntu 2-D . Still compiz is not working

Am I doing something silly here ? Is any one facing similar issues with ATI ? Please help Thanks. It worked awesome in 11.04 but in 11.10 it started giving these problems :(

---

### Post by Adridar on 2011-10-15
Very similar issues here, any of the ATI drivers (Restricted, or from AMD's website) all cause graphics issues for me. If I use the generic open-source drivers, it works fine for my HD 5770, but anything else kills my ability to use dual-monitors, and at one point, the ATI drivers even killed Unity to the point where I had to reinstall 11.10.
Sadly I can't offer any help, all I can do is let you know that you're not alone. XD

---

### Post by martinh78 on 2011-10-15
I had no graphics issues with the open source drivers, but HDMI audio doesn't seem to work on my system without the proprietary drivers. I attempted to install these on 64-bit 11.10 - seemed to go ok, but on reboot I just got a black screen.

I've since installed the 32-bit version of 11.10 and installed the proprietary driver and everything is working.

I think I'm going to avoid 64 bit versions of Ubuntu from now on. Apart from the additional ram in my system - which PAE can pick up on 32-bit Ubuntu - I don't actually need the enhancements 64-bits offer as I'm not a scientist or mathematician. Plus 32-bit seems to be more compatible and have more software targeting it.

---

### Post by martinh78 on 2011-10-16
Scratch that.

I just tried to reinstall 32-Bit Ubuntu 11.10, followed the same steps as I did previously and now I get the same black screen as I did with 64-Bit Ubuntu.

What complete and utter crap. WTF changed over night?

---

### Post by silf on 2011-10-16
I'm on a VAIO FW31M (ATI Radeon HD3400) and I just upgraded from 11.04 to 11.10 yesterday (64 bit version). Everything worked fine on 11.04 (although at times there were some weird things going on with the graphics). I had and still have fglrx and Catalyst v11.8 (not sure if it's safe to have both) installed. 
Like you I noticed some graphics issue at times: top bar getting unresponsive, dash not showing up, smplayer having some trouble to switch to fullscreen or when I right-click on it (although none of this happened with vlc), whole laptop freezing. 
I tried uninstalling fglrx but then top bar and left launcher didn't show up, smplayer wouldn't even play a video file.
Going to try updating Catalyst Control Center, see how it goes.

:/

---

### Post by the_v1s1onary on 2011-10-17
Have you guys tried compiling the drivers yourself? 

Here's the link on how to do that:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)
Make sure you REMOVE PREVIOUS Ati drivers before compiling though.

Just did it today for my laptop:

HP Pavillion dv6
Ati Mobility Radeon HD - 4200 and 5650M Graphics
Played Fallout New Vegas today too, also a fresh install.

---

### Post by Mark Phelps on 2011-10-17
> **martinh78 said:**
> WTF changed over night?

The kernel version.  It's not uncommon for new Ubuntu versions to have major upgrades to the kernel as well, and since restricted drivers are kernel-version-specific, it's also not unusual for restricted driver to NOT work for a while until they get fixed to work with the newer kernel version.

It's generally a very good idea to read the Release Notes before you install a new Ubuntu version, as they often highlight video driver problems.

---

### Post by Trisket on 2011-10-17
> **martinh78 said:**
> Scratch that.

I just tried to reinstall 32-Bit Ubuntu 11.10, followed the same steps as I did previously and now I get the same black screen as I did with 64-Bit Ubuntu.

What complete and utter crap. WTF changed over night?

   I had the same exact issue on two laptops...one x86 and one 64...i personally think the new ati drive is a joke and actually the native open source driver looks better and shutters less when using two monitors than either of the available ati drivers, at lease on my machine.

---

### Post by phlancelot on 2011-10-17
I can confirm I am having similar issues using a Dell Studio XPS with an ATI radeon hd 3670.

The system seems to work alright with the default driver which I'm guessing is open source. It does feel a bit unstable at times and I've had a few crashes. It asks me to update to proprietary drivers and when I do this and reboot all I see is my desktop background with the nautilus file menu bar on the top. No indicator panel, no unity sidebar nothing else. I am forced to reboot the PC manually and revert back to the old drivers. I get the same problem when I install the catalyst drivers from ATIs website.

Guess I'll be stuck using the unstable form of open source driver until ATI can sort this out with a new version. Next time I am buying a ubuntu authorized PC for sure :P

---

### Post by Mark Phelps on 2011-10-17
> **phlancelot said:**
> Next time I am buying a ubuntu authorized PC for sure :P

Good idea!  But when you do that, be sure the check the system specs in advance.  Don't be surprised if the "Ubuntu PC" also uses AMD/ATI video card/chip.

---

### Post by kaldor on 2011-10-17
Just to chime in here regarding the drivers.

If you don't do 3d-intensive stuff (gaming, 3d modeling) or graphics-heavy stuff (movie editing, HD playback) then there's not much reason to install the proprietary driver. The default open source driver should also work more smoothly with GNOME 3 (in which Unity is on top of) at this point.

---

### Post by Mark Phelps on 2011-10-17
Have to agree regarding the questionable value of installing AMD/ATI restricted drivers in 11.10.

Was a time (back in Ubuntu 8.x days) that the ONLY way you could get resolutions beyond 1024x768 was either (1) LOTS of hacking around with Xorg files, Xrandr and the like, or (2) installing ATI drivers -- which was vastly simplified using Envy.

The open-source drivers have improved a LOT over the years such that, with 11.10, I can now get full 1920x1200 resolution plus separate dual-monitor support (different stuff on each monitor) -- ALL with the open-source drivers.

So, unless you really NEED the restricted drivers, save yourself a lot of trouble and grief and stick with the open-source drivers.

---

### Post by maddyu on 2011-10-29
i've been having the same problem with my vaio, and after some searching i found this:
[http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-problems-with-ati.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-problems-with-ati.html)
i'm following his/her method as i type, hopefully it'll make things ok. just thought i should share it soon as i can... :)

---

### Post by daniel_w93 on 2011-11-01
> The default open source driver should also work more smoothly with GNOME 3 (in which Unity is on top of) at this point.

what are the default drivers and how can I get them back?

I installed 11.10 yesterday everything looked and worked beautifully...then I made the mistake of installing the ATI drivers via jockey and it messed up the graphics to a point where I couldn't get a clear picture (everything was chopped up and had static around the edges).

I uninstalled ATI drivers and installed Mesa drivers. Now Mesa X11 is listed as my graphics driver...but it doesn't look or work like after the fresh install (e.g. my screen flickers like the Hz frequenzy is wrong).

Is Mesa X11 the default driver?

---

