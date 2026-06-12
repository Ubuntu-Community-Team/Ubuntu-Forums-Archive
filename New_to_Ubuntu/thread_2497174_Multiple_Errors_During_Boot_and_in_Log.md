---
title: "Multiple Errors During Boot and in Log"
date: 2024-04-25
forum: New to Ubuntu
---

### Post by nicolasdentremont on 2024-04-25
[SIZE=1]Hello all. 

Before I start, here's a link to the output of the Ubuntu Forums system-info script:
[URL="https://paste.ubuntu.com/p/fDwy9YzSfW/"]
[/URL][https://paste.ubuntu.com/p/fDwy9YzSfW/](https://paste.ubuntu.com/p/fDwy9YzSfW/) 

I've been using Ubuntu for probably a month now. I've been noticing a few error messages appearing during Boot:

kernel: x86/cpu: SGX disabled by BIOS
integrity: Problem loading X.509 certificate -65
Bluetooth: hci0: Malformed MSFT vendor event: 0x02 

I did some googling of the error messages and haven't found much conclusive information.

For the SGX disabled by BIOS one I found that it can be fixed by enabling SGX in the BIOS but I have no option in there.

[/SIZE][SIZE=1]Problem loading X.509 certificate -65, seems to be common for Acer laptops. I read that it's cause by out of date certificates in the BIOS.

[/SIZE][SIZE=1]Bluetooth: hci0: Malformed MSFT vendor event: 0x02. My Bluetooth still seems to work fine.

Anyway while trying to figure out those errors since they appear I checked the log program and found a whole list of errors in the log, I also uploaded that to pastebin:

[https://paste.ubuntu.com/p/4FRdf7BvB4/](https://paste.ubuntu.com/p/4FRdf7BvB4/)

My system seems to be operating fine, I've been playing games, running CAD software and just using my computer as normal. Most games seem to work better on Ubuntu than they did on Windows once I get them running.

I was wondering if any of those log messages are anything I should worry about? Most of the results I got from searching them had comments saying they were nothing overly serious.

Thanks.
[/SIZE]
[SIZE=1]
[/SIZE]

---

### Post by #&amp;thj^% on 2024-04-25
> **nicolasdentremont said:**
> [SIZE=1]
kernel: x86/cpu: SGX disabled by BIOS
integrity: Problem loading X.509 certificate -65
Bluetooth: hci0: Malformed MSFT vendor event: 0x02 

I was wondering if any of those log messages are anything I should worry about? Most of the results I got from searching them had comments saying they were nothing overly serious.

Thanks.
[/SIZE]
[SIZE=1]
[/SIZE]

Those errors/warnings  come in some Acer laptops as its BIOS contains two obsolete certificates. The error message's is harmless and can be ignored. 

Enjoy your Buntu. :)

EDIT how ever you can look at the drive with:
```
sudo badblocks -sv /dev/sda2
```
For example mine would look like this:
```
sudo badblocks -sv /dev/nvme0n1p1
Checking blocks 0 to 307199
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)

```

---

### Post by nicolasdentremont on 2024-04-25
> **1fallen said:**
> Those errors/warnings  come in some Acer laptops as its BIOS contains two obsolete certificates. The error message's is harmless and can be ignored. 

Enjoy your Buntu. :)

Thanks for the info, that's basically what most of the comments I found regarding that were.

> **1fallen said:**
> EDIT how ever you can look at the drive with:
```
sudo badblocks -sv /dev/sda2
```
For example mine would look like this:
```
sudo badblocks -sv /dev/nvme0n1p1
Checking blocks 0 to 307199
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)

```

I will give that a try, It looks like it's going to take a long time to complete the test.

---

### Post by nicolasdentremont on 2024-04-26
No bad blocks found.

---

### Post by oldfred on 2024-04-26
Your UEFI firmware version number looks low or older.
Best to make sure you have latest firmware for both UEFI and NVMe drive.
You can directly see that:
sudo lshw | grep -m 1 -A 5 "*-firmware" & 
udisksctl status
or
sudo nvme list

---

### Post by nicolasdentremont on 2024-04-26
> **oldfred said:**
> Your UEFI firmware version number looks low or older.
Best to make sure you have latest firmware for both UEFI and NVMe drive.
You can directly see that:
sudo lshw | grep -m 1 -A 5 "*-firmware" & 
udisksctl status
or
sudo nvme list

sudo lshw | grep -m 1 -A 5 "*-firmware"

```
 *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: V1.01
          date: 03/06/2019
```

udisksctl status
```
[1] 4391
MODEL                     REVISION  SERIAL               DEVICE
--------------------------------------------------------------------------
WDC PC SN520 SDAPNUW-512G-1014 20110000  191653800146         nvme0n1 
ST9500325AS               0005HPM1  6VEMJ8AA             sda  
```

But: sudo nvme list
Results in:
```
sudo: nvme: command not found
```

[On the Acer website, in BIOS/Firmware section for my specific model number]("https://www.acer.com/us-en/support/product-support/AN515-54/NH.Q5VAA.007/downloads") there is a Update Insyde solution v1.33. That looks like the updated version of my current BIOS V1.01.

It looks like I'll have to install it with Windows since the file is a .exe.

---

### Post by oldfred on 2024-04-26
Many UEFI can update from UEFI directly if file extracted into FAT32 partition which UEFI can read.
Some also update from a DOS bootable flash drive.

If nvme not installed you have to installed it, but udiskctl showed version.
If NVMe drive probably withwhile to install nvme.
sudo apt install nvme-cli

---

### Post by nicolasdentremont on 2024-04-26
> **oldfred said:**
> Many UEFI can update from UEFI directly if file extracted into FAT32 partition which UEFI can read.
Some also update from a DOS bootable flash drive.

If nvme not installed you have to installed it, but udiskctl showed version.
If NVMe drive probably withwhile to install nvme.
sudo apt install nvme-cli

I do have a NVMe drive in the laptop but my Ubuntu is on a regular HDD. The NVMe drive is what my Windows is on.

Anyway I updated the BIOS. It was a suprisingly quick and easy process. I don't have any new BIOS options and all the error messages are still there. No new ones at least.

---

