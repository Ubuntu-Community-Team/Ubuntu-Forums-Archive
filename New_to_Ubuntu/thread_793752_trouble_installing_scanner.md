---
title: "trouble installing scanner"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by vidyadhara on 2008-05-14
Hi,
I have just installed ubuntu 8.04.
I got my printer working with it fine. A Xerox 3117 phaser printer.

I am not able to get the scanner to work. I dont know what to look for.

I have a Microtek Scanmaker 3630 scanner. 
The sane website tells me that this scanner is not supported.

I did a sane-find-scanner on my machine.
here are the results.

----
$ sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a7, product=0x0224) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
-----


Apparently it found something.
"found USB scanner (vendor=0x04a7, product=0x0224) at libusb:001:005"

I dont know what to do with this discovery. Help is greatly appreciated. I can kick out windows from my office if I get this running.

Thanks in advance.

regards
Vidyadhara Buddhiraju

---

### Post by nicedude on 2008-05-14
Some simple googling and I find that there may not be any support for your scanner as no linux drivers appear to be available, here is a link to a page with some info

[http://brainstorm.ubuntu.com/idea/8010/](http://brainstorm.ubuntu.com/idea/8010/)


Here is a project supporting 3600 and they claim doubts about 3630 working but wanted feedback so you might look here as well.
[http://sm3600.sourceforge.net/](http://sm3600.sourceforge.net/)

You should also send a Email to Microtek stating that your next scanner will be anything but Microtek since they won't support Linux. In fact everyone with a brick device out there should send the same Email and then do what you say and support any company that does support Linux, I mean its pretty pathetic when in some cases all the linux gurus want is some info so they can build the drivers themselves and companies still wont comply - this sort of behavior doesn't deserve the reward of your future purchase.

The linux comunity should come up with lists by device of manufacturers who will work with us and we should in turn support those manufacturers.

---

