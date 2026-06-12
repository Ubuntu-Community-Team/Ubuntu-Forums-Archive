---
title: "Sony Ericsson W580i Problem.."
date: 2008-08-27
forum: New to Ubuntu
---

### Post by k1ngb0b0 on 2008-08-27
Hello!  I recently bought a new Sony Walkman phone and am having trouble transferring music files to it.

Does anyone know how to go about doing this in Linux?  I've looked for awhile now and haven't found any help whatsoever.  I've seen tutorials and links about transferring things such as contacts and other entries, but I'm interested in music.

I plug the phone in, put it in "file transfer mode" and wait.  It shows up as "USB Drive" but I cannot mount it or do anything with it at all.

Does anyone know how to put songs on this phone?  I don't have a memory card for it so maybe that's the problem, but it has memory that I should be able to put songs on anyway...

If anyone has this phone and could shed some light on this for me that'd be great :)

---

### Post by philinux on 2008-08-27
If it shows up on your desktop that normally means it's mounted. What's the error message when you double click the icon.

---

### Post by k1ngb0b0 on 2008-08-27
> **philinux said:**
> If it shows up on your desktop that normally means it's mounted. What's the error message when you double click the icon.

It's not mounted, it's located in computer:///  I right click and try to mount it, but it doesn't work.  I don't even get an error.

When I double click on it, it says "No Media in the Drive"

---

### Post by bapoumba on 2008-08-27
Only the small extension card can be (automatically in my case) mounted, not the internal memory from the telephone.

---

### Post by k1ngb0b0 on 2008-08-27
So basically to put songs on my phone I have to buy a memory stick?

---

### Post by philinux on 2008-08-27
Ok so I've just plugged my sony K810i in and after I select "file transfer mode" I get both the internal memory card and the inserted stick mounted on my desktop. They show up as Phone and Phone Card. I've just checked that I can copy stuff to the internal card.

So we just need to work out why you model does not automount.

Plug it in and then open a terminal and post the output of

```
dmesg | tail -30
```

Copy and paste the command.

---

### Post by k1ngb0b0 on 2008-08-27
[71910.651091] cdc_acm 1-7:3.3: ttyACM1: USB ACM device
[71910.685324] usb0: register 'cdc_ether' at usb-0000:00:0b.0-7, CDC Ethernet Device, 02:80:37:0f:03:00
[71921.576895] usb 1-7: USB disconnect, address 9
[71921.579484] usb0: unregister 'cdc_ether' usb-0000:00:0b.0-7, CDC Ethernet Device
[71923.739921] usb 1-7: new full speed USB device using ohci_hcd and address 10
[71923.964038] usb 1-7: configuration #2 chosen from 1 choice
[71923.983594] scsi8 : SCSI emulation for USB Mass Storage devices
[71923.983878] usb-storage: device found at 10
[71923.983880] usb-storage: waiting for device to settle before scanning
[71928.981987] usb-storage: device scan complete
[71928.988078] scsi 8:0:0:0: Direct-Access     Sony Eri Memory Stick     0000 PQ: 0 ANSI: 0
[71929.002098] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[71929.002146] sd 8:0:0:0: Attached scsi generic sg3 type 0
[72190.645486] usb 1-7: USB disconnect, address 10
[74191.128173] usb 1-7: new full speed USB device using ohci_hcd and address 11
[74191.357056] usb 1-7: configuration #3 chosen from 1 choice
[74191.365989] cdc_acm 1-7:3.1: ttyACM0: USB ACM device
[74191.378002] cdc_acm 1-7:3.3: ttyACM1: USB ACM device
[74191.405199] usb0: register 'cdc_ether' at usb-0000:00:0b.0-7, CDC Ethernet Device, 02:80:37:0f:03:00
[74201.601927] usb 1-7: USB disconnect, address 11
[74201.604476] usb0: unregister 'cdc_ether' usb-0000:00:0b.0-7, CDC Ethernet Device
[74203.834994] usb 1-7: new full speed USB device using ohci_hcd and address 12
[74204.059607] usb 1-7: configuration #2 chosen from 1 choice
[74204.068111] scsi9 : SCSI emulation for USB Mass Storage devices
[74204.068254] usb-storage: device found at 12
[74204.068256] usb-storage: waiting for device to settle before scanning
[74209.062646] usb-storage: device scan complete
[74209.069631] scsi 9:0:0:0: Direct-Access     Sony Eri Memory Stick     0000 PQ: 0 ANSI: 0
[74209.085628] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[74209.085651] sd 9:0:0:0: Attached scsi generic sg3 type 0

---

### Post by philinux on 2008-08-27
That looks ok.

I know this sounds daft but open Gthumb from the graphics menu and see if you can import photo's. It sometimes kickstarts the usb memory.

I had to do this with my previous phone.

---

### Post by k1ngb0b0 on 2008-08-27
Couldnt get it to open at all with Gthumb.

---

### Post by philinux on 2008-08-27
With the phone plugged in what does

[FONT=Lucida Console]lsusb
[/FONT] 
report

---

### Post by k1ngb0b0 on 2008-08-27
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 06a3:8020 Saitek PLC 
Bus 001 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000

---

### Post by philinux on 2008-08-27
[FONT=Arial Narrow]Looking on google. It seems other people have the same problem. But their phone card mounts ok.[/FONT]

[http://forums.cingular.com/cng/board/message?board.id=sonyericsson&thread.id=33591](http://forums.cingular.com/cng/board/message?board.id=sonyericsson&thread.id=33591)
Message 3.

[FONT=Arial Narrow]I would raise a bug at launchpad.[/FONT]

---

### Post by k1ngb0b0 on 2008-08-27
Ok, that's probably what I'll do then.

Thanks for the help :)

---

### Post by mick222 on 2008-08-27
i use bluetooth to transfer files with this phone works great.

---

### Post by Thelasko on 2008-08-27
> **mick222 said:**
> i use bluetooth to transfer files with this phone works great.

I have the same phone W580i and I agree, you can only transfer files to the phone memory via bluetooth in Linux.  I also found the memory cards to be fairly inexpensive at Amazon.com.

---

### Post by k1ngb0b0 on 2008-08-27
Maybe I'll purchase a memory card then...I don't have a bluetooth dongle atm.

---

### Post by Thelasko on 2008-08-27
A good price for a bluetooth dongle is about $10 US.  Any more than $20 is a ripoff.  They are pretty standardized, even my off brand one is compatible with Ubuntu.
Edit:
I think [this]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1699115&CatId=909") is the one I bought.  I don't have it in front of me at the moment.

---

