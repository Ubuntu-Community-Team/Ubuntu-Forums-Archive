---
title: "Xsane cannot find my scanner?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by japtar10101 on 2008-04-27
I checked out the xsane page first to make sure my Visioneer OneTouch 7300 scanner was supported by the program.  Surely enough, it's marked as [supported](http://www.sane-project.org/sane-mfgs.html#Z-VISIONEER).

Yet, oddly, when I try to open Xsane, it tells me it cannot find the device
> 
Failed to open device 'gt68xx:libusb:001:003': Invalid argument

Is there an extra library I have to download or something to get it to work?

Thanks in advance!

EDIT: 

I forgot to mention this, but when I did Windows install for this scanner, I had to also install Paperport, something NOT supported by xsane.  Is that the reason it can't read it?

---

### Post by japtar10101 on 2008-04-28
Bump.  Hmm, I checked synaptics, but no library exists...

---

### Post by trumpcouptimmy on 2008-05-01
I'm getting the same thing with a different scanner. It worked fine before I upgraded to 8.04 and it is the last issue with the upgrade. I really hate the cryptic error message "invalid argument". It should tell me what is invalid and where I can find it. It might as well say "something's wrong-too bad, so sad"

---

### Post by japtar10101 on 2008-05-01
> **trumpcouptimmy said:**
> I'm getting the same thing with a different scanner. It worked fine before I upgraded to 8.04 and it is the last issue with the upgrade. I really hate the cryptic error message "invalid argument". It should tell me what is invalid and where I can find it. It might as well say "something's wrong-too bad, so sad"

I figured I wasn't alone in this.;)

---

### Post by jerryclement on 2008-05-13
Hi,
I also have a Visioneer 7300 scanner with the same error message that it can't be found. Has anyone found a solution??

Thanks,
Jerry

---

### Post by ElSlunko on 2008-05-15
Epson CX-6000 here and I'm getting a similar error.

---

### Post by galleonway on 2008-05-19
> **japtar10101 said:**
> I checked out the xsane page first to make sure my Visioneer OneTouch 7300 scanner was supported by the program.  Surely enough, it's marked as [supported](http://www.sane-project.org/sane-mfgs.html#Z-VISIONEER).

Yet, oddly, when I try to open Xsane, it tells me it cannot find the device

Is there an extra library I have to download or something to get it to work?

Thanks in advance!
Have you tried "sudo xsane"?

---

### Post by japtar10101 on 2008-05-21
> **galleonway said:**
> Have you tried "sudo xsane"?

Now I did.  Same error occurs.

---

### Post by alienexplorers on 2008-05-21
When you do:
> sane-find-scanner
and
> scanimage -L
what are the outputs of those commands?

---

### Post by japtar10101 on 2008-05-21
Hmph, I have to install sane-utils for those commands to work.

Anyway, sane-find-scanner results.
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a7, product=0x0444 [1200dpi USB Scanner], chip=GT-6816) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

scanimage -L
```
device `gt68xx:libusb:002:002' is a Visioneer OneTouch 7300 flatbed scanner

```


I forgot to mention this, but when I did Windows install for this scanner, I had to also install Paperport, something NOT supported by xsane.  Is that the reason it can't read it?

---

### Post by buellman on 2008-05-21
Hi,

look at this [howto]("http://fedoraunity.org/Members/vector/using-the-visioneer-7300-onetouch-usb-scanner"). You only have to adopt some of the Fedora-spezific parts to Ubuntu (use apt instead of yum) and dl the driver from the correct location ([http://support.visioneer.com/drivers/7300/ENU/7300.3031120.EN.exe](http://support.visioneer.com/drivers/7300/ENU/7300.3031120.EN.exe))

Greets. Buellman

Ps: if you have a Windows Installation, you can skip the wine-part and try to find the firmware (Cis3r5b1.fw) there (after you have installed the driver).

Ps2: if you are really lazy you can search for Cis3r5b1.fw for example in aMule. There is at least one source. Don't know if it is the right one and if you should really use aMule as nobody can tell you if the firmware is no malware or anything else... and i don't know if it is legal to dl it with aMule.

---

### Post by STuPiDiCuS on 2011-08-22
Between this : [https://lists.ubuntu.com/archives/ubuntu-users/2007-July/119680.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-July/119680.html)

And the above Fedora Forum post, I learned that all I had to is: 

```
sudo cp Cis3r5b1.fw /usr/share/sane/gt68xx
``` 

from wherever the file is. Then start simple scan/xsane/whatever. 

The first time you scan something after you plug it in, it does take about 15-30 seconds before the spinner goes away and the scan actually begins. 


I'm on 11.04 64bit, btw.

Thanks for posting that link, buellman!

---

### Post by buellman on 2011-08-23
I am glad that my post helped you... even though it is 3 years old :D

Greets. Buellman

---

