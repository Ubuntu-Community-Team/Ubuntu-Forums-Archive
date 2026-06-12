---
title: "Should I download the 32 bit or 64 bit version?"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by fuubaa on 2014-01-13
Hi,

I'd like to install Ubuntu 12.04 LTS for Desktop.

I have a laptop with an Intel Centrino Duo, with 2.5GB of RAM.

I believe this is a 32 bit processor. However since it has over 2GB of RAM, I don't know if I should be downloading the 32 bit version of Ubuntu, or the 64 bit version!

Which should I download?

Thanks!

---

### Post by hoopia on 2014-01-13
It depends on your CPU, which I believe is a 64-bit CPU. Your RAM doesn't really have anything to do with system requirements in regards to whether or not you should use a 64-bit OS. If you do use a 64-bit OS, you have the ability to use more than 4GB of RAM (technically ~3.2GB) on your system. With 2.5GB RAM and a Centrino Duo, I doubt you will see much of a difference, but if you can confirm your CPU is 64-bit compatible, then you can use the 64-bit version of Ubuntu.

---

### Post by TheFu on 2014-01-13
32-bit unless you plan to increase the RAM above 3.5G. 2G is not the limitation, 4G addressing is.
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

Running a 64-bit OS will suck up more memory than is necessary. "Pointers" are twice as large and there are many, many, many pointers used in programming, so each of those will be double the size needed for your system, wasting the RAM you do have.

---

### Post by tfrue on 2014-01-13
Well, if you are unsure then 32bit always, but you should be able to boot into BIOS and look at system info which would tell you 32bit or 64bit processor.

---

### Post by oldfred on 2014-01-13
I am currently running 64 bit Ubuntu but not Unity on a 2006 laptop with core duo chips with 1.5GB of RAM. If I load two larger apps, it see it using swap as it pauses, but my normal use of one larger app like Firefox and a text editor and terminal work without issue.

       32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

   Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by ibjsb4 on 2014-01-13
Yes you are 64bit capable.

[http://www.intel.com/Assets/PDF/perfbrief/mobiletechnology.pdf](http://www.intel.com/Assets/PDF/perfbrief/mobiletechnology.pdf)

Got enough ram?

---

### Post by Dave_L on 2014-01-13
To determine whether the CPU is 32 or 64 bits:

a) grep -w lm /proc/cpuinfo
If you see "lm" in red, it's 64 bits. Otherwise it's 32 bits.

b) sudo lshw | grep "description: CPU" -A 12 | grep width
It says clearly whether it's 64 or 32 bits (may take a little while to finish).

---

