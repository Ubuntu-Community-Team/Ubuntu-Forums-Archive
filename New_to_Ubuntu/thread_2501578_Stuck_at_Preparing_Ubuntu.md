---
title: "Stuck at Preparing Ubuntu"
date: 2024-10-13
forum: New to Ubuntu
---

### Post by skylinestar on 2024-10-13
I flashed my USB with the current Ubuntu 24.04.1 iso via Rufus.
When I go to the menu selection of starting a live boot, Ubuntu starts with a "Welcome to Ubuntu" titled window and a center text that says "Preparing Ubuntu". Then, the pc just freezes.
What's going on?

I have never had any issue live booting older versions of Ubuntu in USB.

---

### Post by yancek on 2024-10-13
Did you verify that the iso file was not corrupted during the download?  You can do that by clicking on verifying your download in the upper left of the download page at the link below.

[https://ubuntu.com/download/desktop/thank-you?version=24.04.1&architecture=amd64&lts=true](https://ubuntu.com/download/desktop/thank-you?version=24.04.1&architecture=amd64&lts=true)

The link below explains creating a bootable usb and booting from a usb.  Note that Balena Etcher is recommended although I would expect rufus to work.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by grahammechanical on 2024-10-14
How long did you wait? In my experience USB memory sticks are very slow. In the old days when we installed from DVD-ROM we could hear the drive spinning. But with USB memory sticks we have no indication that any data is being transferred. It is the same with SSD and NVME drives.

Preparing Ubuntu means that the installer is examining the hardware. If we are connected to the internet we might see the LED indicators on the modem/router flashing.

Regards

---

### Post by skylinestar on 2024-10-14
> **yancek said:**
> Did you verify that the iso file was not corrupted during the download?  You can do that by clicking on verifying your download in the upper left of the download page at the link below.

[https://ubuntu.com/download/desktop/thank-you?version=24.04.1&architecture=amd64&lts=true](https://ubuntu.com/download/desktop/thank-you?version=24.04.1&architecture=amd64&lts=true)

The link below explains creating a bootable usb and booting from a usb.  Note that Balena Etcher is recommended although I would expect rufus to work.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

SHA256 checked. OK.

---

### Post by skylinestar on 2024-10-14
> **grahammechanical said:**
> How long did you wait? In my experience USB memory sticks are very slow. In the old days when we installed from DVD-ROM we could hear the drive spinning. But with USB memory sticks we have no indication that any data is being transferred. It is the same with SSD and NVME drives.

Preparing Ubuntu means that the installer is examining the hardware. If we are connected to the internet we might see the LED indicators on the modem/router flashing.

Regards

When I say the pc freezes, the mouse pointer doesn't move. This doesn't look right though.

I tried the same usb stick on an older PC. Surprisingly, it startup ok (choose language, keyboard, accessibility options, etc). 

Why is there internet connectivity at the preparation page?

---

### Post by yancek on 2024-10-14
Did you try writing it to a usb with Etcher as recommended on the Ubuntu site?

If the current usb boots on an 'older' computer, you could post some information on the computer on which you are trying and failing to use it.  How new/old is it?  Manufacturer, specs on CPU, RAM, video, etc.

There has usually been a selection option to download specific drivers during installation which would require internet but there is no need to select or use that.  I haven't used 24.04 so I don't know if there has been some change.

---

### Post by davetheoldcoder on 2024-10-15
> **skylinestar said:**
> SHA256 checked. OK.

Did you also verify that the USB drive was correctly flashed? The flasher application may not do that.

Here are two methods:

(In these examples, the USB drive's path is /dev/sdb and the downloaded source file is ubuntu-24.04-desktop-amd64.iso. The USB drive's path can be determined by viewing the output of the *mount* command.)

Flush device buffer:
$ sudo blockdev --flushbufs /dev/sdb
Eject USB drive, remove it, and re-insert it.

File compare method:
$ sudo cmp -n `stat -c '%s' ubuntu-24.04-desktop-amd64.iso` ubuntu-24.04-desktop-amd64.iso /dev/sdb
If no output: good comparison.

Checksum method:
$ sudo head -c $(stat -c '%s' ubuntu-24.04-desktop-amd64.iso) /dev/sdb | sha256sum
Output is SHA-256 of USB drive, which should be compared to the expected SHA-256.

The above *cmp* and *sha256sum* commands may take a while to run.

---

### Post by paulycalvin on 2024-10-18
When I was installing mine freezed at keyboard selection. I read that turning off networking for the install was a work around. So I went into the BIOS and turned off networking and the install went through. You could also try using the safe graphics install. After installing you will have to reboot into the bios and enable networking again.

---

### Post by skylinestar on 2024-11-02
I have found the issue. It will get stuck at the preparing screen if I boot with "toram" option.

---

