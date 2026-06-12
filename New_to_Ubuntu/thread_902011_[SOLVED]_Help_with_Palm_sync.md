---
title: "[SOLVED] Help with Palm sync"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by GrnFrag on 2008-08-26
Hi all, i'm not able to sync my palm, and i'm trying to troubleshoot.   I was wondering if anyone could tell me where in the logs I would find any information regarding my pilot connecting?   I can't get gpilot to connect at all, but lsusb shows my palm.   so i'm wondering if theres something i'm missing in logs.    

Also i was wondering how much space Ubuntu allocates to logs, and should i worry about them...

---

### Post by meanburrito920 on 2008-08-27
Dont worry about the logfiles taking up to much space, The old ones get trashed after a while (unless you specifically set it not to). 

As for finding any info regarding your palm in the logs, I don't think that the system logs will be very useful unless you already speak in their esoteric language. I would suggest a google search regarding the model of your palm and Ubuntu and/or linux.

---

### Post by GrnFrag on 2008-08-27
I've searched.   Been trying to get this going for 2 days :(   Found a few other posts about m130's and Ubuntu.   seems like no go, no info really.   So i'm digging into some older debian instructions, see if i can't override Ubuntu's stock sync method



Nothing mechanical wins!

---

### Post by patrickballeux on 2008-08-27
I had a m130 a while ago and it was working fine.  Are you using Jpilot or the gnome-pilot applet?

When setting your connection for the craddle, try setting the speed at 9600 bps, then raise the speed.  I think it was working at 9600 or 57600.  Setting the highest speed nerver worked for me.


One was to make sure that your m130 is detected is to call "dmesg" in a console, just after starting a sync.

You should have a device call /dev/pilot during the sync operation.

If it is not working with /dev/pilot, look for /dev/ttyUSB1 (or /dev/ttyUSB0)...  Try connecting to those.

But from my memory, setting /dev/pilot, 57600 bps and starting the sync on the Palm first then on the PC was working like a charm.

Good luck!

---

### Post by GrnFrag on 2008-08-27
I'm using gnome-pilot, pretty much default settings.   I have tried alot of things, and tracked and reversed all changes.   Currently dmesg says
[HTML][  296.264805] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  296.437492] usb 1-1: configuration #1 chosen from 1 choice
[/HTML]when i press Hotsync.   When it times out, i get
[HTML] 296.264805] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  296.437492] usb 1-1: configuration #1 chosen from 1 choice
[  368.825210] usb 1-1: USB disconnect, address 2
[/HTML]
obviously there is alot of other stuff in there.   There are a couple of additional lines about USB,
[HTML][   24.385506] usbcore: registered new interface driver usbfs
[   24.385558] usbcore: registered new interface driver hub

[   24.478836] USB Universal Host Controller Interface driver v3.0
[   24.479015] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 17
[   24.479036] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.479043] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   24.479592] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   24.479637] uhci_hcd 0000:00:1f.2: irq 17, io base 0x00002440
[   24.479921] usb usb1: configuration #1 chosen from 1 choice
[   24.479965] hub 1-0:1.0: USB hub found
[   24.479977] hub 1-0:1.0: 2 ports detected


[   24.581041] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   24.581080] uhci_hcd 0000:00:1f.4: irq 18, io base 0x00002460
[   24.581312] usb usb2: configuration #1 chosen from 1 choice
[   24.581354] hub 2-0:1.0: USB hub found
[   24.581366] hub 2-0:1.0: 2 ports detected

[/HTML]
these are onboard USB v1, there are 2 pairs of ports.  I'm starting to wonder if that's not the issue.   I notice that when i Hotsync, usb opens 2 devices, one right after the other.   the first always disconnects right away, then the second connects.    

Thanks again to all in the thread.  every idea helps!!!

---

### Post by GrnFrag on 2008-08-27
Bump, still not resolved.   Please help
additional information.  

When i follow the instructions from this doc

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

then try and sync, in /var/log/messages i get the following error when i tell gnome pilot to connect for the first time
 kernel: [  439.434103] visor: probe of 1-1:1.0 failed with error -5

---

### Post by patrickballeux on 2008-08-27
There is always 2 usb device when connecting with the m130.  That is a normal behavior.

Normaly, /dev/pilot is a symlink on /dev/ttyUSB1.  I do not know that the error is, but something is failing for sure.

Can you do some testing with JPilot package to validate the connection.

>sudo apt-get isntall jpilot.

Remove the gnome-palm-applet to avoid conflict with JPilot.

Set your connection on /dev/ttyUSB1 as 9600 bps.  It then start the sync on th Palm and then the sync in JPilot

Let me know what happens with JPilot.

Also, pre-load the "visor" module just in case...  

> sudo modprobe visor

It can help...  If this is the problem then simply add "visor" on 1 line in "/etc/modules" (Text file...)


Let me know!

---

### Post by GrnFrag on 2008-08-27
thanks for your response.   When i try to uninstall gnome-pilot, it tells me that it's also going to uninstall dependant package ubuntu-desktop.   I'm not sure thats a good idea.
when i run jpilot i get  
Syncing on device /dev/ttyUSB1
 Press the HotSync button now
****************************************
pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

In addition, this is a fresh boot, didn't load gnome-pilot.   i notice that even with my palm connected theres no /dev/ttyUSB any number, nor is there a /dev/*Pilot*

Edit*   I remembered a post i tried a while ago that suggesting adding these ports.
[HTML]gksudo mknod /dev/ttyUSB1 c 188 1 
[/HTML] and USB0 c 188 0 CHMOD 666 a+rw 
 and i get the same message.   i think i rm /dev/ttyUSB? after i applied the fix from the other post.   i wonder if i'm not adding them back correctly

---

### Post by GrnFrag on 2008-08-28
ok, some more info.    in the post above i've listed the steps i took to create /dev/ttyUSB0,1    However when i try to mount that to /mnt/foobar (info i got from IRC #ubunbtu)  I get the message that ttyUSB0 isnt' a block device.    

So my question is this.   How can i recreate the /dev/ttyUSB1 and /dev/ttyUSB0 then remount them?

---

### Post by patrickballeux on 2008-08-28
The ttyUSBx is not a removeable media.  It won't work.  It is a kind of serial port.

They should appear when you press sync on your palm.  Could you do this test?

> sudo modeprobe visor
> dmesg 
See if the visor module was correctly loaded
then connect your Palm then press "Hotsync" on it (do mind with Jpilot for now...)

Right after this, enter this command :

> ls /dev/ttyUSB*

You shoud see at least /dev/ttyUSB0 and /dev/ttyUSB1.

If it is not the case, then 

> dmesg

To see the error.

It you see them then start Jpilot.  Wait for your palm to timeout.  Configure JPilot for /dev/ttyUSB1, speed at 9600, USB.  

1 - Press hotsync on your palm
2 - Wait a few seconds (5-6)
3 - Press Sync in JPilot

If it does not work, do it again with /dev/ttyUSB1

Let me know.

Good luck.

---

### Post by GrnFrag on 2008-08-29
ok, visor loads fine.
[HTML][  453.861292] usbcore: registered new interface driver usbserial
[  453.861956] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  453.862250] usbcore: registered new interface driver usbserial_generic
[  453.862257] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  453.881340] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
[  453.881373] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
[  453.881397] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
[  453.881439] usbcore: registered new interface driver visor
[  453.881444] /build/buildd/linux-2.6.24/drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[/HTML]
these are the last lines in dmesg.   I press hotsync, run ls /dev/USB* and get
[HTML]every1@MoonRock:~$ ls/dev/ttyUSB*
bash: ls/dev/ttyUSB*: No such file or directory
every1@MoonRock:~$ ls /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory
[/HTML]
And when i run dmesge again, i get
[HTML][  254.134452] /build/buildd/linux-2.6.24/drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[  264.219417] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  264.388213] usb 1-1: configuration #1 chosen from 1 choice
[  264.399827] visor: probe of 1-1:1.0 failed with error -5
[/HTML]
Now if only someone has seen and resolved this error.    
Edit    People have found this error.   A bunch.   Doesn't help me, tho, it's a bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226197](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226197)
so i guess we can mark this thread as 'unfixable' or something.   Guess i'll have to put Windows back on these machines.   shitty

---

