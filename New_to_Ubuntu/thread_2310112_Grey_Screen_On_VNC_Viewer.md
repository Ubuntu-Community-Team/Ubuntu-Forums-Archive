---
title: "Grey Screen On VNC Viewer"
date: 2016-01-16
forum: New to Ubuntu
---

### Post by neolestro on 2016-01-16
hello,

i'm quite newbie.

i tried to read lots of things before i post this thread. I failed everytime.

I have a vps which i installed ubuntu desktop on it. i tried to install vnc server and i'm able to connect from my windows7(via tight vnc viewer)  but unfortunately i'm getting this screen;

[IMG]http://i.imgur.com/j8ivPGC.jpg[/IMG]
my **root/.vnc/xstartup** like this;

[PHP]#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &

[/PHP]

i checked to permission and it's alright. when i reboot the vps, i need to start my vnc server manually everytime..

i tried to change "gnome-session &" instead of "x-window-manager &". didnt work.

i dont know what to do. i spent like 4-5 hours already to fix this. i really tired :\

---

### Post by TheFu on 2016-01-16
The "xsetroot -solid grey" is why it is grey. Nothing magical there. X is running.
Try right clicking anywhere on that gray background - may need to wait a few seconds - and a menu should appear. If you want a panel/menu, run one - something like lxpanel is probably what you want, but a window-manager must be running. I don't see any borders, so don't think a WM is running. Try openbox - may need to install it first.

Can't really use gnome3 or Unity over VNC. A lighter WM is needed, especially for remote connections.  I don't use VNC, but with x2go (which has ssh tunneling built in), openbox or openbox + LXDE work great.

---

### Post by neolestro on 2016-01-16
> **TheFu said:**
> The "xsetroot -solid grey" is why it is grey. Nothing magical there. X is running.
Try right clicking anywhere on that gray background - may need to wait a few seconds - and a menu should appear. If you want a panel/menu, run one - something like lxpanel is probably what you want, but a window-manager must be running. I don't see any borders, so don't think a WM is running. Try openbox - may need to install it first.

Can't really use gnome3 or Unity over VNC. A lighter WM is needed, especially for remote connections.  I don't use VNC, but with x2go (which has ssh tunneling built in), openbox or openbox + LXDE work great.

i really appreciated for you help and explanation. After i tried lots of things then i decided to install ubuntu 12 and xfce4. now everything is definately working smoothly.

thanks for advice!

---

### Post by TheFu on 2016-01-16
12.04? Really?  Not sure I'd do that today.  Sure, it is "supported" for another yr, but ... 

I'd use x2go. More secure than VNC, faster, easier to get working. Downside is there are clients for only full OSes, not iWhatever or Android.  I've been using NX (which is the protocol used by x2go) to remote into my desktop for almost 4 yrs now.  I'm using it now from a Win7 machine.  Lots of posts here like yours where a few of us recommend x2go.  night/day. If you go that direction, be certain to use the PPA and follow the install instructions for both the client-side and server-side. 1st time should take about 15 minutes (assuming ssh is already working). After that, 2-3 minutes tops.  On Windows, get the extra font package installer too. Not needed on OSX or Linux clients.

---

### Post by neolestro on 2016-01-16
> **TheFu said:**
> 12.04? Really?  Not sure I'd do that today.  Sure, it is "supported" for another yr, but ... 

I'd use x2go. More secure than VNC, faster, easier to get working. Downside is there are clients for only full OSes, not iWhatever or Android.  I've been using NX (which is the protocol used by x2go) to remote into my desktop for almost 4 yrs now.  I'm using it now from a Win7 machine.  Lots of posts here like yours where a few of us recommend x2go.  night/day. If you go that direction, be certain to use the PPA and follow the install instructions for both the client-side and server-side. 1st time should take about 15 minutes (assuming ssh is already working). After that, 2-3 minutes tops.  On Windows, get the extra font package installer too. Not needed on OSX or Linux clients.


i have no idea what is x2go or what OS will be good on my tiny and weak  vps. if you have any suggestion to install step by step that i can  follow it. because now i stuck at install kind of "notepad". this linux  gonna kill me but im trying so hard right now and i dont want to give  up.  :-({|=

enlighten me if you have some guide.

---

### Post by TheFu on 2016-01-16
googled ... "x2go ppa" - that found: [https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative](https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative) and about 50 others. HowtoForge is reputable for getting things to work, but don't expect everything there to secure at completion.  Security is always the installer's responsibility. ALWAYS.

google is always your friend. If you think there is 1 manual for anything you need to know about Linux or Ubuntu, you are mistaken.  Linux is extremely flexible. That makes it complicated, but useful for all sorts of things that we never considered possible 3, 5, 10, 20 yrs ago.  That flexibility is where the power comes, but it also means that YOU need to be flexible too.  We always say there are 500 different ways to solve any specific problem with Unix.  Sometimes there are more and sometimes there are less.  For remote desktops, there are about 20 different options, 7 are reasonable and IMHO, x2go is the best (for my needs). Other people will push you to use some unpaid, free, closed, software from a web service. How secure is that company?  We don't know. We won't know until something bad happens.  One of those companies had their remote access DB hacked for over a year and we only learned about it 3 months ago. Nice. Even if we run all the software only on our own hardware/systems, we trust the guys who create that software.  VNC, ssh, x2go, rdp, Ubuntu, Linux, etc... I prefer layered security - so x2go uses ssh for access. This week, a vulnerability in ssh was announced - updates have been available for a few days to address it. It is only client-side, not server-side. Still, a tool we all "trust" had an issue.  ssh is the primary way I use to connect to systems around the world. Scary, but easily addressed.

If you are really new at this stuff, a VPS with a GUI isn't the best way to learn Linux.  Use the VPS without any GUI and spend the next 6 months immersed.  Or, better, load Linux into a virtual machine on your normal desktop and use it 8+ hrs a day, avoid using "that other OS" more than 1 hr a day and only for things you can't get working on Linux.

People ask me all the time how to learn Linux - so much that I wrote a blog article about it: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - forget the GUI. The GUIs change every few years and you'll forever be learning some new GUI. That is counter productive, IMHO. Almost all of the shell/CLI commands I learned in 1993, still work.  The GUI is convenient like a credit card, but you always have to pay for it later with cash.  Better to just use cash to start, IMHO. Others have different opinions, which is fine.  90% of the power for Unix is in the shell and scripting, NOT in the point-n-click stuff.

This stuff should be fun.  Stay immersed in Linux to learn the most, the quickest.

---

### Post by neolestro on 2016-01-16
> **TheFu said:**
> googled ... "x2go ppa" - that found: [https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative](https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative) and about 50 others. HowtoForge is reputable for getting things to work, but don't expect everything there to secure at completion.  Security is always the installer's responsibility. ALWAYS.

google is always your friend. If you think there is 1 manual for anything you need to know about Linux or Ubuntu, you are mistaken.  Linux is extremely flexible. That makes it complicated, but useful for all sorts of things that we never considered possible 3, 5, 10, 20 yrs ago.  That flexibility is where the power comes, but it also means that YOU need to be flexible too.  We always say there are 500 different ways to solve any specific problem with Unix.  Sometimes there are more and sometimes there are less.  For remote desktops, there are about 20 different options, 7 are reasonable and IMHO, x2go is the best (for my needs). Other people will push you to use some unpaid, free, closed, software from a web service. How secure is that company?  We don't know. We won't know until something bad happens.  One of those companies had their remote access DB hacked for over a year and we only learned about it 3 months ago. Nice. Even if we run all the software only on our own hardware/systems, we trust the guys who create that software.  VNC, ssh, x2go, rdp, Ubuntu, Linux, etc... I prefer layered security - so x2go uses ssh for access. This week, a vulnerability in ssh was announced - updates have been available for a few days to address it. It is only client-side, not server-side. Still, a tool we all "trust" had an issue.  ssh is the primary way I use to connect to systems around the world. Scary, but easily addressed.

If you are really new at this stuff, a VPS with a GUI isn't the best way to learn Linux.  Use the VPS without any GUI and spend the next 6 months immersed.  Or, better, load Linux into a virtual machine on your normal desktop and use it 8+ hrs a day, avoid using "that other OS" more than 1 hr a day and only for things you can't get working on Linux.

People ask me all the time how to learn Linux - so much that I wrote a blog article about it: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - forget the GUI. The GUIs change every few years and you'll forever be learning some new GUI. That is counter productive, IMHO. Almost all of the shell/CLI commands I learned in 1993, still work.  The GUI is convenient like a credit card, but you always have to pay for it later with cash.  Better to just use cash to start, IMHO. Others have different opinions, which is fine.  90% of the power for Unix is in the shell and scripting, NOT in the point-n-click stuff.

This stuff should be fun.  Stay immersed in Linux to learn the most, the quickest.

first of all, i didnt expect this kind of long reply and be sure, i read it double times. Google is really a friend but i believe that it's not working what u expecting in these years cause bunch of trash informations. 7-8 years ago, when u want to check somethings, it was directly showing to correct content for you even with simple "keyword" but now you need to use more specific search terms and yes this is my second time that i'm drowning into flexible linux system. I can't find what i looking for or don't have so much idea what exactly should i look for. i bought this vps for my couple business things but i noticed that i'm focusing on how to use linux stable instead of doing business things. unfortunately i need gui system for it(browsing). my another idea is, gonna buy a mid-range laptop and try to install some linux on it. i think i can learn faster on it.

secondly, you're totally right about security thing. So much exploits, vulnerables coming out with new systems and even on old systems.

i'm gonna check your link to use it right now, probably it will gonna like a charm and when i get some free time, also want to read ur blog. i appreciated your thoughtful advices and ideas.

---

### Post by TheFu on 2016-01-16
I'm a touch typist. Unix taught me that. I type faster than I speak. ;) Worked as a programmer before learning Unix and used 3 fingers to type for about 4 yrs. With Unix, typing is mandatory to access the powerful stuff; it is expected. OTOH, these days with tab-completion, running commands, usually needs just 2-3 characters to fill in the rest of the data with a {tab} - command completion rocks.  There are lots of youtube videos about Linux these days.  Learning to use tab-completion ASAP will save you hours, weeks, months of frustration.

Random google results aren't always the best place to find the answer YOU need.  It is best to add "ubuntu 14.04" - assuming you run that - to the search. Lots of important things have changed since 14.04 and with 16.04 even more will change for how to start/stop daemons/services on a system.  It isn't just Ubuntu, but debian, redhat, centos and most of the major distros are all going through this huge change.  That means all the "sudo service XYZ start" commands won't work anymore, for example.

Linux servers aren't meant for casual users. If that is your expectation, pay the 2x costs and get a Windows VPS. Then you can struggle with the Windows-isms and commercial software stuff. At least then, you'll be in a comfort zone.

You don't need another laptop to run Linux on. Use a virtual machine.  Most computers made in the last 3-5 yrs have enough power and RAM to easily run 2-25 virtual Linux servers.  Heck, I have a $200 chromebook (wiped ChromeOS and loaded Ubuntu on it) that has enough CPU to handle 6 VMs. Because it is so cheap, it doesn't have the necessary RAM to run them all concurrently, but the CPU is faster than many Core 2 Duo desktop CPUs.  Chromebooks cannot be upgraded with more RAM (usually).

Just picked up another 3 lbs Chromebook with more RAM and more faster CPU - it is like a $1000 ultrabook for 60% off!  Of course, it takes a little effort to install Linux on these devices and I cannot suggest it for someone new to Linux. There are some dangers which could "brick" the chromebook if not extremely careful.  Ok, it isn't really "bricked" - just requires about $60 in extra hardware to re-write the firmware using a Raspberry Pi and specialized clip-tool to connect to a specific firmware chip from above. Unexpected, but necessary in my situation.  All because I wanted NOT to run a google OS on my hardware.

Most of my blog articles aren't written for people really new to Linux.  They are notes for myself to help remember things that I've learned. Most probably aren't of any interest to you, but feel free to browse.

In conclusion - setup a VM, run Linux in that on your existing PC. If you need help, there are lots of how-to guides. If you need more personalized help, post the system config (CPU/RAM/DISK/Network) into the "Virtualization" subforum here and someone should reply with ideas.

Don't forget, this stuff is fun!

---

### Post by neolestro on 2016-01-16
> **TheFu said:**
> I'm a touch typist. Unix taught me that. I type faster than I speak. ;) Worked as a programmer before learning Unix and used 3 fingers to type for about 4 yrs. With Unix, typing is mandatory to access the powerful stuff; it is expected. OTOH, these days with tab-completion, running commands, usually needs just 2-3 characters to fill in the rest of the data with a {tab} - command completion rocks.  There are lots of youtube videos about Linux these days.  Learning to use tab-completion ASAP will save you hours, weeks, months of frustration.

Random google results aren't always the best place to find the answer YOU need.  It is best to add "ubuntu 14.04" - assuming you run that - to the search. Lots of important things have changed since 14.04 and with 16.04 even more will change for how to start/stop daemons/services on a system.  It isn't just Ubuntu, but debian, redhat, centos and most of the major distros are all going through this huge change.  That means all the "sudo service XYZ start" commands won't work anymore, for example.

Linux servers aren't meant for casual users. If that is your expectation, pay the 2x costs and get a Windows VPS. Then you can struggle with the Windows-isms and commercial software stuff. At least then, you'll be in a comfort zone.

You don't need another laptop to run Linux on. Use a virtual machine.  Most computers made in the last 3-5 yrs have enough power and RAM to easily run 2-25 virtual Linux servers.  Heck, I have a $200 chromebook (wiped ChromeOS and loaded Ubuntu on it) that has enough CPU to handle 6 VMs. Because it is so cheap, it doesn't have the necessary RAM to run them all concurrently, but the CPU is faster than many Core 2 Duo desktop CPUs.  Chromebooks cannot be upgraded with more RAM (usually).

Just picked up another 3 lbs Chromebook with more RAM and more faster CPU - it is like a $1000 ultrabook for 60% off!  Of course, it takes a little effort to install Linux on these devices and I cannot suggest it for someone new to Linux. There are some dangers which could "brick" the chromebook if not extremely careful.  Ok, it isn't really "bricked" - just requires about $60 in extra hardware to re-write the firmware using a Raspberry Pi and specialized clip-tool to connect to a specific firmware chip from above. Unexpected, but necessary in my situation.  All because I wanted NOT to run a google OS on my hardware.

Most of my blog articles aren't written for people really new to Linux.  They are notes for myself to help remember things that I've learned. Most probably aren't of any interest to you, but feel free to browse.

In conclusion - setup a VM, run Linux in that on your existing PC. If you need help, there are lots of how-to guides. If you need more personalized help, post the system config (CPU/RAM/DISK/Network) into the "Virtualization" subforum here and someone should reply with ideas.

Don't forget, this stuff is fun!

that's right. maybe i just buy low-range laptop for this. frankly, i prefer windows vps at lots of time but sometimes i'm getting great discounts for linux vps servers. So somehow, my hands getting dirty with linux which i hate and also like it. that means i need to learn more about it. 
Btw, i could do install it without any problem via ur guide link and i noticed that it's really working so fast. Again, thanks for your advices and informations. 

that is painful and also enjoyable fun :)

---

### Post by TheFu on 2016-01-16
Since Microsoft forced UEFI onto the world, Linux installs have gotten very complicated in some situations.  Sometimes a good distro setup "just works", but in about 5% of the cases, it takes much, much, much more knowledge than the person doing the install has.  I've avoided UEFI installations completely to this point.

Again - I would NOT buy another computer just to learn Linux.  I would use a virtual machine running on my current PC. Why spend any money at all?  A PC with 4G of RAM and a Core 2Duo or better CPU will do virtualization nicely. Some celerons and Atoms can do virtualization, though only the newest versions aren't painful.

---

