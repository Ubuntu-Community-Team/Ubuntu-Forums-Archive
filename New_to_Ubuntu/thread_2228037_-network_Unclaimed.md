---
title: "-network Unclaimed"
date: 2014-06-05
forum: New to Ubuntu
---

### Post by ebsf on 2014-06-05
So, Linux noob, clean/bare install of 12.04 desktop 64 on an Asus P9X79-E WS motherboard with two on-board Intel NICs.  My earlier 14.04 install failed for unknown reasons but I had network connectivity.  The 12.04 install worked fine but I have no network connectivity.

I have figured out that I need to install a new device driver for the NICs but I don't know how.  I am posting from a Windows laptop, so can't copy screenshots.  I ran <sudo lshw -class network> and for each of the two NICs got a <*-network UNCLAIMED> response.  I've spent hours reviewing other posts concerning this issue and they all seem to require connectivity, besides relating to different hardware.

How do I fix this?

---

### Post by ebsf on 2014-06-05
So, got the Linux driver for the Intel i210 from the Intel site, 

[https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13663&lang=eng&OSVersion=Linux*&DownloadType=](https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13663&lang=eng&OSVersion=Linux*&DownloadType=)

I'll try putting this on a USB stick, sneaker-net it over to the workstation, and fiddle with it for a bit.  Stay tuned.

---

### Post by ebsf on 2014-06-05
I got the Intel tarball over to the workstation with a USB stick but after unzipping it, I got a number of error messages after using the <make> and <make install> commands.

Any thoughts on how to get a new driver installed?

---

