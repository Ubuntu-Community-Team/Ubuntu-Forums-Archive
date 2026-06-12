---
title: "Configure Compiz on Ubuntu 8.04 running on VMware"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by neo_bahamut on 2008-08-05
Hi all, 

I am new around here, so I am sorry if this has been discussed before. I have VMware Workstation 6.04 install on my pc, and I decided to create a new virtual machine and install Ubuntu. 

Everything went very smoothly, so I started reading about what can I do with Ubuntu and find about Compiz. I tried using several walkthroughs but I am not able to get it to work. 

I noticed that most of the guides are for stand alone Ubuntu computers, so I don’t know if there's if there’s a different process to get Compiz working with VMware. 

Could you help me out with this?

Thanks in advance.

---

### Post by Qchan on 2008-08-05
> **neo_bahamut said:**
> Hi all, 

I am new around here, so I am sorry if this has been discussed before. I have VMware Workstation 6.04 install on my pc, and I decided to create a new virtual machine and install Ubuntu. 

Everything went very smoothly, so I started reading about what can I do with Ubuntu and find about Compiz. I tried using several walkthroughs but I am not able to get it to work. 

I noticed that most of the guides are for stand alone Ubuntu computers, so I don&#8217;t know if there's if there&#8217;s a different process to get Compiz working with VMware. 

Could you help me out with this?

Thanks in advance.

[b][color=darkred]
From my understanding, 3D applications are not supported in Vmware (by default). You'll have to enable them by editing a configuration file.

I'm not sure what version you're running, but you should be able to find your answer here:

[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)

[/b][/color]

---

### Post by cariboo on 2008-08-05
VMWare uses virtual hardware, so there is no real support for all the whiz bang features of Ubuntu. You can get a working installation that will do everything you need. To use the special affects you have to do a real install.

Jim

---

