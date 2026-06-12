---
title: "Toshiba Satellite A4"
date: 2014-10-02
forum: New to Ubuntu
---

### Post by Aberlour on 2014-10-02
*Not sure where to post this . .*  I have a salvaged **Toshiba Satellite A4** with 2.8GHz CPU, 2Gb Ram + 120GBHDD and no OS on it. I loaded Ubuntu 14.04 successfully with no issues. But System Monitor show *100% of CPU usage at all times* . 'Top' shows 2 desktop GUI apps gobbling resources (can't remember the names). the Tosh. runs dreadfully slowly, about 1/4 of the speed of a Thinkpad T61 with its 1.8GHz CPU and 2GB RAM (WinXP). 'Official' Ubuntu requirements suggest the Toshiba _*should*_ run 14.04, but there are many online moans about the heavy CPU usage which I too am experiencing.

Which direction would give me a usable laptop? > Downgrade to 12.04 (unsuppoerted) or Xubuntu, or simply try Win7 ?? Is Ubuntu 14.04 really just too 'obese' and pointless for 'legacy' computers? Applications used will just be web and a few recipes printed out: nothing very demanding.

Any suggestions please? This is my first experience with Ubuntu - so far I am a bit underwhelmed.

AA

---

### Post by oldfred on 2014-10-02
My Toshiba is even older from about 2006 with 1.5GB of RAM. The intel video just is not enough for Unity.
But I install full Ubuntu and then add fallback/flashback which is now gnome-panel. That is like the old gnome2 menu system. That is a lot lighter weight gui. You could also use Xubuntu or Lubuntu as they also are lighter weight gui. Full Ubuntu with Unity is really more for newer systems with better video.

I do have Ubuntu on Desktop and Unity runs fine on it, but I prefer older menu system and since my monitor is older 4:3 the menu bars at top make more sense than using the side. Wider laptop screens may make more sense with Unity and controls on side.
But I wanted same system on old laptop, so it also is 64 bit (which most suggest needs more RAM), Ubuntu. I do find if I try to load more than one larger app and several smaller ones it starts using swap and gets slow. But my normal use it is ok.

If you do not want to install Xubuntu or Lubuntu you can easily try gnome-panel, but it works better if you change a lot of settings as documented by kansasnoob.

 sudo apt-get install gnome-panel
Log out or reboot to get to login screen:
On login screen click on logo/cog-wheel/star and choose which gui to use:


       Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)

---

### Post by grahammechanical on 2014-10-02
I cannot comment about those two GUI apps "gobbling resources" as you do not identify them. The slowness problem might be due to that or something else. What does System Monitor show when it is the only application loaded? There is somthing in the Ubuntu Software Centre called System Load Indicator (or indicator-multiload). That will put an indicator in the top panel that will show what is happening with the CPU, memory and Internet download and upload. I use it to keep an eye on things.

There is another thing that you can check. Go to the Power/Cog menu and select About This Computer. Does the Details page list llvmpipe as the graphics driver? Ubuntu uses llvmpipe as an open source graphic driver a) when the graphic adapter cannot do hardware accelerated 3D rendering (in other words cannot run Unity 3D); b) if we have loaded the desktop from Recovery mode; c) if there is some conflict with the proprietary video driver that is installed.

If you see llvmpipe mentioned open System Settings and load Software and Updates and open the Additional Drivers tab. Allow time for the utility to find drivers for your graphic adapter (internet connection needed) and experiment with the drivers on offer. I suggest this because llvmpipe does give an approximation of Unity 3D but it is slow. Noticeably.

By the way, I have 1GB of RAM and a Core2 Duo at 2.40 Ghz. And it is running 14.04 just fine. I do have a graphic adapter with 1 GB of its own memory. I think that makes all the difference.

Regards.

---

### Post by Aberlour on 2014-10-02
Thanks for those quick responses. I'll boot up the Tosh shortly and have a closer look 'under the hood'. CPU load is 100% with System Monitor running and nothing else. According to Toshiba, very little RAM is assigned to the graphics - possibly around 64Mb, but I need to check that.  I have yet to learn enough about Ubuntu to know what some terms mean = steep learning curve. AA

---

### Post by snowmobiler on 2014-10-02
I have Ubuntu running on a dell latitiude D820 running at 1.66GHz and only 1GB RAM. Runs just fine.

---

### Post by QIII on 2014-10-02
Rather than System Monitor, please use top (or install htop and use that) from the terminal and post the results.

---

### Post by buzzingrobot on 2014-10-02
> **Aberlour said:**
> According to Toshiba, very little RAM is assigned to the graphics - possibly around 64Mb...

Sometimes the  amount of RAM alloted to onboard video can be adjusted in BIOS setup.  Increases will come from main memory, but could easily be worth it.

---

### Post by Vladlenin5000 on 2014-10-03
> **buzzingrobot said:**
> Sometimes the  amount of RAM alloted to onboard video can be adjusted in BIOS setup.  Increases will come from main memory, but could easily be worth it.

Indeed. Keep in mind that in this scenario doing that - increasing the reserved VRAM - always imply a trade-off.

My experience with Unity tells me the bare minimum RAM for it to work acceptably is 2GB (and 32-bit Ubuntu). Any system with integrated graphics and a total RAM of 2GB will have less that that (total - reserved) for the OS. S, here's the trade off:
- Does increasing the VRAM helps? Yes, but not much.
- Does reducing the memory available below the 2GB threshold, a direct consequence of the former, impacts significantly the OS responsiveness? Yes, it does, quite noticeably.

It follows that whenever possible adding a graphics card (with its own memory) is the best approach. It really makes a huge difference.

---

### Post by Aberlour on 2014-10-07
Many thanks for all the information. I have *disabled automatic updates* which were taking up resources.  Now the 'Top' cmd show that with the system idle:

Compiz uses 16% CPU and 9% Ram resources.
XORG uses 4% CPU and 1.5% Ram.
Unity panel uses <1% of CPU or Ram.
All other applications are using very little resources.

Switching off the update manager has had a minor effect, but launching programs, like Firefox and Libre Writer, seems no faster although they don't take up many resources when running. BIOS doesn't allow changing the allocation of RAM to the onboard video.   Maybe matters might improve with a faster HDD or changing the SWAP file settings, etc.  I haven't had an opportunity to do any other suggested changes yet; I will find time shortly. Thanks again.

---

### Post by Aberlour on 2014-10-13
This is all very frustrating. Despite changing swappiness and setting up the Gnome fallback, and hence now having a much faster GUI, some bits of Ubuntu 14.04 are nevertheless still desperately, chronically, pathetically slow. Firefox takes ages to load, despite many tweaks and re-sets - opening a second tab takes an absolute eternity (sometimes 5 minutes). Also, installing Flash Player fails every time. Even Dash takes about 8 seconds to load. All of this even with Compiz and Xorg only taking 15% of CPU resources and virtually no RAM.

It is like turning the clock back to Windows 3.1 days. If this is what the alternative to Windows XP, 7 or 8 amounts to I may as well put Win7 on it and suffer the consequences. I have tried a couple of other versions of Linux and each has awful weaknesses and sometimes truly antique apps that look like they were written in the 1980s. Ubuntu 12.04 seems the best of the bunch: it is much much faster than 14.04 - even when running from DVD, so I may try that and attempt to install Flash Player on it. 

Sorry to be sooo negative, despite some great advice, but I must represent a lot of new users who are severely discouraged by systems, applications, etc, that have great potential but which require one to wrestle with unrecognisable monsters in the antediluvian swamps of geekiness to make them 95% effective. . . . .  "Been there, done that, now want an easier time". 

 Kind  regards to you folks who tried to help - thank you.

***Edit: Just installed Zorin Free - works "well out of the box" and does have a Flash Player installed by default: instantly recognises PCMCI wireless network card. Seems fast enough aside from the limits of internet connectivity. Adequate GUI.***

---

### Post by buzzingrobot on 2014-10-13
Although it's seems to be popular, I don't think playing with swappiness on low-RAM hardware does much of anything useful.  Swap is used, essentially, when sufficient physical memory is not available. Nothing magic is going to fit 2.1 gigs of memory requests into 2 gigs of RAM.

Load time seems more likely to be a disk issue than an issue of CPU demand. Swap would be involved if the process attempting to load triggered its use.  You might take a look at the efficiency of the SSD, especially its use to hold a swap partition.

Booting something that targets low-RAM hardware, like Lubuntu or Xubuntu, in live mode off a USB stick might provide some useful comparisons. 

Ubuntu Unity is not targetted as a low-resource platform, although plenty of people here use it on such hardware.

For comparision's sake, on Xubuntu 14.10 at the moment here, Firefox with three tabs open, and Adblock installed (gobbles memory), is at 417 MiB; Thunderbird is at 186 MiB, and the Dropbox daemon is at 93 MiB.  When I run Unity, Compiz starts near 90 Mib and often increases to approx. 150 Mib.

---

### Post by oldfred on 2014-10-13
You mention fallback, but also Dash. 
Dash is in Unity, not in fallback.
Are you selecting correct desktop at login screen?

[http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)
[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

---

### Post by Aberlour on 2014-10-19
Thanks for the additional info. The killer factor was that I couldn't get Flash to install in Ubuntu 14.04 even after 3 attempts and several clean-ups. I loaded Zorin 9 first time, with Flash support and no hassle. Also, the option to chose different desktops from a menu makes it very user friendly; removing animation, etc, makes it really quite fast. I understand Zorin 9 is based on Ubuntu 14.04, but in comparison I much prefer it, so I will install it on a couple more family laptops. Thanks for all the advice. AA

---

