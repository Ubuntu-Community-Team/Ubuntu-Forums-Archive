---
title: "Plustek Opticslim 2420 scanner not working."
date: 2008-10-11
forum: New to Ubuntu
---

### Post by x3qt0r on 2008-10-11
This scanner aint working.
And it is the only thing keeping me from going completely into the ubuntu 8.04 world, I have to go back to windows just for this scanner!
And being a newbie at using terminal, I am not able to follow online tutorials to set up the scanner.

I tried to follow some  online tutorial that asked me to check for scanning devices and heres the o/p:

durgesh@durgesh:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x07b3 [PLUSTEK], product=0x0806 [USB2.0 SCANNER], chip=GL841) at libusb:005:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.



Please help me to get rid of windows altogether.
Thanks in advance.

---

### Post by phidia on 2008-10-11
You will need to install the correct backend for your scanner.
See the sane page for [plustek]("http://www.sane-project.org/cgi-bin/driver.pl?manu=plustek&model=optic+slim+2420&bus=any&v=&p=") scanners and the Ubuntu scanner [wiki]("https://help.ubuntu.com/community/ScanningHowTo?") too.

---

### Post by x3qt0r on 2008-10-11
On the SANE page the plustek opticslim scanner 2420 is under "unsupported" tag.
And the ubuntu wiki isnt much of a help either.

Atleast to a newbie, these things look  difficult.

---

### Post by phidia on 2008-10-11
> OpticSlim 2420 	USB 	0x07b3/0x0806 	unsupported 	GL841 based, to be added to genesys backend

You're right I missed that because I saw the opticslim 2400 was listed as working. 
If it's not supported-it's going to be very difficult if not impossible to get working in linux.

---

### Post by x3qt0r on 2008-10-12
:(

---

### Post by x3qt0r on 2010-10-05
After almost two years of this post about my "unsupported" scanner, its surprising that there is still no support for the plustek 2420 scanner.

I have been using that scanner under virtualbox+winxp for this long, but for some weird reasons it has stopped detecting it.

So I thought, I would check if there is any support for after 2 years.. but alas :(, atleast not that I can find. Kindly tell me if am missing something.

I am running 10.04 LTS.

---

### Post by nugencs on 2010-10-13
I've been using Plustek Opticslim 2400 scanner under Ubuntu 10.04 for a while now. It's working under Ubuntu 10.10 as well. Here's what I did to make it work: 

- I copied the file "Cis3r5b1.FW" from the Opticslim software's directory in Windows ("C:\Program Files\ScannerU\") to this location ("/usr/share/sane/gt68xx\")

I hope this helps.

---

