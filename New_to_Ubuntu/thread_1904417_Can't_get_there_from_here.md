---
title: "Can't get there from here"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by flyfishingphil on 2012-01-04
Hoped the title might create a little interest and help.

Have a Toshiba laptop (info at bottom) and just purchased a Toshiba Thrive with android version 3.1. Plug USB into both and the laptop doesn't show connection to anything via USB.

Does anybody know what might need to be done to connect the 2 together using USB? (Keep steps simple. You're dealing with a 40 watt bulb in a 5 watt outlet.)

Have looked at the Thrive forum but not many are familiar with Linux from what I have found so far.

Thanks for any assist.

---

### Post by lindsay7 on 2012-01-04
look under settings on your tablet.  look something that says connect to pc. You have to tell the tablet to act like a disk drive or it thinks it is charging. also look for the application setting and developement, there is a setting called usb debugging. it may need to be checked.

---

### Post by flyfishingphil on 2012-01-04
Found and checked the USB debugging but nothing about connecting to PC. Plugged it in and a little box that says "usb debugging connected" appeared at bottom of tablet screen but nothing on the laptop. Not charging either. I'll keep looking for the "hidden" trick. Thanks for the try.

---

### Post by Henkdroid on 2012-01-04
Plug the tablet in and look for a USB symbol at the bottom of the screen. Tap the icon and it should bring something up about connecting to your computer.

---

### Post by flyfishingphil on 2012-01-04
All that shows on the tablet is the usb debugging icon. No USB icon on either the tablet or the laptop.

Had one suggestions on tablet forum regarding Udev. Checked in Synaptic and have UDEV showing 167-ubuntu3, system-config-printer and libudev0 showing. Something missing or need something else?

---

### Post by anewguy on 2012-01-04
Turn the debugging off.

Then retry what Henkdroid just posted again.  On most Android devices it is the same - the symbol comes up, you tap it and select use as disk drive.

---

### Post by flyfishingphil on 2012-01-04
> **anewguy said:**
> Turn the debugging off.

Then retry what Henkdroid just posted again.  On most Android devices it is the same - the symbol comes up, you tap it and select use as disk drive.

Turned the debugging off. It now shows it charging but no USB icon on either screen. 

If nobody else can find a quirky problem let me try it. I'm the one they wait for.

---

### Post by anewguy on 2012-01-05
> **flyfishingphil said:**
> Turned the debugging off. It now shows it charging but no USB icon on either screen. 

If nobody else can find a quirky problem let me try it. I'm the one they wait for.

;)  I'm the same way on a lot of stuff.  I call it excessive coordination, but my friends have other less-friendly names for it!

If you tap on the USB charging symbol what happens?

Dave ;)

---

### Post by flyfishingphil on 2012-01-05
Forgot to edit the last one. 

Had it plugged in when I noticed the charging light. Unplugged the charger and light went off. No connection between the 2 so still unable to connect. 

Think I'll take a break and go fishing for a few. Maybe that will clear my head enough to think straight.

---

### Post by flyfishingphil on 2012-01-09
A new problem. Received a suggestion on the Thrive forum regarding connecting the Thrive tablet to the laptop via usb. Followed instructions step by step, double checked entries, finished process and still cannot get the tablet to connect via usb. Second problem that developed is I can no longer access the SDHC card, to transfer anything on to it, when it is plugged in to the laptop slot. 

Here is the link to the instructions: [http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html]("http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html")

When I mount the SDHC card I can open what's on it but can't add anything. When I try to put anything on the card I get:
*There was an error copying the file into /media/usb0*. Under Details it shows: 
*Error opening file '/media/usb0/Tips&Tricks written.doc': Permission denied*

When I try to unmount the card I get this:
*umount: /media/usb0 is not in the fstab (and you are not root)* and I have to pull it out and restart  to get the icon off the desktop.

EDIT: Just tried the flash drive and have the same problems there. The only difference is it disappears from the desktop when I unplug it. Also noticed that if I shut down and restart, with the card plugged in on restart, it shows up on desktop as "Thrive card" and is workable and will unmount. Is there a "sudo chown" I need to do here to get it to work correctly again?

Any suggestions?

---

### Post by mcduck on 2012-01-10
> **flyfishingphil said:**
> Hoped the title might create a little interest and help.

Have a Toshiba laptop (info at bottom) and just purchased a Toshiba Thrive with android version 3.1. Plug USB into both and the laptop doesn't show connection to anything via USB.

Does anybody know what might need to be done to connect the 2 together using USB? (Keep steps simple. You're dealing with a 40 watt bulb in a 5 watt outlet.)

Have looked at the Thrive forum but not many are familiar with Linux from what I have found so far.

Thanks for any assist.
Since the device is running Honeycomb, it doesn't function as a removable disc drive but uses MTP instead to transfer files (which allows the devices filesystem to be accessible to the device itself during the transfer, unlike what you'd get with older Android versions).

So, the solution should be simple; connect the device with the USB cable, and then use any MTP-capable application to transfer the files. gMTP has worked fine with my Asus Transformer.

---

### Post by flyfishingphil on 2012-01-10
Thanks mcduck, got it and it appears to connect. Have to spend some time playing around and see what I can do.

Still having problems though with the sdhc card and the verbatim stick. Can't work with either. Trying to figure out how to reset to where it was before I went thru the setup recommended earlier. Card and stick worked before doing that.

---

### Post by mcduck on 2012-01-10
Simply reversing the changes you made based on those instructions should solve any problems they might have caused.

That guide looks interesting, though. It doesn't mention anything about 11.10, but getting mtpfs to work would of course be better than having to use a separate application. I suppose I'll have to give it a try some day... ;)

Edit: You might also be interested in this one: [http://www.omgubuntu.co.uk/2011/12/how-to-easily-mount-the-galaxy-nexus-on-ubuntu-11-10-via-unity/]("http://www.omgubuntu.co.uk/2011/12/how-to-easily-mount-the-galaxy-nexus-on-ubuntu-11-10-via-unity/") (The guide is about Galaxy Nexus and Ice Cream Sandwich-devices, but I would assume that's only because the writer never owned a Honeycomb device since it was never used for phones... However HC works just like ICS does when it comes to accessing the device through USB, so the guide should work for HC devices as well)

---

### Post by flyfishingphil on 2012-01-10
Tried everything I could but still could not get it to recognize a smart card or the flashstick so I gave up and did a full update change. Did a full installation on 11.10 so here I am, trying to get everything up and operational, and trying to remember what I forgot to write down that I had on my Firefox toolbar for locations.

Now I need to look around and see if I can find info on how to get rid of the sidebar and go back to the classic style in 11.10.

Didn't solve the problems but need to mark it as such since I am now working on 11.10 instaed of 11.04.

---

