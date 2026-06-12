---
title: "Ubuntu 8.10 monitor resolution problems."
date: 2008-11-30
forum: New to Ubuntu
---

### Post by mike-a on 2008-11-30
I have Ubuntu 8.10 installed on a 2.2 Ghz P4 system (Asus P4B533VM motherboard). Video card is an ATI rage Pro128. Monitor Atec 18.1 LCD capable of 1280x1024 at 60 Hz. This is used with analogue input from the video card. All of this is recognized and runs in Win XP just fine. 

Installing 8.10 gives 800x600 resolution which is the highest resolution available in the monitor resolution application . Additionally the monitor gets an out of range signal (46.3KHz & 86 Hz ) after Grub starts up and during shut down. 

xorg.conf includes 

Section “ Monitor” 
	Identifier “Configured Monitor”
EndSection

Modifying this to include
 Horizsync 	31.5 – 80 
Vertrefresh	60 – 75

gave me a full range of resolutions available in the resolution app and the monitor would run at  1280x1024 @ 60Hz but after one or two reboots the system was back to its original condition even though xorg.conf  remained in its modified state. The out of range behavior remained when the resolution was fixed. 

I have also had a go at finding out if the video card is being recognized. I installed the hardware manager app. This sees an ATI Rage 128 Pro Ultra TF but with a grey ? beside it.  Unfortunately the help for the app is limited to a screenshot and an advanced manual section which says this is a complex program so I am only somewhat wiser 

Ubuntu seems tantalizingly good so far except for this. Any help would be much appreciated - I am reasonably experienced with windows systems but a complete newcomer to Ubuntu and the command line stuff.

Mike

---

### Post by jeyaganesh on 2008-12-10
Try, 
'sudo dpkg-reconfigure xserver-xorg' in the terminator.

Then follow the on screen instruction to select 'key board layout' and 'screen resolution'. Choose your resolution there. 

After finishing everything, restart the Xserver by pressing 'Alt+Ctrl+Backspace'. It takes you to log in window.

Or do restart the system after selecting your resolution.:popcorn:

---

