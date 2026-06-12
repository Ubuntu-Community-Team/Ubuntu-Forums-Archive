---
title: "Mounting USB drive in 8.04"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by dr_james2k on 2008-05-08
I recently updated to Hardy Heron and Ubuntu will no longer mount my external usb drive when I turn it on.  It used to detect it and open a nautilus window before but now it wont even show its there with the lsusb command.  

I can get it to be detected and treated as normal with the command:
> sudo modprobe -r ehci_hcd

but playing video and music files from it is jittery unlike before - is there a better way to correct this?

---

### Post by ichbinesderelch on 2008-05-08
what filesystem has your external hdd?

---

### Post by kpkeerthi on 2008-05-08
Reboot you PC so we are in a clean state. Now, plugin your USB drive and check if the module **usb_storage** is loaded.
```
lsmod | grep -i usb
```

---

### Post by dr_james2k on 2008-05-08
Thanks for the quick responses!

The drive is NTFS.  I just plugged in a usb stick and it didn't recognize that either.

The *lsmod | grep -i usb *gave me:

> usbcore               146028  4 ndiswrapper,ohci_hcd,ehci_hcd


I don't see usb_storage on it so I'm guessing this is the problem.  How do I go about fixing this?

---

### Post by vanadium on 2008-05-08
This is a frequent issue. Disk was probably not properly closed in Windows. Solution: boot into Windows, have the disk checked and then properly disconnect the drive using the icon, or shut down Windows completely. Next time, Ubuntu will automatically mount it.

---

### Post by dr_james2k on 2008-05-08
Yeah, that was my initial thought.  It used to be the same in Gutsy where I'd need to boot into windows to safely remove it when I needed it - but now that doesn't seem to work either.  I've even formatted recently and still no difference.

---

### Post by kpkeerthi on 2008-05-08
I'm not in front of ubuntu. So I can't test it for you at the moment. May be you can give the below steps a try:

1. Disconnect the USB drive
2. Run this command in a terminal window ```
sudo modprobe usb-storage
```
3. Now connect the drive
See if it is getting displayed in nautilus left panel or under 'Places' menu in top gnome panel.

---

### Post by dr_james2k on 2008-05-08
Nothing I'm afraid.  I tried both the external drive and my usb pen.  Neither appeared in nautilus or the gnome places panel.

---

### Post by kpkeerthi on 2008-05-08
Nothing? Did you load the module **usb-storage** manually?
Type **dmesg | tail** and post the output here.

---

### Post by kpkeerthi on 2008-05-08
I think it is **usb_storage** and not **usb-storage**. :confused:

---

### Post by dr_james2k on 2008-05-08
How do I load it manually?

Anyway dmesg output:
> [  177.265696]  [<c0118885>] smp_apic_timer_interrupt+0x55/0x80
[  177.265703]  [<c01054d8>] apic_timer_interrupt+0x28/0x30
[  177.265715]  =======================
[  177.265717] handlers:
[  177.265718] [<f88a8b80>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  177.265737] Disabling IRQ #7
[  854.396050] usbcore: registered new interface driver libusual
[  854.399976] Initializing USB Mass Storage driver...
[  854.400219] usbcore: registered new interface driver usb-storage
[  854.400416] USB Mass Storage support registered.


---

### Post by kpkeerthi on 2008-05-08
I don't see kernel detecting your USB device in there. Can you connect you USB device now and give me the **dmesg | tail **output one last time?

---

### Post by dr_james2k on 2008-05-08
This is the output with both my external drive in and usb pen:

> [  177.265696]  [<c0118885>] smp_apic_timer_interrupt+0x55/0x80
[  177.265703]  [<c01054d8>] apic_timer_interrupt+0x28/0x30
[  177.265715]  =======================
[  177.265717] handlers:
[  177.265718] [<f88a8b80>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  177.265737] Disabling IRQ #7
[  854.396050] usbcore: registered new interface driver libusual
[  854.399976] Initializing USB Mass Storage driver...
[  854.400219] usbcore: registered new interface driver usb-storage
[  854.400416] USB Mass Storage support registered.


---

### Post by honeydew on 2008-05-08
Im running into the same issues.. the drive mounts fine in windows.. and was mounting fine in hardy beta.. but now it just boots up and the light on the drive blinks/flashes like crazy.. all the modprobes havnt helped.. sucks cause I use this drive at work..

---

### Post by ichbinesderelch on 2008-05-11
is gnome-volume-manager running? for hdds not cleanly shut down you could also use "ntfsfix"

---

### Post by sistoviejo on 2008-05-23
Hello,
I am having the same problem (using an Ipod Classic).
Here's my dmesg output:
```
[ 9062.411532] scsi 5:0:0:0: rejecting I/O to dead device
[ 9062.411535] scsi 5:0:0:0: rejecting I/O to dead device
[ 9062.411539] scsi 5:0:0:0: rejecting I/O to dead device
[ 9062.411543] scsi 5:0:0:0: rejecting I/O to dead device
[ 9062.411545] scsi 5:0:0:0: [sdb] READ CAPACITY failed
[ 9062.411547] scsi 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9062.411550] scsi 5:0:0:0: [sdb] Sense not available.
[ 9062.411553] scsi 5:0:0:0: rejecting I/O to dead device
[ 9062.411556] scsi 5:0:0:0: [sdb] Write Protect is off
[ 9062.411558] scsi 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 9062.411560] scsi 5:0:0:0: [sdb] Assuming drive cache: write through
```
After that I tried this:
```
silvio@silvio-laptop:~$ ls /dev/sdb*
ls: cannot access /dev/sdb*: No such file or directory
```
Thanks for all the help!
What should I try?

**UPDATE: NEVERMIND IT WORKED AFTER REBOOTING**

---

### Post by honeydew on 2008-05-26
the only way I have been able to get usb drives to work is to remove the ehci_hcd module.    

```
modprobe -r ehci_hcd
```

after this I connect the usb drive and vwala.

---

### Post by honeydew on 2008-05-26
however after I did updates this morning.. It seems I no longer have todo this(modprobe -r ehci_hcd).. did they squash this bug?

---

### Post by dr_james2k on 2008-05-29
Yup, just updated and now I can use my harddrive whenever I want.  Also I was having issues with my usb keyboard and now those have cleared up as well.  Fantastic!

---

