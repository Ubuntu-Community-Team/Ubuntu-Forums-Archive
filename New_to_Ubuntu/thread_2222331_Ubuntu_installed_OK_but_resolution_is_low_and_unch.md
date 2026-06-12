---
title: "Ubuntu installed OK but resolution is low and unchangeable"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by Bonzadog on 2014-05-06
Tuesday 6.5.2014

I thought I had already submitted this thread - but cannot find it. so here it is again.

I installed Ubuntu 14.4 under VM on my ASUS laptop (Intel I7  8GB ram) both the the two boxes in the pre-installation phase were checked..
The are two screens , one Samsung and the inbuilt screen on the laptop. The screen setup (from Win 8.1) is that the Samsung display is active and the Laptop not.

The install went well and Ubuntu  runs - but I have a low screen resolution.
Going to system settings--> display shows an **unchangeable resolution of 640  by 480**. Which is unsatisfactory.

The previous version of Ubuntu worked fine in the same screen configuration.

Switching the Win 8 display mode to just laptop shows the same low res.

Can someone help me?

BD

---

### Post by coffeecat on 2014-05-06
> **Bonzadog said:**
> I installed Ubuntu 14.4 under VM on my ASUS laptop

What virtualisation software are you using and do you mean you are running Ubuntu as a VM inside Windows?

I only have real experience of VirtualBox and that some time ago, but if you are running a VirtualBox Ubuntu VM, you wouldn't be able to adjust the resolution from the default 640x480 until you install the guest additions. I believe something similar is true for VMWare, but I have no experience of other virtualisation applications.

If you post more details of your setup, I'm sure someone will be able to help you.

---

### Post by Bonzadog on 2014-05-06
I am using Oracles VirtualBox and Windows 8.1 is the main operating system. 

I must repeat: The last Ubunu 13.x was installed in exactly this configuration and I had no problems. 
I suppose I could download the previous version and work with that, but that is not the way to go.
Have I missed a paramenter in the install of Ubuntu? Doesn't seem likely though.

Please assist me on this.

Thanks  BD

---

### Post by sandyd on 2014-05-06
What version of Virtualbox are you using - only versions after 4.3.10 will run 14.04 with a correct resolution

For the guest modules: see
[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1282758](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1282758)
and
[https://www.virtualbox.org/ticket/12623](https://www.virtualbox.org/ticket/12623) (fixed in 4.3.8 onwards)

---

### Post by Bonzadog on 2014-05-06
I am using Version Virtual Box 4.3.10 r93012 German version - no updates are available.

Thank you for the links - the first link seem relevant but seems to offer no solution and the 2nd URL doesn't seem to apply.

BD

---

### Post by Bonzadog on 2014-05-10
I have re-installed the previous version of Ubunti in  VM 4.3 10. There were no problem ajd runs with 
the  corrrect resolution.

Have anyone further advice on how I should proceed with the Ubuntu 14 problem? Wait for the next version od Ubuntu?

Thanks to all

---

