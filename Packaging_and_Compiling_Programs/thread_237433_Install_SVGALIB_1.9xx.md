---
title: "Install SVGALIB 1.9xx"
date: 2006-08-16
forum: Packaging and Compiling Programs
---

### Post by Ninnghizidha on 2006-08-16
Hello!

I got dapper-alternate installed and 'd like to install svgalib >1.9.xx too. Since I found no backports for this, I'd liek to install it from source - but it doenst work.

Steps downloaded the build-essentials, the kernel-headers and created a symlink to the kernel-sources at /usr/src/linux, just like [tytalus]("http://www.ubuntuforums.org/showthread.php?t=181630") did it. But it fails to make modules... 

Im really stuck right now. Is there a guide who/which can help me to install the [dev-version]("http://www.arava.co.il/matan/svgalib/") of svgalib or is there a package already i have missed? 

Any help would be appreciated,
Ninn.

---

### Post by moma on 2006-08-16
All you need is 
$ sudo apt-get install build-essential
and 
$ sudo apt-get install --reinstall linux-headers-$(uname -r)

---

### Post by Ninnghizidha on 2006-08-16
That worked great! Now i go SVGALib installed! :-D

Thanks a lot! :)

---

### Post by G8HAV on 2010-10-21
> **moma said:**
> All you need is 
$ sudo apt-get install build-essential
and 
$ sudo apt-get install --reinstall linux-headers-$(uname -r)

Hi,
Downloaded and extracted the tar.gz for svgalib 1.4.3 into a folder of the same name in Downloads. I am very new to Ubuntu (ver 10.04) and I cant get it installed. Tried the above commands in a terminal console but got 'command not found' I am having trouble with screen resolution (only can get 800 x 600) and hoping this may help but the install is required for another program I want to run.
Thanks in advance

---

