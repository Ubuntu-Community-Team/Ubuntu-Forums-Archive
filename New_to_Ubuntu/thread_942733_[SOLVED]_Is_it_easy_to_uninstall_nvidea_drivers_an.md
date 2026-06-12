---
title: "[SOLVED] Is it easy to uninstall nvidea drivers and change to ATI"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Andrew U.K. on 2008-10-09
Hi,

I have bought a new LCD tv and no longer need the Nvidea graphics card with the tv out.The motherboard,a Gigabyte GA-MA78GM-S2H has an AMD 780G chipset board with built in ATI HD3200 graphics.

I am relativley new to linux and I am wondering whether to do a fresh install of mythbuntu or try to change the drivers. My experience so far runs to setting up mythbuntu, lirc, acpi, etc.etc. I have looked through the threads and I'm a little confused. 

Could anyone help me with simple instructions if they are simple?

Cheers

---

### Post by Elfy on 2008-10-09
IT should be as simple as removing the nvidia driver with hardware drivers (or envy if you used it to install).

Reboot without the driver and it shoudl revert to default, you can then go back to hardware drivers and install the driver for the ati

---

### Post by Andrew U.K. on 2008-10-09
Thanks

> **forestpixie said:**
> IT should be as simple as removing the nvidia driver with hardware drivers (or envy if you used it to install.


Is there a simple command i can put into the terminal for this?

Cheers

---

### Post by Elfy on 2008-10-09
Not sure tbh - probably, but you'll need to know which one you have installed.

I think you can use similar to this ```
sudo apt-get purge *someofthepackagename**
``` eg nvidia-glx-* - but it could go wrong if you don't read what it says it will do - you can abort.

Then I'm not sure of which driver you would need for the ati afterwards, so it might be easier to use envy or hardware drivers to do so.

Example - 

> sudo apt-get purge linux-headers*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting linux-headers-server for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-generic for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-2 for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-3 for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-4 for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-5 for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-6 for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.26-1-rt for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-4-generic for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-5-server for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.25-2-386 for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6 for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-386 for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-2-generic for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-rt for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-6-server for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-5-generic for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-2.6.27-6-generic for regex &#8216;linux-headers*&#8217;
Note, selecting linux-headers-virtual for regex &#8216;linux-headers*&#8217;
The following packages were automatically installed and are no longer required:
  xaw3dg
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-headers-2.6.27-4* linux-headers-2.6.27-4-generic*
  linux-headers-2.6.27-6* linux-headers-2.6.27-6-generic*
  linux-headers-generic*
0 upgraded, 0 newly installed, 5 to remove and 43 not upgraded.
After this operation, 104MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

### Post by Andrew U.K. on 2008-10-09
Thanks 

Will have a go, at worst I just have to do reinstall anyway.

I'm going to use the new The radeonhd driver.

Thanks again

Andrew

---

### Post by Elfy on 2008-10-09
be good to know how you get on with it ;)

---

### Post by porchrat on 2008-10-09
With the ATI catalyst drivers you merely run the file you downloaded as an executable file.  It creates .deb files that you then load into the kernel using dpkg...it is REALLY simple.  Here is a guide for a more detailed description:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

Also I don't know about the nvidia drivers, but the ATI catalyst drivers include an uninstall script that you can run to completely remove any trace of the old driver (reverts to the original xorg.conf file and everything) so it really is completely easy. Perhaps there is something similar for the nvidia drivers?

---

### Post by Andrew U.K. on 2008-10-13
I bottled it,
just did a fresh install.

---

