---
title: "Switch back to Windows"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-04-26
perhaps I'll have to switch back to windows.

When I plug my android phone into the computer via USB and try to open files with linux on my laptop I get the message "Failed to read from file '/media/40B2-AA14/00002.vcf': Input/output error"

It's the same for all files on the android sdcard.

In Dolphin the sdcard comes up as "Huawei Incorporated Ideos"
When I do 
usb-devices
 one of them reports:
T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1037 Rev=02.26
S:  Manufacturer=Huawei Incorporated
S:  Product=Ideos
S:  SerialNumber=xxxxxxxxxxxxxx
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

when I do mount, one of the results is:
/dev/sdc on /media/40B2-AA14 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
Maybe it's not mounted, I don't know. 

I can see the files on the sdcard but I can't open them or move them or anything.

---

### Post by llamabr on 2012-04-26
> **Kevin McCready said:**
> perhaps I'll have to switch back to windows.



Probably. But before you do, post the output of:
```
dmesg | tail
```
So at least we'll know what was going on.

---

### Post by Kevin McCready on 2012-04-26
[18928.897701] sr 7:0:0:1: rejecting I/O to offline device
[18928.897725] sr 7:0:0:1: rejecting I/O to offline device
[18930.897363] sr 7:0:0:1: rejecting I/O to offline device
[18930.897389] sr 7:0:0:1: rejecting I/O to offline device
[18932.895811] sr 7:0:0:1: rejecting I/O to offline device
[18932.895822] sr 7:0:0:1: rejecting I/O to offline device
[18934.895506] sr 7:0:0:1: rejecting I/O to offline device
[18934.895532] sr 7:0:0:1: rejecting I/O to offline device
[18936.894572] sr 7:0:0:1: rejecting I/O to offline device
[18936.894598] sr 7:0:0:1: rejecting I/O to offline device

---

### Post by anewguy on 2012-04-27
If you have enough CPU and memory, you could always install Virtualbox, run Windows as a virtual machine in it, and try accessing your phone.  It would just be a click away to the Windows window from the Linux desktop.

---

### Post by Rasa1111 on 2012-04-27
I never have issues connecting my android devices to my Ubuntu machines.

---

### Post by anewguy on 2012-04-27
> **Rasa1111 said:**
> I never have issues connecting my android devices to my Ubuntu machines.

And my eggs fry in a pan ---  both your post and this one do nothing to help the OP at all.

---

### Post by llamabr on 2012-04-27
What he meant was, plug in your phone, wait a second, and then run dmesg.  Then post the output.

---

### Post by Rasa1111 on 2012-04-28
> **anewguy said:**
> And my eggs fry in a pan ---  both your post and this one do nothing to help the OP at all.

lol, while true...
my purpose of posting it was to let others know that this is not "the norm". 
I know how people interpret (or misinterpret) things, and Im sure many would read this thread and think *"What? I can't connect an android device to an ubuntu machine?" *
So my post was to "counter" that thought, should it arise. 
and Im sure it would/will. 
So yeah, my post helped the OP none, but it may 'help' others who stumble upon this thread. 
):P

---

### Post by Kevin McCready on 2012-04-28
I plugged in adroid phone, waited a few secs then ran 
dmesg | tail
here's result:
[25962.109735] scsi7 : usb-storage 2-1.2:1.0
[25962.109900] usbcore: registered new interface driver usb-storage
[25962.109904] USB Mass Storage support registered.
[25963.108527] scsi 7:0:0:0: Direct-Access              Ideos            0000 PQ: 0 ANSI: 2
[25963.109092] scsi 7:0:0:1: CD-ROM                     Ideos            0000 PQ: 0 ANSI: 2
[25963.159975] sd 7:0:0:0: Attached scsi generic sg3 type 0
[25963.167604] sr1: scsi3-mmc drive: 0x/0x caddy
[25963.167720] sr 7:0:0:1: Attached scsi CD-ROM sr1
[25963.167913] sr 7:0:0:1: Attached scsi generic sg4 type 5
[25963.168629] sd 7:0:0:0: [sdc] Attached SCSI removable disk

I then waited a minute and on the android enabled the USB sharing. Then I again ran 
dmesg | tail
here's result:

[25963.167604] sr1: scsi3-mmc drive: 0x/0x caddy
[25963.167720] sr 7:0:0:1: Attached scsi CD-ROM sr1
[25963.167913] sr 7:0:0:1: Attached scsi generic sg4 type 5
[25963.168629] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[26103.120257] sd 7:0:0:0: [sdc] 62535680 512-byte logical blocks: (32.0 GB/29.8 GiB)
[26103.123373] sd 7:0:0:0: [sdc] Asking for cache data failed
[26103.123383] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[26103.128502] sd 7:0:0:0: [sdc] Asking for cache data failed
[26103.128511] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[26103.130824]  sdc:

---

### Post by FatFrog on 2012-04-28
Not that it matters much, but for the sake of knowing, what kind of phone is it?
I'm pretty sure there are some issues with Samsung Android devices and mounting them in Linux.

---

### Post by 3rdalbum on 2012-04-28
This is a Huawei Ideos, is it? What version of Android are you running?

If you take out the SD card and put it straight into the computer, does it work?

Does the phone connect properly to a Windows machine or another computer?

How about a different port on your computer - maybe a port on the back, and unplug anything non-essential. Could be an issue with power.

---

### Post by Kevin McCready on 2012-04-29
Yes it's Huawei Ideos. I've now discovered it's a variable fault. Sometimes it works, others it doesn't. Yes it's a common problem. Still no solution.

---

### Post by rgreener25 on 2012-04-29
just wondering have you tried plugging the memory card in via an adapter just so you could determine if it was actually the phone or if you have a dodgy memory card

---

### Post by Kevin McCready on 2012-04-30
It's a variable fault when I plug into Linux. No prob with windows. Huawei IDEOS U8150 Android 2.2. I haven't taken out the SD card to put it into a reader - it's quicker to use my wife's old bloated expensive legacy system.

---

### Post by QIII on 2012-04-30
Are both Windows and Linux on the same machine; i.e.:  dual boot?

---

### Post by RJARRRPCGP on 2012-04-30
> **Kevin McCready said:**
> Yes it's Huawei Ideos. I've now discovered it's a variable fault. Sometimes it works, others it doesn't. Yes it's a common problem. Still no solution.

Sounds like a dodgy USB port.

---

### Post by Kevin McCready on 2012-05-03
windows is on another machine.
I doubt if it's USB port because I get something all the time, just that sometimes I can look but not touch if you get my meaning.

---

### Post by QIII on 2012-05-03
If it's on another machine than windows and it is intermittent, you can't conclude it's the OS.  

I'll leave the innuendo alone.

---

### Post by llamabr on 2012-05-03
> **Kevin McCready said:**
> windows is on another machine.
I doubt if it's USB port because I get something all the time, just that sometimes I can look but not touch if you get my meaning.

This doesn't necessarily follow.  Even if the USB is seeing something, it may not have the power to connect.  Try:

```
rmmod ehci-hcd
```

and give it another go

---

### Post by llamabr on 2012-05-03
and:

[http://ubuntuforums.org/showthread.php?t=1214003](http://ubuntuforums.org/showthread.php?t=1214003)

---

### Post by Kevin McCready on 2012-05-09
sudo modprobe -l | grep ehci
gives no results and the thread which was recommended mentioned that the kernel has been updated since the time when that might have been an option.

---

