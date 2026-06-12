---
title: "HOWTO: AllTel, Motorola MotoRAZR V3a, EVDO Internet Access, and Ubuntu / Kubuntu"
date: 2007-09-21
forum: Outdated Tutorials &amp; Tips
---

### Post by SilentDissonance on 2007-09-21
It was a long journey for me to get this much to work, so I hope to save some people some time.  I intend to give a brief overview of how to setup EVDO Internet access in Linux for this phone, and the steps I took to achieve it.

First, contrary to popular belief, this is a very competent little phone.  It serves my needs quite well, as my needs are few.  I wanted good sound quality (Motorola has always provided this, even in my old T720 that I had for years), good battery life (this phone stays powered easily after 24 hrs and a few calls, and charges off USB when connected), bluetooth (for my headset, easier to use when in the car), and EVDO 'net access.  The final bit there, proved a bit difficult, as I run Linux, specifically Kubuntu 7.04.

I spent a good 5 hours the night I got home getting this functioning.  It should not take this long, and by writing this, I hope no one else takes this long either.

This should work for just about any phone out there not being recognized by the kernel, at least for Internet access.

Step 1 - Get the phone recognized.
This is, by far, the hardest part, and what caused most of my problems.  The V3a is unique enough that the kernel build in Kubuntu 7.04 didn't recognize it, and give it a port immediately.  I felt my way along many a blind alley trying to get cdc-acm to work, and finally found a solution in usbserial (info for that gleaned from [http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)).

When you plug the cellphone into the computer, cdc-acm is supposed to automatically assign it a /dev point to bind to.  With the V3a being so new, the kernel can't figure it out, and you end up with the following in dmesg:

```
~$ dmesg | tail
[23574.428000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[23574.644000] usb 2-1: configuration #1 chosen from 1 choice
```

Notice, no info on a port assignment or the like, it notes that there's only one choice available to the kernel, and that's basically that it's there, and nothing more.  A useless brick, if you will, connected via USB.

cdc-acm is supposed to kick in here and assign it a point.  As I said, that doesn't happen with the V3a.  So, we have to determine the info from the phone that we can, and use usbserial instead.

We'll need to compare device listing outputs to do this, so for now, disconnect your phone.
```
~$ cat /proc/bus/usb/devices > devices
```

This will create a file ~/devices, basially a listing of all devices currently connected to your machine.  A snapshot, if you will, of the current stuff attached to your computer.

Now, connect your phone.  Give it a few moments, the phone should beep a few times.  We can now compare what's currently connected to what was connected, and find the info from the phone itself.
```
~$ diff /proc/bus/usb/devices devices | grep Vendor
```

What that command does is looks at the current device list (/proc/bus/usb/devices) and compares it (using the diff command) to what you had when you didn't have the phone connected.  Finally, we filter it through grep (a search engine of sorts) for just what we want, the vendor info.  You should get a single line detailing the vendor and product ID.
```
~$ diff /proc/bus/usb/devices devices | grep Vendor
< P:  Vendor=22b8 ProdID=2ac4 Rev= 0.01
```

Now, we have the vendor and product info for the phone.

Next, we need to load the usbserial module in, with that specific information associated with it.

```
~$ sudo modprobe usbserial vendor=0x22b8 product=0x2ac4
```

That loads usbserial in, and gives it a vendor and product to work with.  If you do this while the phone is still connected, it should beep at you.

Finally, disconnect the phone, and reconnect it.  After a few seconds (and a few beeps from the phone), check the message log again.

```
~$ dmesg | tail
[24439.348000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[24439.564000] usb 2-1: configuration #1 chosen from 1 choice
[24439.564000] usbserial_generic 2-1:1.0: generic converter detected
[24439.564000] usb 2-1: generic converter now attached to ttyUSB0
[24439.568000] usbserial_generic 2-1:1.1: generic converter detected
[24439.568000] usb 2-1: generic converter now attached to ttyUSB1
```

As you can see, we've now got it assigned to a port we can work with, in this case, /dev/ttyUSB0.

Step 2 - setting up a ppp dialer
Everyone will have their favorite method of doing this, what with the multitude of ppp dialers out there.  Everything from fancy GUIs to collections of shell scripts.  Personally, I use KDE, and like the KPPP dialer.  It manages everything rather well for me.

The basics:
Username - your 10-digit phone [email]number@alltel.net[/email]
Password - alltel
Number   - #777
Device   - /dev/ttyUSB0

That should be what you'd need for most any dialer out there.  The rest that follows is specific to KPPP.

Launch KPPP, click Configure.

On the Accounts tab, click New.  In the warning, click Manual Configuration.  For configuration name, put in anything you want (I put AllTel).  Click Add, and enter #777 for the phone number. Click OK twice, and you'll be back on the KPPP Configurations dialog.

On the Modems tab, click New.  For modem name, enter anything (I put V3a), for device, choose /dev/ttyUSB0.  Click OK.

OK out of the KPPP Configuration dialog.

Enter your username (remember, your 10-digit phone [email]number@alltel.net[/email]), and the password (alltel).

You should be all set now, you can choose to "show log window" if you want, to see the progress, but otherwise, click connect and go!

There's 2 problems with this setup, you'll need to modprobe that same device every time you want to use your EVDO 'net access, but the Prod/vendor info never change.  Easily done in a shell script or during boottime, up to you.  The other issue is if you disconnect, then want to reconnect right away, it appears the phone doesn't really 'let go' properly, and must be unplugged and reconnected to make that 2nd ppp connection.  Again, you don't have to go through the finding/modprobe step again, just pull the cable and reconnect it.

On a side note, I have yet to find any info on getting this phone setup and working with bitpim, kmobiletools, moto4lin, etc., so I still have no way to add ringtones, wallpaper, etc. to my phone yet.  If anyone has any info on that, please, let me know!

---

### Post by price903 on 2008-01-26
FYI

I'm running ubuntu 7.04 and have tried and tried to connect to my motorola v3a to transfer pictures and videos.  I tried bitpim, moto4lin, kmobiletools, etc, with no luck.  

Today I finally had success.  I have a usb bluetooth adapter for my pc.  I installed gnome-bluetooth from synaptic package manager and it works.  I can transfer pictures, videos, and even make my own ringtones.

---

### Post by svfd7200 on 2008-02-24
I tried this and it did not work on alltel utstarcom um150. Any idea's on what I might try. Using Ubuntu 7.10, the utsrtarcom is usb.

---

### Post by coyotepod on 2008-02-26
I would like to use UTStarcom UM150 with 7.10 Ubuntu, any one get it to work yet? I haven't actually purchased the UTStarcom UM150, maybe I should just consider a different alltel phones. Recommendations?  Thanks

---

### Post by lsearcey on 2008-05-07
how do I run the kppp dialer?  I don't have internet so I can't download a patch.  Thats why i need ubuntu to read my phone.  I'm using 7.10 ubuntu my phone is motorola E815 with Alltel.

Thanks

---

### Post by stptrx on 2008-10-28
Hey guys, you have to try and specify where a thing fails and any error messages etc. It is difficult to troubleshoot "It doesn't work." I know that I am attempting to get a phone working on UBUNTU hardy (ultimate gamers edition) We fell into a snag where: cat /proc/bus/usb/devices > devices returned  No file or Directory. The following is from a post 
( [http://ubuntuforums.org/showthread.php?t=739701&highlight=cat+%2Fproc%2Fbus%2Fusb%2Fdevices%3A+No+such+file+OR+directory](http://ubuntuforums.org/showthread.php?t=739701&highlight=cat+%2Fproc%2Fbus%2Fusb%2Fdevices%3A+No+such+file+OR+directory) ) regarding external harddrives and virtualbox actually, but it addresses this issue directly. 

"Code:
gksudo gedit /etc/init.d/mountdevsubfs.sh

Once you’ve got that open in Gedit, type CTRL-F to search for a string. Search for ‘magic’ (sans quotes).

That should bring you to this:

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount –rbind /dev/bus/usb /proc/bus/usb

All those pound signs are comments. Remove them from the last four lines so you end up with this:

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount –rbind /dev/bus/usb /proc/bus/usb

Save the file and exit Gedit. Round one goes to the user!"

There are further instructions on making a usb group and such. I have yet to get her phone to connect. I will get the make of it and any other pertinent details and post the results of any further steps that seem relevant to this thread as it seems the closest yet to a solution. (cause seriously have fun getting information like APN from alltel. they need support for there tech support. Those guys seem not to have the documentation required to assist with any actual technical question. To there credit there moderator, or whomeber was assisting the tech I spoke to had evidently done a google search and came up with some information regarding a file I was editing. unfortunately they read me the line that I was attempting to edit with the APN information but could not give me the APN)  Good Luck!

---

### Post by jpeery on 2008-10-30
So how did you create the ringtone and get it on the phone?

---

