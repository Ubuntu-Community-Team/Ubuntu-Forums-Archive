---
title: "Fresh install of 12.10 on a hp t2 went wrong."
date: 2012-12-07
forum: New to Ubuntu
---

### Post by newcityboy on 2012-12-07
Just did an install on my hp tablet and now it cannot get past the BIOS screen. The one where you have to hit a button to get into BIOS and if you leave it alone it will load the OS. Well mine now gets stuck there. I cannot get into the bios and I can get past that screen. I think it may have had something to do with the loss of the HP_TOOLS partition. Which I am finding out was actually an extension to the BIOS. Any suggestions to get it back up and running. I can't figure out what to do to get past the initial screen.

---

### Post by verzx on 2012-12-07
You should press escape on start up and a screen will open asking to go to BIOS and more options. If that works put in the disc you got with your laptop and restore or try start up repair.

If it doesn't work then I have no idea.

---

### Post by newcityboy on 2012-12-07
Doesn't work. Tried that initially. And no luck.

---

### Post by Favux on 2012-12-07
I won't swear to it but I don't think HP_TOOLS is needed for the boot.

Can you boot on a Ubuntu live CD or usb stick?  I'm wondering if you didn't damage the mbr so it can't access your hard drive and that's why it can't get past the BIOS screen.

But that doesn't explain why you can't get into BIOS options.  Again that shouldn't depend on whether the hard drive is accessible or not.  You might want to try turning it off and pulling the battery and letting it sit an hour or two.  If some residual is affecting the keyboard that might clear it.  And you are using the right key or key combination?

---

### Post by Bartender on 2012-12-08
I goggled - whoops, googled - "is HP_TOOLS needed".

[http://h30434.www3.hp.com/t5/Notebook-Hardware-e-g-Windows-8/Hp-Tools-Partion/td-p/228360]("http://h30434.www3.hp.com/t5/Notebook-Hardware-e-g-Windows-8/Hp-Tools-Partion/td-p/228360")

[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/Delete-HP-Tools-Partition/td-p/479927]("http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/Delete-HP-Tools-Partition/td-p/479927")

[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g/What-do-these-partitions-do-HP-Tools-Recovery-Boot/td-p/180944]("http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g/What-do-these-partitions-do-HP-Tools-Recovery-Boot/td-p/180944")

[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g/What-is-inside-the-quot-HP-Tools-quot-partition/td-p/216428]("http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g/What-is-inside-the-quot-HP-Tools-quot-partition/td-p/216428")

Doesn't look like it.  Interesting to note that nobody seems to be absolutely sure what's in the partition, even HP employees on their own support forums.

To the OP: what speed did you burn your Ubuntu install CD at?  To me, it sounds like a bad disc.  Just a hunch, and it might be a total waste of your time.  But if you let the disc burn utility burn the disc at full crank the first time, you might want to do it again at 4X or so and start all over again.

EDIT: I agree with others; you should be able to get into BIOS even if all data is wiped off drive.  Heck, you should be able to get into BIOS with no HDD at all.  BIOS runs off a small EPROM chip on the motherboard.

---

### Post by newcityboy on 2012-12-08
I loaded it from a USB stick. And I did a live boot with the stick, and installed from there. When I did the reboot to get into the fresh install this happened. I feel the same that I should be able to get into the bios but is simply isn't happening.

---

### Post by Bartender on 2012-12-08
I can't find an HP T2 on the google.  Found an [HP TX2]("http://www.amazon.com/HP-TX2-1020US-TouchSmart-12-1-Inch-Dual-Core/dp/B001LF35VY").

Can you provide a link to your exact model?

Also, part of your original post is confusing...

*"The one where you have to hit a button to get into BIOS and if you leave it alone it will load the OS."*

Typically, there's a keystroke that stops the boot and puts you into BIOS.

And there's almost always another keystroke that stops the boot, then takes you to a screen that lists the devices that the computer recognizes as bootable - typically the list will include HDD's, optical drives, USB, and network.

Neither one of those keys continues to the OS if you leave it alone, so I don't know what you're referring to.

The fact that you installed it from a thumb drive has me wondering if it needs the thumb drive in place to work.  Have you tried that?  I think I remember reading a few threads in the past where people installed from a thumb drive, then Ubuntu wouldn't work unless the thumb drive was in place.  I could be completely off-base with that, but it's worth trying if you haven't already...

---

### Post by newcityboy on 2012-12-08
Touchsmart tm2-1000
The more technical designation tm2t-1000
here is the link to the driver support page.
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=4121373]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=4121373")

This is the link that I found describing how to extract the .bin file for the bios I cannot get it to work the way he described it though. The files that are extracted do not even closely resemble what he is showing.
[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g/How-to-flash-BIOS-without-having-HP-Tools-Partition/td-p/533561]("http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g/How-to-flash-BIOS-without-having-HP-Tools-Partition/td-p/533561")



An I tried to boot with the USB in place. 


I tried pretty much every single combination of key strokes during boot up. And where it hangs is that initial screen that tells you to press esc for setup. Normaly only visible for a second or so.

---

### Post by oldfred on 2012-12-08
Your manual says this:

> To start Setup Utility:
&#9650;
Open Setup Utility by turning on or restarting the computer. While the “Press the ESC key for
Startup Menu” message is displayed in the lower-left corner of the screen, press f10.
– or –
1. 2. 
ENWW
Open Setup Utility by turning on or restarting the computer. While the “Press the ESC key for
 Startup Menu” message is displayed in the lower-left corner of the screen, press esc.
When the Startup Menu is displayed, press f10.


---

### Post by newcityboy on 2012-12-08
Just tried all that again. it just beeps at me and remains on the "Press The ESC Key for Startup Menue"

---

### Post by newcityboy on 2012-12-09
Been doing some more research and I came across an article that mentioned something that I failed to mention here. My caps lock light blinks while it sits hung up. This apparently is an indicator light informing the user of bad news. Mine blinks five times which is termed as a "General System Board Failure" Which sounds terrifying.... But it could also be caused by a BIOS Corruption, which I have suspected most of the time. Some industrious person did extensive digging and found that the computer can read the five blinks of doom due to one of these: 

A) BIOS - 	BIOS corruption failure (Oh please let that be the problem)
B) BIOS -	BIOS authentication failure (Not really sure of the difference there)
C) Graphics - 	Graphics controller not functional (Not Likely)
D) Memory - 	Module error not functional (Bother)
E) CPU - 	CPU not functional (Bugger...)
F) Mother Board - Mother Board not functional (As my Filipino friend would say.... Puck...)

I'm running with the possibility that it is the BIOS for the moment

When Windows 7 is installed and the HP_TOOLS is present it will automatically , flash the BIOS, and restart the computer with the fresh and new BIOS. Problem is I cannot figure out how to manually flash the BIOS with an uncorrupted set.  The instructions are there, but whenever i download my computers BIOS, and I do as instructed I don't end up with what I am supposed to end up with. What I have found says to do is this.

Using 7-ZIP Extract the .BIN file from SP51577.exe (Which is my most up to date BIOS)
Place this .BIN file into a USB Thumb Drive named HP_TOOLS. And Restart. 

My problem is I cannot locate the .bin file within the sp51577.exe nor in any of the other versions of BIOS for my computer. 

I think what I need is a way to manually reinstall BIOS. I have read how its done but I cannot find the files that I will need to place within the USB Drive. Any suggestions?

---

