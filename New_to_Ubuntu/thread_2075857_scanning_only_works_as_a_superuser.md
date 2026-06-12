---
title: "scanning only works as a superuser"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by eduardo saxel on 2012-10-24
Hi there,

I'm only able to use my scanner as superuser. ¿ Is there a way to use it as a normal user?

Thanks on advance

---

### Post by sandyd on 2012-10-24
What type of scanner (i.e. USB, Parallel Port, Firewire) are you using?

This page : [https://help.ubuntu.com/community/ScanningHowTo#Permission_Issues](https://help.ubuntu.com/community/ScanningHowTo#Permission_Issues)

contains instructions on how to fix the permissions.

Also, if typing
```

groups
```
in the terminal does not show 'scanner' in the list, run

```

sudo usermod -a -G scanner [username]
```

replacing [username] with your username. 

You can find your username in the terminal, where it says [username]@xxxxxx

---

### Post by eduardo saxel on 2012-10-24
> **sandyd said:**
> What type of scanner (i.e. USB, Parallel Port, Firewire) are you using?

I'm using USB.
I typed what you wrote, but is still not working
thanks for the time

---

### Post by sandyd on 2012-10-24
> **eduardo saxel said:**
> [QUOTE=sandyd;12316152]What type of scanner (i.e. USB, Parallel Port, Firewire) are you using?

I'm using USB.
I typed what you wrote, but is still not working
thanks for the time

then check the page [https://help.ubuntu.com/community/ScanningHowTo#Permission_Issues](https://help.ubuntu.com/community/ScanningHowTo#Permission_Issues)

---

### Post by eduardo saxel on 2012-10-24
> **sandyd said:**
> [QUOTE=eduardo saxel;12316174]

then check the page [https://help.ubuntu.com/community/ScanningHowTo#Permission_Issues](https://help.ubuntu.com/community/ScanningHowTo#Permission_Issues)

I typed 

sudo adduser saned scanner

as still not working, I typed sane-find-scanner:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04f9, product=0x0204) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

then I type scanimage -L:

device `brother3:bus1;dev1' is a Brother DCP-165C USB scanner

and then... don't know what to do

---

### Post by squakie on 2012-10-25
Ok, I'm on the outside looking in, but isn't the adduser supposed to be the group name and the userid (unless you actually are trying to use it with a log on id of "scanner")?

---

