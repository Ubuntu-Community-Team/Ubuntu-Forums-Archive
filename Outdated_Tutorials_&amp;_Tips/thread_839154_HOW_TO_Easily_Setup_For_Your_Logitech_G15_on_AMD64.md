---
title: "HOW TO: Easily Setup For Your Logitech G15 on AMD64"
date: 2008-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Nullack on 2008-06-24
So your using Ubuntu 64bit edition and you want to easily setup your Logitech G15 keyboard.  In this easy to follow guide, I will show you how to quickly get your keyboard setup. The setup will get your volume control working, your clock working and you'll be able to configure the clock to your preference. Importantly you will be able to set it up so that the keyboard is functioning regardless of a user being logged in or not.


This guide will not show you advanced ways of using your G15. The G15 comes with powerful tools for Ubuntu and other GNU Linux distros that enables people to use the G15 is new and exciting ways. This guide focuses on getting your G15 working and does not look at additional  plugins, macros and other cool stuff you can with your G15 once it is setup.


**[COLOR="Red"]CAUTION: I have tested my how to on a version one G15. This how to has not been tested on a version 2 G15. There is no good reason to suspect it will not work on a version 2 G15, but it is noted nonetheless. Once a user with a version 2 G15 reports it as working I will remove this caution.[/COLOR]**

**[COLOR="Red"]CAUTION: This guide is for Hardy Heron and prior Ubuntu releases. If you are on the Intrepid repos, Intrepid has the packages within the Ubuntu repos.[/COLOR]**


Normally, we would use the Ubuntu software sources for our software. One of the key reasons why so many G15 users on Ubuntu are having problems is they are using outdated versions of the keyboard software. The people writing our G15 software have moved ahead of where Ubuntu is up to and having the latest software is important for an easy, reliable experience.


If you have already installed the default Ubuntu versions, dont worry! This process will update them to the latest versions.


Thanks to the generosity of [cdukes]("http://ubuntuforums.org/member.php?u=381073") this person has already obtained the latest source, compiled it and packaged it into 64bit Deb packages for us. :)


**1. Grab the four packages from cdukes**


Goto [cdukes post by clicking here into]("http://ubuntuforums.org/showpost.php?p=4756785&postcount=432") a new browser session.


Now, download these four files to your home directory:


[INDENT][LIST]
[*]g15composer_3.2-1_amd64.deb
[*]g15daemon_1.9.5.3-1_amd64.deb
[*]libg15_1.2.6-1_amd64.deb
[*]libg15render_1.2-1_amd64.deb
[/LIST][/INDENT]


**2. Install the four packages**


Simply click each of the four packages and select install. Hopefully the old Ubuntu packages will be updated soon so we can use the official Ubuntu repos for this.


**3. Download the init script**


I have attached at the bottom of this post my script called g15daemon-rc.init. Again, download this file into your home directory.


**4. Extract the init script**


The file is a compressed archive so open up a terminal session (Accessories -> Terminal). Now copy the following command and paste it into the terminal, hitting enter. Be careful to get all of the command into the cut and paste action.


[INDENT]```
tar -xvjf g15daemon-rc.init.tar.bz2
```[/INDENT]


**5. Move the init script**


Your a wiz on the terminal now, you know what to do!


[INDENT]```
sudo mv g15daemon-rc.init /etc/init.d/
```[/INDENT]


**6. Enable the init script**


[INDENT]```
cd /etc/init.d/
```[/INDENT]


[INDENT]```
sudo chmod +x g15daemon-rc.init
```[/INDENT]


[INDENT]```
sudo update-rc.d g15daemon-rc.init start 51 S .
```[/INDENT]


**7. Startup your G15!**


The big moment is here :)


[INDENT]```
sudo /etc/init.d/g15daemon-rc.init start
```[/INDENT]


You can also use the stop command to bring the service down.


Notice how you can use the buttons near the LCD on the G15 to change the clock. You can change things such as 12 hour or 24 hour time, analogue or digital, show the date or not.


:popcorn:

---

### Post by d2globalinc on 2008-09-16
So is it possible to change the default layout of the default clock to 12 hour instead of 24 so it shows that one every boot so I dont have to hit the LCD buttons to change after every reboot?

Thanks!

D2G

---

