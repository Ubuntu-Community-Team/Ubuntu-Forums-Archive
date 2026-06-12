---
title: "Installing Ubuntu 12.04 on (old) Android Phone"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by Frimbleglim on 2013-05-24
I have and HTC Desire phone running the firmware version of android.  It makes very poor use of the 16 GB SD card I have so I want to try running Ubuntu on it instead.  How do I go about installing this OS?

---

### Post by Cheesemill on 2013-05-24
Ubuntu 12.04 isn't available but there is a port of Ubuntu Touch based on 12.10 that you can use with the Desire...
[http://forum.xda-developers.com/showthread.php?t=2165711](http://forum.xda-developers.com/showthread.php?t=2165711)

Be aware that Ubuntu Touch is still in development, so expect frequent breakage.

---

### Post by Frimbleglim on 2013-05-24
Thanks, at the moment I can't even keep the android apps updated due to the phone refusing to install anything to the SD card.  It can make phone calls and text ok it can take pictures but that's about it.  I'll give those instructions a try once I find my micro SD to SD adapter.

---

### Post by Frimbleglim on 2013-05-24
Ok, so I tried to follow the instructions but I can't find the Ubuntu FS file that the instructions mentioned.  Where can I download this?

ED. Got it!

---

### Post by Mark Phelps on 2013-05-24
> **Frimbleglim said:**
> Thanks, at the moment I can't even keep the android apps updated due to the phone refusing to install anything to the SD card.

NOT being able to install or move apps to an external SD card has been prevented in Android ever since ICS came out. So, if your phone is running ICS or JB, it's an Android OS limitation.

As to your question about where to get the FS ... You DID see the comments that this is only for Advanced Users, right? The link to the ZIP file containing what you need is clearly display on the screen.  IF you aren't advanced enough to understand that and extract compressed files in Linux, you should NOT be doing this -- as you will most likely BRICK your phone!

---

### Post by Frimbleglim on 2013-05-24
I copied the files accross at step 8 but there were several errors of the form chown "/FILELOCATION/" failed: Opperation not Permitted is it safe to continue?

@ Mark Phelps, Yes I realise that and that is why I want to try ubuntu touch.  I'm currently running an altered version of 2.3 (Gingerbread)

---

### Post by Frimbleglim on 2013-05-24
OK well I can't delete the android OS from the phone however hard I try so I think I'll have to leave it there.  I managed to follow the rest of the instructions.

---

### Post by Frimbleglim on 2013-05-25
I have finally managed to route my phone and have followed the instructions up to number 13.  The phone is now running Evervolv.  How do I perform step 14 to make it run ubuntu?

---

### Post by josephmills on 2013-05-25
you could make a rootstock script ?
[https://wiki.ubuntu.com/ARM/RootfsFromScratch](https://wiki.ubuntu.com/ARM/RootfsFromScratch)

---

### Post by Frimbleglim on 2013-05-25
I'm not sure I understand what is going on here.  Is the idea to run ubuntu in an emulator on the phone or to actually load ubuntu native using evervolv as a very elaborate bootloader?  

@josephmills I can't really understand that link can you explain what these scripts would do?

---

### Post by josephmills on 2013-05-25
Here is the man page for it 
[http://manpages.ubuntu.com/manpages/karmic/man1/rootstock.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/rootstock.1.html)

 rootstock is a tool to generate a .tgz file or qemu image containing an  armel rootfsIn order to get 12.04 on my nexus 7 it took me 3 days and a lot of hacking and still nothing worked the way that I wanted it to there is also the whole trick of using sed to change /etc/apt/ and then downgrade all the packages (that is what I ened up doing in the end and still did not work out that well for getting ubuntu tv to work on arm)

---

### Post by Frimbleglim on 2013-05-25
> **josephmills said:**
> Here is the man page for it 
In order to get 12.04 on my nexus 7 it took me 3 days and a lot of hacking and still nothing worked the way that I wanted it to there is also the whole trick of using sed to change /etc/apt/ and then downgrade all the packages (that is what I ened up doing in the end and still did not work out that well for getting ubuntu tv to work on arm)
Hmm.  I doubt I stand much of a chance doing this then.  I don't actually understand how to access the Ext 4 section of the disk from android let alone get the device to boot to it.  And that's even if I could understand the file structure to the extent that I could put each file in the right place.  

Thanks anyway.

---

### Post by Frimbleglim on 2013-05-26
I have now run every step of the tutorial without issue and it still boots into evervolv rather than ubuntu.  Having said that I don't see why this should boot into ubuntu.  It's an evervolv zip.  I can access the ubuntu folder from the evervolv terminal is there some script there I can run to boot up into ubuntu?  If not what script do I need to put there?

I found the problem.  I had the wrong evervolv zip.  Now the phone boots into ubuntu.  My thanks to everyone who posted.

---

