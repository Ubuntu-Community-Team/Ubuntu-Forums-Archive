---
title: "Sony Ericsson C902 mounting"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by gremial on 2008-07-16
I have a SE C902 phone with a 4GB card and am having trouble creating a usb link for file transfer in Hardy. While under certain modes from the phone menu (Phone Mode, Media Transfer) a Camera Import dialogue box appears on my computer desktop, that's about as far as I can get. I had assumed that I'd just plug in and be able to access the phone/card as an external drive. Advice on mounting or whatever else I ought to do, please?

Thanks!

---

### Post by jmmL on 2008-07-18
Not sure how much help this is going to be, but:

I don't have exactly the same as you, but i do have a k770i. If i want to access the memory card in it, i plug the cable in, select "File Transfer Mode" and then wait for the phone to reboot into that mode. Then the memory card becomes automatically mounted (called "PHONE CARD" in my system). You should see a little icon on the desktop or in nautilus.

I've just checked though, and the phone's memory itself doesn't appear to be mounted - i can't see it anywhere at least.

If you want to sync contacts, calls and messages etc, then the program i use in ubuntu is called "wammu" (search for it in synaptic). It seems to have pretty limited functionality with my phone, and i suspect that will unfortunately be the case with yours. I still use MyPhoneExplorer in windows to sync important stuff - it's that and gaming that are keeping me attached. If you're feeling adventurous, you could try getting MPE to work under WINE; I believe a few people have been successful in doing so.

---

### Post by paul101 on 2008-07-18
hi


have you tried the phone on a windows pc. . . ?



the phone you have is relatively new... could be faulty. . . ?



i'kk try to see if i can get someone with a c902 to check that it works with linux

---

### Post by t0p on 2008-07-18
Your problem sounds a little... problematic.  I've had a couple of Sony Ericsson phones (a w300i and now a k800i) and they both mounted automatically for transfer of media (photos, music etc).  I just plug in the USB cable, select File Transfer on the phone's screen, and the phone and phone card would mount automatically, little icons appearing on the desktop.  So, I second what phil101 said: maybe your phone's faulty.

If you want to access other data, synch your calendar and suchlike, the app **gnokii** might be of use.  It was originally designed with Nokia phones in mind, but later versions work with other makes.  I haven't tried it myself with a Sony Ericsson, but I think it'll work.  Gnokii is in the repos.

---

### Post by philinux on 2008-07-18
I've a SE K810i. Plugging in I choose File Transfer and the phones internal and external cards appear on my desktop.

In the past I've used Gthumb to mount a motorola as it wouldn't show up automatically.

---

### Post by cdekter on 2008-07-18
I can confirm that this phone (C902) does not work with Linux AT ALL. I've tried it on two different Linux PCs both running Hardy. On my laptop, the phone locked up hard at the "preparing for mass storage" screen. I had to rip out the battery to get it to restart. On my desktop, the phone just keeps crashing in an infinite loop. 

Tried bluetooth with my laptop, this alternates between crashing the phone and causing a kernel panic on the laptop. BAD software SE!!!

A note: I tested the phone on a Vista PC and that works perfectly.

---

### Post by webworldx on 2008-07-18
I'm feeling it too guys! Bluetooth crashes the phone and restarts itself, Mass File Storage produces a lock up.  Looks like it's "back to Windows" to transfer all me photos... =(

---

### Post by cdekter on 2008-07-18
> **webworldx said:**
> I'm feeling it too guys! Bluetooth crashes the phone and restarts itself, Mass File Storage produces a lock up.  Looks like it's "back to Windows" to transfer all me photos... =(

I managed to figure out how get photos off and music on... at least:

Connect the phone to the USB, and select media transfer mode. After a few seconds F-Spot will pop up a dialog asking if you want to import... voila, you can now import photos off the device.

To transfer music on to the phone, install a program called gnomad2 (search in Synaptic). You have to start gnomad first, then plug the phone in. When the F-spot dialog appears, don't do anything to it... just leave it there. In gnomad switch to the data transfer tab. You should now be able to transfer music onto the phone. Note it won't show you anything that's already on the phone.

There is another method I was looking into, called fuse-mtp which lets you mount the phone as a file system in media transfer mode. However it's very beta and I couldn't get it to stay mounted for long without a SEGFAULT.

Incidentally I couldn't get the phone to bond via bluetooth with a Windows PC either... seems like there might be a few bugs to sort out in the firmware.

---

### Post by adam_kimber on 2008-07-18
I can only get this phone to work in MTP mode. I cannot get Hardy to recognise the USB mass storage at all. Works fine in windows :(

---

### Post by vasilis34 on 2008-07-26
Hi I bought some days before a Sony Ericsson c702 and I am facing the exact same problems. I tried to use SonyEricsson's pc suite through a windows xp virtual machine, using Virtualbox but even there I have problems. It's working with bluetooth but with the usb cable it got connected only once. All the other times the PC suite can not detect the plugged in phone.
Did anyone find any solution?

---

### Post by adam_kimber on 2008-07-29
Hey everyone here who is having problems with the mass storage option on the C902. Do you get the following symptoms. 

1) Plugin cable. Phone says choose mode. Select Mass Storage
2) Phone restarts
3) Phone flickers and then restarts and keeps doing that.

If so can you note the time you plugged it in and then paste the last entries in the log (System menu > Choose Administration > System Log) then select messages. (It is time logged hence the requirement to note the time). If they are all the same there might be related bug or I can sumbit a new one.

---

### Post by fhucho on 2008-08-15
Hi,
I have C702 and am having the same problems.
I tried to watch the changes in several log files after I plugged the phone using Mass Storage mode. I am attaching the logfiles (only with lines which were added after I plugged the phone).

---

### Post by aaronp on 2008-08-26
I have the exact same issue with C702 on HH8.04. Can't get the GNomad option suggested to work - segfault.

Attached log file of the last time I attempted mass storage mode.

---

### Post by sboddy on 2008-08-28
Well judging from this extract:
```
Aug 15 16:57:43 franta-desktop kernel: [ 9535.222978] sd 2:0:0:0: [sdb] 368493 512-byte hardware sectors (189 MB)
Aug 15 16:57:43 franta-desktop kernel: [ 9535.229980] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861535] scsi 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861539] end_request: I/O error, dev sdb, sector 368472
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861542] Buffer I/O error on device sdb, logical block 368472
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861551] scsi 2:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861555] end_request: I/O error, dev sdb, sector 368473
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861558] Buffer I/O error on device sdb, logical block 368473
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861561] Buffer I/O error on device sdb, logical block 368474
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861564] Buffer I/O error on device sdb, logical block 368475
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861568] Buffer I/O error on device sdb, logical block 368476
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861570] Buffer I/O error on device sdb, logical block 368477
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861573] Buffer I/O error on device sdb, logical block 368478
Aug 15 16:57:44 franta-desktop kernel: [ 9535.861576] Buffer I/O error on device sdb, logical block 368479
Aug 15 16:57:44 franta-desktop kernel: [ 9535.864527] Buffer I/O error on device sdb, logical block 368472
Aug 15 16:57:44 franta-desktop kernel: [ 9535.865990] scsi 2:0:0:0: rejecting I/O to dead device
Aug 15 16:57:44 franta-desktop kernel: [ 9535.869062] scsi 2:0:0:1: rejecting I/O to dead device
```
I'd guess at one of two things is happening.
[LIST=1]
[*]The phone is lying about it's size so the system tries to access outside the available area,
[*]The "disk" does not use a partition table like regular disks, but instead has the the whole "disk" as one filesystem.
[/LIST]

I think I've seen 2 before, and it may well have been an old Sony Ericsson T610 which would imply previous form. Instead of a command like:
```
mount /dev/sdc1 <path>
```
you would do:
```
mount /dev/sdc <path>
```
I'm trying to solve what is probably an identical issue, but a C902 and remotely with a non-techie, which is very boring for that person.
If someone can get the udev/hal stuff configured to stop trying to mount everything immediately, some manual commands like the one above may give access to the filesystem.
I'd suggest checking these links as a starter:
[LIST=1]
[*][https://wiki.ubuntu.com/DebuggingRemovableDevices]("https://wiki.ubuntu.com/DebuggingRemovableDevices")
[*][https://wiki.ubuntu.com/DebuggingHal]("https://wiki.ubuntu.com/DebuggingHal")
[*][http://ubuntuforums.org/showthread.php?t=705493&highlight=rsync+renice+usb]("http://ubuntuforums.org/showthread.php?t=705493&highlight=rsync+renice+usb")
[/LIST]
I suspect having to create a custom udev rule, like in 3, for these devices.

---

### Post by sboddy on 2008-08-28
I've looked into this a bit further, and yes, the issue I'm seeing is the same.

After a bit of further investigation, I strongly suspect that a kernel patch is required to add an UNUSUAL_DEV entry to this file:
[INDENT][http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/storage/unusual_devs.h;h=ba412e68d474a70e13bf7b68543eeb5f32c3fad7;hb=HEAD]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/storage/unusual_devs.h;h=ba412e68d474a70e13bf7b68543eeb5f32c3fad7;hb=HEAD")[/INDENT]
which looks to be referenced in:
[INDENT][http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/storage/unusual_devs.h;h=ba412e68d474a70e13bf7b68543eeb5f32c3fad7;hb=HEAD]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/storage/unusual_devs.h;h=ba412e68d474a70e13bf7b68543eeb5f32c3fad7;hb=HEAD")[/INDENT]
As you can see, there are a number of Sony Ericsson devices in here. Unfortunately, I've reached the point where this becomes very difficult to do remotely, especially as it requires recompiling kernels remotely on an old laptop ](*,) Any of you eager lot up to the challenge? :)

This will probably be useful:
[INDENT][http://phildev.net/linux/usb-unusualdevs-notes.html]("http://phildev.net/linux/usb-unusualdevs-notes.html")[/INDENT]

---

### Post by sboddy on 2008-08-28
OK, based on some guestimation, I think this is a reasonable starting point for some trial and error.

From udevmonitor:
```
ID_VENDOR=Sony_Eri          0x0fce
ID_MODEL=Memory_Stick       0x????
```

Based on other SE USB mass storage in the kernel file, this is a start point for a patch:
```
/* Reported by ??? ??? <???@???.???> */
UNUSUAL_DEV(  0x0fce, 0x????, 0x0000, 0x0000,
                "Sony Ericsson",
                "??? Memory Stick ???",
                US_SC_DEVICE, US_PR_DEVICE, NULL,
                US_FL_NO_WP_DETECT | US_FL_FIX_CAPACITY ),
```

Possibly add US_FL_IGNORE_RESIDUE
Possibly add US_FL_CAPACITY_HEURISTICS (or replace US_FL_FIX_CAPACITY with it)

Unfortunately I can't find anything that gives the model id for the phone in hex.

---

### Post by fhucho on 2008-08-29
Have anybody tried connecting C702 on another linux distribution?

---

### Post by cdekter on 2008-08-29
> **sboddy said:**
> I've looked into this a bit further, and yes, the issue I'm seeing is the same.

After a bit of further investigation, I strongly suspect that a kernel patch is required to add an UNUSUAL_DEV entry to this file:
[INDENT][http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/storage/unusual_devs.h;h=ba412e68d474a70e13bf7b68543eeb5f32c3fad7;hb=HEAD]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/storage/unusual_devs.h;h=ba412e68d474a70e13bf7b68543eeb5f32c3fad7;hb=HEAD")[/INDENT]
which looks to be referenced in:
[INDENT][http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/storage/unusual_devs.h;h=ba412e68d474a70e13bf7b68543eeb5f32c3fad7;hb=HEAD]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=drivers/usb/storage/unusual_devs.h;h=ba412e68d474a70e13bf7b68543eeb5f32c3fad7;hb=HEAD")[/INDENT]
As you can see, there are a number of Sony Ericsson devices in here. Unfortunately, I've reached the point where this becomes very difficult to do remotely, especially as it requires recompiling kernels remotely on an old laptop ](*,) Any of you eager lot up to the challenge? :)

This will probably be useful:
[INDENT][http://phildev.net/linux/usb-unusualdevs-notes.html]("http://phildev.net/linux/usb-unusualdevs-notes.html")[/INDENT]

I'm not averse to doing a bit of kernel compilation :P

---

### Post by adam_kimber on 2008-09-03
> **sboddy said:**
> Unfortunately I can't find anything that gives the model id for the phone in hex.

How would find this out?

I am reasonably tech savvy and if you wanted me to do some tests etc to get the kernel patch to work then I am not adverse to compiling, deleting, modifying text files etc. Not to great at coding though. 

I would like to get this to work!

Can post my logs if that helps!

---

### Post by sboddy on 2008-09-04
> **adam_kimber said:**
> How would find this out?
Ordinarily an "lsusb" will give you the vendor and device id's. Unfortunately, because these phones don't play nice, you never see the device in that list because they continuously reset while plugged into the PC in mass storage mode.

There  may be something udev related that will show it, but something in the kernel is taking that device id and turning it into "Memory Stick". I just don't know what that id is, or where it is found. Using udevmonitor as shown in the troubleshooting guides only showed the translated value. Online I found references to e075, but this was for older phones, so I'm not sure if it is the same. It also appears common that the size is misreported, causing the same type of issues seen with these recent phones.

On my system (hardy) /var/lib/misc/usb.ids is an old copy of [http://www.linux-usb.org/usb.ids]("http://www.linux-usb.org/usb.ids"). Neither of these have the above id in them though. For the vendor we can be fairly sure of "0fce Sony Ericsson Mobile Communications AB". For the device id this section only lists the K750i, K608i and K510i. There are some files online with a few other ids, but not for the C902.

I did just have a thought though. Check your CD for the Windows driver software. I think the *.ini files might contain numerical vendor/device ids.

> **adam_kimber said:**
> I am reasonably tech savvy and if you wanted me to do some tests etc to get the kernel patch to work then I am not adverse to compiling, deleting, modifying text files etc. Not to great at coding though. 

Same here, but doing it remotely giving instructions to a non-tech (hi mom ):P)... not good! Otherwise it'll probably be Christmas before I can look into this effectively again, when I've got my hands on the device, and can tinker without boring her to death.

> **adam_kimber said:**
> I would like to get this to work!

Can post my logs if that helps!

Unless your logs are showing some dramatic difference from those already shown, they'd just be additional noise to be honest. What's needed now is a good dig into what is going on.

---

### Post by adam_kimber on 2008-09-04
These are the results of lsusb:

MTP mode

```
Bus 008 Device 002: ID 0fce:00d4 Sony Ericsson Mobile Communications AB 
```

In Phone Mode

```
Bus 008 Device 003: ID 0fce:d0d4 Sony Ericsson Mobile Communications AB 
```

PictBridge Mode

```
Bus 008 Device 004: ID 0fce:10d4 Sony Ericsson Mobile Communications AB 
```


Mass Storage Mode

```
Bus 008 Device 005: ID 0fce:e0d4 Sony Ericsson Mobile Communications AB 
```

IT WORKS?!?

Result of uname -a 

```
Linux zia 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

```

Last lines of the log. 

```
Sep  4 19:44:34 zia kernel: [ 5025.378272] UDF-fs: No VRS found
Sep  4 19:47:29 zia kernel: [ 5199.060290] usb 8-2: new high speed USB device using ehci_hcd and address 2
Sep  4 19:47:29 zia kernel: [ 5199.198119] usb 8-2: configuration #4 chosen from 1 choice
Sep  4 19:49:11 zia kernel: [ 5301.509787] usb 8-2: USB disconnect, address 2
Sep  4 19:49:22 zia kernel: [ 5312.747732] usb 8-2: new high speed USB device using ehci_hcd and address 3
Sep  4 19:49:23 zia kernel: [ 5312.882749] usb 8-2: configuration #3 chosen from 1 choice
Sep  4 19:49:23 zia kernel: [ 5313.039218] cdc_acm 8-2:3.1: ttyACM0: USB ACM device
Sep  4 19:49:23 zia kernel: [ 5313.044439] cdc_acm 8-2:3.3: ttyACM1: USB ACM device
Sep  4 19:49:23 zia kernel: [ 5313.046233] usbcore: registered new interface driver cdc_acm
Sep  4 19:49:23 zia kernel: [ 5313.046235] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
Sep  4 19:49:23 zia kernel: [ 5313.133558] usb0: register 'cdc_ether' at usb-0000:00:1d.7-2, CDC Ethernet Device, 02:80:37:17:03:00
Sep  4 19:49:23 zia kernel: [ 5313.133569] usbcore: registered new interface driver cdc_ether
Sep  4 19:49:56 zia kernel: [ 5346.499976] usb 8-2: USB disconnect, address 3
Sep  4 19:49:56 zia kernel: [ 5346.500962] usb0: unregister 'cdc_ether' usb-0000:00:1d.7-2, CDC Ethernet Device
Sep  4 19:50:19 zia kernel: [ 5369.457067] usb 8-2: new high speed USB device using ehci_hcd and address 4
Sep  4 19:50:19 zia kernel: [ 5369.594165] usb 8-2: configuration #1 chosen from 1 choice
Sep  4 19:50:55 zia kernel: [ 5404.920859] usb 8-2: USB disconnect, address 4
Sep  4 19:51:31 zia kernel: [ 5441.076566] usb 8-2: new high speed USB device using ehci_hcd and address 5
Sep  4 19:51:31 zia kernel: [ 5441.225369] usb 8-2: configuration #2 chosen from 1 choice
Sep  4 19:51:31 zia kernel: [ 5441.292994] usbcore: registered new interface driver libusual
Sep  4 19:51:31 zia kernel: [ 5441.309236] Initializing USB Mass Storage driver...
Sep  4 19:51:31 zia kernel: [ 5441.309715] scsi8 : SCSI emulation for USB Mass Storage devices
Sep  4 19:51:31 zia kernel: [ 5441.310184] usbcore: registered new interface driver usb-storage
Sep  4 19:51:31 zia kernel: [ 5441.310187] USB Mass Storage support registered.
Sep  4 19:51:36 zia kernel: [ 5446.302437] scsi 8:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Sep  4 19:51:36 zia kernel: [ 5446.302934] scsi 8:0:0:1: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Sep  4 19:51:36 zia kernel: [ 5446.304577] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Sep  4 19:51:36 zia kernel: [ 5446.304609] sd 8:0:0:0: Attached scsi generic sg3 type 0
Sep  4 19:51:36 zia kernel: [ 5446.305820] sd 8:0:0:1: [sdd] Attached SCSI removable disk
Sep  4 19:51:36 zia kernel: [ 5446.305848] sd 8:0:0:1: Attached scsi generic sg4 type 0
Sep  4 19:51:37 zia kernel: [ 5447.222146] sd 8:0:0:0: [sdc] 368493 512-byte hardware sectors (189 MB)
Sep  4 19:51:37 zia kernel: [ 5447.223516] sd 8:0:0:0: [sdc] Test WP failed, assume Write Enabled
Sep  4 19:51:37 zia kernel: [ 5447.225012] sd 8:0:0:0: [sdc] 368493 512-byte hardware sectors (189 MB)
Sep  4 19:51:37 zia kernel: [ 5447.226384] sd 8:0:0:0: [sdc] Test WP failed, assume Write Enabled
Sep  4 19:51:37 zia kernel: [ 5447.226390]  sdc: sdc1
Sep  4 19:51:39 zia kernel: [ 5448.519338] sd 8:0:0:1: [sdd] 1869824 512-byte hardware sectors (957 MB)
Sep  4 19:51:39 zia kernel: [ 5448.520709] sd 8:0:0:1: [sdd] Test WP failed, assume Write Enabled
Sep  4 19:51:39 zia kernel: [ 5448.522207] sd 8:0:0:1: [sdd] 1869824 512-byte hardware sectors (957 MB)
Sep  4 19:51:39 zia kernel: [ 5448.523579] sd 8:0:0:1: [sdd] Test WP failed, assume Write Enabled
Sep  4 19:51:39 zia kernel: [ 5448.523586]  sdd: sdd1
```

Works with current kernel by the looks of things! :D :D :D  Can anyone confirm? If so thread can be marked solved. :D

---

### Post by fhucho on 2008-09-05
@adam_kimber
What works? Did you succeeded to actually transfer files between the phone and PC?
Is there a way to install the new kernel you are using via a package manager or do I have to compile it myself?

---

### Post by adam_kimber on 2008-09-05
Just using the latest kernel from the package manager. No compiling required. 

Transferring files in Mass Storage mode works perfectly. It even uses USB2.0 and gets pretty fast speeds.

---

### Post by fhucho on 2008-09-05
Still not working for me even with kernel 2.6.24-21 - my C702 just keeps restarting :(
BTW, the kernel 2.6.24-21 is not in the standard repositories, I had to use hardy-proposed.

---

### Post by fhucho on 2008-09-05
@adam_kimber
What firmware version do you have in your phone?

---

### Post by adam_kimber on 2008-09-05
I have the C902 with R3BA035 by 3 for firmware. 

Oops my bad. I enable backports as soon as install. I want it now! :P

---

### Post by adam_kimber on 2008-09-06
> **fhucho said:**
> Still not working for me even with kernel 2.6.24-21 - my C702 just keeps restarting :(

The C702 might be slightly different in the way it connects and therefore require another patch rather than using the same one as the C902. :( :(

Restarted my machine today and hey its not working again :(

---

### Post by adam_kimber on 2008-09-06
Meh it appears to be not working again. I have the two syslogs here. One working and one not. I hope they might help someone more tech savvy than I. :D

Working version
```
Sep  4 19:51:31 zia kernel: [ 5441.076566] usb 8-2: new high speed USB device using ehci_hcd and address 5
Sep  4 19:51:31 zia kernel: [ 5441.225369] usb 8-2: configuration #2 chosen from 1 choice
Sep  4 19:51:31 zia kernel: [ 5441.292994] usbcore: registered new interface driver libusual
Sep  4 19:51:31 zia kernel: [ 5441.309236] Initializing USB Mass Storage driver...
Sep  4 19:51:31 zia kernel: [ 5441.309715] scsi8 : SCSI emulation for USB Mass Storage devices
Sep  4 19:51:31 zia kernel: [ 5441.310184] usbcore: registered new interface driver usb-storage
Sep  4 19:51:31 zia kernel: [ 5441.310187] USB Mass Storage support registered.
Sep  4 19:51:36 zia kernel: [ 5446.302437] scsi 8:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Sep  4 19:51:36 zia kernel: [ 5446.302934] scsi 8:0:0:1: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Sep  4 19:51:36 zia kernel: [ 5446.304577] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Sep  4 19:51:36 zia kernel: [ 5446.304609] sd 8:0:0:0: Attached scsi generic sg3 type 0
Sep  4 19:51:36 zia kernel: [ 5446.305820] sd 8:0:0:1: [sdd] Attached SCSI removable disk
Sep  4 19:51:36 zia kernel: [ 5446.305848] sd 8:0:0:1: Attached scsi generic sg4 type 0
Sep  4 19:51:37 zia kernel: [ 5447.222146] sd 8:0:0:0: [sdc] 368493 512-byte hardware sectors (189 MB)
Sep  4 19:51:37 zia kernel: [ 5447.223516] sd 8:0:0:0: [sdc] Test WP failed, assume Write Enabled
Sep  4 19:51:37 zia kernel: [ 5447.225012] sd 8:0:0:0: [sdc] 368493 512-byte hardware sectors (189 MB)
Sep  4 19:51:37 zia kernel: [ 5447.226384] sd 8:0:0:0: [sdc] Test WP failed, assume Write Enabled
Sep  4 19:51:37 zia kernel: [ 5447.226390]  sdc: sdc1
Sep  4 19:51:39 zia kernel: [ 5448.519338] sd 8:0:0:1: [sdd] 1869824 512-byte hardware sectors (957 MB)
Sep  4 19:51:39 zia kernel: [ 5448.520709] sd 8:0:0:1: [sdd] Test WP failed, assume Write Enabled
Sep  4 19:51:39 zia kernel: [ 5448.522207] sd 8:0:0:1: [sdd] 1869824 512-byte hardware sectors (957 MB)
Sep  4 19:51:39 zia kernel: [ 5448.523579] sd 8:0:0:1: [sdd] Test WP failed, assume Write Enabled
Sep  4 19:51:39 zia kernel: [ 5448.523586]  sdd: sdd1
```

Nonworking (usual method ;) )

```
Sep  6 10:09:34 zia kernel: [ 5037.063339] usb 2-2: new high speed USB device using ehci_hcd and address 20
Sep  6 10:09:34 zia kernel: [ 5037.206696] usb 2-2: configuration #2 chosen from 1 choice
Sep  6 10:09:34 zia kernel: [ 5037.207414] scsi16 : SCSI emulation for USB Mass Storage devices
Sep  6 10:09:39 zia kernel: [ 5042.197070] scsi 16:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Sep  6 10:09:39 zia kernel: [ 5042.197689] scsi 16:0:0:1: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Sep  6 10:09:39 zia kernel: [ 5042.199048] sd 16:0:0:0: [sdd] 368493 512-byte hardware sectors (189 MB)
Sep  6 10:09:40 zia kernel: [ 5043.031335] sd 16:0:0:0: [sdd] Test WP failed, assume Write Enabled
Sep  6 10:09:40 zia kernel: [ 5043.033575] sd 16:0:0:0: [sdd] 368493 512-byte hardware sectors (189 MB)
Sep  6 10:09:40 zia kernel: [ 5043.035454] sd 16:0:0:0: [sdd] Test WP failed, assume Write Enabled
Sep  6 10:09:40 zia kernel: [ 5043.035461]  sdd: sdd1
Sep  6 10:09:40 zia kernel: [ 5043.038094] sd 16:0:0:0: [sdd] Attached SCSI removable disk
Sep  6 10:09:40 zia kernel: [ 5043.038129] sd 16:0:0:0: Attached scsi generic sg4 type 0
Sep  6 10:09:40 zia kernel: [ 5043.039188] sd 16:0:0:1: [sde] 1869824 512-byte hardware sectors (957 MB)
Sep  6 10:09:40 zia kernel: [ 5043.040688] sd 16:0:0:1: [sde] Test WP failed, assume Write Enabled
Sep  6 10:09:40 zia kernel: [ 5043.047178] sd 16:0:0:1: [sde] 1869824 512-byte hardware sectors (957 MB)
Sep  6 10:09:40 zia kernel: [ 5043.053536] sd 16:0:0:1: [sde] Test WP failed, assume Write Enabled
Sep  6 10:09:40 zia kernel: [ 5043.053544]  sde: sde1
Sep  6 10:09:40 zia kernel: [ 5043.058431] sd 16:0:0:1: [sde] Attached SCSI removable disk
Sep  6 10:09:40 zia kernel: [ 5043.058466] sd 16:0:0:1: Attached scsi generic sg5 type 0
Sep  6 10:09:40 zia kernel: [ 5043.177602] usb 2-2: reset high speed USB device using ehci_hcd and address 20
Sep  6 10:09:40 zia kernel: [ 5043.235159] usb 2-2: USB disconnect, address 20
Sep  6 10:09:40 zia kernel: [ 5043.235190] sd 16:0:0:0: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep  6 10:09:40 zia kernel: [ 5043.235193] end_request: I/O error, dev sdd, sector 368472
Sep  6 10:09:40 zia kernel: [ 5043.235195] printk: 248 messages suppressed.
Sep  6 10:09:40 zia kernel: [ 5043.235574] scsi 16:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Sep  6 10:09:40 zia kernel: [ 5043.235576] end_request: I/O error, dev sdd, sector 368473
Sep  6 10:09:40 zia kernel: [ 5043.235773] scsi 16:0:0:1: [sde] READ CAPACITY failed
Sep  6 10:09:40 zia kernel: [ 5043.235774] scsi 16:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Sep  6 10:09:40 zia kernel: [ 5043.235776] scsi 16:0:0:1: [sde] Sense not available.
Sep  6 10:09:40 zia kernel: [ 5043.235780] scsi 16:0:0:1: [sde] Write Protect is off
Sep  6 10:09:40 zia kernel: [ 5043.235797] scsi 16:0:0:1: [sde] READ CAPACITY failed
Sep  6 10:09:40 zia kernel: [ 5043.235798] scsi 16:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Sep  6 10:09:40 zia kernel: [ 5043.235801] scsi 16:0:0:1: [sde] Sense not available.
Sep  6 10:09:40 zia kernel: [ 5043.235805] scsi 16:0:0:1: [sde] Write Protect is off
```

Spotted it! First one uses libusual and the second does not.

---

### Post by sboddy on 2008-09-09
> **adam_kimber said:**
> Spotted it! First one uses libusual and the second does not.

Not sure about that. Look at your original post where you show it working - no sign of libusual. I'm guessing that might be printed first time you try to do mass storage. I'm guessing libusual is a red herring.

Strange that it did work once though. Did you manage to browse and transfer files to and from the phone?
--
Ack! Please ignore all that lot. I just spotted it further down in the original post. Still need to be sure that the non-working one isn't loading that somewhere else in the log file, though.
--
That libusual looks to be the code that handles the unusual usb devices I think. It's as if it somehow registered with a different id temporarily. V. weird!

---

### Post by sboddy on 2008-09-09
> **adam_kimber said:**
> These are the results of lsusb:

MTP mode

```
Bus 008 Device 002: ID 0fce:00d4 Sony Ericsson Mobile Communications AB 
```

In Phone Mode

```
Bus 008 Device 003: ID 0fce:d0d4 Sony Ericsson Mobile Communications AB 
```

PictBridge Mode

```
Bus 008 Device 004: ID 0fce:10d4 Sony Ericsson Mobile Communications AB 
```


Mass Storage Mode

```
Bus 008 Device 005: ID 0fce:e0d4 Sony Ericsson Mobile Communications AB 
```

Can I suggest that you send a patch to the maintainer of usb.ids that I linked to in one of my earlier posts?

[http://www.linux-usb.org/usb.ids]("http://www.linux-usb.org/usb.ids")

If you don't want to, I will do it, but you did the work, so you should get the credit (assuming there's a changelog with credits.)
--
Looks like the following for the device id:
first byte:
[INDENT]00 - MTP
10 - PictBridge
d0 - Phone
e0 - Mass Storage
[/INDENT]
second byte is the device (i.e. d4 - C902) If you look at the usb.ids file you can see that the SE W810i is listed twice with d042 and e042, so it looks like the W810i currently has Phone and Mass Storage, but no MTP or PictBridge, and is identified with second byte of 42. (The hexadecimal answer to life, the universe and everything ;-) )

From this I think those with the C702 will be able to infer their device id's even if they can't get output from lsusb for all the modes. One of you should do this and also forward the details to the guy at the top of the usb.ids file.

---

### Post by sboddy on 2008-09-10
Random musing:

The 16 bit model_id value is more likely split 4/12, i.e.
[INDENT]xyyy[/INDENT]
where x is the type, and yyy is the phone type.

Otherwise they'd only have allowed for 256 phone types (8 bit). With 12 bits they have 4096 possible phones.

---

### Post by adam_kimber on 2008-09-15
After installing kde4, using the command ```
 apt-get install kubuntu-kde4-desktop 
``` from the following repo ```
http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
``` libusual is the default connection method for the C902. One of the following packages does that. 

```
adept adept-batch adept-common adept-installer adept-manager 

  adept-notifier adept-updater akonadi-server akregator ark-kde4 debtags 

  dolphin-kde4 dragonplayer gwenview-kde4 hplip-gui htdig jockey-kde 

  juk-kde4 kamera-kde4 karm kate-kde4 kde-icons-oxygen kde-window-manager 

  kde4libs-bin kdebase-bin-kde4 kdebase-data-kde4 kdebase-plasma-kde4 

  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data 

  kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data 

  kdebase-workspace-libs4+5 kdelibs5 kdelibs5-data 

  kdemultimedia-kio-plugins-kde4 kdepim-wizards kdepimlibs-data kdepimlibs5 

  kdesudo kdesudo-kde4 kdm-kde4 khelpcenter khelpcenter-kde4 klipper-kde4 

  kmilo-kde4 kmix-kde4 knetworkconf-kde4 knode knotes konqueror-kde4 

  konqueror-nsplugins-kde4 konsole konsole-kde4 kontact kopete-kde4 

  kppp-kde4 krdc-kde4 krfb-kde4 kscd-kde4 ksnapshot-kde4 ksysguard-kde4 

  ksysguardd-kde4 kubuntu-artwork-usplash kubuntu-default-settings 

  kubuntu-docs kubuntu-kde4-desktop kubuntu-konqueror-shortcuts 

  kwalletmanager kwalletmanager-kde4 language-selector-qt 

  libakonadiprivate1 libcapseo0 libcaptury0 libdbd-mysql-perl libdbi-perl 

  libept0 libkcddb4-kde4 libkdecorations4 libkipi5 libkonq5 

  libkonq5-templates libkwineffects1 libnet-daemon-perl libokularcore1-kde4 

  libplasma2 libplrpc-perl libpoppler-qt4-3 libqca2 libqca2-plugin-ossl 

  libqimageblitz4 libqt-perl libskim0 libsmokeqt1 libspectre1 

  libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxapian15 libzip1 

  lockfile-progs mysql-client-5.0 mysql-server-5.0 network-manager-kde 

  network-manager-openvpn network-manager-pptp network-manager-vpnc 

  networkstatus okular-kde4 openoffice.org-kde openvpn openvpn-blacklist 

  pptp-linux python-qt4-dbus python-reportlab resolvconf skim 

  software-properties-kde system-config-printer-kde systemsettings-kde4 

  ttf-dustin vpnc 

```

However I still get errors. :(

---

### Post by sboddy on 2008-09-15
> **adam_kimber said:**
> After installing kde4, using the command ```
 apt-get install kubuntu-kde4-desktop 
``` from the following repo ```
http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
``` libusual is the default connection method for the C902. One of the following packages does that. 

<snip>

However I still get errors. :(

I'm puzzled, Adam. What makes you think that installing kde4 will help? This is a kernel level issue, which appears to be common on Sony Ericsson devices. It looks like their standard SW stack on their devices does not follow the usb mass storage standard properly, and an exception needs to be added to the kernel files previously described for this device. KDE is not relevant to this unless I've completely misunderstood something.

Just for the record, has anyone actually tried compiling kernels yet? I honestly would do this myself, but it's just not practical to do this kind of speculative poke and test debugging remotely when it involves misbehaving pluggable devices. It might take half a dozen recompiles, reboot, replug cycles, and my remote hands would probably give me serious ear-ache about how it would be easier with Windows :roll:

---

### Post by Bush_Roo on 2008-09-15
> **sboddy said:**
> Just for the record, has anyone actually tried compiling kernels yet? I honestly would do this myself, but it's just not practical to do this kind of speculative poke and test debugging remotely when it involves misbehaving pluggable devices. It might take half a dozen recompiles, reboot, replug cycles, and my remote hands would probably give me serious ear-ache about how it would be easier with Windows :roll:

Err... I have done some custom kernel compiling... it isn't sweet, and saying that it is a pain, particularly when it doesn't even help after a long wait, doesn't describe half of it...

use Windoz == better idea THENELSE use real camera ELSE get nother phone
END /* I'll now mind my own business now */ :p

---

### Post by sboddy on 2008-09-15
> **Bush_Roo said:**
> Err... I have done some custom kernel compiling... it isn't sweet, and saying that it is a pain, particularly when it doesn't even help after a long wait, doesn't describe half of it...

use Windoz == better idea THENELSE use real camera ELSE get nother phone
END /* I'll now mind my own business now */ :p

Wow! Thanks for the support and encouragement!

Maybe you should revisit your "about me"
> Interests
[INDENT]Linux breaking and **fixing**[/INDENT]

Perhaps change that to "Linux breaking and... oh I can't be bothered, I'll go use Windows instead".

If it's not obvious, I'm one of those "whinging poms" that tend to be famous for our sarcasm.

FYI, the point of fixing this is to transfer music **to** the device. Getting images **from** it works fine with MTP, so "real camera" is irrelevant. Getting "nother phone" is defeatist. Not my style, cobber!

---

### Post by adam_kimber on 2008-09-15
> **sboddy said:**
> I'm puzzled, Adam. What makes you think that installing kde4 will help? 

My bad. I had two cases on the previous page, one where the device worked perfectly using libusual and one that didn't. The default behaviour in my version of Ubuntu (Hardy) is to use the non-libusual method. 

My thoughts were, "how can I reproduce my libusual working event". I traced back what I had installed and unistalled and confirmed that when kde4 is installed the machine uses libusual. I was hoping this would be a solution that did not require kernel recompiles. 

I need to identify the package from that repo that changes the way the usb interface is handled from the default to the libusual one. 

As I had it working once. I can have it working again.

---

### Post by adam_kimber on 2008-09-15
> **sboddy said:**
> Just for the record, has anyone actually tried compiling kernels yet? 

If you can give me pointers on how to get the patch into a kernel and recompile then I would be happy to have a go. It sounds complicated though :(

---

### Post by sboddy on 2008-09-15
> **adam_kimber said:**
> If you can give me pointers on how to get the patch into a kernel and recompile then I would be happy to have a go. It sounds complicated though :(

The following link will probably do a far better job of explaining than I ever could:
[INDENT][https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")[/INDENT]
Once you get to the "Modify the source for your needs" step, then refer back to posts [#15]("http://ubuntuforums.org/showpost.php?p=5683242&postcount=15") and [#16]("http://ubuntuforums.org/showpost.php?p=5683886&postcount=16").

Please be careful. Yes, you could potentially stuff your install. If this is your only system, and you need it to be working for something important, and you're not comfortable with anything; don't continue.

Read through twice, and only then, decide if you really want to go ahead.

---

### Post by adam_kimber on 2008-09-17
I have attempting to recompile twice. Both successful compiles but neither option works for me. I still get errors. The two options tried so far are below. 

I would like to know if there is a compile log for the kernel compilation process as I would like to check if unusual_dev.h is actually being compiled in. 

```
UNUSUAL_DEV(  0x0fce, 0xe0d4, 0x0000, 0x0000,
               "Sony Ericsson",
               "C902",
               US_SC_DEVICE, US_PR_DEVICE, NULL,
               US_FL_IGNORE_RESIDUE | US_FL_FIX_CAPACITY ), 
```

```
UNUSUAL_DEV(  0x0fce, 0xe0d4, 0x0000, 0x0000,
              "Sony Ericsson",
              "C902",
              US_SC_DEVICE, US_PR_DEVICE, NULL,
              US_FL_NO_WP_DETECT | US_FL_FIX_CAPACITY ), 
```

---

### Post by sboddy on 2008-09-17
Thanks for trying that, Adam. Damn shame it didn't work.

Not sure about the compile log. In theory any file with a new timestamp will cause recompile, But perhaps this is not true for *.h files. Failing that, run a "make distclean" to force/ensure all file are compiled/included from scratch.

You're sure the new kernel is installed and getting loaded at reboot? ("uname -a", but I think you need to modify something somewhere to make the kernel version unique.)

Side note: Ignore the other flag I mentioned (US_FL_CAPACITY_HEURISTICS), as I found the commit, and it is only for a device that sometimes misreports capacity +1, unlke the US_FL_FIX_CAPACITY flag where the device always reports capacity +1.

It looks like something else is possibly going on. To get to the bottom of this we need to increase the debug, so we can understand what size is reported, and what size is available. I'm almost sure this is some stupid error in the SE stack. Then again it could be deliberate. Sony at least are infamous for making everything proprietary. I'll have a dig around the source later, and see if I can come up with some further ideas.

Looks like there's a CONFIG_USB_STORAGE_DEBUG kernel build option. This might give some useful detail (or an extreme amount of noise :-) )

---

### Post by adam_kimber on 2008-09-17
> **sboddy said:**
> 
You're sure the new kernel is installed and getting loaded at reboot? ("uname -a", but I think you need to modify something somewhere to make the kernel version unique.)

Yeah the code on the page you linked me to builds a nice little deb file that can be installed. It adds an entry to the grub menu and off we go. I have -21 and the compiled kernel is -22 which means on the recompiled kernel I have no nvidia graphics or soundcard. :lolflag: 
It works though!

---

### Post by adam_kimber on 2008-09-17
> **sboddy said:**
> It looks like something else is possibly going on. To get to the bottom of this we need to increase the debug, so we can understand what size is reported, and what size is available. 

From the log files posted earlier on. 

```
Aug 26 23:01:32 ap1 kernel: [174810.286639] sd 17:0:0:0: [sdc] 368493 512-byte hardware sectors (189 MB)
```

From the working (libusual that I cannot reproduce method) 

```
Sep  4 19:51:37 zia kernel: [ 5447.222146] sd 8:0:0:0: [sdc] 368493 512-byte hardware sectors (189 MB)
```

The reported sector and byte size are the same :confused:


> **sboddy said:**
> 
Looks like there's a CONFIG_USB_STORAGE_DEBUG kernel build option. This might give some useful detail (or an extreme amount of noise :-) )

Is that added during compliation or do I need to modify a file to add that option in? 

Using this method for compiling, source from GIT tree. ```
AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic
```

---

### Post by sboddy on 2008-09-17
> **adam_kimber said:**
> From the log files posted earlier on. 

```
Aug 26 23:01:32 ap1 kernel: [174810.286639] sd 17:0:0:0: [sdc] 368493 512-byte hardware sectors (189 MB)
```

From the working (libusual that I cannot reproduce method) 

```
Sep  4 19:51:37 zia kernel: [ 5447.222146] sd 8:0:0:0: [sdc] 368493 512-byte hardware sectors (189 MB)
```

The reported sector and byte size are the same :confused:



Yeah, no offense, but I don't trust that one occasion of working. Not being able to repeat the success basically takes us back to square one. :(

> **adam_kimber said:**
> 
Is that added during compliation or do I need to modify a file to add that option in? 

Using this method for compiling, source from GIT tree. ```
AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic
```

I'm not sure for the deb process, but if you were building a kernel using the old fashioned way you'd either:
[LIST=1]
[*]make config
[*]make menuconfig
[*]make xconfig
[/LIST]
Or something similar. In here you would find the option in the config tree, and set it to true.

I'm downloading the kernel so I can take a look and hopefully provide some more assistance.

OK, done that. I'd recommend using
```
gksudo make xconfig
```
and scrolling down to, and selecting, the "USB support". A bunch of options will appear on the right. Scroll down to "USB Mass Storage support" and select the entry just below "USB Mass Storage verbose debug". It should then write these options to the config file for the kernel build. Then proceed as you did before.

Alternatively, just edit the .config file with vi, and change
```
# CONFIG_USB_STORAGE_DEBUG is not set
```
to
```
CONFIG_USB_STORAGE_DEBUG=y
```
and continue as before.

Either one will work, just depends if you're comfortable with the vi editor ;-)

---

### Post by adam_kimber on 2008-09-18
Well that went well. It spewed lots of stuff I have no idea of what it might mean. :)

```
Sep 18 11:02:27 zia kernel: [  399.740686] usb 5-1: new high speed USB device using ehci_hcd and address 2
Sep 18 11:02:27 zia kernel: [  399.881037] usb 5-1: configuration #2 chosen from 1 choice
Sep 18 11:02:27 zia kernel: [  399.937737] usbcore: registered new interface driver libusual
Sep 18 11:02:27 zia kernel: [  399.971061] Initializing USB Mass Storage driver...
Sep 18 11:02:27 zia kernel: [  399.971120] scsi8 : SCSI emulation for USB Mass Storage devices
Sep 18 11:02:27 zia kernel: [  399.971155] usbcore: registered new interface driver usb-storage
Sep 18 11:02:27 zia kernel: [  399.971157] USB Mass Storage support registered.
Sep 18 11:02:32 zia kernel: [  404.956005] scsi 8:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Sep 18 11:02:32 zia kernel: [  404.956617] scsi 8:0:0:1: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
Sep 18 11:02:32 zia kernel: [  404.958724] sd 8:0:0:0: [sdc] 368492 512-byte hardware sectors (189 MB)
Sep 18 11:02:32 zia kernel: [  404.959975] sd 8:0:0:0: [sdc] Test WP failed, assume Write Enabled
Sep 18 11:02:32 zia kernel: [  404.978876] sd 8:0:0:0: [sdc] 368492 512-byte hardware sectors (189 MB)
Sep 18 11:02:32 zia kernel: [  404.981509] sd 8:0:0:0: [sdc] Test WP failed, assume Write Enabled
Sep 18 11:02:32 zia kernel: [  404.981513]  sdc:<7>usb-storage: queuecommand called
Sep 18 11:02:32 zia kernel: [  404.984144]  sdc1
Sep 18 11:02:32 zia kernel: [  404.985073] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Sep 18 11:02:32 zia kernel: [  404.985097] sd 8:0:0:0: Attached scsi generic sg3 type 0
Sep 18 11:02:32 zia kernel: [  404.987731] sd 8:0:0:1: [sdd] Attached SCSI removable disk
Sep 18 11:02:32 zia kernel: [  404.987749] sd 8:0:0:1: Attached scsi generic sg4 type 0
Sep 18 11:02:33 zia kernel: [  405.804813] sd 8:0:0:1: [sdd] 1869823 512-byte hardware sectors (957 MB)
Sep 18 11:02:33 zia kernel: [  405.859010] sd 8:0:0:1: [sdd] Test WP failed, assume Write Enabled
Sep 18 11:02:33 zia kernel: [  406.024530] usb 5-1: USB disconnect, address 2
Sep 18 11:02:33 zia kernel: nsnonn<4oeatit[ss52
Sep 18 11:02:33 zia kernel: nsnonn<4-eatit[s4Ts031 ticates erge22oq2es*c b> brrlicge22oqvs*c A0 _704r,tosf=0 s < 80_704r,tossf i sD6 4t:. s23<7 <t reub[10  E48s68<7 <tarub[10  E. s25  t=4
Sep 18 11:02:33 zia kernel: em-- 4d
Sep 18 11:02:33 zia kernel: g2d  [r ee 
Sep 18 11:02:33 zia kernel: em-- 4d
Sep 18 11:02:33 zia kernel: 3d 2[Ise- b01rt-sor67lk  s0-6uee00rt-sor07less0-ue10UkSus4[etk eeyleen040s0f045etk ee==0cn04 5Ua 0.relorrrlese0[0]Ua 0.relorrrlese0[700_704r,tossf i s < 60_704r,tossf i s <)0ru1 [rrb248] usb-stor=21 sa
Sep 18 11:02:33 zia kernel: 6tsE5l<s72igb82=2sa
Sep 18 11:02:33 zia kernel: 6bgsE0g1y16ro 25ypst0 b]d9 1y16ro 25ypst0  e sr0tY00be7]u6t:k a 9>5*100be9]us6ta 1>5*C0ror59<=r, tossf=0x s < 90_704r,tossf 0 s <)0ru1 [rrlessr=0ga7d70ru1 [rrlessr=0ga7dt 8r07<s na]]r=0ohde)08r07<s na]]gylohde 7 ser=at3 6.026135] usrqty]bx  1m0gC10 s-66.rq]bx  1m0- re>ru2 4ff2 t>20C0o re>ru2 4ff2 t>4Rrerh005 onmae:.
Sep 18 11:02:33 zia kernel: bll[[sasdt -4006] b9ogmr2sa= 03b[02ge rorsfsrs<6sft *d0b]3teronsnoe
Sep 18 11:02:33 zia kernel: 2=f,n. rg6 6.=4ae>2a1l0l>- ga0[06t=cl74r2i7s7beCrs5sb6. e4ro0>4>5o0mou1us06,d6-bB07 76Cfxs a B sfor reset: -tor_  ge1t u6resu0< fst:0as-     C t s6-1se s-6p]:ssCr :-2 -esc[e 0evrrur 7 et004301au ecil-r756 7>he* m8  :ba l abbfs*euur]  u r
Sep 18 11:02:33 zia kernel: 2t.b6:dvfre*E 0to8r
Sep 18 11:02:33 zia kernel: 2t.b9:dvfre*Lstto _  :6ab< 0:=ur  0: 0_  :1ab< 0:=urEe::  f2bt--a40n<0awy 6 C0f2tu--a40n<0awR 0Uer_buf: xfer 31: St]a40saceype=2t*d 0l
Sep 18 11:02:33 zia kernel: er: ]a40scey7t*d :l : ussu ]e [ -:a 06m : ussu ]e [ -:aDee
Sep 18 11:02:33 zia kernel: (0  S43r r d bo<22[ 60
Sep 18 11:02:33 zia kernel: 3443rt;f d bo<62[ 60
Sep 18 11:02:33 zia kernel: k0xf cok4u e ats 47 n0xf cok4u e ats 47 n0xf cok4- e ats 47 n0xf cok4u e ats 48 n0xf cok4u e ats Ed
Sep 18 11:02:33 zia kernel: 7 04 0>f-  Bte]bn00
Sep 18 11:02:33 zia kernel: 7 04 Cuf: xfer 31 bytes
Sep 18 11:02:33 zia kernel: o:tx100O]sest28 r
Sep 18 11:02:33 zia kernel: 2w>ikr:oe03s] usb-storage:  28 00 00 05 9f 68 00 00 04 00
Sep 18 11:02:33 zia kernel: [  406.028493] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:33 zia kernel: [  406.028496] end_request: I/O error, dev sdc, sector 368488
Sep 18 11:02:33 zia kernel: [  406.028714] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:33 zia kernel: [  406.028717] end_request: I/O error, dev sdc, sector 368488
Sep 18 11:02:33 zia kernel: [  406.028935] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:33 zia kernel: [  406.028938] end_request: I/O error, dev sdc, sector 368488
Sep 18 11:02:33 zia kernel: [  406.029155] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:33 zia kernel: [  406.029158] end_request: I/O error, dev sdc, sector 368488
Sep 18 11:02:33 zia kernel: [  406.029381] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:33 zia kernel: [  406.029384] end_request: I/O error, dev sdc, sector 368424
Sep 18 11:02:33 zia kernel: [  406.029593] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:33 zia kernel: [  406.029596] end_request: I/O error, dev sdc, sector 368428
Sep 18 11:02:33 zia kernel: [  406.029818] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:33 zia kernel: [  406.029821] end_request: I/O error, dev sdc, sector 368480
Sep 18 11:02:33 zia kernel: [  406.030028] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:33 zia kernel: [  406.030030] end_request: I/O error, dev sdc, sector 368484
Sep 18 11:02:34 zia kernel: [  406.030246] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.030249] end_request: I/O error, dev sdc, sector 368488
Sep 18 11:02:34 zia kernel: [  406.030464] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.030466] end_request: I/O error, dev sdc, sector 368488
Sep 18 11:02:34 zia kernel: [  406.030719] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.030722] end_request: I/O error, dev sdc, sector 32
Sep 18 11:02:34 zia kernel: [  406.030928] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.030930] end_request: I/O error, dev sdc, sector 36
Sep 18 11:02:34 zia kernel: [  406.031151] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.031155] end_request: I/O error, dev sdc, sector 32
Sep 18 11:02:34 zia kernel: [  406.031359] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.031362] end_request: I/O error, dev sdc, sector 36
Sep 18 11:02:34 zia kernel: [  406.031582] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.031585] end_request: I/O error, dev sdc, sector 32
Sep 18 11:02:34 zia kernel: [  406.031790] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.031793] end_request: I/O error, dev sdc, sector 36
Sep 18 11:02:34 zia kernel: [  406.032012] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.032015] end_request: I/O error, dev sdc, sector 32
Sep 18 11:02:34 zia kernel: [  406.032219] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.032222] end_request: I/O error, dev sdc, sector 36
Sep 18 11:02:34 zia kernel: [  406.032450] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.032453] end_request: I/O error, dev sdc, sector 32
Sep 18 11:02:34 zia kernel: [  406.032657] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 18 11:02:34 zia kernel: [  406.032660] end_request: I/O error, dev sdc, sector 36
```

---

### Post by PocketDog on 2008-09-18
Nevermind.

---

### Post by sboddy on 2008-09-18
:shock:... :-k... :mad:... ](*,)... :cry:

WTF! Although there are a couple of bits that look vaguely like they might mean something, as a whole it's spewed a load of garbage into the logfile.

OK, perhaps I need to suck it in, build a kernel and see why the debug output is useless. [-o<

This is turning out to be much trickier than I first thought it would be.

Anyway, thanks Adam for doing all the legwork so far, you're a :KS.

---

### Post by moggy812 on 2008-09-18
can you not get an USB key adaptor thing for your phone card, that way all you have to do is plug it in to your pc, and it will read it like an USB key, is really simple, ok, you night have to keep taking the phone card in and out of your phone, but at least it'll be less of a head ache for you...
my wife has one, and i am for ever borrowing it :D

---

### Post by adam_kimber on 2008-09-18
> **moggy812 said:**
> can you not get an USB key adaptor thing for your phone card, that way all you have to do is plug it in to your pc, and it will read it like an USB key, is really simple, ok, you night have to keep taking the phone card in and out of your phone, but at least it'll be less of a head ache for you...
my wife has one, and i am for ever borrowing it :D

I have one! That is not really the issue. I want to get this fixed so that I can use it anyway without alternative options. Plus I want to solve this problem as its annoying me :lolflag:

---

### Post by adam_kimber on 2008-09-18
> **sboddy said:**
> :shock:... :-k... :mad:... ](*,)... :cry:

WTF! Although there are a couple of bits that look vaguely like they might mean something, as a whole it's spewed a load of garbage into the logfile.

OK, perhaps I need to suck it in, build a kernel and see why the debug output is useless. [-o<

This is turning out to be much trickier than I first thought it would be.

Anyway, thanks Adam for doing all the legwork so far, you're a :KS.

I could compile in usb storage debug, usb debug and take out libusual altogether? The compiled kernel seems to have it in standard.

---

### Post by Kevbert on 2008-09-18
Take a look at this link for [[COLOR="Red"]gammu[/COLOR]]("http://cihar.com/gammu/phonedb/sony-ericsson/1968/").  As the phone is very new support is limited, but if you put in a bug report the author is very supportive.

---

### Post by sboddy on 2008-09-18
> **Kevbert said:**
> Take a look at this link for [[COLOR="Red"]gammu[/COLOR]]("http://cihar.com/gammu/phonedb/sony-ericsson/1968/").  As the phone is very new support is limited, but if you put in a bug report the author is very supportive.

Thanks for the pointer Kevbert, but I don't think this is related to what we are trying to achieve. Gammu (et al) are all about syncing contacts/alarms etc and handling SMS/MMS's using the phone protocols (i.e. syncml, vcards, file transfers _over obex_) and so on.

This topic is all about trying to get the ubiquitous USB Mass Storage mode working, so that files can be drag'n'dropped to and from the phone as part of the standard filesystem (i.e. no kio or gvfs tricks). The key desire here (for my part in this) is to transfer mp3's to the device, so it can be used as an mp3 player. Bluetooth is too slow for this with any normal number of tracks, and I doubt any of the desktop music players will sync playlists over obex even if obex is possible over a usb data cable.

---

### Post by adam_kimber on 2008-09-18
Just to throw a few more things into the works. I compiled a kernel without any modifications to unusual_devs.h and with libusual turned on (yes yes I am still chasing that one). 

The device initialises properly, does not reset repeatedly but does not seem to register the fact that they are a mass storage device. It looks like it has just stopped midway through the process. 

```
Sep 18 20:21:27 zia kernel: [  219.608933] usb 5-1: new high speed USB device using ehci_hcd and address 2
Sep 18 20:21:27 zia kernel: [  219.757569] usb 5-1: configuration #2 chosen from 1 choice
Sep 18 20:21:27 zia kernel: [  219.762758] usb 5-1: Product: Memory Stick
Sep 18 20:21:27 zia kernel: [  219.762760] usb 5-1: Manufacturer: Sony Ericsson
Sep 18 20:21:27 zia kernel: [  219.762761] usb 5-1: SerialNumber: 3537970221997430
Sep 18 20:21:27 zia kernel: [  219.809189] usbcore: registered new interface driver libusual
```

PS sorted my sound and video problems too. :D Custom kernels are complex!

---

### Post by vasilis34 on 2008-09-23
I tried the latest alpha 6 of Intrepid Ibex on a virtualbox machine and my phone (SonyEricsson C702) gets mounted correctly and its functional.. in a way. First problem the available disk space is refered to the phone's built-in memory even when copying in a folder in the memory card, so it doesn't let me copy enough data. Second problem, usually when copying a lot of mp3s together, the copying fails with an error -2 bad file parameters. When asked when connecting the phone I chosed phone mode. Has anyone faced the same things with Intrepid alpha ?

---

### Post by adam_kimber on 2008-09-23
Have been waiting for Intrepid to come out to see if someone else had fixed the problem :P This offers a glimmer of hope for me.

It is interesting to note that you can copy files using phone mode. That would imply that someone has implemented a version of SE's proprietary file system browser, that works when the phone is in phone mode.

---

### Post by sboddy on 2008-09-24
Well, if it's fixed in the updated kernel, it would suggest that something in the fundamental usb mass storage must have changed. When I was digging through the "unusual devices" files I was looking at the latest Linus Torvalds branch of the kernel. which is the same as the likely 2.6.27 that will go into intrepid.

For my part looks like we're going to fall back to using a dead cheap Kensington usb key that takes Micro SD's, and comes with a 2GB card too. Only £7. Can't go wrong!!!

---

### Post by sboddy on 2008-09-29
> **sboddy said:**
> For my part looks like we're going to fall back to using a dead cheap Kensington usb key that takes Micro SD's, and comes with a 2GB card too. Only £7. Can't go wrong!!!
Unless you don't triple check everything...

Breakdown in communication: I asked and concluded it was Micro SD. Forgot we were dealing with Sony. I really should have known better! Bloody propriety Sony M2 rubbish.

Sigh! Never mind. Reverted to older Micro SD compatible phone for now, which she prefers anyway.

I'll take another look at Christmas.

---

### Post by adam_kimber on 2008-09-29
Ah yes Sony and their proprietary formats. They seem to like them a lot. I will have another bash at this problem when my phone comes back from repair (it would no longer make stable calls) and I have fixed my USB subsystem on my machine (I deleted the wrong files and cannot get it back :P)

---

### Post by barrrrt on 2008-09-30
Hi all. Got same problem here too. Do u think it will be fixed and devlivered through update in ubuntu?

---

### Post by adam_kimber on 2008-10-01
Probably will be fixed at some point in the future. Time will tell. :P

---

### Post by TeoBigusGeekus on 2008-10-21
Problem solved in Intrepid Ibex - at least for C702!!!

---

### Post by cdekter on 2008-10-25
My C902 also now works in Intrepid, but only in Phone mode - mass storage mode still exhibits the same resetting problem. Phone mode seems to satisfy most requirements though, so yay :)

---

### Post by adam_kimber on 2008-10-25
> **cdekter said:**
> My C902 also now works in Intrepid, but only in Phone mode - mass storage mode still exhibits the same resetting problem. Phone mode seems to satisfy most requirements though, so yay :)

Phone mode worked in Hardy too! :D So the mass storage still has not been fixed. :(

---

### Post by rrsn on 2008-11-19
> **gremial said:**
> I have a SE C902 phone with a 4GB card and am having trouble creating a usb link for file transfer in Hardy. While under certain modes from the phone menu (Phone Mode, Media Transfer) a Camera Import dialogue box appears on my computer desktop, that's about as far as I can get. I had assumed that I'd just plug in and be able to access the phone/card as an external drive. Advice on mounting or whatever else I ought to do, please?

Thanks!

Did you solved the problem? How? I did not understand the messages in topic

---

### Post by adam_kimber on 2008-11-24
> **rrsn said:**
> Did you solved the problem? How? I did not understand the messages in topic

Unfortunately the problem is still there. There appears to be problems with Lenny also with the mass storage mode on the C902. 

I could not get my Kernel Patch to work and the other person working on it is tied up until after Christmas. So if its urgent I would suggest trying a non-debian based distro. If not. Just wait and it will be fixed. :)

---

### Post by abickerton on 2008-11-29
While mass storage mode works just fine for me. (Apart from F-prot opening twice when it detects the device) The filesystems are mounted in /media/PHONE and /media/PHONE CARD. 

I have mtpfs installed and the latest libmtp snapshot running on Hardy (amd64)

The problem I'm having is with MTP sync(Media transfer mode) as Rhythmbox sees the C902 but seg faults when I try to write anything to the device. I think the problem is that libmtp tries to write to the root which of course is read only.

---

### Post by adam_kimber on 2008-11-30
> **abickerton said:**
> While mass storage mode works just fine for me. (Apart from F-prot opening twice when it detects the device) The filesystems are mounted in /media/PHONE and /media/PHONE CARD..

Hmm. Working  mass storage you say. Your setup might be the golden cup.... Right can you open a terminal and type uname -a and after you plug in the C902 in mass storage can you type dmesg and paste the results here???! :D

---

### Post by bobharvey on 2008-12-15
Well, just for comparison, I have just plugged my new one into suse 11.0 (my ubuntu machine is in the other room, backing up)

Nothing happened.
I went into the phone-connectivity menu and tried to change to usb mass storage mode, but it wanted me to unplug the cable first.  I did that, changed mode, and plugged in.  

It worked first time.  See dmesg:
usb 2-1: new high speed USB device using ehci_hcd and address 4
usb 2-1: configuration #2 chosen from 1 choice
usb 2-1: New USB device found, idVendor=0fce, idProduct=e0d4
usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 2-1: Product: Memory Stick
usb 2-1: Manufacturer: Sony Ericsson
usb 2-1: SerialNumber: 3587900245294910
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
scsi 2:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
sd 2:0:0:0: [sdb] Attached SCSI removable disk
sd 2:0:0:0: Attached scsi generic sg1 type 0
scsi 2:0:0:1: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
sd 2:0:0:1: [sdc] Attached SCSI removable disk
sd 2:0:0:1: Attached scsi generic sg2 type 0
usb-storage: device scan complete
sd 2:0:0:0: [sdb] 368493 512-byte hardware sectors (189 MB)
sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
sd 2:0:0:0: [sdb] Assuming drive cache: write through
sd 2:0:0:0: [sdb] 368493 512-byte hardware sectors (189 MB)
sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
sd 2:0:0:0: [sdb] Assuming drive cache: write through
 sdb: sdb1
SFW2-INext-DROP-DEFLT IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1c:f0:75:ed:d3:08:00 SRC=10.0.0.2 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=6129 DF PROTO=2 
SFW2-INext-DROP-DEFLT IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1c:f0:75:ed:d3:08:00 SRC=10.0.0.2 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=6130 DF PROTO=2 
SFW2-INext-DROP-DEFLT IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1c:f0:75:ed:d3:08:00 SRC=10.0.0.2 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=6131 DF PROTO=2 
bobh@Harvey14:~> 

and this on a kernel that refuses to mount my sony walkman mp3 player because it mis-reports the size.

I will report back on the Ubuntu machine tomorrow.

---

### Post by bobharvey on 2008-12-16
> **bobharvey said:**
> I will report back on the Ubuntu machine tomorrow.

Well, it certainly does not work on Ubuntu 8.10 at all.

Herewith the log entry.

> 
usb 1-5: new high speed USB device using ehci_hcd and address 5
usb 1-5: configuration #2 chosen from 1 choice
scsi11 : SCSI emulation for USB Mass Storage devices
scsi 11:0:0:0: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
scsi 11:0:0:1: Direct-Access     Sony Eri Memory Stick        0 PQ: 0 ANSI: 0
sd 11:0:0:0: [sdf] 368493 512-byte hardware sectors (189 MB)
sd 11:0:0:0: [sdf] Test WP failed, assume Write Enabled
sd 11:0:0:0: [sdf] 368493 512-byte hardware sectors (189 MB)
sd 11:0:0:0: [sdf] Test WP failed, assume Write Enabled
 sdf: sdf1
sd 11:0:0:0: [sdf] Attached SCSI removable disk
sd 11:0:0:0: Attached scsi generic sg7 type 0
sd 11:0:0:1: [sdg] Attached SCSI removable disk
sd 11:0:0:1: Attached scsi generic sg8 type 0
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
sd 11:0:0:0: [sdf] Sense Key : No Sense [current] 
sd 11:0:0:0: [sdf] Add. Sense: No additional sense information
The two repeating lines repeat indefinitely

But since it works on Suse, it seems unfair to blame the whole of Linux.

---

### Post by adam_kimber on 2008-12-16
Can you give me the uname -a results from your Suse box and the Ubuntu box. If the kernels are an exact match then it must be something to do with a module.

---

### Post by bobharvey on 2008-12-16
> **adam_kimber said:**
> Can you give me the uname -a results from your Suse box and the Ubuntu box. If the kernels are an exact match then it must be something to do with a module.

Ubuntu:
Linux Harvey10 2.6.27-8-generic #1 SMP Thu Nov 6 17:33:54 UTC 2008 i686 GNU/Linux

OpenSuse:
Linux Harvey14 2.6.25-18-0.2-pae #1 SMP 2008-10-21 16:30:26 UTC i686 i386 GNU/Linux

---

### Post by bobharvey on 2008-12-18
> **adam_kimber said:**
> Phone mode worked in Hardy too! What software are you using to talk to it in phone mode?

---

### Post by noteviljoe on 2008-12-19
Just read through this hoping that it would come to a solution at the end :-(

I'm just testing out Ubuntu at the moment. should this issue put me off? 

I suppose I could just set up a duel boot system and use windows everytime I want to load music on to my phone.

On the issue of the m2 card. My m2 card came with a little SD adapter.

Now to try my archos media play I hope that works [-o<

---

### Post by sim_thomas96 on 2008-12-27
Well, my new SE C902 doesnt work with my Ubuntu laptop, whereas K800i do. Browsing files on the device doesnt work whereas sending do. I think that the only solutions to this are: 

1. Use Windows for receiving.
2. Send files to spare mobile that works and use spare mobile for receiving.
3. Host files online, but on Pay as you Go it would cost A LOT!
4. Install the software from older mobile, which is dangerous and makes you lose your guarantee.

---

### Post by Tsume on 2009-01-07
> **bobharvey said:**
> Ubuntu:
Linux Harvey10 2.6.27-8-generic #1 SMP Thu Nov 6 17:33:54 UTC 2008 i686 GNU/Linux

OpenSuse:
Linux Harvey14 2.6.25-18-0.2-pae #1 SMP 2008-10-21 16:30:26 UTC i686 i386 GNU/Linux

They broke it sometime between 2.6.26 and 2.6.27 I believe.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960) (bug says nokia 5310 but it affects many more devices than that, including my iomega external hdd)

---

### Post by adam_kimber on 2009-01-07
> **Tsume said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960) (bug says nokia 5310 but it affects many more devices than that, including my iomega external hdd)

Thank you Tsume! The mount now works....

The above link contains a further link to a file from a previous version. 

If you replace the ```
60-persistent-storage.rules
``` file in the ```
 /etc/udev/rules.d
``` directory with that file (rename from 65 to 60) the mount works perfectly. 

I have attached that file (and have renamed it). Hope it helps others. If it does work post here and we might have a viable solution. 

NOTE: This file is from an older version of Ubuntu/Linux and therefore might break other stuff. :(

---

### Post by adam_kimber on 2009-01-08
> **sim_thomas96 said:**
> Well, my new SE C902 doesnt work with my Ubuntu laptop, whereas K800i do. Browsing files on the device doesnt work whereas sending do. I think that the only solutions to this are: 

1. Use Windows for receiving.
2. Send files to spare mobile that works and use spare mobile for receiving.
3. Host files online, but on Pay as you Go it would cost A LOT!
4. Install the software from older mobile, which is dangerous and makes you lose your guarantee.

Hi! 

In esponse to your comments 

1) MTP mode works fine without adjustments, So you can send and receive pictures and MP3s. 

2) Bluetooth OBEX send from phone to PC should work for this. 

3) Not quite sure why your would want to do this. Its slooooow. :D 

4) I have unbranded all my previous phones and this takes time. Not for the faint hearted.

Try out the patch in my post above to see if that works!

---

### Post by adam_kimber on 2009-01-08
> **bobharvey said:**
> What software are you using to talk to it in phone mode?

In Intrepid I just plugged in the phone and off it went with a pop up saying configure mobile broadband! Selected my network and presto. Sending and receiving data via the phone though you have to change an option on the phone under ```
 Settings --> Connectivity --> USB --> USB Network --> USB network type
``` to ```
Phone as Modem
```

Also more of interest for those who cannot use Mass Storage, phone mode also pops up a window with access to both memory card and phone.

---

### Post by scorpfromhell on 2009-01-23
> **adam_kimber said:**
> 

I have attached that file (and have renamed it). Hope it helps others. If it does work post here and we might have a viable solution. 

NOTE: This file is from an older version of Ubuntu/Linux and therefore might break other stuff. :(

Thanks a lot for the file! Now my C702 works in Mass Storage mode too! :D Dont know if this has broken anything else.

Thanks a bunch again :popcorn:

Regards,
Prem

---

### Post by Maneta on 2009-02-04
> **adam_kimber said:**
> Thank you Tsume! The mount now works....

The above link contains a further link to a file from a previous version. 

If you replace the ```
60-persistent-storage.rules
``` file in the ```
 /etc/udev/rules.d
``` directory with that file (rename from 65 to 60) the mount works perfectly. 

I have attached that file (and have renamed it). Hope it helps others. If it does work post here and we might have a viable solution. 

NOTE: This file is from an older version of Ubuntu/Linux and therefore might break other stuff. :(

Hey Man!

Thanks a lot! this has worked for me on my C702

Best Regards,

Maneta

---

### Post by compeanansi on 2009-02-14
> **adam_kimber said:**
> Thank you Tsume! The mount now works....

The above link contains a further link to a file from a previous version. 

If you replace the ```
60-persistent-storage.rules
``` file in the ```
 /etc/udev/rules.d
``` directory with that file (rename from 65 to 60) the mount works perfectly. 

I have attached that file (and have renamed it). Hope it helps others. If it does work post here and we might have a viable solution. 

NOTE: This file is from an older version of Ubuntu/Linux and therefore might break other stuff. :(
nice one!
finally my c902 works in a mass storage mode :)

---

### Post by ThespWill on 2009-02-17
Hurrah - I can access the C902. I've kept the old .rules file though - just in case ;)

A word of caution though - I managed to brick my old sony phone by not being careful when unmounting it - thing seems to be a bit more sensitive than other storage devices.

Thanks again.

---

### Post by Carl H on 2009-02-27
> **adam_kimber said:**
> If you replace the ```
60-persistent-storage.rules
``` file in the ```
 /etc/udev/rules.d
``` directory with that file (rename from 65 to 60) the mount works perfectly. 

I have attached that file (and have renamed it). Hope it helps others. If it does work post here and we might have a viable solution. 

This works for me too. Nice one, thank you. :guitar:

---

### Post by aminurmi on 2009-03-03
hello :)

thanks a lot :)

it works under gentoo 2.6.28-r2 perfectly too :)

(with the massstorage option)

best greetings !

siggi:D

Edit: hmm it works but only for the internal 189MB of the cellphone and not for the 1GB sony-flashcard where I store all my phonestuff :(

---

### Post by Walldorf2000 on 2009-03-03
> **aminurmi said:**
> hello :)

thanks a lot :)

it works under gentoo 2.6.28-r2 perfectly too :)

(with the massstorage option)

best greetings !

siggi:DWith or without any additional modifications?

---

### Post by letorbi on 2009-03-20
Thx Adam for your work!

the old 60-persistent-storage.rules you've found work's like a charm. finally I can access both internal and additional memory of my C902.

I wonder if anyone has posted a bug report for ubuntu, yet. It would be great if this issue is fixed out of the box in the next release. It doesn't seem to bee too complicated to fix this now it is clear where the problem lies, therfore I think there's a good chance this fix could be included in the next release already...

I think Adam should post the bug, since he's the guy who finally solved it. However, if it's ok, i can post it anyway...

bai

---

### Post by adam_kimber on 2009-03-24
> **letorbi said:**
> .

I think Adam should post the bug, since he's the guy who finally solved it. However, if it's ok, i can post it anyway...

bai

[Bug submitted]("https://bugs.launchpad.net/ubuntu/+bug/318939"). Though not much happening with it. I need to work on a patch and submit that. The will be a trial and error procedure to establish what in the new file actually broke. 

This is what I have so far. A file containing the changes from one to the other and a file with what has been added in the new one. (Where I refer to new I mean the updated broken file in Intrepid that is newer than the one in my previous post). 

ADDED TO NEW FILE (INTREPID FILE)
```
# forward scsi device event to corresponding block device
ACTION=="change", SUBSYSTEM=="scsi", ENV{DEVTYPE}=="scsi_device", TEST=="block", ATTR{block/*/uevent}="change"
```
from top of file. 

ALTERED FROM OLD FILE (WORKING) TO NEW FILE (INTREPID FILE)
```
WORKING 
<<<<>>>> 
INTREPID (NOT WORKING)

ACTION!="add", GOTO="persistent_storage_end" 
<<<<>>>> 
ACTION!="add|change", GOTO="persistent_storage_end"

# ignore partitions that span the entire disk
ATTR{whole_disk}=="*", GOTO="persistent_storage_end" 
<<<<>>>> 
# ignore partitions that span the entire disk
TEST=="whole_disk", GOTO="persistent_storage_end"

KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted --fallback-to-sysfs -s %p -d $tempnode"
KERNEL=="cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted --ignore-sysfs -s %p -d $tempnode", ENV{ID_BUS}="cciss"
<<<<>>>> 
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted -d $tempnode", ENV{ID_BUS}="scsi"
KERNEL=="cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted -d $tempnode", ENV{ID_BUS}="cciss"

KERNEL=="sr*", GOTO="persistent_storage_end"
KERNEL=="hd*[!0-9]", ATTR{removable}=="1", GOTO="persistent_storage_end"
<<<<>>>> 
# skip unpartitioned removable media devices from drivers which do not send "change" events
ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"
# skip optical drives without media
ENV{DEVTYPE}=="disk", KERNEL=="sr*", ENV{ID_CDROM_MEDIA_TRACK_COUNT}!="?*", GOTO="persistent_storage_end"

ENV{DEVTYPE}=="partition", IMPORT{program}="vol_id --export $tempnode"
<<<<>>>>
# import filesystem metadata
IMPORT{program}="vol_id --export $tempnode"
```

Currently this means very little to me.... Time to swot up I think. :D

---

### Post by adam_kimber on 2009-03-26
> **adam_kimber said:**
> [Bug submitted]("https://bugs.launchpad.net/ubuntu/+bug/318939"). Though not much happening with it. I need to work on a patch and submit that.D

Updated bug report and assigned to myself. It is now confirmed! Once I have sorted the cuase of the problem I can create a patch for you guys to try. If that works I can submit it to upstream.

Has anyone tried a 'vanilla' Jaunty with this phone? Apparantly, the bugs in unsual_devs and various other udev bugs have been rectified. if so I won't need to work on this anymore?

---

### Post by maverick340 on 2009-04-17
> **Maneta said:**
> Hey Man!

Thanks a lot! this has worked for me on my C702

Best Regards,

Maneta

> **adam_kimber said:**
> Thank you Tsume! The mount now works....

The above link contains a further link to a file from a previous version. 

If you replace the ```
60-persistent-storage.rules
``` file in the ```
 /etc/udev/rules.d
``` directory with that file (rename from 65 to 60) the mount works perfectly. 

I have attached that file (and have renamed it). Hope it helps others. If it does work post here and we might have a viable solution. 

NOTE: This file is from an older version of Ubuntu/Linux and therefore might break other stuff. :(

Thanks! Worked for my Sony Ericsson T700 too :-)
Damn updated kernel made a boo-boo !

---

### Post by rrsn on 2009-04-27
> **adam_kimber said:**
> Thank you Tsume! The mount now works....

The above link contains a further link to a file from a previous version. 

If you replace the ```
60-persistent-storage.rules
``` file in the ```
 /etc/udev/rules.d
``` directory with that file (rename from 65 to 60) the mount works perfectly. 

I have attached that file (and have renamed it). Hope it helps others. If it does work post here and we might have a viable solution. 

NOTE: This file is from an older version of Ubuntu/Linux and therefore might break other stuff. :(

Hey Adam Kimber, tks a lot, My C902 works perfect on my Ubuntu 8.10. 
I'll have any problem in the future? do you know?

---

### Post by adam_kimber on 2009-04-27
> **rrsn said:**
> I'll have any problem in the future? do you know?

Yup. You will have to replace the 60 rules file everytime you reinstall the OS. 

NOTE:

A fresh install of Jaunty does not have the 60 rules file and guess what? Mass storage does not work. But hey guess again? The 60 rules file works in Jaunty (for me) too!

---

### Post by maverick340 on 2009-05-03
> **adam_kimber said:**
> Yup. You will have to replace the 60 rules file everytime you reinstall the OS. 

NOTE:

A fresh install of Jaunty does not have the 60 rules file and guess what? Mass storage does not work. But hey guess again? The 60 rules file works in Jaunty (for me) too!
So the phone's mass storage works on a vanilla jaunty ? Think there is some mistake in your line above :)

---

### Post by adam_kimber on 2009-05-03
> **maverick340 said:**
> So the phone's mass storage works on a vanilla jaunty ? Think there is some mistake in your line above :)

Oops. If it was not clear. C902 does NOT work on a vanilla Jaunty install.

 If you use the previously posted 60 rules file it DOES work! 

Hope that clears things up!

---

### Post by JohnDawg25 on 2009-05-04
I managed to get this problem fixed in Jaunty for my tm506.  Thanks for all the advice on editing the kernel.  I edited a kernel, rebuilt it, and it works perfect now.  Should I send a patch to the unusual-devs maintainer, and send the .deb of my custom kernel to the debian maintainers?  It reminds me of a time when the kernel didn't recognize the joystick port on my SoundBlaster clone, way back in 96 or thereabouts.  I emailed my patch to the kernel maintainer in charge of the joystick, he emailed me thanking me and that he would put it in the next version, and lo and behold the next version came out, I compiled it, and it broke my joystick.  I emailed him and he acted like I was a green-skinned man from mars and he had no clue what I was talking about. So I patched it again and decided to forget about sending patches to him.  I just patched every new kernel I installed on that slackware system. :)

---

### Post by maverick340 on 2009-05-08
John, Maybe you could assign the bug to yourself and try to fix it ? :-)

---

### Post by maverick340 on 2009-06-10
How do you fix this in Jaunty now ? The rules.d/ folder has only two files 
70-persistent-cd.rules  70-persistent-net.rules
The media storage mode seems to be working with fspot. Howerver nautilus shows three devices now and none of them are mountable (gives error)

---

### Post by adam_kimber on 2009-06-10
> **JohnDawg25 said:**
> . So I patched it again and decided to forget about sending patches to him. 

Unfortunately I attempted to get a few things straightened out with Unusual Devs file and other patches for the C902 mounting problem with the package devs. I think they are extremely busy and also your patch might only work for you. 

Opening a bug and solving it might give others the opportunity to test it. Once multiples are confirmed the bug tracking system should automagically add confirmed solutions to the distro. That way direct interaction is not required! :D

---

### Post by adam_kimber on 2009-06-10
> **maverick340 said:**
> How do you fix this in Jaunty now ? The rules.d/ folder has only two files 
70-persistent-cd.rules  70-persistent-net.rules
The media storage mode seems to be working with fspot. Howerver nautilus shows three devices now and none of them are mountable (gives error)

Copy the 60 rules file previously posting without renaming it to the rules.d folder. That will allow for mass storage mode to work. The C902 should work out of the box with all other modes without this file. I have used my phone as a 3G modem without any tweaks whatsoever.

---

### Post by amksep on 2009-07-19
I had the same problem with my w595.
I just used the update service in my phone to update its software.

Now..Everything works perfect.

Note: I set my USB connectivity mode to mass storage.

Hope this will help you with C902.

---

### Post by rileyrg on 2009-10-06
> **adam_kimber said:**
> Thank you Tsume! The mount now works....

The above link contains a further link to a file from a previous version. 

If you replace the ```
60-persistent-storage.rules
``` file in the ```
 /etc/udev/rules.d
``` directory with that file (rename from 65 to 60) the mount works perfectly. 

I have attached that file (and have renamed it). Hope it helps others. If it does work post here and we might have a viable solution. 

NOTE: This file is from an older version of Ubuntu/Linux and therefore might break other stuff. :(

Wonderful.

This also fixed Debian Lenny mounting a W760i.

---

### Post by Khushboo_khan on 2009-10-08
hi
i am new to ubuntu.. and i am facing the same problem. i have sonyericsson C905. it works good at windows PC but creating trouble in accesing memory card. please help me??

---

### Post by Graham A on 2009-11-26
I rarely post but I was suffering this problem. Sorry if I'm reviving a dead thread.

I have a Sony Ericsson C902 and I'm currently using Kubuntu Intrepid. I was suffering a problem mounting the phone in Mass Storage mode.

```
[13194.643895] sd 7:0:0:1: [sdc] Sense Key : No Sense [current]             
[13194.643899] sd 7:0:0:1: [sdc] Add. Sense: No additional sense information
[13194.645770] sd 7:0:0:0: [sdb] Sense Key : No Sense [current]             
[13194.645774] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information

```

I'm pleased to say that replacing **/etc/udev/rules.d/60-persistent-storage.rules** has fixed this error for me and the device now mounts as Mass Storage both Internal and 2GB M2 memory card.

I haven't tried phone mode or media transfer, if there's anything I can do to help with the issue I'd be happy to support the fix.

---

### Post by Graham A on 2009-11-30
And it's broken!

Recently changed from KDE to Gnome, as such I'm now on Ubuntu 9.10. I'm back to the original error of:
```
[ 5600.462497] sd 7:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 5600.462500] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 5600.472871] sd 7:0:0:1: [sdc] Sense Key : No Sense [current] 
[ 5600.472875] sd 7:0:0:1: [sdc] Add. Sense: No additional sense information

```

Nautilus seems to see it, I'm presented in computer:/// with cake  I've put the 60-persistent-storage.rules in the rules.d folder but it doesn't seem to be working correctly. Renaming it 70-persistent-storage.rules doesn't seem to have helped.

---

### Post by K-Veikko on 2009-12-22
> **adam_kimber said:**
> If you replace the ```
60-persistent-storage.rules
``` file in the ```
 /etc/udev/rules.d
``` directory with that file (rename from 65 to 60) the mount works perfectly.

This Helped me with ubuntu 9.04. - Just added the file because there was no file with that name.
[http://georgia.ubuntuforums.org/showpost.php?p=6513274&postcount=75](http://georgia.ubuntuforums.org/showpost.php?p=6513274&postcount=75)

See also
[http://georgia.ubuntuforums.org/showpost.php?p=6518070&postcount=77](http://georgia.ubuntuforums.org/showpost.php?p=6518070&postcount=77)

---

### Post by pabc on 2010-03-26
I too couldnt mount my C902 on 9.04 or 9.10

I'm running Lucid 10.04 Beta 1 and just plugged it in on the off-chance and voila - success.

it automounted the phone and the 4GB card as 2 mount points once I'd selected mass storage on the device.

---

### Post by canadiandude007 on 2010-12-18
Here's how to get pics/videos off your phone.

```

sudo apt-get install mtpfs
sudo apt-get install mtp-tools

```

If you don't have f-spot installed, then do this:
```

sudo apt-get install f-spot

```

Once those packages are installed, connect your c902 to Ubuntu (I'm using 10.04) and open F-Spot, then click on 'Import' and for Import Source choose 'MTP Device'.

Find your pics/vids and select 'Import'.

This will then copy them all (can select videos even though won't be viewed using F-Spot) to folder on Ubuntu (mine was Pictures -> Photos, then had them listed by date).

Hope that helps!

---

