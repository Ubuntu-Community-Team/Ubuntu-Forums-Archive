---
title: "Monitors do not power down when screen blanks"
date: 2021-06-11
forum: New to Ubuntu
---

### Post by robkampen on 2021-06-11
Hi, New to Ubuntu, been a CentOS user for the last 15 years. Just working on a new box - ASUS MINI PN50 with Ubuntu 21.04 fully updated. System CPU is an AMD Ryzen 7 4700u with radeon graphics x8
I have two 27 inch screens, one via DV and other via HDMI
Under settings power I have enabled "dim screen when inactive" and set blank screen to 5 minutes, auto suspend is off as I need the machine to be up 24x7 but want the monitors to turn off after 5 minutes.
I have searched and read lots of junk but most talks about Xorg which I believe is not in use with 21.04.
I have tried xset dpms and get
server does not have extension for dpms option
search on this phrase also doesn't help.
I have libxcb-dpms0 is already the newest version (1.14-3ubuntu1)
not sure where to head next.
Finding quite a few subtle differences between my CentOS 7 experiences and Ubuntu. It seems to be aimed at Windows type users and assumes a little too much for my comfort. 
i.e. when a wifi link has no internet access it just takes it upon itself to look for other wifi links - not what I need when I'm configuring a new network device and want it to stay locked to the link I select. 
I have tried a number of solutions but NetworkManager (?) thinks it knows better.
Was contemplating using Ubuntu for some servers but this kind of take-over-control is not acceptable.
Anyway, first things first - need to get my monitors to go into power save mode after 5 minutes.
Suggestions please.
Rob

---

### Post by grahammechanical on 2021-06-11
I feel like getting some things straight from the beginning but I think that I might transgress the Code of Conduct. So, I will limit myself to saying that I consider myself a Ubuntu type user and not a Windows type user. I have never used CentOS and I suspect that there are more than subtle differences between CentOS and Ubuntu. Thanks to the Linux developers we have choice.

Ubuntu 21.04 uses a Wayland compositor by default but it does have an option to use the X-Server. At the login screen press enter and before entering the password click the Ubuntu icon that appears at the bottom right of the screen and select Ubuntu on X-Server.

I only have one monitor and as it does not get its power from the motherboard I do not expect the monitor to power off when I power off the computer. The monitor will enter power save mode when it is without a signal. It will do that after a defined number of minutes. It is a function of the monitor's own settings.

Regards

---

### Post by robkampen on 2021-06-12
Hi, no offence intended by the windows comment - was referring to the way that more and more setup is assumed by the OS, and in many cases one cannot over-ride it - the developer knows better than the user. 
Linux has mostly recognised that the user should have choice and thus creates lots of options and setup becomes more complex.
thanks for the suggestion about X11/xorg vs wayland - I'm now trying xorg and will see if that fares any better.
Turns out - no difference.
The display blanks, the monitors detect no signal - briefly (don't always see their no signal message) - then the pointer appears and the display remain on full power but dark, other than pointer.
Just FYI, I have my old CentOS box hooked up to the same two displays but using the other HDMI connector and it behaves just fine, after five minutes, displays dim and once dark the monitors detect no signal and go into power save mode. 
Move the mouse, press a key and it all wakes up.
So, I am still looking for the required setting / driver / other, that will enable me to have the computer remain alive and responsive to SSH or apache requests, but have the displays asleep and saving power.
It is clear that the monitors / Energy Star whatever, works just fine, so it must be the OS/computer hardware combo that I need to tame.
Thanks
Rob

---

### Post by mikewhatever on 2021-06-12
I've never used CentOS, so not sure what kind of server environment it offeres. Ubuntu server edition is a command line system without Xorg, Wayland or Network Manager, while you seem to have a Desktop Edition. I am also not sure why have two monitors connected, and not use ssh for administration.

PS: The Network Manager can see all wireless APs in range. Not sure what you mean by "takes it upon itself to look for other wifi links".

---

### Post by ajgreeny on 2021-06-12
Somewhere in the power-management settings there should be a section for the monitor where you can set the time for screen blanking and screen power-off.

I use Xfce and Xubuntu with the xfce4-power-manager an d this may be different from your system but it's  worth a search.

---

### Post by robkampen on 2021-06-13
Thanks for your responses.
The Ubuntu settings power has the screen brightness and dim screen when inactive and blank screen time select box.
No screen power off.
I found and installed xfce4-power-manager along with dependencies, and invoked via xfce4-power-manager-settings.
Adjusted the three sliders - blank after 1 minute, - put to sleep after two minutes - switch off after 3 minutes.
No difference - display dims after 1 minute, mouse pointer blanks out last, screen back light turns off, about 10 second later the display says no signal and then the back light comes on with mouse pointer showing, and rest of screen dark.
Interestingly, if the pointer is on the second display, it always reappears on the first display. If on the first display it remains where it was.
So it seems something is triggering the wake up. I have removed my MX master3 wireless/bluetooth mouse and used a USB corded mouse but no difference.
Any other ideas?

---

### Post by ajgreeny on 2021-06-13
When you started to use xfce4-power-manager did you also stop the gnome version from running; I am not even sure if it is possible to run both together but perhaps gnome version is taking charge even when the xfce version is running.

---

### Post by TheFu on 2021-06-13
I have some time and appreciate a good rant. Thanks for providing the opportunity!  Take this in that same vein.

> **robkampen said:**
> Hi, New to Ubuntu, been a CentOS user for the last 15 years. Just working on a new box - ASUS MINI PN50 with Ubuntu 21.04 fully updated. System CPU is an AMD Ryzen 7 4700u with radeon graphics x8

21.04 isn't for people new to Ubuntu. It is not an LTS and gets 9 months of support only. Think of it as Fedora, just with much less support.  Canonical inflicts new ideas on non-LTS releases.  If you seek something more like CentOS, load 20.04 LTS. I have no idea which level of Ryzen iGPU is well supported on 20.04. Sorry. I stay away from bleeding edge hardware and kernels and most software.  Learned that over 25 yrs of Linux. Newer isn't better.  It is just newer and requires much more patching.

CentOS is a server OS meant for server admins, not end users.  Ubuntu Desktops are meant for your Grandma and people who don't want to know too much about what is happening underneath the GUI.  Very different philosophies.  Isn't it great that we can have similar, but very different choices?

Why not just stay with CentOS if that is your comfort zone?   I'm not really asking, BTW.

> **robkampen said:**
> I have two 27 inch screens, one via DV and other via HDMI
Under settings power I have enabled "dim screen when inactive" and set blank screen to 5 minutes, auto suspend is off as I need the machine to be up 24x7 but want the monitors to turn off after 5 minutes.
Sorry. Can't help with GUI stuff.  My desktop doesn't use Gnome, nor a bleeding edge kernel. I run fvwm as the WM.
To enable screen blanking for X11, I use
```
xset +dpms &
xset s on &
```
Obviously, X11 is my windowing server of choice.  Wayland breaks many of my normal workflows. It just isn't ready for normal use yet, IMHO.  Most of my windows are actually running on other systems.

> **robkampen said:**
> 
I have searched and read lots of junk but most talks about Xorg which I believe is not in use with 21.04.
Wayland is attempted first on Desktop Ubuntu systems. If that fails, there is an automatic fallback to X11. You can force either to be used, if you like. There's a config file.  I've posted the answer for that in these forums in the last month or so.

> **robkampen said:**
> 
I have tried xset dpms and get server does not have extension for dpms option
Are you running Ubuntu Server or one of the 10 Ubuntu Desktop installs?  It matters from a "what is already installed" standpoint and how certain things are configured.
A quick look at the DPMS-related manpages makes it clear that is part of X11, so if Wayland is being used, I'd expect some other method would need to be used.

> **robkampen said:**
> 
Finding quite a few subtle differences between my CentOS 7 experiences and Ubuntu. It seems to be aimed at Windows type users and assumes a little too much for my comfort. 
i.e. when a wifi link has no internet access it just takes it upon itself to look for other wifi links - not what I need when I'm configuring a new network device and want it to stay locked to the link I select. 
I have tried a number of solutions but NetworkManager (?) thinks it knows better.

Yes, network manager sucks for non-trivial situations.  I purge it from all my systems to prevent NM-abuse. Ubuntu Server uses Netplan YAML files for configuration since 18.04.  They became useful around the fall of 2019.  For my laptop, I use wicd-cli still when I need wifi control. I find it easier.  To each their own.

> **robkampen said:**
> 
Was contemplating using Ubuntu for some servers but this kind of take-over-control is not acceptable.
Anyway, first things first - need to get my monitors to go into power save mode after 5 minutes.

Ubuntu Server is much more like Debian Server, but without all the really old software.  Ubuntu releases begin with Debian Stable, then add selected, Debian-Testing packages and integrate those all into a fairly stable release that gets maintained for 5 yrs assuming we choose only the LTS releases.  LTS releases happen even years, in April.  14.04, 16.04, 18.04, 20.04, 22.04 .... you get the idea.  Any other release is NOT LTS and likely to have "here, hold my beer, watch this!" software selected by Canonical.  Any non-LTS release is just a toy IMHO. Not worth my time and 9 months of support definitely makes this true.  I did my bleeding edge time with Linux in the 1990s. Never again.

> **robkampen said:**
> 
Suggestions please.
Rob

The normal, bloated, Ubuntu Desktop is Canonical's attempt to provide a Mac-like experience to be used by Grandma. Keep that in your mind. That's why Ubuntu is so popular.  OTOH, if you don't like that, then you can rip it out and us any DE or WM that you prefer just fine.  A few things I remove from every Ubuntu install: 
[LIST]
[*]nano
[*]network-manager-*
[*]nm-*
[*]avahi
[*]update-notifier-common
[*]gedit
[*]leafpad
[*]chrome
[*]bluez
[*]unity-asset-pool
[*]geoclue-ubuntu-geoip
[/LIST]

I also remove some kernel modules related to bluetooth and IPv6.  I've been burned by those previously.

Let me see what google finds for turning off a monitor under Wayland.  [https://askubuntu.com/questions/979334/how-to-turn-off-the-screen-in-ubuntu-17-10](https://askubuntu.com/questions/979334/how-to-turn-off-the-screen-in-ubuntu-17-10)
Has a number of script that would make any linux guru happy in the complexity required. ;)

Can't wait until you rant about snap packages.  That should be good! ;)  I've done my best, but failed to get snaps to work with any NFS locations or NFS home directories.  There are just a few "mandatory" snaps that I need. Most packages can be found in non-snap mode by adding a few PPAs from trusted sources.

---

### Post by grahammechanical on 2021-06-13
I contend that there is a big difference between an OS blanking the monitor screen and setting the monitor in standby/power save mode. I am not even sure if it is technically possible for an OS to send such a signal through the video adapter electronics on through the HDMI cable to the OS in the monitor.

I would like to see evidence that the Gnome developers have put the functionality into Gnome Shell so that the Ubuntu developers can implement it. This link shows that it is technically possible but it is not a trivial thing to achieve. You need to read all the way down the page and keep in mind the difference between blanking the screen and putting the monitor in power save/standby mode.

[https://superuser.com/questions/648805/is-it-possible-to-power-on-off-a-monitor-using-the-computer](https://superuser.com/questions/648805/is-it-possible-to-power-on-off-a-monitor-using-the-computer)

Regards

---

### Post by robkampen on 2021-06-18
Hi grahammechanical
Thanks for the link, very useful.

I am unsure of quite the right terms - and what I have enjoyed for the last decade or so is that when my system goes into "blank screen" it locks - thus need password to access. A movement of mouse or keyboard wakes up the system.
The monitors see the blank screen and after some seconds go into power save mode - i.e the backlight goes off and the on indicator light typically changes colour. - I call this standby as the application of a signal wakes the monitor up. 
Power off is when all the indicator lights are off - this does not typically mean zero power, as the on/off button is typically a momentary press button - i.e. there is something awake and powered up, looking for the power button key press.

So my issue with Ubuntu / my new hardware, is that the monitors do not go into standby - they do blank, and then backlight goes off, then they momentarily go to standby but immediately wake up again.
With the link you gave me I have now set up 4 very simple one line scripts that I have called monitor1-on, monitor1-off, monitor2-on, monitor2-off and these do turn the monitors into standby and back on - thus the hardware is capable of doing all that is needed.
Monitor 1 is where the login dialog takes place.

If I use monitor1-off then monitor 1 goes into standby. With monitor 1 already in standby, when the screen dim takes place, the second monitor correctly dims, blanks and goes into standby.
Movement of the mouse / keyboard activity wakes up monitor 2 but monitor 1 remains in standby. As linux allows one to simply type in the password for the currently logged in user, that wakes up the system and monitor 2 goes from screen saver into active view of screen 2 contents. Monitor 1 remains in standby. I can run monitor1-on and it wakes up and shows screen content.

Trying the opposite i.e. running monitor2-off puts monitor 2 into standby but monitor 1 will dim, blank, monitor shows a brief "no signal" message but then immediately wakes up again - thus much like the default Ubuntu behaviour.
I have my old CentOS box connected the the alternate HDMI connectors of both the monitors and this works as expected - both monitors enter standby until I move the mouse or type on the keyboard.

So my question remains - how do I set up Ubuntu to work properly - it seems to try, but something goes wrong unless I have monitor 1 already in standby. Please note that this manual process of putting a display into standby does not seem to communicate itself to the OS as the mouse continues to behave like the screen is there.
If I manually put the monitors into standby, then I can press the monitor power buttons (twice - once to turn from standby to off, then again to turn on) and the screens will wake and depending upon period will either need login or just show both screens.

None of the combos I have tried are really what I want, they all cause extra steps and if someone else wants to use the machine they have to power cycle both monitors.
I am not yet sufficiently adept with Ubuntu to try different versions to see if it is a particular version of  OS related, or if it is a hardware / OS relationship issue.

It would be nice to know if other dual monitor users have these problems or do their monitors simply behave like I'm used to. 

While not a total show stopper, this is of sufficient aggravation to drive me to look for an alternative OS for my hardware.
Regards
Rob

---

### Post by TheFu on 2021-06-18
GUI stuff isn't the OS on any Linux system. Any GUI is tacked on after.  That means, trying different GUIs until you find one that behaves in the way expected isn't a big deal.  The GUI is just another program to be installed, tested, and removed.  Most definitely NOT the OS.

Gnome3 has lots of issues. If this is a show stopper, perhaps trying KDE would make sense?  Or Mate or XFCE or LXQt or Cinnamon or ... dropping a DE completely and going with a Window Manager-only setup?  Lots of options.

I'm actually a little confused that CentOS has a GUI.  Servers shouldn't have any GUI.

---

### Post by Das Goat on 2021-07-23
It has been a month an a half and maybe your found your answer. If so what was the ultimate solution? I'm not sure why the other posters went off the rails about differences between OS' and didn't address you issue, but maybe this will help as I have the same issue:

Monitors go blank, but do not power down

Background: I received a donation of a small stack of identical Dell 5040's. I decided to replace three PC of various makes, all running dual monitors, all working before the swap. Each got a fresh install of the latest build of Ubuntu 20.04.2.0  Two of the builds work exactly as expected, but one exhibits the problem you are reporting.

Since I have a small stack of identical units, I swaped out the box but kep the already build HD. The problem was still there. Next, I booted to the USB installation media and selected "Try Ubuntu" and let it sit for 10-15 mintues. It work liked you would expect it to. So I figured something must have gone wrong in the original installation. Give it a fresh installation and ... I still have the problem. :(

So it's not that hardware, the monitors turn off properly if Ubuntu is ran from the installation USB, but will not turn off properly after a full installation. I also reran all updates. Later today I will receive new HDMI to Displayport cables and swap those out (for an unrelated reason) so maybe that will change something. But again, because the monitors turn off normally when booted from the installation media, this is not likely the cause. And of course it's not the PC because I changed it, and the other two are behaving normally. The only thing left is the monitors themselves. They are a pair of InnoView 24".

Years ago I had a thread going about an odd problem with my Toshiba laptop. Similar to this issue, when the laptop was booted to the installation media, the keyboard and touchpad worked fine, but once the OS was installed, they would stop working until I entered some 'no splash' and mux=1 strings in my grub config file. I have no idea why that worked, but I have always had to do that when installing Ubuntu to that laptop. Perhaps there is some weird combination going on with the InnoView monitors and the Dell 5040. I will try the 'no splash' trick later today and let you know if it changed anything.

---

### Post by TheFu on 2021-07-23
Do newer Ubuntu Desktop installs switch to a proprietary driver in the "Try Ubuntu" environment or are they using the F/LOSS GPU driver?  That could be the difference for why some commands work and others do not.

Proprietary GPU drivers have always caused more problems then they should for Linux.  The best capability and stable GPUs are from Intel.  Then AMD, and lastly nvidia.  The first two provide driver code to Linux. nVidia provides objects which aren't always so good.  I have systems with all three types of GPUs.  By far, I have the least issues with Intel iGPUs and the most issues with nvidia.  nvidia (430 GT and a 1030 GT) is just a pain, honestly. Really wish I would have gotten an AMD rather than the 1030.

---

### Post by Das Goat on 2021-07-24
So I did some more testing:

Got new cables. Made no difference, but I didn't expect them to.

Looked up my old post on the laptop. Entered this:
                    
                sudo nano /etc/default/grub
                        changed this line to look like this              GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux i8042.reset"
                sudo update-grub
                Reboot        
               
This had no effect, but I knew it was just a shot in the dark. I reversed my changes

I tried booting to the installation USB agan and verified the screens turn off as expected.

Pulled an identical unit from another station that has been working normally and connected it to these two InnoView monitors. This unit exhibits the same off behavior: Screens go blank except the cursor remains inexplicitly on the screen anf the monitors never power down.

I could think of only one other thing to try. Many of these came with an add on video card: AMD RADEON R5 340X 2GB DDR3 PCI-EXPRESS GRAPHICS VIDEO CARD KG8WY 7122107700G. I pulled the card from the unit I have been working with and tried that. It made no difference.

The bottom line: When I hook up a Dell 5040 to these two InnoView monitors and boot from the installation USB into "Try Ubuntu" mode, the monitors go blank and power off per normal operation, but for some inexplicable reason when the OS is loaded from the internal HD, the monitors go blank except for the pointer which is left on the screen, and they never power off

I sure hope someone out there has a clue on this weird behavior.

---

### Post by TheFu on 2021-07-24
Das Goat, if you would like help, please open your own thread. This thread is for robkampen.

---

### Post by Das Goat on 2021-07-24
One final note:

I though maybe the BIOS might be causing this behavior, so I did an upgrade to the current version 1.17.1  Now, when the screen goes blank the monitors DO turn off ... but just for a second and come on again. I set the time to 1 minute so I could observe and the system just kept doing that.

Finally, I have a model 7020 that I was going to decommission. I hooked it up to these monitors and gave it a try. This one does this second behavior, turning things off then immediately back on. So this whole issue seems to be this particular monitor model paired with a Dell Optiplex computer.

I put the original HP computer back that I was going to decommission after giving it a good cleaning and the problem went away. So ... HP+InnoView=GOOD  Dell+Innoview=BAD

I hope this helps someone.

---

### Post by airbag888 on 2022-03-27
> **TheFu said:**
> Das Goat, if you would like help, please open your own thread. This thread is for robkampen.
I for one am grateful that this information is consolidated in 1 thread. What's the point of spreading this around - They all seem connected.

@DasGoat
I have been on a merry go around to find a distro that actually WORKS with screen blanking and standby. NONE work.
Those I tried: Debian, Ubuntu (LTS and not), LinuxMint (cinnamon/mate), PopOS, Fedora and more. No luck at all.
The closest I got is that this is somehow dpms related.

Meanwhile exact same setup works perfect under... windows. Come on Linux help me get off MS.
Having my monitors not standby is a huge waste of electricity, especially when wfh.

I also can't find anything at all in the logs showing something failed.

Baffling this has not happened to more users. This is clearly dual monitor related (perhaps tri+) and potentially when you are using both dP and hdmi simultaneously

Specs:
5600x, 6700XT, 32GB RAM, installed on fresh nvme drive
Monitor1: HDMI - Generic Acer 1080p @ 60Hz
Monitor2: dP - LG 34GK950-F @ 144Hz

---

### Post by wildmanne39 on 2022-03-27
Hi airbag888 
> What's the point of spreading this around - They all seem connected.
The keyword is seems, although the symptoms are the same there is usually a different underlying cause plus it gets confusing for everyone when more then one person is being helped in a thread I know this from personal experience and the OP of this thread deserves individual help just like you do so if you want help with your issue please start your own thread also this thread is like 9 months old and has not had a post all this time and we close old threads, so I am closing this one for house keeping sake.

Old thread back to sleep.

---

