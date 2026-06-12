---
title: "ubuntu desktop, X Server I think, screwed"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by PoopyTheJ on 2008-05-01
ok, I tried to install new ATI drivers using envy, well when I rebooted I had a resolution of 800x600 and the system couldn't see my video card. I had a low res screen saying your system cannot determine the vdeio card or something along those lines, and I'd have to configure it myself. I went into the config, chose ati fglrx proprietary, my monitor, Viewsonic g220f, althoug h mine is a g225f, chose 1600x1200 tested, it all looked fine, I clicked ok, it said all users must log off and log back on for changes to take effect. I did so, I couldn't see the login because it was all squiggly lines, I entered my user name and password though and hit enter and my desktop looks like green and blue and pink lines going horizontally across the screen. I can't see anything. What can I do to fix this. I have a number of files on my desktop I have to have, and I need to do schoolwork on it so what can I do to fix this isue?

I'm running an ATI3850HD, that was working beautifully before I tried to update the drivers, also running or was running compiz.

---

### Post by iSplicer on 2008-05-01
Hey 

Boot into recovery mode, and type

sudo dpkg-reconfigure xserver-xorg

---

### Post by PoopyTheJ on 2008-05-01
ok now I have a onfiguration thing to go through, what driver should I choose, I have a vesa, and ati and nvidia and everthing else under the sun.

---

### Post by iSplicer on 2008-05-01
Ati, if that fails, vesa

---

### Post by PoopyTheJ on 2008-05-01
Thanks for that help,I really appreciate it.I ran through that configuration, and I chose my video card driver and monitor, typed exit and went into x, however it's running in low resolution mode, doesn't recognize my monitor or video card. What's my next step? Do I need to uninstall drivers, reinstall drivers, uninstall compiz, what can I do to get my desktop back to accelerated beauty? You got me here so worst case I can back everything up, I think, and reinstall though I really would rather not do that, I'd hate to have to reinstall after I screw every little thing up, as I have a feeling that would take a lot of reinstalls!  :)

---

### Post by iSplicer on 2008-05-01
> **PoopyTheJ said:**
> Thanks for that help,I really appreciate it.I ran through that configuration, and I chose my video card driver and monitor, typed exit and went into x, however it's running in low resolution mode, doesn't recognize my monitor or video card. What's my next step? Do I need to uninstall drivers, reinstall drivers, uninstall compiz, what can I do to get my desktop back to accelerated beauty? You got me here so worst case I can back everything up, I think, and reinstall though I really would rather not do that, I'd hate to have to reinstall after I screw every little thing up, as I have a feeling that would take a lot of reinstalls!  :)

Dont get frustrated in the slightest bit, this should be fairly easy to work out.

Are you typing in

sudo dpkg-reconfigure xserver-xorg 

from your regular desktop or from a pure terminal screen with no GUI?

Go to system -> Administration -> HardwaRE Drivers and enable your driver. If there is an error please post it here

Good luck

---

### Post by PoopyTheJ on 2008-05-01
I don;t have a section for hardware drivers in system-adminiistration, I have restricted drivers but my system tells me I don;t need any restricted drivers, running a radeon 3850HD, 7.10 doesn't really recognize the card and the previous ati drivers I was using sorta recognized it but as an earlier card I think, a 2900, at least it seemed to operate as though my card was that. Also I typed in that command from a pure command prompt, the recovery mode kernel in the grub boot menu

---

### Post by Riffer on 2008-05-01
It would be under "Restricted Driver"

If I were you I would use Envy and un-install all ATI drivers, reboot.. and then try envy again.

---

### Post by PoopyTheJ on 2008-05-01
ok did that, now do I need to uninstall anything else, or do anything to compiz? I'm wondering becuse I saw a tutorial on installing ATI drivers somewhere and it talked about blacklisting fglrx because the 7.10 kernel uses an old fglrx, I'm not sure i understand all that but I wanted to make sure there was nothing else I needed to do

---

### Post by PoopyTheJ on 2008-05-01
After running envy, I'm in 800x600 and it won;t detect my monitor, though it did before. The restricted drivers manager says my system doesn't require any restricted drivers though in system administration synaptics package manager there is a restricted section and my driver is in there. I'm attaching my x11 xorg.conf file section that's relevant below...

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Videoram	524288
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"G225f"
	Option		"DPMS"
	Horizsync	30-75
	Vertrefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"G225f"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1920x1440"	"1792x1344"	"1600x1200"	"1400x1050"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by Riffer on 2008-05-01
No just uninstall the old drivers.

FYI With Envy you have to unistall the old drivers before installing new ones.  I did that with my nVidia card and got pretty much the same results as you.  Also I hope you got the right Envy as it is version specific.

Also the command line that you were given is a good one and can save you but it has to be done in a particular way.  You have to hit Ctl ALT F2 to go to the correct terminal run your command there and when finished hit Ctl ALT F7 to bring up the GUI again.

---

### Post by Riffer on 2008-05-01
Sorry I'm at a lose, you may want to reboot again just to see.

Also I do know that ATi cards are a bit of a bear, I would do a search on this forum for howto to installing the right driver.  I know there is a very good one.  And keep at it I know there is a solution.

---

### Post by PoopyTheJ on 2008-05-01
I just now saw your post re: CTRL + ALT + something to run that command, I didn;t do that the first time should I try it again using those keystrokes?

---

### Post by PoopyTheJ on 2008-05-01
Ok, It's late time for bed for me I'll tackle this again tommorrow night, thanks for the help, worst case scenario I can back up all my data and just reload... Though I'd like to learn how to ix things rather than just blowing them out and reinstalling. If no one grabs here what would you say would be a good way to search for a solution ?

---

### Post by PoopyTheJ on 2008-05-01
Got the drivers reinstalled and my desktop is back, monitor recognized, or at least the resolution is right, BUT, everything is slow as hell! Even typing here my characters don;t show up intil well after I've finished typing. Movies stutter, windows being drawn take forever. What can I do to fix this? Is there some output I should check, or log or something? Some driver setting?

---

### Post by PoopyTheJ on 2008-05-01
ok, I uninstalled xserver-xgl and things seem to be running pretty smoothly now. Video plays back nicely etc. This all started because I wanted to see if my drivers were causing the crash in switching users, which seems to be the general consensus. How do I switch from the proprietary ATI drivers to the Open source fglrx drivers? I'd like to see the difference and see if that fixes my user switch crash. Anyone can help I'd really appreciate it!

---

