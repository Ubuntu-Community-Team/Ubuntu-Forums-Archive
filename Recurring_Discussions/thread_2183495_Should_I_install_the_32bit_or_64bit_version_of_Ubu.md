---
title: "Should I install the 32bit or 64bit version of Ubuntu?"
date: 2013-10-25
forum: Recurring Discussions
---

### Post by mithen2 on 2013-10-25
OS: Ubuntu 12.04 LTS (32bit version)
  Laptop: HP Probook 6465b
  CPU: AMD A series A6-3410MX / 1.6 GHz ( 2.3 GHz ) ( Quad-Core )
  RAM: 4GB
  GPU: AMD Radeon HD 6520G
  HDD: 500GB

Somebody mentioned that my laptop hardware is designed for a 64bit OS. What are the benefits for using a 64bit OS? From my limited knowledge 64bit OS is meant for systems with 8GB+ RAM where a 32bit OS can only effectivley use 4GB RAM? I have no idea if this is correct but I was curious to ask.

---

### Post by sudodus on 2013-10-25
I think you can use both 32-bit and 64-bit systems with your computer. The focus of development is gradually moving from 32-bit to 64-bit. Today most programs would work as well or better with 64-bits in your computer. But there might still be some multimedia codecs and other special programs, that might work better (or only) with 32-bits. In some cases special libraries can be installed to run such programs in 64-bit systems.

With less than 4 GB 32-bit systems might be preferred because they use less RAM for the same tasks. With more than 4GB 64-bit systems might be preferred because they use large RAM more efficiently.

One thing that might cause problems for you is the Radeon GPU. And this is probably independent of 32-bits or 64-bits. Try first without any tweaking to run a live system (booted from the install CD/DVD/USB drive) but do not install. Only try how it works. Maybe you need a boot option to get the graphics to work. Maybe you need to install a proprietary driver to get good performance. But take it step by step.

---

### Post by oldfred on 2013-10-25
Moved to recurring along with the 100's of other threads on exactly same issue.

       Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

Benchmarks going back to 2009 show 64 bit better and recent ones show it better even on systems with little RAM.

 Post by VeeDub on choosing 64 bit:
[http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619](http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619)
[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by BigSilly on 2013-10-26
All I can add to the above is that I am in a similar position to Mithen insofar as my m/b will only go as high as 4Gb RAM, which I have installed (spec below). However, Ubuntu 13.04 64 bit runs like a dream on this system, so I wouldn't hesitate to recommend it. In fact I've been running 64 bit since about 8.10 when I only had a dual-core CPU, and it's never let me down. Gonna install 13.10 later and see how that goes, but from what I gather it's even faster than 13.04, which I am excited to see. :)

---

