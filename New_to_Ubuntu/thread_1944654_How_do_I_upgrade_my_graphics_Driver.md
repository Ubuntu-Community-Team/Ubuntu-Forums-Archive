---
title: "How do I upgrade my graphics Driver"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by Lefaid on 2012-03-21
This is a long story and you can skip to the next paragraph if you just want my basic question.  If you could solve any of my other problems, that would be much appreciated.  I have been trying to get League of Legends to run on my laptop.  I have gotten to the point where I can get to the champion selection and then the game crashes with a "Visual C++" error.  I have done everything I can think of.  One thing I have noticed is that when ever I open PlayOnLinux, it tells me that I don't have a 3D acceleration.  I do not know why it says that.  I have an Nvidia Geforce 360M in my computer with 1 GB of video ram.  I am out of date on my graphics driver, currently at v. 280.13 so I have been thinking, maybe I need to update my driver.

Whenever I try to run the script in the driver I get an error telling me I need to turn off my curent driver, but any time I type in sudo /etc/init.d/gdm stop, it tells me that I should do it some other strange what that does not work at all.  Could I get some advice on figureing out how to get this to work on my comptuer.  Thanks.

Edit:  I should mention I am on 11.10 right now.

---

### Post by HiImTye on 2012-03-21
the best way is to use a [PPA]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") to update your video drivers (and keep them up to date).

---

### Post by grahammechanical on 2012-03-21
So, you are on 11.10 but what user interface are you on? At the log-in screen you may be able to select the user interface. It could be Ubuntu (Unity 3D) or Ubuntu 2D or some other UI. The point being if you are in Ubuntu 2D then you are not using 3D acceleration even though you have a video card capable of it and a driver suitable for the card.

Another point GDM is not your video driver. It is the log-in manager. And I may be mistaken but I think the GDM has been replaced in 11.10 with LightDM. Unless you are using some other user interface.

You turn off your current video driver by opening Additional Drivers and de-activating it. Then you re-boot and when you get back to the desktop you will be using an open source driver in 2D mode. Then you can install the new driver and re-boot for it to take effect.

First, I would determine if you are running this game in a desktop that is in 2D mode when it needs to be run in a desktop that is in 3D mode.

Regards.

---

### Post by Lefaid on 2012-03-22
I checked to see what enviornment I was in and it looks like I am in the 3D environment.  I concluded this because at the login screen I clicked the gear and Unity was selected instead of 2D unity.

I think I do have the ppa to update my driver.  Could someone go over the commands with me please?

---

