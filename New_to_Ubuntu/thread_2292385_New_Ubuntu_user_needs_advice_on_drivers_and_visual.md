---
title: "New Ubuntu user needs advice on drivers and visual issues"
date: 2015-08-27
forum: New to Ubuntu
---

### Post by mt_100 on 2015-08-27
I admit I am new to Linux but a Windows Engineer professionally.

I wanted to delve into Linux to learn for work related reasons and don't see a reason why Linux can't be my home OS.

My home laptop is a Lenovo Ideapad N580 with 8GB RAM and Intel graphics.

I installed 15.04 and the install went great. Once in the OS I was using Firefox and other applications and was annoyed that the font size and general size of everything was larger that what Windows would be. The resolution was set correctly for the monitor in the settings so everything looked good there.

I also noticed Firefox was very slow browsing the internet.

So I downloaded and installed 14.04.3 which I noticed is the long term support release and installed it. Everything went great again and Firefox was performing better. but the fonts, text, and other screen aspects were still annoyingly larger than they should be (opinion).

I ended up reverting to my Windows 7 image to continue to use my laptop so I cannot do any troubleshooting at the moment so I am asking more from an advice for my next attempt perspective.

1. Is there a way to make the screen, windows, dialogs, browser, and everything you see look more like Windows in the size aspect? Felt like I was on a computer with some sort of visual aid enabled to make things larger even with the resolution set correctly.

2. Is there a way to verify that all the hardware was detected correctly? In Windows you can always go to Device Manager and look for unknown devices or see the names of things and know they are detected and running the right driver.

3. Is there another version or release of Ubuntu that changes the look to be more like what I am looking for like Xubuntu or something else?

I'd really like to give Linux a go and think I can with a little help so I appreciate any advice.

---

### Post by Bucky Ball on 2015-08-27
There are ways to do all of these things but without having an install to do them it might be tricky. :)

Perhaps you can dual-boot with Windows so you can 'acclimatise' to Linux without making a total one or the other switch. It's normal. Many of us have Windows on at least one box, even if it's not used much.

As for 3., best thing to do is download the Xubuntu ISO, or whatever other flavour you like, create boot media, boot from it and 'Try *buntu'. Have a look and see if you like. This won't do anything to your hard drive unless you install. 

As for 1. and 2. the tools can depend on the flavour you're using. And yes, 14.04 LTS is stable and supported until 2019 (2017 for Xubuntu).

---

### Post by Geoffrey_Arndt on 2015-08-27
Screenshots help us to see what you're saying.

Also, did other browsers also lag?   Chrome, Chromium, Opera, Midori, etc.?

As an Engineer, you know the IP protocols are unix/linux derived (70%+ of internet runs on Linux hw/sw) - - so, if all browsers lag, that says one thing,  if only FF, that says another.

As for "appearance" issues or questions, there are many many more types of desktop environments, themes, etc. in Linux as in Windows . . . fact is, most Linux users including myself don't especially want a clone of the Windows look (give me a headache just thinking about it).   BUT - - if you want that, Linux provides the choice.   There's even a whole distro designed to look and function just like Windows (Zorin OS).

---

### Post by mt_100 on 2015-08-27
I don't want it to look just like Windows but I also don't want everything to be so large. Everything in Ubuntu seemed like it was blown up hideously large text with no way to change it.

I'll try a different release or distro to see if I can find anything I like and report back.

---

### Post by grahammechanical on 2015-08-27
For Ubuntu there is System Settings>Screen Display>Scale for menus and title bars. The default is 1 but the slider will move below and above 1 and effect the font sizes accordingly.

 And also System Settings>Appearance>Launcher icon size. Again we can increase or decrease the size of the icons in the launcher. Applications allow us to change the text size. It is in the View menu>Zoom.

---

### Post by mt_100 on 2015-08-27
Loaded up the Xubuntu live CD tonight and it looked better, not 100% perfect but 90% there. With a few tweaks I think it will work fine.

How about driver verification? Does it even matter?

---

### Post by Geoffrey_Arndt on 2015-08-28
If you think Xubuntu is 90% there, take a look at Linux Mint Cinnamon . . very classy, pro-style "traditional" wimp interface.   MS could take some pointers re Cinnamon's start menu org and human factors design.   The Windows 10 start menu is still a mess . . 1/2 tile and 1/2 cat groupings.

Re driver verification,  most intel hardware does not require (external) driver support . . . modules pre-built into kernel.   Intel based wireless and gpu stack work seamlessly to user.   nVidia and ATI video usually require proprietary drivers installed via system settings, Software & Updates, Addtional Drivers tab.   IF wireless doesn't work, check for additional drivers availability (same place as with video).    Sometimes the driver for wireless will require building from source, or use of windows drivers via ndiswrapper.   (I've done each, but these days I just go with usb wireless adapters which are known to be plug & play with Linux).   

That leaves printers - - just use HP for simple setup (hplip/CUPS provided in install).   Epson has Linux drivers, as does Brother.   IF not working, little minor things like bluetooth can also be solved via various methods.    

Other system settings (software and hardware) are config'd via various text files in /etc.

One more comment here . . . if someone wants about a 10 minute flawless, brain-dead simple Linux install & setup, just buy a "pre-loaded" linux PC via these vendors:

[http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

### Post by Bucky Ball on 2015-08-28
> **mt_100 said:**
> How about driver verification? Does it even matter?

If everything's working as it should, probably not. Be aware that a lot of the drivers, unlike Windows, come as part of the Ubuntu kernel. You don't need to load them manually. 

The main two things you need drivers for and that can be problematic are wireless and graphics. Wireless working, graphics ok? You can look in Additional Drivers and see what's being used as far as third-party, proprietary drivers goes. To check video and wireless drivers, try:

```
sudo lshw -C video
sudo lshw -C network
```

You will find the driver being used toward the bottom along with details of your cards. 

There is a probably a command that lists all used drivers but I'm not aware of it. :)

PS: On Xubuntu, Applications> Settings to tweak your settings. Good luck.

---

### Post by Mark Phelps on 2015-08-28
> **mt_100 said:**
> I don't want it to look just like Windows but I also don't want everything to be so large. Everything in Ubuntu seemed like it was blown up hideously large text with no way to change it.

I'll try a different release or distro to see if I can find anything I like and report back.

If you want something that is more traditional menu-based, and want to stay with Ubuntu, then try Ubuntu Mate. I quit using Ubuntu daily when the new smarthphone-like interface came out and switched over to using Mint.  Then recently, when Ubuntu Mate came out, I installed it -- and am back to using Ubuntu daily.

---

### Post by Geoffrey_Arndt on 2015-08-28
Excellent suggestion . . . Ubuntu-Mate (aka Gnome2) is still a great desktop for mouse/hot-key input (fast, flexible, looks decent, etc.).

---

### Post by mt_100 on 2015-08-28
I will download Mate now and give it a shot.

I really appreciate all the information and suggestions from everyone, thank you.

---

### Post by mt_100 on 2015-08-28
Booted up Ubuntu Mate 14.04.2 and it looks very nice. Used it for a bit and ended up changing the 6System->Preferences->Appearance->Fonts->Details->Resolution setting to 86 from 96 and it looks even better yet.

I couldn't find one setting that Ubuntu had, the display scale mentioned before. Must be in another location but I would like to play with it if I can find it. I tried google but couldn't find info on where to find that setting.

I will certainly have to install Mate when I get back from a business trip and give it a run. Probably is the desktop OS change I am looking for.

---

### Post by Mike_Walsh on 2015-08-30
Hallo, mt_100.

Pardon my asking this, but why exactly do you want the appearance (font's etc.) in Firefox (and Linux generally) to **be** so small? Any particular reason?

I only ask because a number of Linux users (myself included) are no longer 'spring chickens'.....and our eyesight is not necessarily what it once was! Therefore the somewhat larger scale of things is definitely appreciated by some of us...

And in **my** case, using an old 1024 x 768 monitor as I do, it looks better **anyway**. (My gear is all 'cast-offs', from family Windows users, when they upgrade. It's got years of life left in it.....so , why not?)


Regards,

Mike. :)

---

### Post by mt_100 on 2015-09-01
I don't mind you asking.

I'm actually young..er...ish and have great eyesight as well as really like clean, crisp interface and screen real estate when computing so that is why I like smaller fonts more like a Windows style.

Pretty sure once I return from vacation I will be firing up Ubuntu Mate but I do want to try RoboLinux first as it was mentioned by a coworker as being worth a look.

---

### Post by Bucky Ball on 2015-09-02
> **mt_100 said:**
> 
Pretty sure once I return from vacation I will be firing up Ubuntu Mate but I do want to try RoboLinux first as it was mentioned by a coworker as being worth a look.

Just a tip about using more exotic spins/distros. Check the support community. I have personally never heard of RoboLinux, which says little, but what it does say is that it is a more obscure spin which may have a very small support community. This means that if things go pear-shaped you may be close to own your own. This is one of the reasons Ubuntu is popular. Apart from being a great OS, the community is large, friendly, and helpful. 

Good luck however you go. :)

---

