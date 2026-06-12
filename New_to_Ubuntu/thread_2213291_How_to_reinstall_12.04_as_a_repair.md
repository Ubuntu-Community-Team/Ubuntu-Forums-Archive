---
title: "How to reinstall 12.04 as a repair?"
date: 2014-03-25
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-03-25
I just installed 12.04 on my kids' laptop and then while trying to get the wireless setup done I accidentally clicked the "turn off LAN" button and then the Network icon vanished. After an hour of trying to get it back, I would now like to admit defeat and simply reinstall the 12.04 ISO.  Is there a way to do this?  I installed it from XP by booting from USB.  XP is history, so is it possible to boot from USB in 12.04?

And this is all because I got a message that the new driver (from get new drivers) would not work.  

Pleeeeease?

---

### Post by PondPuppy on 2014-03-25
It seems to me that if you booted to a thumb drive -- ie, just plugged the drive into the cold machine and then powered up -- then you should be able to do the same thing regardless of whether Ubuntu or XP is installed. You should -- "should" -- be able to boot any laptop old enough to have XP as the first OS from either USB or from a CD/DVD, I would think. 

Your post says "installed it from XP by booting from USB" though, and that makes me uncertain about how you originally installed.

On the repair subject, have you tried opening Dash (click the super ("windows") key) and then typing "network" in the search box, to find the available utilities? (I'll bet you have, pardon if that's the case.)

---

### Post by riverguy99 on 2014-03-25
<p>
	I orignally installed 12.04 on a laptop that was running XP. I installed with a downloaded 12.04 on a USB drive and did it by changing the XP boot order to boot from the USB drive. Easy to do in Windoze!</p>
<p>
	I chose the option of replacing XP with 12.04.</p>
<p>
	Booting an Ubuntu computer frome the USB port? Not unless you can somehow tell it to do that, otherwise it simply ignores whatever is in the USB port and does its usual bootup into Ubuntu.</p>
<p>
	I have tried opening the network utilites available as you suggested and nada. There seem to be no options to do much of anything. The utility that appeared at the top right of the screen at least allowed the ethernet connection to work, but since I accidentally hit the &quot;disonnect wired&quot; button in that menu, the icon vanished so I cannot go back in and click on &quot;connect wired.&quot;</p>
<p>
	Right now, I&#39;d settle for that to work. But eventually, I will need this thing to work wireless, as it is my kids&#39; computer and they are going nuts while it is out to lunch. If I could only get the wired to work, I could start trying to find a driver that would work with the wireless card.</p>
<p>
	That&#39;s how this all started! Thanks for your help. Got any more ideas?</p>

---

### Post by Mark Phelps on 2014-03-25
never mind ... you were typing as I was responding ... and have answered the question I was going to ask.

---

### Post by mansonfan78 on 2014-03-25
Your laptop's boot order isn't controlled by the operating system, it's controlled by the bios setup program in the motherboard.  When you turn on the computer is there a message on the screen that says something like "to enter setup press..." or "press .... to interrupt normal startup"?  It's usually either f10, the delete key, or a special button ("thinkvantage" on my Thinkpad).  Once you're into that program it should have a menu or submenu for boot order.

---

### Post by mastablasta on 2014-03-26
wow reisntalling the OS because you turned off networking? i turn it off and on all the time. ok i use kubuntu.
Are you saying wired network is also not working now?
did you check network settings to reenable the network? i am not sure where this is in ubuntu but there should be some system setting and within that option to configure your netwrok-.

i would first make sure that wireless network is on on computer.

have a look here for some tips : [http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/)


similar issue here: [http://ubuntuforums.org/showthread.php?t=1907529](http://ubuntuforums.org/showthread.php?t=1907529)
But you can see if there is actualkly any connection and only the applet is off by pinging from terminal command is same as in windows for exmaple: 
ping google.com

---

### Post by 3rdalbum on 2014-03-26
Log out, delete the hidden folders in your home directory, then log in again. Pretty sure that will reset your Network Manager preferences.

---

### Post by mörgæs on 2014-03-26
If you are going to reinstall (not saying it's necessary for solving the network problem) you could use the occasion and install something lighter than Ubuntu. If the computer is from the XP era then Ubuntu might be too heavy.

---

### Post by PondPuppy on 2014-03-26
If you wish to re-install, then I think mansonfan78 answered your question. To expand on that answer just a little, if you Google your laptop model and the key for getting into the BIOS -- ie, Google something like "Dell latitude C600 key to enter BIOS" -- then you should be able to find out how to get into your basic boot setup menu. Once there, look for an entry called "boot order" and make sure "boot from USB" is before "boot from hdd".

However, the fact that it booted from a USB for the first install but will not do it again is kinda puzzling. Installing Ubuntu shouldn't change the boot order in the BIOS, so -- in the words of Joseph Heller -- "something happened."

And on that note, an option might be to make a bootable Ubuntu CD (it's easy) and try installing from that. Again, you may have to go into the BIOS setup and make sure that "boot from CD" comes before "boot from hdd" in your boot order.

---

### Post by riverguy99 on 2014-03-26
> **3rdalbum said:**
> Log out, delete the hidden folders in your home directory, then log in again. Pretty sure that will reset your Network Manager preferences.

I would love to try something as simple as that.  So how does one find "hidden folders?"  I see nothing like that in my home directory.

---

### Post by riverguy99 on 2014-03-26
All I really want to do is to get the network back operational as it was before I accidentally hit the "disconnect wired network" button in the drop-down menu upper right of screen. The instant I did that, the network icon vanished from the screen.  
 On boot, I get a message that I need to download the firmware and driver for the network card which I could do if I could get the wired network back into operation.  I'm hoping that there is a Terminal entry that would get the network icon back on my screen.

---

### Post by riverguy99 on 2014-03-26
The laptop is a well-configured Dell XPS Studio and can handle Ubuntu with ease.  I have another one with dual-boot with XP and it has been working great.  I just want to get this network thing working again!!!  :(

---

### Post by riverguy99 on 2014-03-26
It's easy to change the boot order on a Windoze machine.  The issue here is that I installed 12.04 onto a Windoze machine by booting from a usb Ubuntu ISO and installing Ubuntu as the sole OS, thus removing every trace of XP from the machine.  So now there is no longer any way (that I can find) of changing the boot order on boot-up.  Can this be done in 12.04?

---

### Post by 3rdalbum on 2014-03-26
Press Control-H to view hidden folders. They are the ones with a period at the start of the name, and they hold preferences for your user account. Obviously you wouldn't need to delete ".libreoffice" or ".pulseaudio" as they are clearly not associated with networking, and if you can find which hidden folder contains only the Network Manager settings that's all you would need to delete.

Edit: Or create a new user account, it will not have the first user's settings.

---

### Post by 3rdalbum on 2014-03-26
> **riverguy99 said:**
> It's easy to change the boot order on a Windoze machine.  The issue here is that I installed 12.04 onto a Windoze machine by booting from a usb Ubuntu ISO and installing Ubuntu as the sole OS, thus removing every trace of XP from the machine.  So now there is no longer any way (that I can find) of changing the boot order on boot-up.  Can this be done in 12.04?

The boot order is governed by the computer's BIOS, not by any operating system. Otherwise how would you install an operating system in the first place?

---

### Post by stalkingwolf on 2014-03-26
F2 should get you into bios set up  you should be able to change your boot order there.  there should also be 2 keys shown on the dell screen ( doesnt always come up on reboot) one to enter set up and one for a boot menu usually f8 f10 or f12.

DEL ESC and f1 are also possibles for getting into set up.

---

### Post by PartisanEntity on 2014-03-26
[I]Please create 1 thread per topic to avoid confusion.

I am closing this thread as another thread by the same author addresses the same issue. I have closed the older of the two threads.[/I]

---

