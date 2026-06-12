---
title: "Upgraded from 11.10 to 12.04. No longer starts up."
date: 2012-05-05
forum: New to Ubuntu
---

### Post by dxm050 on 2012-05-05
I upgraded from 11.10 to 12.04. My computer no longer loads but jams on start up. I have rebooted a number of times but it always jams and I get the same screen. What do I do? When it jams the black screen indicates:
 
*Starting Clam AV virus database updater freshclam [ok]
 
Starting GNUstep distributed object mapper gdomap.
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 
[COLOR=red]*[/COLOR]modprobe vboxdrv failed. Please use 'dmesg' to find out why
 
Starting Winbind daemon winbind [ok]
 
*Starting bluetooth [ok]
 
[COLOR=orange]*[/COLOR] PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
 
*Checking battery state... [ok]

---

### Post by dxm050 on 2012-05-15
Its hard to believe that no one has ever had my problem before or that no one knows what to do about it. Over a week and 60 views no answers! In the meantime my computer is useless and I have to use my wife's to check my emails and do research on what to do. Did I not have enough memory to upgrade? Or is it a virus? Its frustrating!

---

### Post by HunterDX77M on 2012-05-15
Are you able to do anything at all? What I mean by that is that will it take any sort of input (keystrokes) from you? If you can't put any input at all, I don't know if there is anything that can be done.

Also, do you get to the boot screen (where you choose OS's) or is Ubuntu the only OS on the machine?

---

### Post by steeldriver on 2012-05-15
Does hitting Ctrl-Alt-F1/F2/F3/F4 get you to a virtual terminal? If so it may just be a problem with the X server and/or graphics driver

[http://ubuntuforums.org/showthread.php?t=1859820](http://ubuntuforums.org/showthread.php?t=1859820)

Some details on your computer might help narrow it down - desktop? laptop? make and model? graphics card if you know it

---

### Post by Linux_junkie on 2012-05-16
How did you upgrade? For example, did you hit the upgrade button on update manager or fresh install from a cd/usb?

If you had upgraded from update manager I would suggest downloading the iso and installing a fresh installer.

---

### Post by dxm050 on 2012-05-18
Hi Steeldriver,  hitting Ctrl-Alt-F1/F2/F3/F4 does get me to some kind of a virtual terminal. I didn't know about this before, thanks. It prompts me for a login and then my password. I cannot remember either my login or password so cannot get any further. 

My system is a Dell desktop Precision Workstation 530MT Series with a  1.70 GHz Intel Xeon processor and a 34GB hard drive. Ubuntu is the only OS on my system.   I'm not sure about  my graphics card.  My settings show graphic driver is unknown.  Does that indicate I need to install a new driver? Where do I check to ID my graphic card?

My brother who installed Ubuntu on it originally suggested I created CD disk to boot from and this works. He also suggested I stay away from the latest version as it may not be as stable as the previous one. Since it works from a CD, does this mean my graphics card is  fine?

Before installing either 11.10 or 12.04  I checked to see if I could access my personal files on the hard drive like photos but was not able to find them anywhere. Is there a way to access them before I do anything else? The reason I originally set the update manager to advise me on new versions was to stay current while getting my files imported. If I install from the CD or the web will it not write over everything? Or are my files that I haven't backed up already lost?

---

