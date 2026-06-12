---
title: "Digital Camera not recognised after installing 14.04"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by hunterrjh on 2014-04-24
I have a Canon SX280 hs and I had not problems with 13.10, after a clean install of 14.04, system is not recognising camera when I plug it into the USB port.

---

### Post by Larry_Laird on 2014-04-24
Add me to the list. Same situation, new install of 14.04 64 bit and software doesn't see the camera. Always worked in 12.04. The stick can be accessed outside the camera. Camera is a Canon Powershot A2500.

---

### Post by a-web on 2014-04-25
Dito.  Same problem, different camera.  Any advice out there?

---

### Post by monkeybrain20122 on 2014-04-25
Maybe a kernel problem. Can you install a 13.10 kernel and boot into it to see if the cam works?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by hunterrjh on 2014-05-02
> **hunterrjh said:**
> I have a Canon SX280 hs and I had not problems with 13.10, after a clean install of 14.04, system is not recognising camera when I plug it into the USB port.

My son-in-law just had a look at terminal entries, and whilst he could not fix the problem, suggested that I post the following from the terminal entry.
28796.385058] usb 2-5: Product: Canon Digital Camera
[28796.385060] usb 2-5: Manufacturer: Canon Inc.
[28796.385063] usb 2-5: SerialNumber: 8A73E0608A1247DBB0E12BC9F2EF8781
[28821.729133] usb 2-5: USB disconnect, device number 17
[34983.376069] usb 2-5: new high-speed USB device number 18 using ehci-pci
[34983.509079] usb 2-5: New USB device found, idVendor=04a9, idProduct=325f
[34983.509085] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3

Does this help at all?  I have no idea

---

### Post by ibjsb4 on 2014-05-02
I have notice that canon cameras are about the only cameras that I ever see in the forums.  I have never had anyone come to me with a canon camera and this problem, but in the pass I have had this problem with other brands.  

I have found a work-a-round for other camera brands. A program called Shotwell for some reason will see these cameras when ubuntu cannot.  I do not know if this will work for canon, but maybe its worth a try.

[http://packages.ubuntu.com/trusty/shotwell](http://packages.ubuntu.com/trusty/shotwell)

---

### Post by hunterrjh on 2014-05-02
I am using Shotwell, but problem persists

---

### Post by Grendel336 on 2014-05-04
I have a Nikon coolpix point & shoot camera. Same problem. Shotwell did not work for me. 
Previous releases of Ubuntu and Mint both mounted camera without issues.

---

### Post by Dangerous Curves on 2014-05-17
I have a Fujifilm Finepix F500 with the same problem. Shotwell doesn't see it either. It worked fine in previous version.

---

### Post by JeQhdMD on 2014-05-17
This is a known bug in Ubuntu 14.04.  See Launchpad link:   [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1296275]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1296275")

I don't know if this has a "top priority"(although it is rated "high", and may be a gnome bug) re the fix. 

The temporary work-around is easy (i.e., popping out the media card (sd, xd, mcsd . .) and inserting it to either a builti in reader (which almost all pc's, tablets now have), or just using an older media card hub device from your closet or shoebox.  ;)

When inserted, the photos can be imported via shotwell, digikam, or a host of other installed software.   This is sometimes a better method than attaching a clunky usb cable>camera>usb port and also allows actual admin of the files (via properties or command line).

BTW, IF you're prefering the camera mount method because of USB battery recharging, there are better ways (via portable ac-usb recharger).

---

### Post by impliedconsent2 on 2014-05-17
No issues with Nikon S8100

```
Manufacturer: Nikon Corporation
Model: S8100
  Version: COOLPIX S8100V1.1
  Serial Number: xxxxxxxxxxxxx
Vendor Extension ID: 0xa (1.0)
Vendor Extension Description: microsoft.com: 1.0; 


Capture Formats: JPEG
Display Formats: Undefined Type, JPEG, Association/Directory, DPOF, MS Wave, Apple Quicktime, Defined Type


Device Capabilities:
    File Download, File Deletion, File Upload
    Generic Image Capture, No Open Capture, No vendor specific capture


Storage Devices Summary:
store_00010001:
    StorageDescription: None
    VolumeLabel: None
    Storage Type: Removable RAM (memory card)
    Filesystemtype: Digital Camera Layout (DCIM)
    Access Capability: Read-Write
    Maximum Capability: 32450281472 (30947 MB)
    Free Space (Bytes): 32271532032 (30776 MB)
    Free Space (Images): 5323


Device Property Summary:
Battery Level(0x5001):(read only) (type=0x2) Enumeration [2,5,25,50,65,80,100] value: 100% (100)
Date & Time(0x5011):(readwrite) (type=0xffff) '20140517T132106'
Property 0xd005:(read only) (type=0x4) Enumeration [1,2] value: 1
Property 0xd280:(read only) (type=0x2) 3
Property 0xd407:(read only) (type=0x6) 1
Property 0xd303:(read only) (type=0x2) 1

```

---

### Post by evanherk on 2014-06-17
I also have a Canon (ixus 510 HS) camera that is not recognized on the USB connection after upgrading to 14.04. My several other cameras not from Canon are recognized with no problems.

---

### Post by druidkat7 on 2014-07-02
Hi, all!

I, too, had issues with 14.04 and docking my Nikon Coolpix L22 (yes, I know, a 3-year-old camera) on my Dell Latitude D620. So far, other than the camera not being recognized (whereas with Quetzal, it WAS recognized), Trusty Tahr works great--so far. Yeah, I get an occasional screen lockup, but that doesn't happen too often. Plus I don't have one of those "laptop cooling pads,"
which doesn't help matters..

I DID see someone else have camera docking probs on the Dell Latitude D620 and its sister-systems and then the following suggestion to use an external media hub in which one can plug in the camera's memory card. Great advice, except, I'm one of the ones who doesn't have this sort of thing. Then I saw the suggestion to drop back to 13.08 (Saucy), which I don't have.

I DO however, have a copy of Raring Ringtail I have not even opened yet. Even if it is only short-term support, if I can get my camera to dock with that, I may use that OS until Ubuntu fixes the camera bug in Trusty Tahr. I might even find a disk of Mint 9 64-bit to try. ANYthing to get my camera to work on my computer--simply because I DO sell stuff on eBay and I want really good pics.

I will go and install Raring to see what happens and report back! Hopefully Trusty gets an update soon. :-)

---

### Post by squakie on 2014-07-02
Check launchpad.  This is a known bug and MANY have posted to the thread in launchpad.  Supposedly a fix has been made but I have yet to see it for 14.04.  This bug report also mentions adding a udev rule, but it didn't work for me.  I'd suggest anyone with these problems in 14.04 watch that bug report.

---

### Post by squakie on 2014-07-02
> **druidkat7 said:**
> Hi, all!

I, too, had issues with 14.04 and docking my Nikon Coolpix L22 (yes, I know, a 3-year-old camera) on my Dell Latitude D620. So far, other than the camera not being recognized (whereas with Quetzal, it WAS recognized), Trusty Tahr works great--so far. Yeah, I get an occasional screen lockup, but that doesn't happen too often. Plus I don't have one of those "laptop cooling pads,"
which doesn't help matters..

I DID see someone else have camera docking probs on the Dell Latitude D620 and its sister-systems and then the following suggestion to use an external media hub in which one can plug in the camera's memory card. Great advice, except, I'm one of the ones who doesn't have this sort of thing. Then I saw the suggestion to drop back to 13.08 (Saucy), which I don't have.

I DO however, have a copy of Raring Ringtail I have not even opened yet. Even if it is only short-term support, if I can get my camera to dock with that, I may use that OS until Ubuntu fixes the camera bug in Trusty Tahr. I might even find a disk of Mint 9 64-bit to try. ANYthing to get my camera to work on my computer--simply because I DO sell stuff on eBay and I want really good pics.

I will go and install Raring to see what happens and report back! Hopefully Trusty gets an update soon. :-)

You can try Mint, but keep in mind it's an Ubuntu derivitive - mainly the desktop manager is different.

---

### Post by Z80A on 2014-07-07
Aalong with many other users I was also affected by this bug and had to to use gphoto CLI to transfer images. The bug was fixed (a workaround) some time ago and the fix was distributed through regular software updates. Make sure you have all updates installed - works perfectly fine on my machines now.

```
This bug was fixed in the package libgphoto2 - 2.5.3.1-1ubuntu2.2

 ---------------
libgphoto2 (2.5.3.1-1ubuntu2.2) trusty-proposed; urgency=medium
   * Add debian/libgphoto2-6.udev: Provide rule for generic "PtP device" to
    unbreak cameras which aren't explicitly known to libgphoto by
    vendor/product ID, until either hwdb or gvfs get fixed properly.
    (LP: [#1296275]("https://bugs.launchpad.net/bugs/1296275"))
 -- Martin Pitt <email address hidden>   Tue, 10 Jun 2014 18:00:51 +0200
```

---

### Post by david266 on 2014-08-13
Have two different model Fuji Finepix camera's both worked perfectly in earlier versions of Kubuntu, 11, upwards. neither will work properly on 14.04.  Both appear to be mounted and picutures can be copied accross using Dolphin.  However using Digikam or other photo managers such as Shotwell, the preview is available but picutures fail to open. i.e. a small preview snap opens but when the picture is selected for viewing it will not open.  Nor can the cameras be managed, i.e files deleted or moved whereas all these functions worked in Digikam in earlier versions of Kubuntu. It's not a big 'deal' I'm simply transferring the pictures using Dolphin but it is a shame since Digikam worked perfectly in earlier versions of Kubuntu

---

