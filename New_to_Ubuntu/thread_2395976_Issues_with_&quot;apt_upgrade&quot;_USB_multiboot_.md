---
title: "Issues with &quot;apt upgrade&quot; USB multiboot with persistence"
date: 2018-07-09
forum: New to Ubuntu
---

### Post by dgilz1234 on 2018-07-09
trying to prepare my machine to run a virtual box for some sandbox hacking. Unfortunately, my apt upgrade does not properly download LSB kernel or Linux Headers. While unpacking upgrades, I get the following fatal errors:

```
dpkg: unrecoverable fatal error, aborting:
 failed to write status database record about 'librygel-core-2.6-2' to '/var/lib/dpkg/status': No space left on device
dpkg: error: failed to write status database record about 'librygel-core-2.6-2' to '/var/lib/dpkg/status': No space left on device
dpkg: error: failed to write status database record about 'librygel-core-2.6-2' to '/var/lib/dpkg/status': No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)
E: Sub-process dpkg --set-selections returned an error code (2)
E: Couldn't revert dpkg selection for approved remove/purge after an error was encountered!
E: Sub-process dpkg --set-selections returned an error code (2)
E: Couldn't restore dpkg selection states which were present before this interaction!

```

---

### Post by Geoffrey_Arndt on 2018-07-09
Are you describing a scenario of updating a _USB Flash Stick with Persistence enabled_?    If so, that is not the right environment for running a sandbox/test install of any OS.   Very insecure, unstable and limited functionality - - and not a mirror of an installed system (therefore useless as a sandbox).

---

### Post by oldos2er on 2018-07-09
"No space left on device " means exactly what it says. Maybe you could tell us how big your flash drive is?

---

### Post by dgilz1234 on 2018-07-09
@oldos2er the flashdrive is 16 GB

---

### Post by dgilz1234 on 2018-07-09
@Geoffrey_Arndt I am using a USB Flash Stick with Persistence enabled. I am trying to install the virtual box on the Kali Linux OS that I have on the USB stick. Should I use another drive to store Kali Linux? I was trying to avoid using a virtual box, as I prefer the natural OS. If security is the only issue, would encrypting the USB stick be an option?

---

### Post by Geoffrey_Arndt on 2018-07-10
USB Flash Sticks with "Persistence" should not be equated with a fully installed iso of Ubuntu on a portable usbv3 SSD.    The fully installed SSD is the same as an internal HDD or SSD install, but is highly portable.   It is also MUCH easier to update and maintain.   Here's a youtube video of what it looks like and it's features.    This requires a standard live usb installer (flash-stick) to target the install to the SSD.   Be sure to also add the grub bootloader to the SSD device versus the internal drive.

Then, any VM can be installed on the SSD for your sandboxes (Virtual Box, VMware, Qemu/KVM, etc. etc.

[https://www.youtube.com/watch?time_continue=1&v=4qtr9QaYJ7U](https://www.youtube.com/watch?time_continue=1&v=4qtr9QaYJ7U)

---

