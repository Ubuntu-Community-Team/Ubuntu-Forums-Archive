---
title: "SE W980 - USB not recognised."
date: 2008-08-09
forum: New to Ubuntu
---

### Post by gordo_099 on 2008-08-09
Hi,

Trying to get music onto the new SE w980, 8gb player.. :) 

The computer is not recognising the phone as a drive at all.

Looking into 'dmesg' I get..

[  684.109677] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  684.454392] usb 2-2: configuration #2 chosen from 1 choice
[  684.712266] usbcore: registered new interface driver libusual
[  684.726013] Initializing USB Mass Storage driver...
[  684.726117] scsi4 : SCSI emulation for USB Mass Storage devices
[  684.726185] usbcore: registered new interface driver usb-storage
[  684.726189] USB Mass Storage support registered.
[  684.726360] usb-storage: device found at 4
[  684.726366] usb-storage: waiting for device to settle before scanning
[  687.225402] usb-storage: device scan complete
[  687.226811] scsi 4:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
[  687.237642] sd 4:0:0:0: [sdb] 15520084 512-byte hardware sectors (7946 MB)
[  687.239562] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  687.239575] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  687.243804] sd 4:0:0:0: [sdb] 15520084 512-byte hardware sectors (7946 MB)
[  687.245804] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  687.245816] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  687.245824]  sdb: sdb1
[  687.248272] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  687.248323] sd 4:0:0:0: Attached scsi generic sg1 type 0
[  702.772489] usb 2-2: reset high speed USB device using ehci_hcd and address 4
[  717.908357] usb 2-2: reset high speed USB device using ehci_hcd and address 4
[  736.912150] usb 2-2: reset high speed USB device using ehci_hcd and address 4
[  754.953511] usb 2-2: reset high speed USB device using ehci_hcd and address 4
[  770.101372] usb 2-2: reset high speed USB device using ehci_hcd and address 4
[  785.910547] usb 2-2: reset high speed USB device using ehci_hcd and address 4
[  785.995566] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  785.995574] end_request: I/O error, dev sdb, sector 15520064
[  785.995578] Buffer I/O error on device sdb, logical block 3880016

and in lsusb I get..

Bus 002 Device 004: ID 0fce:e0da Sony Ericsson Mobile Communications AB 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1241:1111 Belkin Mouse
Bus 001 Device 001: ID 0000:0000  

So the laptop can see the thing, but at the same time it's not..

I'm running a Compaq V6000. Any thoughts at all? Thank you!

---

### Post by gingerlizard on 2008-08-16
You'll have to excuse my ignorance of how to investigate this, but I'm getting pretty much the same effect (ThinkPad T23, USB 1.0 only, Hardy Heron).

I can get the w980 to connect (using USB) as a camera, but when connecting it by USB as a mass storage device I get the same results as you.

Via bluetooth I can send single files to the phone, but try to see the w980 filesystem and the phone reboots!

There also seems to be an issue about getting music files to play once on the device - it will accept an m4a via bluetooth from linux, pops into the track list, you can select it - but the phone responds "Failed" when you try to play it.

With a good bit of farting about I loaded all that awful SE connection software under windows, and downloaded and played a tracked. Seems to be tonnes of "stuff" to basically do file browsing. Tried the w980 software update utility as well - nothing available for my handset.

Doesn't seem much prospect of using the w980 as a 3G modem under linux at the mo, pity as Orange have a 1 quid a day anytime, unlimited download offer.

---

### Post by nicedude on 2008-08-16
It might just be that mounting the device is failing due to you not having proper permission to it. You could try installing a utility pysdm which will mount drives for you and thereby make them accessable. To install it use the following command and then use the next command to launch it. Once you have it open you can look at the last drive in the list and that propbably will be your disk, now select to mount it and it just may be all you need. Otherwise you would need to read up on the mount command and craft one to mount this device.

hope that helps

---

### Post by ddales on 2008-09-04
I'm having the same types of problems.  I can get it to work as a camera and transfer pictures but nothing else.

I just "upgraded" from the w850i which has a mini-sd card which worked fine.

The built-in 8Gb in the w980 just doesn't want to play with Linux at all.

It also doesn't work within an XP VMware guest.

---

### Post by bwana on 2008-10-08
This seems to be related ?
[https://developer.sonyericsson.com/message/121675#121675](https://developer.sonyericsson.com/message/121675#121675)

---

### Post by ralphphil on 2008-10-25
Hi all..

Same problems here anyone seen any progress ?

Thanks

---

### Post by zachalekos on 2008-10-27
Same issue here

---

### Post by zachalekos on 2008-10-27
I've used pysdm and now  I can use it.

sudo aptitude install pysdm

in the terminal.

Then there should be an entry in the Applications Menu.

Thanks to nicedude

---

### Post by gingerlizard on 2008-11-10
My problems with w980 partially fixed with Intrepid Ibex 8.10 - OS now recognizes the model (connected via usb, not tried bluetooth recently).

However copying files (mp4's to the music folder) to the phone fails with -1.

The files do seem do get copied in spite of failure, are then listed as tracks, but are unplayable.

------------------
This worked for me to get the w980 working as a modem (on a Orange UK account, connecting a Thinkpad T23). 

First change 2 settings on the phone:
1. From the main screen, centre click to to bring up the menu, navigate to bottom right and click on "Settings".
2. Tab across to "Connectivity" and then scroll down and select "USB"
3. Select "USB Network", then "USB network type", then set the "Phone as Modem" radio button.
4. Go back up a level and select "USB data accounts", then select an appropriate account type (in my case "Orange Internet" for a UK Orange pay monthly account).

(Step 5 is optional). Go back up a level and select "USB default mode". If you change the setting from the default "Show menu" to "Phone mode", then the modem connection will be made automatically when the USB cable is plugged in without having to flip the phone open or press buttons on either the laptop or phone. If you stay with "Show menu" then you'll have to flip the phone open and select "Phone mode", then it'll connect - but you have the option to select "Media transfer" if you want to download photos from the phone instead. You know if you want this or not. I don't want it at the moment, but at other times I might.

Now on Ubuntu (Intrepid), right click on connection icon on the top bar, and select "Edit Connections...", then select the "Mobile Broadband" tab in the dialog box. Click the "Add" button and follow the wizard. The "Orange (contract)" option worked for me with no further adjustment.

So now I can plug in the phone and select "Phone mode" to get a mobile connection, or "Media transfer" to get photos off it.

But I'm still making no progress at downloading music to the phone (other than the awfulness of Sony's connection software and windows).

---

### Post by saneman on 2008-12-16
I am thinking of getting this handset, I use Ubuntu at work and at home and having to use a windows box would be a deal breaker. Have any of you tried using wine to install the SE software that comes with the phone? or maybe run virtualbox or something like that?

---

### Post by zachalekos on 2008-12-16
it's a good phone and you can use wammu. It syncs contacts and messages with the phone.

---

### Post by gingerlizard on 2008-12-16
> **saneman said:**
> I am thinking of getting this handset, I use Ubuntu at work and at home and having to use a windows box would be a deal breaker. Have any of you tried using wine to install the SE software that comes with the phone? or maybe run virtualbox or something like that?

The SE software is a special kind of dreadfulness, beyond even MS.

The best download results I got (of a bunch of my SoundJuiced cd's) was to set the phone to mass transfer mode and use MS File Manager - I couldn't get it to connect to Ubuntu in this mode at all.

In any mode, with any OS there were random file transfer failures, occassional misplacement of files (like a a single mp3 whilst transferring a whole album), duplicate folders and other weirdness.

I put up with this, and just cleaned up mistakes as they happened (about once every 5-10 cd's in mass transfer mode with MS File Explorer).

I suspect directory navigation is somehow broken on the phone, but I couldn't figure out a pattern. 

What you want to do is set up a file structure like Artist/Album/Track on the phone. The SE software can't do this, it transfers one track at once, into a Album/Track structure discarding the Artist info - probably a dirty fix because they know directory navigation is broken.

Oh and the phone can recognise but not play mp4's ripped with Juicer, stick to transferring mp3's.

Haven't tried using Wine, and all my results are using usb 1.1 on my old thinkpad t23 (my only dual boot machine).

---

### Post by johol on 2008-12-19
I have successfully transferred an MP3-file to my W980 from a Linux PC (running SLES 10.0 and kernel 2.6.13-15.11 i686). In order for the phone to recognize the MP3 I had to get the phone to re-synchronize (I can't find the option now, perhaps it is only available when files has been added/removed?).

I only post this information here, since if it worked with SLES 10.0 and 2.6.13 (which is ancient stuff), there is something that has been introduced after that which causes the problems with the phone in mass storage mode and Ubuntu.

---

### Post by saneman on 2009-01-08
so can we confirm that the W980 usb storage mode now works in ubuntu 8.10(intrepid ibex)?

All i need to be able to do is tranfer mp3's via usb to the phone.

pretty pointless having a WALKMAN phone that won't allow you to transfer music onto it unless u purchase an expensive OS

---

### Post by theduffman on 2009-01-22
> **ddales said:**
> I'm having the same types of problems.  I can get it to work as a camera and transfer pictures but nothing else.

I just "upgraded" from the w850i which has a mini-sd card which worked fine.

The built-in 8Gb in the w980 just doesn't want to play with Linux at all.

It also doesn't work within an XP VMware guest.

I have it working in a virtualbox running xp, altho its somewhat slower at transferring files.. works tho

---

### Post by imackee on 2009-03-01
The Sony Ericsson W980 mobile phone can be used with Ubuntu Hardy (8.04).   My installation was originally Gnome but I have since changed to KDE, effectively this means that it is Kubuntu. I could not get file transfer to work via the USB system.The phone shows up as a camera but it is not possible to transfer music files, currently, via USB; this applies even after installing pysdm.
With Bluetooth, however, just plug in the Bluetooth adapter to the pc, turn Bluetooth on at the phone and then go to the phone menu to select the connect to the PC option – the PC will show up in the ‘devices’ list on the phone.
Two screens then pop up, one on the phone asks you to enter a pin number. Enter the number and then go to the PC and enter the same number.
You should then have a small icon on the tasklist, it may simply be the default icon in appearance but if you hover over it with the mouse it should show the name of the PC and details on the Bluetooth connection (Obex).
If you click on this icon it will open another screen with a phone icon and the name of your phone. If you click on this icon it will open another screen (KBluetooth) giving options for Obex file transfer and Obex push. Select the Obex push and you will then get another KBluetooth screen. In the upper section select the directory from which you wish to transfer to the phone. In the bottom left section select the device to which you wish to transfer, usually the phone. At the bottom right is a section to which you can drag the files you wish to transfer, multiple selections are allowed. The click the ‘send’ button at the bottom of the screen.
If nothing happens, check your phone as you will need to click to accept the file. If you phone is setup to ‘ask each time’ for Bluetooth transfers, you will have to click each time for each file. If you set up your phone with the ‘always connect’ option, all the files should go without interruption.
I have sucessfully transferred mp4a files this way but note that the files are passed over in streaming mode. If they are transferred in this way, they seem to play OK on the phone. If you attempt to tranfer a file in a format the phone does not support, such as the ogg format, a warning message appears. Pictures also seem to transfer well from the PC to the phone using the obex push. It is also possible to send pictures from the phone to the PC using the media menu on the phone and selecting the ‘send’ option and then the Bluetooth option. Depending on settings you may have to click on a popup window on the PC to accept the transfer.
I hope this helps someone, it is sent by a simple user.
imackee, Durham UK

---

