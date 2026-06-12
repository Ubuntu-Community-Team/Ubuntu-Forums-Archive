---
title: "Please help me install ATI drivers(tried everything I can and failed)"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Jimnast on 2008-10-11
Hello, I recently purchased a new desktop system, 
ASUS P5Q,
INTEL E8400
MSI ATI RADEON HD 4850 512MB

Running ubuntu 8.04.

I've spent days, trying to install ati's catalyst 8.9 drivers, I've tried, envy, I've seen similar posts posted on these forums and elsewhere, I've been through the faqs, etc... I don't know what else to do. fglrxinfo always tells me I have mesa drivers. I don't even know anymore what packages are installed, what's going on. I've uninstalled , re-installed, tried the "hardware drivers" selection. And now, linux isn't detecting my screen properly anymore, my max res is 1280x1024 and linux only allows me to go up to 800x600. I'm a complete newbie when it comes to linux. 

So I ask pretty pretty please, if anyone out here knows how to install these drivers, can they please give me a step by step guide to do so.

---

### Post by Sava8420 on 2008-10-11
Have you went to ATI's website and read their instructions?  You can download the driver straight off their site and they have decent instructions there.  Also, when you go to hardware drivers what does it show there?

---

### Post by Jimnast on 2008-10-11
Jesus, I finally found something that seems to have worked. [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I followed the manual installation for a 32-bit ubuntu. However, one thing I'm curious about is that when I created the deb packages from the ati driver, the instructions only made me install 3 .debs, when there were 2 others, that were not installed. Don't know if they were important or not.  They were fglrx-modaliases and xorg-driver-fglrx-dev. Must I install them? If so can I do it now or I must I re-install everything from the beginning?

---

