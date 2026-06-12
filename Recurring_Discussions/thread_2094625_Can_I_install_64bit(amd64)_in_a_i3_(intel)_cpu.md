---
title: "Can I install 64bit(amd64) in a i3 (intel) cpu?"
date: 2012-12-14
forum: Recurring Discussions
---

### Post by jonnymr on 2012-12-14
Hi

I want install lubuntu 12.10.

I've a i3. I don't know if is better install 32bits version or 64bits version.
Anybody can help me?

If I install 32bits version. There is a way to make my computer se 6GB of RAM?

thank you for any help.

---

### Post by Abhinav Kumar on 2012-12-14
> **jonnymr said:**
> Hi

I want install lubuntu 12.10.

I've a i3. I don't know if is better install 32bits version or 64bits version.
Anybody can help me?

If I install 32bits version. There is a way to make my computer se 6GB of RAM?

thank you for any help.
Hi jonnymr,
i3 processor supports 64 bit OS and so to utilise its full potential, you should go for 64 bit version.

[http://ark.intel.com/products/46472/Intel-Core-i3-530-Processor-4M-Cache-2_93-GHz](http://ark.intel.com/products/46472/Intel-Core-i3-530-Processor-4M-Cache-2_93-GHz)

Regards,
Abhinav

---

### Post by oldfred on 2012-12-14
Moved to Recurring Discussions.

Most motherboard for i-series chips are UEFI capable. If you have Windows 8 pre-installed it also will be secure boot with UEFI. The 64 bit 12.04 will install to UEFI, but only the 64 bit 12.10 will currently work with secure boot. 12.04 will get grub2 2.00 with the secure boot capability with the next point release in Jan.

       [http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

