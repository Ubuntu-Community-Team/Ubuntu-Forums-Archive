---
title: "Live USB 4GB format problems"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by verybadsector on 2011-11-29
I have hard times trying to make a working ubuntu (11.10) live usb stick (in windows xp):

- downloaded the latest 11.10 iso from ubuntu.
- tried to make a Live USB by using Universal-USB-Installer-1.8.7.1(pendrivelinux) and LinuxLiveUSBCreator (LiLi) 2.8.7, on Kingmax 1GB Stick, **FAT32** formatted - can't boot

- formatted the same stick to **FAT** (instead of FAT32) and i managed to make a bootable (live mode only - no persistance) usb stick with LiLi. 
It boots Ubuntu much faster then livecd does. 

- but then i wanted to have a persistent bootable drive as well, and this one (of 1gb) is too small for that.
So i tried the same procedure with a new 4GB Verbatim stick, but i had to preformat it in FAT inside live ubuntu with gparted (since windows has a _limit of 2GB_ for FAT formatting).
I formatted it to FAT in ubuntu (booted from the previous 1GB stick), installed No-persistance live usb in windows (as a test, to see would the larger FAT formated stick work in live mode only /without persistence/ in the first place) and it worked perfectly well.

Then i deleted the content and installed Live Usb _WITH Persistence_ via LiLi.
But when i tried to boot ubuntu, i got a terminal window with ubuntu@ubuntu~1: prompt.
Then i repeated the procedure (including fat format in ubuntu), this time with pendrivelinux-UniversalUSBInstaller, and it managed to boot, but i got user/password prompt and i didn't know (at the time) what to put in, so after several trial/errors i turned the system off.

Next time boot just hung. 
When i tried to reformat the stick one more time inside ubuntu (gparted), it saw the stick as unallocated space and it reported (if i remember correctly) non-existent file allocation table, and offered to Repair it.
I accepted, and subsequently formatted the stick normally to FAT again.

FROM THEN ON, whatever i do with this stick (in any mode), ubuntu boot hangs after several lines:
```
USB Storage Device : VerbatimStore n Go Drive1100
IDE Channel 0 . Master Disk HDD S.M:A:R:T: capability .... Disabled

PCI Devices Listing... 
Bus Dev Fun Vendor SVID SSID Class Device Class  IRQ
.
. 
                                  ACPI Controller  9
```12th device is "ACPI Controller irq 9" /but no Bus Dev Fun Vendor SVID SSID Class Device Class/ 

What happened to my 4GB stick?

(Just to see is it still alive i reformated it back in FAT32 in Windows, and put some files in it successfully.)

Thanks a lot in advance

---

### Post by BC59 on 2011-11-29
Try unetbootin for Windows.

---

### Post by searchfgold6789 on 2011-11-29
Try using the Startup disk creator tool in Ubuntu *from the live cd* instead of going through all that hassle. All you do is boot from the live cd, open the USB creator program, select your thumb drive and press "erase", select your persistence and then you're good to go. It copies all the files right off the CD, or an .iso file if you want to.
 - search

---

### Post by verybadsector on 2011-11-29
Thank you both so much for the extremely prompt answers.

I'll try the both suggestions at once..

---

### Post by verybadsector on 2011-11-29
Unetbootin failed.. the same effect as with LiLi and UniversalUsbInstaller.

I'll try now with Startup Disk Creator in Ubuntu.
Which file system should i choose? I'll try ext3..

---

### Post by verybadsector on 2011-11-29
I have an ubuntu iso image on a (ntfs) drive, but when i point its path as a "source disk image" in Startup Disk Creator in Ubuntu (and my second (4gb)usb drive as a "disk to use"), the **Make Startup Disk** button along with "reserved extra space" slider stays grayed out / inactive... :(

edit:
Sorry, haven't **erased** the disk... my bad.
Now the installation is going.
I will report results.

---

### Post by BC59 on 2011-11-29
Then go here and try to check the integrity of the .iso file


[http://ubuntuforums.org/showthread.php?t=290339](http://ubuntuforums.org/showthread.php?t=290339)

---

### Post by verybadsector on 2011-11-29
Startup disk creator finished installation successfully on my 4GB usb drive with the message "you can now boot with this disk on other computers"..

But **it cannot boot**.. it's ignored and boot goes to Windows (on my hard disk, as a second boot device). ](*,)
Could it be because of **ext3** file system to which i formatted the usb stick prior to installation? (i've noticed that disk creator formated persistent file as **ext2**)

I'm not sure i should check integrity of the ubuntu iso, as i already have one working live usb installation from very that iso, on another 1GB usb drive.

---

### Post by Paddy Landau on 2011-11-29
> **verybadsector said:**
> I'm not sure i should check integrity of the ubuntu iso, as i already have one working live usb installation from very that iso, on another 1GB usb drive.
Check the integrity anyway. There may be a corrupt driver that affects the persistent USB but not the other.

That's probably not the problem, but it's best to check the fundamental first to rule it out.

---

### Post by BC59 on 2011-11-29
Then you have to be concentrated to the USB pen drive. Are you sure it's ok?

---

### Post by Scott Baker on 2011-11-29
Howdy live sector, hope this will help. First, if your comp is booting to windows first, you'll want to check your BIOS settings to make sure that your machine will check for the USB stick first. You'll want to make sure that's done first. Next, DON'T try to put your UBUNTU on a 1gig stick. As you've discovered, it's normally a problem. Minimum should be 2gig, with 4 or more being better. Based on what you've shared, that it was indicated that you have a bootable USB drive, you should be able to reboot your comp to UBUNTU after the adjustments to your BIOS. ( BTW, to adjust your BIOS settings, you'll need to find your comps information online to see how to access your particular machines BIOS set-up program ) Hope this helps.

---

### Post by verybadsector on 2011-11-29
@[Paddy Landau]("http://ubuntuforums.org/member.php?u=572807")
Where can i find ubuntu iso checksum ?

@[BC59]("http://ubuntuforums.org/member.php?u=1498360")
Well this usb pen drive works ok in windows (as a storage).

At first i managed to install non-persistent live ubuntu on it with Lili, but problems started when i installed a new persistent installation (problems like terminal window at start, and it even managed to boot once (install by UniversalUsbCreator) but i didn't know user/password).

But since i allowed Ubuntu to REPAIR its file allocation table (it was the first time that ubuntu saw the drive as an unallocated space), it hangs at the very beginning of boot process (at black screen and several checking lines).
Since then, it's completely dead for linux boot, whatever i try to do.

---

### Post by verybadsector on 2011-11-29
My boot sequence has been set in bios correctly (usb-hdd as a first boot device), and i can boot with my 1GB in ubuntu without a problem.
The only thing i had to change with it is to reformat it as FAT instead of FAT32 (as fat32 it didn't boot /i guess a hardware issue with my comp/).

My 1GB live usb (live-only mode) works ok, and i actually use it all the time too boot in linux, for formatting the other one of 4GB.

As for "Howdy live sector", what does it actually mean? I'm completely new to linux.
LOL

edit:
Could the problem be with sector size on my 4GB FAT drive?
[http://www.syslinux.org/archives/2007-March/008284.html](http://www.syslinux.org/archives/2007-March/008284.html)
Can i change it using gparted?

---

### Post by Paddy Landau on 2011-11-29
Oh, and it's OK to format the USB stick as FAT32. That is the normal (and expected) way to do it.

---

### Post by verybadsector on 2011-11-30
I've managed to boot ubuntu with the 4GB FAT32 formatted live usb (the same Verbatim stick) on 2 other computers. But definitely on my Gigabyte mb with 945 chipset i'm able to boot only with 1GB stick formatted in FAT.

---

### Post by oklokl on 2011-11-30
I was the same
 Unexplained
 Please install from Linux os
 Installation on another computer
 But
 usb does not recommend
 cd-rom recommendations

&#54620;&#44397;&#50612;&#47196;&#46020; &#50416;&#44192;&#49845;&#45768;&#45796;..
&#51200;&#51032; &#44221;&#50864;&#46020; usb&#47196; &#50952;&#46020;&#50864;(windows)&#50640;&#49436;
&#51208;&#45824; &#48512;&#54021;(booting no start)&#46104;&#45716; &#54788;&#49345;&#51060; &#51068;&#50612; &#45228;&#49845;&#45768;&#45796;..
Fat32 &#46608;&#45716; Fat&#47196; &#54616;&#50688;&#51648;&#47564; mbr &#44620;&#51648; &#49352;&#47196; &#49444;&#51221; &#54644;&#51452;&#50632;&#51648;&#47564; &#46104;&#51648; &#50506;&#50520;&#49845;&#45768;&#45796;..
&#51060;&#50976;&#45716; &#50508;&#49688; &#50630;&#51648;&#47564; &#50952;&#46020;&#50864;&#50640; &#44628;&#47536; &#47924;&#50631; &#51064;&#44032;&#44032; &#48169;&#54644;&#47484; &#54616;&#45716; &#44163; &#44057;&#50520;&#49845;&#45768;&#45796;..
&#51204; &#44536;&#47000;&#49436; cd-rom&#51004;&#47196; &#49444;&#52824;&#47484; &#44200;&#50864; &#54616;&#50688;&#49845;&#45768;&#45796;..
&#44536;&#47000;&#49436; &#51204; cd-rom&#51012; &#52628;&#52380; &#54633;&#45768;&#45796;..

&#52628;&#52380; &#45796;&#47480; &#52980;&#54504;&#53552; &#50640;&#49436; &#49444;&#52824; &#54616;&#49884;&#44600; &#44428;&#54633;&#45768;&#45796;
&#47532;&#45573;&#49828;&#44032; &#46104;&#46020;&#47197; &#44628;&#47536; &#52980;&#54504;&#53552;&#44032; &#51339;&#49845;&#45768;&#45796; 
&#54665;&#50868;&#51012; &#48716;&#50612;&#50836;

---

### Post by verybadsector on 2011-11-30
Yes, i also tried to install it from another live usb ubuntu, and also from a live cd, to no avail.
4GB fat32 usb just cannot boot on 945 chipset (only 1Gb FAT).

Live cd is not an option for me, because i need persistence.

---

### Post by BC59 on 2011-11-30
Check the Ubuntu documentation because there are some issues with the USB stick.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by I2k4 on 2011-11-30
I've experimented with half a dozen recent versions of Ubuntu, and other supported distros,  using the Pendrive installer, and found Ubuntu's step-by-step instructions bullet proof:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

The one additional step (at end of Ubuntu's "Show me how" Step 2) is setting Persistence, and on a 4GB USB I'd set it to around 2.5GB with the slider - that will handle the new, fatter 11.x builds, you can set 3GB Persistence if you're using 10.x versions.  If your system can boot from the USB (older system's can't) and is properly set for USB boot priority in BIOS, this should work fine.

That said, I've found Live USB starts out great but gets a little flaky over a few weeks of use.  I'm hoping my dual boot on my little netbook will be reliable and consistent enough to convince me to install it on my main machine.

---

