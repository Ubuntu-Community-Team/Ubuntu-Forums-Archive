---
title: "HOWTO: Bluetooth &amp; Bitpim Under Ubuntu Karmic"
date: 2009-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by greyfox1 on 2009-11-09
[COLOR="Red"]**NOTE that this tutorial has changed as of 11/11/09 and connecting to rfcomm0 in raw mode is no longer recommended**[/COLOR]

This guide is based on a similar one posted to Ars Technica ([http://arstechnica.com/open-source/news/2007/12/using-a-bluetooth-phone-with-linux.ars](http://arstechnica.com/open-source/news/2007/12/using-a-bluetooth-phone-with-linux.ars)).

I have found that a couple of things have changed since that guide has written, so I thought it would be worthwhile to post an updated version and share my findings.  Everything in this tutorial is possible under Karmic without installing any packages that aren't installed by default (except for Bitpim, of course).

**Getting Started**

This works for my LG Dare (Firmware version 05) and should work for many/most/all other Verizon LG phones that support the proper Bluetooth profiles -- possibly many more beyond that.

Just to keep things relatively short, we will assume that you have already managed to pair your phone with your computer.

Unless otherwise specified, assume any commands I ask you to issue will be done in Terminal.

**Step 1: Find your phone's MAC address**

The easiest way to do this is to browse the device via Nautilus: from the Bluetooth icon in the Gnome Panel, choose your device and then choose Browse Files. This will open a new Nautilus window and your phone's MAC address will be displayed in the address bar in the format obex://[mac:address:here]/.

**Step 2: Find the channel used by the Bluetooth Serial Port service**

Issue the command: sdptool browse mac:address:here. 

My Dare uses Channel 5 for Serial Port as shown here:

Service Name: Serial Port
Service RecHandle: 0x10006
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 5

Note: Some phones may not show anything labeled "Serial Port". In the case of my old phone (an LG VX9900), for example, I used the BT DIAG service instead and it worked. If you don't have a Serial Port section, you may have to try another service instead (but no guarantees it works).

**Step 3: Create an RFCOMM binding by editing the appropriate config file**

Open the config file by running: gksudo gedit /etc/bluetooth/rfcomm.conf

Uncomment the rfcomm0 section (remove the # from each line) and change it to look like this:

rfcomm0 {
	# Automatically bind the device at startup
	bind yes;

	# Bluetooth address of the device
	device mac:address:here; 
	# RFCOMM channel for the connection
	channel 5;

	# Description of the connection
	comment "Needed by BitPim";
}

**Step 4: Make sure your bluetooth bindings are added at startup**

Due to a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/416056") in 9.10, the rfcomm bindings that we specified above (in rfcomm.conf) will probably be ignored at startup. Reply #5 in the LP bug report provides a workaround for this issue. The instructions there are written for users who have upgraded to 9.10-- on my fresh 9.10 installation however, I needed only to follow step 3, which I will repeat here.

Open rc.local (gksudo gedit /etc/rc.local) and add the line: 

rfcomm bind yes

Above the last line (which should say exit 0). 

**Step 5: Restart the Bluetooth service**

Issue the commands:

sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/bluetooth start

Note: running sudo /etc/init.d/bluetooth restart did not work for me: this caused the BT service to stop, but it wouldn't start again on its own. This appears to be another bug in 9.10. 

**Step 6: Start Bitpim and check available com ports**

Start Bitpim and go into Settings, then click the Browse... button to the right of "Com Port". You should see "Bluetooth (/dev/rfcomm0) listed under Available Ports. If you do, you are all set! You can now start reading/writing your phone data using Bitpim. If not, you may have done something wrong. Double check your work above and try again before continuing.

**Step 7: Have fun hacking away at your phone!**

If you have any questions or run into problems, please be as specific as possible when asking for help. 

Thanks to:

[Ars Technica]("http://arstechnica.com/open-source/news/2007/12/using-a-bluetooth-phone-with-linux.ars") for the original tutorial
[tony]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/416056/comments/5") for the tip about editing rc.local.

---

### Post by ionFreeman on 2010-01-09
Thanks, Greyfox1. I still have to
:~$ rfcomm connect 0 00:1A:72:DF:1E:A2 16 &

before BitPim will connect.

---

### Post by realgt on 2010-03-04
> **ionFreeman said:**
> Thanks, Greyfox1. I still have to
:~$ rfcomm connect 0 00:1A:72:DF:1E:A2 16 &

before BitPim will connect.


same here, but at least it works.

thx!

---

### Post by Redundant Username on 2010-03-29
Bitpim says the device is busy. :(

---

### Post by Redundant Username on 2010-03-30
Nevermind, fixed. I didn't edit my post because Chromium crashes when I try that

---

### Post by greyfox1 on 2010-04-04
Do you mind sharing your fix for the "Device Busy" error in case others run into it?

---

