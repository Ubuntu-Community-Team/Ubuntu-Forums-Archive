---
title: "Color management &amp; calibration on HP 250 G3 laptop running Ubuntu 12.04"
date: 2015-09-26
forum: New to Ubuntu
---

### Post by Lyta on 2015-09-26
The colours on my computer's screen and camera seem to be a little off. When accessing the System settings > Color tab I am able to add a color profile, but that doesn't change anything since the default profile added by the system isn't editable, and doesn't change anything in terms of visual display. In the Help section it says that I should take a picture and use it as a calibration template. That doesn't help my case as I don't know the proper settings to make a template, and I don't want to expand these custom settings over every visual display option in my computer. Are there *.icc or *.icm color profiles available for Ubuntu somewhere, that I can download and import? In the HP page the only available options are for Windows.

---

### Post by tgalati4 on 2015-09-26
Welcome to the forums.

If your laptop is dual-boot, you can boot into Windows and use a Color Manager to create a *.icc file then move it to the correct location in Ubuntu.

Some reading: 

[https://help.ubuntu.com/stable/ubuntu-help/color-whatisprofile.html](https://help.ubuntu.com/stable/ubuntu-help/color-whatisprofile.html)
[http://askubuntu.com/questions/199661/how-do-you-set-system-display-color-profiles-in-xubuntu-and-lubuntu](http://askubuntu.com/questions/199661/how-do-you-set-system-display-color-profiles-in-xubuntu-and-lubuntu)
[http://askubuntu.com/questions/155552/where-does-gnome-color-manager-store-the-icm-or-icc-files](http://askubuntu.com/questions/155552/where-does-gnome-color-manager-store-the-icm-or-icc-files)
[http://askubuntu.com/questions/442828/edit-an-icc-profile](http://askubuntu.com/questions/442828/edit-an-icc-profile)

---

### Post by Lyta on 2015-09-29
I'm not dual booting from this computer, there's just Ubuntu installed. The third link is some help though, I'll try downloading the Windows-specified profile, run the *.exe and snatch the icc file from there. Thanks for the help! Let's see if I get anywhere.

---

### Post by tgalati4 on 2015-09-29
Unfortunately there are no decent Color Management tools under Linux.  If you can find or make a *.icc file then that will get you the color correction you need and you won't miss the Linux tools.  You only need to do it once for the environment you typically work under.

---

### Post by buzzingrobot on 2015-09-30
The DispCalGUI tool is very good at generating a profile for Linux if you have the right tool to do that, like a ColorSpyder calibration device or similar commercial product. There's also ColorHgger, which is an open hardware product.

There are ways to generate a profile by simply eyeballing the screen and deciding what you think looks good, but that can't be as precise as a hardware-generated profile.

DispCalGUI can set up the profile it creates to be installed properly and activated on logging in.  I've found I need to be sure the gnome-color-manager package is installed and that I make sure the profile is set in Systems Settings->Color. (Sometimes, DispCalGui complains it can't load the profile on the first new session after the profile is installed, but it's fine after I reconfirm it's setup in Color.)

Profiles really need to be generated on the display in use and under the lighting conditions that prevail there. That applies for any platform, not just Linux.  So, profiles found on the web may or may not be much of an improvement. But, certainly worth trying.  Default profiles from manufacturers are often rather bluish.

DispCalGUI is in the repos, along with its dependencies.  The newest version is available, packaged for Ubuntu, at its site: [URL="http://dispcalgui.hoech.net/"]http://dispcalgui.hoech.net/.


[/URL]

---

### Post by Lyta on 2015-10-01
It's a relatively new computer model so there aren't any pre-made colour profiles that I managed to find in the net. In the HP website there aren't any profiles that I managed to find, even for Windows, so no help there. And it's not for professional use that has to do with design, photo processing etc, so I don't have a commercial tool to calibrate the screen. I just think the screen colours look a bit more washed out than what they normally should be, and trying to correct that. I downloaded and installed dispcalGUI and running it now, although the Calibrate and Profile buttons seem to be grayed out and not active. I tried to download Spyder through the program, but it can't find the packages. I'll look into the Help section to see if I'm doing something wrong.

---

### Post by buzzingrobot on 2015-10-01
I'm not sure what, if anything, DispcalGUI will do if it finds no hardware calibration device. Pretty sure, though, that's why the Calibrate and Profile buttons are greyed out. It uses the device to create the profile.

Does the HP offer a way to adjust the display settings? Contrast, Brightness, color temperature, that sort of thing?

The differences that I perceive here, by eye, on a Dell display, when I enable a profile are very subtle.

---

