---
title: "No USB detection"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by ricardobentes on 2008-05-02
Hi all!
I just installed Ubuntu 8.04 and found a problem. It doesn't detect anything connected to my USB ports.
I have a 500GB external drive, a usb pen disk and a USB card reader. It fails to read any of them.

I already looked in Media folder and mnt but nothing appears. 

What do you sugest I should do?

Thanks!

---

### Post by rbc on 2008-05-02
They don't automount? Have you tried mounting from terminal?

---

### Post by ricardobentes on 2008-05-02
I'm trying but it's been a few years since I used linux... :oops:
Care to guide me?

---

### Post by rbc on 2008-05-02
I've never used a card reader in Ubuntu, so let's try one of the other. Plug in either the external HD or the thumb drive, then go to terminal and type:
"sudo fdisk -l" (without the quotes)

---

### Post by rbc on 2008-05-02
I've never used a card reader in Ubuntu, so let's try one of the other. Plug in either the external HD or the thumb drive, then go to terminal and type:
"sudo fdisk -l" (without the quotes)
Post back with the results. This should show whether they are being recognized at all

---

### Post by ricardobentes on 2008-05-02
done.
results:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x954c954c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94709470

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14945   120045681    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd625d625

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4227    33953346    7  HPFS/NTFS
/dev/sdc2            4228        4865     5124735    f  W95 Ext'd (LBA)
/dev/sdc5            4228        4865     5124703+   b  W95 FAT32

```

sorry I took a long time, was having dinner. :)

Apparently only my 3 internal hard disks appear.

---

### Post by lswest on 2008-05-02
that doesn't show any 500GB drive, so i'm pretty sure it's not recognizing the devices.  Could you disconnect and reconnect the drive then post the output of ```
dmesg|tail -n 100
``` (i think that's the command, not in Linux atm, so i can't check).

---

### Post by ricardobentes on 2008-05-02
done.

```
ricardo@Osiris:/dev$ dmesg|tail -n 100
[ 2151.206703] usb 3-6: new high speed USB device using ehci_hcd and address 34
[ 2151.318512] usb 3-6: device descriptor read/64, error -32
[ 2151.534135] usb 3-6: device descriptor read/64, error -32
[ 2151.749767] usb 3-6: new high speed USB device using ehci_hcd and address 35
[ 2151.861575] usb 3-6: device descriptor read/64, error -32
[ 2152.077210] usb 3-6: device descriptor read/64, error -32
[ 2152.292952] usb 3-6: new high speed USB device using ehci_hcd and address 36
[ 2152.700142] usb 3-6: device not accepting address 36, error -32
[ 2152.811965] usb 3-6: new high speed USB device using ehci_hcd and address 37
[ 2153.219248] usb 3-6: device not accepting address 37, error -32
[ 2396.775921] usb 3-1: new high speed USB device using ehci_hcd and address 38
[ 2396.887730] usb 3-1: device descriptor read/64, error -32
[ 2397.103358] usb 3-1: device descriptor read/64, error -32
[ 2397.318992] usb 3-1: new high speed USB device using ehci_hcd and address 39
[ 2397.430812] usb 3-1: device descriptor read/64, error -32
[ 2397.646435] usb 3-1: device descriptor read/64, error -32
[ 2397.862067] usb 3-1: new high speed USB device using ehci_hcd and address 40
[ 2398.269368] usb 3-1: device not accepting address 40, error -32
[ 2398.381214] usb 3-1: new high speed USB device using ehci_hcd and address 41
[ 2398.788476] usb 3-1: device not accepting address 41, error -32
[ 2399.028079] usb 3-6: new high speed USB device using ehci_hcd and address 42
[ 2399.139890] usb 3-6: device descriptor read/64, error -32
[ 2399.355519] usb 3-6: device descriptor read/64, error -32
[ 2399.571152] usb 3-6: new high speed USB device using ehci_hcd and address 43
[ 2399.682961] usb 3-6: device descriptor read/64, error -32
[ 2399.898596] usb 3-6: device descriptor read/64, error -32
[ 2400.114230] usb 3-6: new high speed USB device using ehci_hcd and address 44
[ 2400.521514] usb 3-6: device not accepting address 44, error -32
[ 2400.633340] usb 3-6: new high speed USB device using ehci_hcd and address 45
[ 2401.040635] usb 3-6: device not accepting address 45, error -32
[ 5495.311923] usb 3-1: new high speed USB device using ehci_hcd and address 46
[ 5495.423739] usb 3-1: device descriptor read/64, error -32
[ 5495.639373] usb 3-1: device descriptor read/64, error -32
[ 5495.854998] usb 3-1: new high speed USB device using ehci_hcd and address 47
[ 5495.966818] usb 3-1: device descriptor read/64, error -32
[ 5496.182446] usb 3-1: device descriptor read/64, error -32
[ 5496.398077] usb 3-1: new high speed USB device using ehci_hcd and address 48
[ 5496.805370] usb 3-1: device not accepting address 48, error -32
[ 5496.917192] usb 3-1: new high speed USB device using ehci_hcd and address 49
[ 5497.324483] usb 3-1: device not accepting address 49, error -32
[ 5497.564092] usb 3-5: new high speed USB device using ehci_hcd and address 50
[ 5497.675891] usb 3-5: device descriptor read/64, error -32
[ 5497.891524] usb 3-5: device descriptor read/64, error -32
[ 5498.107161] usb 3-5: new high speed USB device using ehci_hcd and address 51
[ 5498.218965] usb 3-5: device descriptor read/64, error -32
[ 5498.434608] usb 3-5: device descriptor read/64, error -32
[ 5498.650232] usb 3-5: new high speed USB device using ehci_hcd and address 52
[ 5499.057528] usb 3-5: device not accepting address 52, error -32
[ 5499.169354] usb 3-5: new high speed USB device using ehci_hcd and address 53
[ 5499.576645] usb 3-5: device not accepting address 53, error -32
[ 5863.935302] usb 3-1: new high speed USB device using ehci_hcd and address 54
[ 5864.047112] usb 3-1: device descriptor read/64, error -32
[ 5864.262745] usb 3-1: device descriptor read/64, error -32
[ 5864.478394] usb 3-1: new high speed USB device using ehci_hcd and address 55
[ 5864.590187] usb 3-1: device descriptor read/64, error -32
[ 5864.805827] usb 3-1: device descriptor read/64, error -32
[ 5865.021452] usb 3-1: new high speed USB device using ehci_hcd and address 56
[ 5865.428750] usb 3-1: device not accepting address 56, error -32
[ 5865.540579] usb 3-1: new high speed USB device using ehci_hcd and address 57
[ 5865.947863] usb 3-1: device not accepting address 57, error -32
[ 5866.059679] usb 3-5: new high speed USB device using ehci_hcd and address 58
[ 5866.171490] usb 3-5: device descriptor read/64, error -32
[ 5866.387126] usb 3-5: device descriptor read/64, error -32
[ 5866.602764] usb 3-5: new high speed USB device using ehci_hcd and address 59
[ 5866.714565] usb 3-5: device descriptor read/64, error -32
[ 5866.930195] usb 3-5: device descriptor read/64, error -32
[ 5867.145837] usb 3-5: new high speed USB device using ehci_hcd and address 60
[ 5867.553131] usb 3-5: device not accepting address 60, error -32
[ 5867.664944] usb 3-5: new high speed USB device using ehci_hcd and address 61
[ 5868.072246] usb 3-5: device not accepting address 61, error -32
[ 9283.284226] usb 3-1: new high speed USB device using ehci_hcd and address 62
[ 9283.396033] usb 3-1: device descriptor read/64, error -32
[ 9283.611675] usb 3-1: device descriptor read/64, error -32
[ 9283.827295] usb 3-1: new high speed USB device using ehci_hcd and address 63
[ 9283.939118] usb 3-1: device descriptor read/64, error -32
[ 9284.154736] usb 3-1: device descriptor read/64, error -32
[ 9284.370376] usb 3-1: new high speed USB device using ehci_hcd and address 64
[ 9284.777672] usb 3-1: device not accepting address 64, error -32
[ 9284.889502] usb 3-1: new high speed USB device using ehci_hcd and address 65
[ 9285.296777] usb 3-1: device not accepting address 65, error -32
[ 9294.980286] usb 3-6: new high speed USB device using ehci_hcd and address 66
[ 9295.092083] usb 3-6: device descriptor read/64, error -32
[ 9295.307725] usb 3-6: device descriptor read/64, error -32
[ 9295.523357] usb 3-6: new high speed USB device using ehci_hcd and address 67
[ 9295.635161] usb 3-6: device descriptor read/64, error -32
[ 9295.850798] usb 3-6: device descriptor read/64, error -32
[ 9296.066432] usb 3-6: new high speed USB device using ehci_hcd and address 68
[ 9296.473713] usb 3-6: device not accepting address 68, error -32
[ 9296.585549] usb 3-6: new high speed USB device using ehci_hcd and address 69
[ 9296.992837] usb 3-6: device not accepting address 69, error -32
[ 9737.841056] usb 3-5: new high speed USB device using ehci_hcd and address 70
[ 9737.952862] usb 3-5: device descriptor read/64, error -32
[ 9738.168511] usb 3-5: device descriptor read/64, error -32
[ 9738.384131] usb 3-5: new high speed USB device using ehci_hcd and address 71
[ 9738.495937] usb 3-5: device descriptor read/64, error -32
[ 9738.711568] usb 3-5: device descriptor read/64, error -32
[ 9738.927211] usb 3-5: new high speed USB device using ehci_hcd and address 72
[ 9739.334500] usb 3-5: device not accepting address 72, error -32
[ 9739.446318] usb 3-5: new high speed USB device using ehci_hcd and address 73
[ 9739.853608] usb 3-5: device not accepting address 73, error -32

```

I was trying with the pen drive but now it's the 500GB disk.

thenks

---

### Post by lswest on 2008-05-02
well, it does recognize the device but the problem is this: > [ 9739.853608] usb 3-5: device not accepting address 73, error -32  Not entirely sure what this error means, but one thing i just want to be sure of, did you safely remove the USB stick and the 500GB hdd (maybe even the card reader) from Windows before plugging it into Ubuntu (if they were used on a Windows PC before)?

P.S. thanks for the thanks ^^

*EDIT* also, the card reader may not become visible until you stick a card in it for reading (i can only see mine the hardware manager/with "lshw" unless i stick a card in it)

---

### Post by ricardobentes on 2008-05-02
Well, the external was pluged in when I turned off windows for the last time (just before I erased uninstaled it and instaled ubuntu) :) so I guess it unmounted alright. same goes for the card reader. Now the pen I don't remember because i didn't use it in a long time. Do you think that's the cause? It's a bit strange no? Because it's happening in with all USB devices...

---

### Post by lswest on 2008-05-02
hmm, i googled the error and the most helpful comment i found was that it seemed to be resulting from an "interrupt error" however, no clarifications on what it is or how to resolve it.  Sorry, this is out of my league.  However, try sticking a card in the card reader, and i'm not sure about the usb stick/500GB hdd.

---

### Post by ricardobentes on 2008-05-02
Ok, thanks for the help!

---

### Post by ricardobentes on 2008-05-02
Anyone else has any idea?

---

### Post by ricardobentes on 2008-05-02
Hi!
I found someone who had the same problem so I did what they sugested:

[http://ubuntuforums.org/showthread.php?t=482989]("http://ubuntuforums.org/showthread.php?t=482989")

I disconnected the device, and ran the command:

```
sudo modprobe -r ehci_hcd
```

Then I connected the disk to my windows laptop and saffely removed it and TADA!!! It detected it perfectly.

Now, my final (I hope) question.

I don't know what that command does (I know I shouldn't run commands without having no idea what they do....) but I think it configured my usb ports to usb 1 speed. Right? If it's true, how can I put it back to USB 2?

Thanks!

---

