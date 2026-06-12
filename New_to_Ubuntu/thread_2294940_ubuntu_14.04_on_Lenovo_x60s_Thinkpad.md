---
title: "ubuntu 14.04 on Lenovo x60s Thinkpad"
date: 2015-09-14
forum: New to Ubuntu
---

### Post by jacoby-i-r on 2015-09-14
Hello.
I am new to linux, and I have been using a live USB drive to run 64 bit Ubuntu 14.04. I really want to run said USB onto an old thinkpad x60s with a Core Duo processor. When I do this, however, by running it without installing, the drive freezes and I never get my Desktop. I have heard that it needs a special 32 bit version. How do I solve this problem without installing it to the hard drive?

---

### Post by yancek on 2015-09-14
If you have 64bit software (Ubuntu 14.04) then the hardware needs to be 64bit also.  If your hardware on the old machine is not 64bit, you will need a 32bit OS.

---

### Post by grahammechanical on 2015-09-14
The Lenovo Thinkpad x60 has an Intel Core Duo T2300 CPU and it is a 32 bit CPU.

[https://support.lenovo.com/us/en/documents/pd010033](https://support.lenovo.com/us/en/documents/pd010033)

[http://ark.intel.com/products/27233/Intel-Core-Duo-Processor-T2300-2M-Cache-1_66-GHz-667-MHz-FSB](http://ark.intel.com/products/27233/Intel-Core-Duo-Processor-T2300-2M-Cache-1_66-GHz-667-MHz-FSB)

So, there you are. 32Bit Ubuntu needed.

---

### Post by tgalati4 on 2015-09-14
Try downloading a 32-bit version and boot from that.  I thought these Core Duo's were 64-bit.  [http://www.thinkwiki.org/wiki/Intel_Core_Duo_(Yonah)](http://www.thinkwiki.org/wiki/Intel_Core_Duo_(Yonah))

You might need to use the forcepae switch or a distro with the forcepae work-around.

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

[http://askubuntu.com/questions/460623/ubuntu-14-04-installation-hangs-despite-of-forcepae-option](http://askubuntu.com/questions/460623/ubuntu-14-04-installation-hangs-despite-of-forcepae-option)

---

### Post by mörgæs on 2015-09-15
Forcepae is not relevant for this processor. It only applies to a certain part of the Pentium M family.

---

