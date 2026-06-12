---
title: "xbmcbuntu no video output at all"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by matt77 on 2014-03-24
I am pretty new to ubuntu and I am experiencing a problem  that hopefully someone can help me with. I have a HP N54L server that I  have had XBMCbuntu running on for about 12 months now. I have a radeon  HD6450 video card in it that I use to connect to my TV. I have caused a  problem whilst trying to install Teamviewer which originally made the  resolution 640x480. My attempts to "fix" this problem has now caused me  to not have any video output at all. Even on initial startup (BIOS)  there isn't any output at all. All I get is a blank screen via the on  board VGA and No Signal on my TV via the HDMI on the HD6450.
  Looking at the system remotely it seems fine. I can still ssh into  it. I can still get to my web GUI of all of the services that I am  running (sickbeard, couchpotato etc.) and they are all working as they  should. Locally however I can't do anything as I have no video  whatsoever. 
  [h=3]Steps taken to create the fault:[/h]  
[LIST=1]
[*]Installed Couchpotato and configured - working perfectly

[*]Installed Teamviewer remotely via ssh

[*]Started the teamviewer daemon remotely via ssh

[*]Couldn't get the status of teamviewer to work and give me the ID so that I could log in and connect to it remotely. 

[*]Checked the physical machine and and the resolution was set to 640x480
[/LIST]
  [h=3]Attempts to fix[/h]  
[LIST=1]
[*]As this is XBMCbuntu it loads by default to XBMC so I went to the  settings menu within XBMC to change the resolution back to 1080p but  there were no other available resolution options.
[*]Reboot - still the same
[*]Quit XBMC and log on to ubuntu desktop - still 640x480

[*]Tried to install proprietary drivers (although from memory I  think that catalyst control centre was available in settings already so  it may have already been using that driver)

[*]reboot

[*]**No video, not even in on boot**

[*]Panic took hold and I tried uninstalling drivers, installing Radeon standard driver etc etc but I just can't get it to work. 

[*]Found an older xorg.conf file that I had backed up from a few  months ago when I must have edited it for some reason. The driver is set  as fglrx so it was already configured with that driver anyway so I  probably never had to mess with it 

[*]Copied this old xorg.conf onto the system

[*]I can no longer ssh into or ping the machine

[*]Found a forum thread and followed the suggestion I found there. Ran:
  sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get remove --purge fglrx*
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install --reinstall
libgl1-mesa-glx libgl1-mesa-dri
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure xserver-xorg

[*]I removed the HD6450 video card out and managed to get it booted  with the onboard VGA. It booted up to a menu which I think is grub. I  selected ubuntu from the menu and it brought up the XBMC logo but then  went to a black screen after this. At this point **I could ping again**. 

[*]I am now using the old xorg.conf file and it gives a pretty good resolution over the on board VGA. 

[*]Put the 6450 back in. Still no output on HDMI as expected BUT I  hooked up the VGA that comes with the 6450 and it is sending video out  on that. It is only 640x480 though. 
[/LIST]
  [h=3]Current state of affairs[/h]  I now have pretty decent resolution on the 6450 via VGA but just not  getting anything on the HDMI. When I run xrandr it says DFP1 and DFP2  are disconnected. I am pretty sure that DFP1 is the HDMI. I need that to  be 1080P! 
  How can I get 1080P on this machine over HDMI again? I would prefer not to reinstall but if I do, will I lose data?

---

### Post by matt77 on 2014-03-24
Edit above to hopefully make more sense....

---

### Post by squakie on 2014-03-25
Dumb question - how is your BIOS set for the video?  Onboard first, PCI first, auto?  It sounds to me like it is grabbing onboard first, which can make for a most interesting time trying to debug this.  I might also suggest using the fglrx-updates driver from the package manager and not the "plain old" fglrx.  Fglrx-updates is supposed to be the driver for that series (I'm running a 6450 myself).

You may also want to post back what you have for the parts of xorg.conf and where they are.  The newer versions of Ubuntu have used a different layout and requires pieces of what used to be the xorg.conf file in different config files.

Personally, I would just rename the xorg.conf to some other name so it's saved and then try:

- remove the 6450
- hook up the on-board VGA
- power on and go to the BIOS
- check the setting(s) for video and modify as needed to boot using the PCI card, not the onboard video
- save changes
- power off
- put the 6450 back in the PC and restart
- rename the xorg.conf file so it is saved but not in place to be used
- remove flgrx
- install fglrx-updates
- reboot
- use the Catalyst control center (be sure to use the "as root" one and enter your normal password)
- set up your monitor as needed and be sure it is being detected.  Set the resolution (and frequencies if needed)
- save it all
- reboot again
- now, is it any different?

I'm running 13.10 and have installed the XBMC package to it and all is well.  You might also want to look at a low-cost alternative that also takes less space - I use a Raspberry Pi, powered USB hub, external USB disk, flash card (needed to boot) and a USB stick as the actual system and storage partitions needed.  There are several free OS's to try - I personally just use OpenELEC.  These will all boot straight into XBMC.  The Pi has HDMI with sound  output,, or you can use composite and a cable to connect analog audio.  I use a cheap ($13 at Micro Center) Tenda W322v1 USB adapter (in the hub)so I can get the libraries updated and watch previews as well.  All of this for way under $200, it takes next to nothing space.  Just a thought.

---

### Post by matt77 on 2014-03-25
Hi there.  Thanks for the reply.  I checked the BIOS but couldn't see a boot sequence setting for the video.  This probably doesn't matter anyway as I now have the 6450 working on its VGA port.  I still however have no HDMI.  I used the package manager to uninstall fglrx, fglrx-amdcccle and fglrx-dev.  I then installed fglrx-updates and it wanted to also install fglrx-amdcccle-updates so they are both now installed.  I also moved xconf.org.  I have rebooted but still no HDMI.  However now I have a different catalyst control centre which allows me to see the settings for the displays which I couldn't do before.  The problem is it only shows the VGA display and doesn't see the HDMI.  It recognises the card as a 6450 which is good.  I will install fglrx-updates-dev and see what happens.

Xrandr shows DFP1 and DFP2 and disconnected still.  If I do DISPLAY=0 xrandr (asked to do this on another forum) it say can't open display 0.  Don't know if that means anything?

---

### Post by matt77 on 2014-03-25
Just went to post the xorg.conf file here and it isn't there.  Obviously I backed it up to a different file name but obviously the system doesn't need it I am guessing.  This is in etc/X11/

---

### Post by matt77 on 2014-03-25
I am sort of getting somewhere with this now.  In synaptics package manager I marked all updates for install.  One was linux-imagexxxxxxx something.  Once they were installed and I rebooted I now am getting the HDMI working.  It still only shows the VGA output on boot but once it gets to the ubuntu desktop the HDMI panel comes on at 640x480.  I can now see it in catalyst control centre but it only allows me that resolution.  I can force resolutions under the TV tab but on boot it remains 640x480 and the bios boot screen etc is all still on the VGA.

---

### Post by matt77 on 2014-03-27
Fixed!  Now I don't know how or why but it is now working....  After many attempts and about 30 solid hours of amlost smashing this thing I ended up pulling the power out of the wall as a last attempt before a reinstall and it worked....  I had to end up reloading the drivers again to get it going properly but it is sorted....  Thanks for the help guys.

---

### Post by squakie on 2014-03-30
Do you have sound over the HDMI connection?  If you need it, there is a boot parameter of "radeon.audio=1".  You can test this at boot, and if it's what you want, there is a config file to put the option in.  If you need that also just post back.

---

