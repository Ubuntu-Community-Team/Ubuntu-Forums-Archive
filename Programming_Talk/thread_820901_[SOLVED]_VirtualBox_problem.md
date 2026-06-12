---
title: "[SOLVED] VirtualBox problem"
date: 2008-06-06
forum: Programming Talk
---

### Post by thornmastr on 2008-06-06
I want to compile and test a program under Windows XP. Rather than going through the process of offloading from one machine to another, I thought I would take this opportunity to install VirtualBox. I used Synaptic and installed VirtualBox-OSE. I built a Windows XP virtual machine. I made certain I had the right permissions, and started it up. I got the following error condition. 

The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

The only thing I found from Google was a post pertaining to installing Windows 98 under VirtualBox and the error had something to do with the Kernel. Hopefully that is not the issue here; but if that information is important, I am running under Ubuntu (hardy) 8.04.The
kernel is 2.6.24-18-generic.

Can anyone shed some light on this and hopefully tell me what I have to do to have a viable Windows XP virtual box running?

Thanks for the assistance.


Robert

---

### Post by mocha on 2008-06-08
It has to do with the lastest kernel upgrades.  There is a bug filed here

[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/237278]("https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/237278")

But building a new kernel module didn't work for me since I'm not using the open source edition.  I had to download and install the latest version to get it working again.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

---

### Post by xlinuks on 2008-06-08
Perhaps a bit offtopic, I tried installing MacOS (x86) but didn't work. Does anyone know whether there's some other tool to do that?

---

### Post by thornmastr on 2008-06-08
Mocha & xlinuks,

It didn't take too long, and too many failed attempts using Google and some of my own ideas to realize I was fighting a kernel issue. 

However, I found a far better and workable solution. I removed VirtualBox entirely and with some trepidation began researching VMWareServer. The more I learned the more I realized this would be just as good and perhaps a bit easier to install. 

I used the folowing Ubuntu tutorial, *_Install VMWare in Ubuntu 8.04ll _*, by
bodhi.zazen located at [http://ubuntuforums.org/showthread.php?t=779934&highlight=vmware+server+tutorial](http://ubuntuforums.org/showthread.php?t=779934&highlight=vmware+server+tutorial)

It was remarkably easy and went very well. I now have a virtual machine running Windows XP and have downloaded the Mingw32 compiler so I will be
able to do some cross compilations relatively soon. Xlinuks, this solution might solve your problem as well. Mocha, I think yu already solved your original problem, but you might, just for giggles, want to look at this tutorial. Actually, it was a lot of fun. Again, thanks for your input.

Robert

---

### Post by Cha0tik on 2008-06-23
VMWare isn't free though.

---

### Post by Cha0tik on 2008-06-23
I tried that :

sudo apt-get install virtualbox-ose-source
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart

Everything works fine for me except the last line which simply returns 
sudo: /etc/init.d/vboxdrv: command not found

where else could that file be ?

---

### Post by dwhitney67 on 2008-06-23
> **Cha0tik said:**
> VMWare isn't free though.
Vmware-server is free... Vmware-workstation costs money for a license.

---

