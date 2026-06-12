---
title: "Custom Xubuntu KDM Theme..."
date: 2005-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by mhancoc7 on 2005-11-28
I have recently started using Xubuntu and I love it. The one thing that I wanted was a KDM theme for Xubuntu. I like for my boot up process to look and feel consistent.

[COLOR="Red"]Use this at your own risk! Be sure to make appropriate backups before proceeding![/COLOR]

This how to assumes that you have the following installed on Breezy 5.10:
kdm (as default)
kubuntu-desktop, kde
xubuntu-desktop, xfce4

[LIST=1]
[*]Download the attached file to your home directory.


[*]Extract the file to your home directory. You should now have a  directory(folder) named kdm_themes in your home directory.


[*]Open a terminal window and run the following command: sudo gedit /etc/kde3/kdm/kdmrc


[*]Find the section [X-*-Greeter]. Now locate the line in that section that    reads Theme=/... Now change it to read Theme=/home/YOUR_USER_NAME/kdm_themes/xubuntu


[*]Save the file and close gedit.


[*]Now in the terminal window run the command kcontrol.


[*]Once the KDE Control Center is open, select System Administration. Then select Login Manager. Now Click the Administrator Mode button and enter your password when prompted. Now select the Background tab. Enable the background and then use the browse button and set the background to /home/YOUR_USER_NAME/kdm_themes/xubuntu/background.png.


[*]Click Apply and close Kcontrol.


[*]Now click the Xfce4 menu button and choose Settings > Xfce4 Splash Screen Settings.


[*]Select Simple as the splash screen.


[*]Click Configure and set the font size to 12.


[*]Set the custom image to /home/YOUR_USER_NAME/kdm_themes/xubuntu/logo.png.


[*]Now close out Splash Screen settings and reboot.
[/LIST]

Now you should have a simple clean Xubuntu KDM theme at login. The theme is a combination of a modified version of the Default Kubuntu theme, the [linux_passion theme]("http://www.kde-look.org/content/show.php?content=28724"), and Xubuntu artwork found here: [https://wiki.ubuntu.com/XubuntuArtwork]("https://wiki.ubuntu.com/XubuntuArtwork").
This is my first theme and is really simple. It is really just a modified combination of other themes. I did this for myself and I thought that there might be other Xubuntu users out there that would like to have a Xubuntu login screen.

I hope that you will like this theme. I would love to hear what you think.

God Bless, Jereme

------------------
[www.WhatWouldJesusDownload.com]("http://www.whatwouldjesusdownload.com")

My System Specs:
Compaq Armada 1750
Pentium III 500mhz
320MB RAM
40GB HardDrive
Breezy 5.10 Enlightened Xubuntu
Win4Lin [Windows98]

---

