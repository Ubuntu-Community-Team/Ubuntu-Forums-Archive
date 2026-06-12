---
title: "[SOLVED] How can I get my camera to be recognised as removable media."
date: 2008-06-21
forum: New to Ubuntu
---

### Post by philinux on 2008-06-21
Nautilus or something has a bug at the moment which means when I import pics from the camera it loses the creation date. It get a date modified as like todays date.

If I can use cp then it preserves the timestamp. 

The camera is not showing up in places.

---

### Post by fatality_uk on 2008-06-21
Phil, what camera are you using?
I ask because if I connect using USB with my Nikon D50, I have that issue, but if I take the SD card out it carries it all across

---

### Post by wlgyyk on 2008-06-21
I haven't find this bug yet.I consider that it has something to do with the brand of your camera. Mine is Canon and seems it goes all right.

---

### Post by philinux on 2008-06-21
> **fatality_uk said:**
> Phil, what camera are you using?
I ask because if I connect using USB with my Nikon D50, I have that issue, but if I take the SD card out it carries it all across

It's a canon G5. I've not got a card reader. When I was using Gutsy I had no problem. I've just checked all the pics previously imported and they have the correct date modified that match the properties>Image tab date taken.

This is a bug 215499. It's not nautilus though glib I think.

---

### Post by silkstone on 2008-06-21
This issue applies to all file transfers to and from removable media when using Nautilus - the file timestamp is changed to the current date and time. I understand that this is actually default Linux behaviour, but was tweaked out of Ubuntu in previous releases. Hopefully it will soon be changed in Hardy.

Does the camera show in 'Places'? If so, there are three ways around the timestamp issue. One is to copy the files from the terminal using the cp -p switch which preserves the date/time. The second is to use grsync, and the third is to use gnome-commander. At the moment I'm using gnome-commander for file transfers, and it works very well - preserves timestamps.

I'd also get a card reader - much quicker and easier than hooking up the camera. 7dayshop do one for peanuts, and it's very good.

---

### Post by philinux on 2008-06-21
Thanks for that. 

The camera is not showing up in places. Is there any way to mount it?

I was going to use the cp preserve.

---

### Post by ajgreeny on 2008-06-21
Rather than use nautlius for these transfers of photos and files from other drives to your main drive, I suggest you use another file manager, eg thunar (from xfce) gnome-commander, or xfe.  All can be downloaded and installed with synaptic and none of them suffer this timestamp problem.

---

### Post by silkstone on 2008-06-21
Perhaps try this....

[http://packages.ubuntu.com/feisty/utils/gphotofs](http://packages.ubuntu.com/feisty/utils/gphotofs)

Also, I've seen it suggested that if you boot your machine with the camera connected, switched on and in image review mode, it will recognise it, and in future you won't need to reboot - it will appear in Places when you connect it, so you can mount it. I've not tried that, since I always use a card reader.

HTH. :)

---

### Post by philinux on 2008-06-21
> **ajgreeny said:**
> Rather than use nautlius for these transfers of photos and files from other drives to your main drive, I suggest you use another file manager, eg thunar (from xfce) gnome-commander, or xfe.  All can be downloaded and installed with synaptic and none of them suffer this timestamp problem.

It's f-spot or gthumb doing the transfers. If I can get the camera mounted I'll give the other file managers a go.

---

### Post by philinux on 2008-06-21
> **silkstone said:**
> Perhaps try this....

[http://packages.ubuntu.com/feisty/utils/gphotofs](http://packages.ubuntu.com/feisty/utils/gphotofs)

Also, I've seen it suggested that if you boot your machine with the camera connected, switched on and in image review mode, it will recognise it, and in future you won't need to reboot - it will appear in Places when you connect it, so you can mount it. I've not tried that, since I always use a card reader.

HTH. :)

Off for a reboot then.

[edit] Didn't work.

---

### Post by philinux on 2008-06-21
Tried gphotofs. Same result as using gthumb, can get the pics off the cam with it but it's still not mounting in places.

---

### Post by philinux on 2008-06-22
Anyone know how to get the camera mounted. So it appears in places.

---

### Post by ajgreeny on 2008-06-22
Is the camera definitely not mounted?  Try ```
sudo fdisk -l
``` in terminal and you might find that it is mounted somewhere unexpected, though I can't imagine why.

---

### Post by philinux on 2008-06-22
dmesg shows my usb stick connecting correctly then disconnecting and it mounts on my desktop.

The last two lines are the camera being plugged in. As you can see it doesn't get scsi emulation as it should do.
```
 usb 6-3.1: new full speed USB device using ehci_hcd and address 5
[  139.870193] usb 6-3.1: configuration #1 chosen from 1 choice
[  186.590787] usb 6-3.1: USB disconnect, address 5
[  192.486841] usb 6-3.4: new high speed USB device using ehci_hcd and address 6
[  192.522681] usb 6-3.4: configuration #1 chosen from 1 choice
[  192.522766] scsi8 : SCSI emulation for USB Mass Storage devices
[  192.522859] usb-storage: device found at 6
[  192.522860] usb-storage: waiting for device to settle before scanning
[  194.373506] usb-storage: device scan complete
[  194.374000] scsi 8:0:0:0: Direct-Access     Ut163    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[  194.375004] sd 8:0:0:0: [sdc] 7897087 512-byte hardware sectors (4043 MB)
[  194.375433] sd 8:0:0:0: [sdc] Write Protect is off
[  194.375438] sd 8:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  194.375441] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  194.376947] sd 8:0:0:0: [sdc] 7897087 512-byte hardware sectors (4043 MB)
[  194.377408] sd 8:0:0:0: [sdc] Write Protect is off
[  194.377412] sd 8:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  194.377414] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  194.377417]  sdc: unknown partition table
[  194.424925] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[  194.424960] sd 8:0:0:0: Attached scsi generic sg3 type 0
[  205.164759] sd 8:0:0:0: [sdc] READ CAPACITY failed
[  205.164763] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  205.164766] sd 8:0:0:0: [sdc] Sense not available.
[  205.164945] sd 8:0:0:0: [sdc] Write Protect is off
[  205.164947] sd 8:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  205.164949] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  205.165065] usb 6-3.4: USB disconnect, address 6
[  205.166029] scsi 8:0:0:0: rejecting I/O to dead device
[  205.166037] scsi 8:0:0:0: rejecting I/O to dead device
[  205.166040] scsi 8:0:0:0: rejecting I/O to dead device
[  205.166043] scsi 8:0:0:0: [sdc] READ CAPACITY failed
[  205.166044] scsi 8:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  205.166046] scsi 8:0:0:0: [sdc] Sense not available.
[  205.166049] scsi 8:0:0:0: rejecting I/O to dead device
[  205.166052] scsi 8:0:0:0: [sdc] Write Protect is off
[  205.166053] scsi 8:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  205.166055] scsi 8:0:0:0: [sdc] Assuming drive cache: write through
[  251.355805] usb 6-3.1: new full speed USB device using ehci_hcd and address 7
[  251.391235] usb 6-3.1: configuration #1 chosen from 1 choice
```

```
sudo fdisk -l
[sudo] password for philcb: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8484877a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460        1702     1951897+  82  Linux swap / Solaris
/dev/sda3            1703       30401   230524717+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6e96290

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1459    11719386   83  Linux
/dev/sdb2            1460        1702     1951897+  82  Linux swap / Solaris
/dev/sdb3            1703       30401   230524717+  83  Linux



```

---

### Post by philinux on 2008-06-23
Bump,

I really need this as when the pics are copied they all get the current system date/time. Not the date taken as they did in gutsy.

Once it's mounted I can use cp with preserve.

---

### Post by ajgreeny on 2008-06-23
You can still copy at the moment and keep timestamps, you just can't do it with nautilus, a real bummer, I know.  Get xfe installed, and that will copy with correct timestamps, no problem.

---

### Post by philinux on 2008-06-25
That would be nice aj but it wont mount as a usb mass storage device. So I cant browse it even when it connected with gthumb or f-spot.

---

### Post by ajgreeny on 2008-06-25
OK, gotcha!

---

### Post by philinux on 2008-06-25
Any solution will get terminalled with immediate effect.

---

### Post by F W Adams on 2008-06-29
Had any luck philinux? I have the same problem, everything was fine with 7.10, now problem introduced by 8.04.

Just to summarise:
USB ok, lsusb gives
       Bus 003 Device 006: ID 04a9:3138 Canon, Inc. PowerShot A710 IS

import by f-spot works but no good as destroying date stamps

Camera does not appear in:
/media
/mnt
places or as far as I can tell anywhere at all.

Even when f-spot is about to import there is still no sign of the camera being mounted.

---

### Post by philinux on 2008-06-30
No, I've raised two bugs at launchpad maybe you could add your text from your post to them.

[https://bugs.launchpad.net/ubuntu/+bug/242644](https://bugs.launchpad.net/ubuntu/+bug/242644)
[https://bugs.launchpad.net/ubuntu/+bug/242647](https://bugs.launchpad.net/ubuntu/+bug/242647)

I think the devs are into 8.04.1 as I've had no official comments yet.

---

### Post by oldsoundguy on 2008-06-30
save yourself the grief and spend 10 bucks on eBay for a un1versal card reader.  THOSE are seen by the system.  I have 3 Gutsy boxes with built in readers and have had NO problem dropping in a card from my Nikon and reading it into the editor.  On top of that you will save that much in burned out camera batteries if you do a lot of shooting!

---

### Post by philinux on 2008-06-30
> **oldsoundguy said:**
> save yourself the grief and spend 10 bucks on eBay for a un1versal card reader.  THOSE are seen by the system.  I have 3 Gutsy boxes with built in readers and have had NO problem dropping in a card from my Nikon and reading it into the editor.  On top of that you will save that much in burned out camera batteries if you do a lot of shooting!

Yep I'm going that way. Whats annoying is that it worked in gutsy. Also my phone mounts as a mass storage device so why not the camera.

---

### Post by silkstone on 2008-06-30
Sorry I can't suggest anything else re mounting the camera, but just a small caution about card readers. External ones work fine, and the cheapo one from 7dayshop is excellent.

I have had a problem with an internal card reader, which I referred to in another thread. Ubuntu was picking up a voltage change every second (presumably something in the reader looking to see if a card had been inserted). The trouble was that it wrote this change to kern.log every second, so there was regular disk access and a very large log file!

I'm not sure if this was just a peculiarity of the reader I bought (branded X-PRO from Microdirect), but I ended up removing it and going back to an external reader - which is actually more convenient because I don't have to reach down to the system unit to plug the card in.

---

### Post by philinux on 2008-06-30
Is there a way of mounting it manually using mount from the command line.

---

### Post by silkstone on 2008-06-30
I've just dug this out from my notes on an earlier version of Ubuntu - Edgy, I think. I've no idea if it has any relevance to Hardy, but just in case...

To enable direct import of files from camera via USB:

Edit:

/etc/udev/rules.d/45-libgphoto2.rules

REM out the third line (BUS!="usb*" .... ) and replace with...

```
SUBSYSTEM!="usb_device",GOTO="libgphoto2_rules_end"
```

I remember doing that and it working in Edgy, but I don't know if the files and filenames have changed in Hardy.

P.S. Not sure if you have to reboot for it to take effect.

---

### Post by philinux on 2008-06-30
Different file and slightly different content.
```
/etc/udev/rules.d/45-libmtp7.rules

# UDEV-style hotplug map for libmtp
# Put this file in /etc/udev/rules.d

ACTION!="add", GOTO="libmtp_rules_end"
ATTR{dev}!="?*", GOTO="libmtp_rules_end"
SUBSYSTEM=="usb", GOTO="libmtp_usb_rules"
# The following thing will be deprecated when older kernels are phased out.
SUBSYSTEM=="usb_device", GOTO="libmtp_usb_device_rules"
GOTO="libmtp_rules_end"

```

Not sure what to hack.

---

### Post by silkstone on 2008-06-30
That file looks like it's for MP3 players and phones - all the devices listed are audio.

I've just tried plugging my camera in direct - Canon 30D - no joy, so it isn't just you!

---

### Post by silkstone on 2008-06-30
Again not much help I'm afraid, but I just tried again and the camera is being picked up in kern.log

Jun 30 22:35:40 silkstone-desktop2 kernel: [39057.244355] usb 1-6: new high speed USB device using ehci_hcd and address 7
Jun 30 22:35:40 silkstone-desktop2 kernel: [39057.391608] usb 1-6: configuration #1 chosen from 1 choice
Jun 30 22:36:12 silkstone-desktop2 kernel: [39089.142589] usb 1-6: USB disconnect, address 7

---

### Post by philinux on 2008-06-30
Yes I've seen that. If I plug in my usb stick those lines appear in message.log too, but also it gets registered as a scsi device which the cameras are not doing.

---

### Post by cariboo on 2008-06-30
I was looking at the output of dmesg from a couple of days ago I see a sdc in there when you plug in your camera. Have you tried to mount a /dev/sdc1.

Another thing to look at I know when I connect my camera in anything but preview mode I can still transfer pictures, but the camera itself does not show up anywhere. If I put the camera in preview mode it ges automagically mounted.

Jim

---

### Post by philinux on 2008-06-30
Yep tried that.

Nothing shows up in /media

---

### Post by silkstone on 2008-06-30
I don't want to give up on this!

From synaptic or apt-get, install....

gphoto2
gphotofs

Nope, that doesn't work for me. Grrrr...

---

### Post by philinux on 2008-06-30
Yep been down that road. 

I think the the £10 card reader is looking good.

The main beef I have is that this was fine in Gutsy. 

I might install gutsy in my VBox

---

### Post by silkstone on 2008-07-01
£2.50 + postage. :)

[http://www.7dayshop.com/catalog/product_info.php?cPath=777_6&products_id=100315](http://www.7dayshop.com/catalog/product_info.php?cPath=777_6&products_id=100315)

---

### Post by philinux on 2008-07-01
Shame it cant do SDHC, maybe a couple of quid more needed.
[http://www.amazon.co.uk/Hama-USB-2-0-Card-Reader/dp/B000IH1W20/ref=sr_1_1/026-8725871-1351605?ie=UTF8&s=electronics&qid=1214903262&sr=8-1#moreAboutThisProduct](http://www.amazon.co.uk/Hama-USB-2-0-Card-Reader/dp/B000IH1W20/ref=sr_1_1/026-8725871-1351605?ie=UTF8&s=electronics&qid=1214903262&sr=8-1#moreAboutThisProduct)

---

### Post by silkstone on 2008-07-01
Yes - in fact that looks very similar to the 7dayshop one except for the transparent case. It's probably an updated version - the 7dayshop reader is now shown as a clearance item so they may be getting rid of old stock ready for the new version. You can't go wrong at that price.

---

### Post by philinux on 2008-07-01
> **silkstone said:**
> Yes - in fact that looks very similar to the 7dayshop one except for the transparent case. It's probably an updated version - the 7dayshop reader is now shown as a clearance item so they may be getting rid of old stock ready for the new version. You can't go wrong at that price.

It's on order, postage was £2.50 but hey it gonna solve my problem and the reviews were excellent.

---

### Post by silkstone on 2008-07-01
Well I've just ordered two! (I keep one in the laptop bag, and I'll replace the 7dayshop one on the desktop PC just so I can use SDHC if I want).

With yet another Sandy Denny CD and Led Zep IV that came to just over the threshold for free delivery. Not sure that's really an economical way of buying a £4 card reader, but... :)

---

### Post by philinux on 2008-07-02
Arrived this morning.

Excellent card reader, they fixed the nautilus bug so copying the files of the CF card preserved the date/time taken.

Should have got one sooner the copy is instantaneous unlike copy from cam which took eons.

---

### Post by oldsoundguy on 2008-07-02
GOOD MOVE!  Saves so much grief as the chip set up for playback in every make of camera is just a bit different.  Some work out of the box and some do not, whereas a reader is set with a standard chipset and usually DOES work out of the box. (figure it this way, most camera makers make cameras (and other stuff) and do not do software or firmware in house .. (Nikon the exception) .. so the stuff is not all that good INSIDE the camera
I am not a laptop user, but I still carry a card reader in my gadget bag so that I can download and do basic toss or save at the end of a day.  I can then use my pda and send the saved images to my inbox for retrieval when I get home.  That can also be done on some hotel lobby computers or Kinko's (in the US) if you have a reader!

---

### Post by F W Adams on 2008-07-02
plilinux

Looks like I'll get one of those cards, would have bought yesterday but wanted to buy something else as well to make the postage look less ridiculous and there was nothing else I wanted.

Glad to see Nautilus date error fixed, I hadn't realised.

I'm sure it must be co-incidence but everyone having this camera problem is from the UK

---

### Post by philinux on 2008-07-02
> **F W Adams said:**
> plilinux

Looks like I'll get one of those cards, would have bought yesterday but wanted to buy something else as well to make the postage look less ridiculous and there was nothing else I wanted.

Glad to see Nautilus date error fixed, I hadn't realised.

I'm sure it must be co-incidence but everyone having this camera problem is from the UK

The reader really is well made. Transfer speed with nautilus copy and paste was milliseconds for 60 files each around 2/3 meg each

---

