---
title: "First install"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by Nicholas_Williams on 2013-11-22
I am taking the plunge and adopting Ubuntu as my main OS for the foreseeable future. I have a couple of questions that I hope the community might be able to answer. As a preface to this here are some of the machine specs Ubuntu will be installed upon;

CPU: Intel Core i7-4800MQ(Haswell)
RAM: 16 GB DDR3
HDD: Crucial M500 960GB SSD
GPU: NVIDIA GeForce GTX 765M 2048MB GDDR5(w/Optimus)
WiFi: Intel Dual Band Wireless-AC 7260 (with Bluetooth)


1. I am very security conscious and was wondering how I would go about setting up full disk encryption on a SSD which already is a self encrypting drive?
2. Does anyone in their experience foresee any support problems with my system setup?
3. Are their advanced options for partitioning during the installation? i.e. separate /, /home, /tmp, /var/tmp

---

### Post by Bucky Ball on 2013-11-22
The answer to three is 'yes'. Choose 'Something else' when you get to the partitioning section and partition manually. Those mountpoint are available as defaults but you can create whatever mountpoint names you want. 

The best way to find out how it will run is to download an ISO, burn a disk and try it from the disk before installing. Graphics and wireless might be problematic but generally easily fixed. Install the 64bit, not 32bit. 

You would be best to post a new thread on the full disk encryption.

Just a tip: You'll have more success providing titles that are descriptive of your support question (although I do like this title). 

(Beast of a machine you have there.)

---

### Post by Nicholas_Williams on 2013-11-22
> **Bucky Ball said:**
> The answer to three is 'yes'. Choose 'Something else' when you get to the partitioning section and partition manually. Those mountpoint are available as defaults but you can create whatever mountpoint names you want. 

The best way to find out how it will run is to download and ISO, burn a disk and try it from the disk before installing. Graphics and wireless might be problematic but generally easily fixed. Install the 64bit, not 32bit. 

(Beast of a machine you have there.)

I have it currently running in a VM and have been using it off and on for a while. I just haven't played with the installer a whole lot.

---

### Post by grahammechanical on 2013-11-22
Does this: [COLOR=#000000](w/Optimus) = with Nvidia Optimus technology? If so then expect problems. Nvidia has taken its time in providing a Linux driver for its Optimus technology and it has still to complete the job. There is an open source Optimus driver project but those developers are up against the usual issues with writing drivers for proprietary hardware and little or no cooperation from the manufacturer.

[http://bumblebee-project.org/](http://bumblebee-project.org/)

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

Regards.[/COLOR]

---

### Post by sandyd on 2013-11-22
> **Nicholas_Williams said:**
> I am taking the plunge and adopting Ubuntu as my main OS for the foreseeable future. I have a couple of questions that I hope the community might be able to answer. As a preface to this here are some of the machine specs Ubuntu will be installed upon;

CPU: Intel Core i7-4800MQ(Haswell)
RAM: 16 GB DDR3
HDD: Crucial M500 960GB SSD
GPU: NVIDIA GeForce GTX 765M 2048MB GDDR5(w/Optimus)
WiFi: Intel Dual Band Wireless-AC 7260 (with Bluetooth)


1. I am very security conscious and was wondering how I would go about setting up full disk encryption on a SSD which already is a self encrypting drive?
2. Does anyone in their experience foresee any support problems with my system setup?
3. Are their advanced options for partitioning during the installation? i.e. separate /, /home, /tmp, /var/tmp

1.
when installing, click the button labled "take over hard disk" or something similar, there should then be a checkbox to allow you to encrypt the whole drive. You might have to select "LVM" as well if its not already selected :)

---

### Post by oldfred on 2013-11-22
I generally prefer to partition in advanced with gparted, but you still have to use Something Else or manual install to specify which partitions are mounted where.

Will you be booting in UEFI or BIOS boot mode?
One advantage of gpt partitioning is that you can boot Ubuntu in either UEFI or BIOS boot mode if correct partitions are on drive. But Windows only boots from gpt with UEFI. 
And both Windows & Ubuntu only boot from the 30+ year old MBR(msdos) partitioning scheme with BIOS.

I think with LVM, both efi & /boot must be outside encryption as UEFI does not directly read the encrypted data until mounted by the /boot process.

If not familiar with partitioning I would not use LVM, unless you really need full disk encryption. LVM adds a logical layer over the physical layer of partitions and requires separate partition tools to manage the LVM.
Not familiar with self encrypting drives.
 [http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)
Only the latest version of Gparted (0.14) supports resizing LVM physical volumes. The version that ships with Ubuntu 12.10 or 13.04 does not support it.

---

### Post by Nicholas_Williams on 2013-11-23
> **grahammechanical said:**
> Does this: [COLOR=#000000](w/Optimus) = with Nvidia Optimus technology? If so then expect problems. Nvidia has taken its time in providing a Linux driver for its Optimus technology and it has still to complete the job. There is an open source Optimus driver project but those developers are up against the usual issues with writing drivers for proprietary hardware and little or no cooperation from the manufacturer.

[http://bumblebee-project.org/](http://bumblebee-project.org/)

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

Regards.[/COLOR]

> **sandyd said:**
> 1.
when installing, click the button labled "take over hard disk" or something similar, there should then be a checkbox to allow you to encrypt the whole drive. You might have to select "LVM" as well if its not already selected :)

> **oldfred said:**
> I generally prefer to partition in advanced with gparted, but you still have to use Something Else or manual install to specify which partitions are mounted where.

Will you be booting in UEFI or BIOS boot mode?
One advantage of gpt partitioning is that you can boot Ubuntu in either UEFI or BIOS boot mode if correct partitions are on drive. But Windows only boots from gpt with UEFI. 
And both Windows & Ubuntu only boot from the 30+ year old MBR(msdos) partitioning scheme with BIOS.

I think with LVM, both efi & /boot must be outside encryption as UEFI does not directly read the encrypted data until mounted by the /boot process.

If not familiar with partitioning I would not use LVM, unless you really need full disk encryption. LVM adds a logical layer over the physical layer of partitions and requires separate partition tools to manage the LVM.
Not familiar with self encrypting drives.
 [http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)
Only the latest version of Gparted (0.14) supports resizing LVM physical volumes. The version that ships with Ubuntu 12.10 or 13.04 does not support it.

Thanks for the information. Am I correct in saying that Ubuntu uses dm crypt/luks to encrypt the volume?

---

