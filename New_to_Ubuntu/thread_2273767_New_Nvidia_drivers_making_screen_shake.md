---
title: "New Nvidia drivers making screen shake"
date: 2015-04-15
forum: New to Ubuntu
---

### Post by chris-burmajster on 2015-04-15
My computer has a Nvidia GeForce GTX 750 graphics card in it. When I installed Ubuntu 14.04 on it originally, it installed Nvidia 331 graphics drivers. These were generally OK, but every so often the System Problem box would pop up with an Nvidia drivers problem. I searched duckduckgo and found this site: [HTML]http://ubuntuguide.net/install-nvidia-proprietary-drivers-in-ubuntu-14-04[/HTML] and installed the later drivers. This got rid of the System Problem pop up, but now the screen shakes for 10 seconds or so every time you do something new like open a new e-mail which is driving me up the wall. I seem to have lost the old drivers in the process, so I can't go back to them. Can anybody suggest how I can solve the shaking issue? The screen is an AOC Q2770 connected via DVI and an Aten KVM CS1782a switch.

Thanks,

Chris

---

### Post by Vladlenin5000 on 2015-04-15
Newer drivers are recommended fir that card. I suggest you search this forum for similar hardware.

---

### Post by buzzingrobot on 2015-04-15
I have a 750ti. And, yes, you need a newer driver. The 331 drivers didn't work at all here.

I've found that the 343 and 346 drivers work. I don't see that they are in the Trusty repos so I would not expect Additional Drivers in Trusty to show them. (Still, worth a look.)

They are available for Trusty in the xorg-edgers PPA [(https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa?field.series_filter=trusty")).  Note that  PPA's are unofficial and unsupported and very much you-break-it-you-buy-it territory. In particular, be certain to read the notes and cautions published on that page and the packages on this specific PPA. Pay attention to the advice to install and be prepared to use the ppa-purge tool, in case things go badly. These drivers install and work on *my* hardware, but that does not mean it's certain they will work on your hardware.

(FYI:  The newer drivers are in the Vivid repos and installable via Additional Drivers, in case you're thinking about upgrading.)

---

### Post by chris-burmajster on 2015-04-16
This ppa installed all the latest drivers according to the Geforce drivers website: 346.59, 349.16 and 346.35. I have a choice of 4 drivers, 3 of them Nvidia and 1 non Nvidia. All the 3 Nvidia give me the screen shake and the non Nvidia one only gives 800 x 600. The 331 drivers may have flagged up the odd problem, but they were better than what I have now! 

What should I do next? Should I remove these drivers and try others? If so, which others?

Chris

---

### Post by dino99 on 2015-04-16
There are tons of graphic issues with 14.04 & 14.10. Canonical graphic team quite only maintain 15.04, which works well with its 346 driver here with a gtx 750.
so i only can propose to upgrade to 'vivid' (can be done via /etc/apt/sources.list, after disabling all ppa & third source)

---

### Post by buzzingrobot on 2015-04-16
If you are OK with using the 331, you have two choices:

1.  Use the 331 and leave the 346 drivers installed. However, since the PPA is in your list of sources, you will receive any updates released by the PPA maintainers.

2.  Use ppa-purge to remove them, per the instructions on the PPA site.  PPA-purge removes the PPA from your system's sources list, then removes the packages installed from that source list. Nvidia releases a "reference card" design that vendors may or may not tweak for their own purposes.

The 346 xorg-edgers drivers work here satisfactorily on my 750ti.  Perhaps the difference between the 750 and the 750ti account for your issues.  Also, there are often small differences between cards from different vendors.

If your system has onboard Intel video and you do not play games or have demanding video requirements, you may find that the Intel is all you need. I do. (I'm using the Nvidia now on 15.04 just as a test for myself before the final release is out.)  The proprietary drivers often cause problems on all distributions.

(The one non-Nvidia drivers you see listed is the Nouveau open source driver.)

---

### Post by chris-burmajster on 2015-04-16
Thanks for the tips. Now that I'm actually at this particular computer I can tell you that I'm currently using v346.59 (open source). Would it be better to get a driver directly from Nvidia's web site?

Chris

---

### Post by buzzingrobot on 2015-04-16
The open source driver is Nouveau. 346.59 is one of the proprietary Nvidia drivers.

You can configure an Nvidia proprietary driver by running "Nvidia Settings".  If it isn't installed (I can't recall if it's installed by xorg-edgers) the package name is "nvidia-settings".  It also rather obviously complains if the proprietary driver is installed but not actually in use, which can be useful.

All the proprietary drivers are from Nvidia, so 346.59 or whatever is the same driver from Nvidia's site or anywhere else.

---

### Post by chris-burmajster on 2015-04-16
Thank you once again for your suggestions. I decided to be brave (as this is the main family computer) and use synaptic to remove the 346 driver and install the 331 driver. After a reboot, the shaking has gone. The settings tab reports that I'm now using the Nouveau display driver, which I've not heard of, but, hey, it works! Now that all is well I'll not fiddle any more......

Thanks again to you all for your helpful suggestions!

Chris

---

### Post by Vladlenin5000 on 2015-04-16
If *nouveau *works for you, fine, but it means you aren't using 331. And, as a side note, some people with similar cards just moved to 15.04 and are happy with it (and 346), very happy.
Also should we assume that now, with the same open source driver as before, you got the correct resolution instead of 800 x 600?

---

### Post by chris-burmajster on 2015-04-17
Ah, that's interesting! Well, whatever driver it is, it works just fine. There's no shake and I get the full resolution of 2560x1440. I will be upgrading to 15.04 next week and if that installs a better driver then so be it, but I'm content at the moment. I don't like to fiddle too much on this particular machine, as it's the main family computer. I leave experiments to my laptop!

Chris

---

