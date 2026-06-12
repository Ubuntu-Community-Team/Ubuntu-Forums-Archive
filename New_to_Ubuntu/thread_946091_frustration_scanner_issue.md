---
title: "frustration scanner issue"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by RottenPeter on 2008-10-13
I have a BenQ 6660 flatbed scanner. It was working within Xsane, and Scanner utility before I switched to Ubuntu, didn't like it as much and reinstalled Xubuntu again.  Now it doesn't work at all.  Scanner not detected, and invalid argument 005003 in utility and xsane respectively.

I have a disc with the driver, but no luck installing it.  Didn't use it before, when it was actually scanning, so I assume I don't need it now.  I've spent hours and hours on add/remove and synaptic, installing various lib files, xsane files, you name it.

I just can't get a handle on this, and I'm getting really peeved.  I really enjoy using Xubuntu, it's been the best of a few I've used, and this seems to be more a Sane issue than anything, and an I don't know how to install my software properly issue.  I have a KVM switch and a windows computer for the less adventurous members of the family, and for when I can't get stuff working like this, but I hate to give up and only be able to scan in XP when I had it working before! I would so love to go completely xubuntu, but this makes it tough to do!  I appreciate any help.    Thanks.

---

### Post by cariboo on 2008-10-13
Have you tried:

```
sane-find-scanner
```

You will have to run this command in a terminal.

Jim

---

### Post by RottenPeter on 2008-10-13
Hey, thanks for the response.  I did that, and this is what I got:

roger1@teabagwalkerpublications:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a5 [Color], product=0x20fe [ FlatbedScanner 22]) at libusb:005:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
roger1@teabagwalkerpublications:~$ scanimage -L
device `snapscan:libusb:005:003' is a Acer FlatbedScanner22 flatbed scanner
roger1@teabagwalkerpublications:~$ 

So, that's the scanner, it is detected, and it was supported by sane 3 days ago, so I'm sure it's not a huge deal, just something I'm overlooking with my relative newness. I tried to find somewhere that I could access permissions, but no dice. I also don't know what backend's manpage is.  Thanks. Roger.

---

### Post by RottenPeter on 2008-10-14
Thanks for the suggestion.  I have now solved the problem, somewhat.  If you hook the scanner up to a windows computer with the software loaded from the disc, it will work fine on xsane when you hook it up to your xubuntu computer, without having to configure anything, provided you don't unplug it.  I hope others can benefit from this, so anyone that can pass it on, please do! I would bet this applies to a lot of people's scanner problems, and there seem to be many.

It would be nice to know how to remedy this without having to rely on windows to bail yourself out, but I'll take the fact it's working as victory enough.  Next scanner I get I will make sure it's totally compatible with Sane, without all this hooey. As long as you have two computers or dual-boot, you're laughing.  Cheers.

---

