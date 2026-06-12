---
title: "Screen resolution problem with Ubuntu 12.04 vm"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by ClientAlive on 2012-06-25
Hi,

I've seen a couple posts about screen resolution issues in 12.04 but nothing that was close enough to my situation. I've been searching the internet and have asked in several irc channels about this; but, so far, have come up empty.

I have two vm's running on kvm and use virt-manager. One is Ubuntu 12.04 LTS (desktop for AMD/ 64 bit) and the other is Fedora 16. Everything is 64 bit. They both only use only part of the screen and no option for higher relolution setting is available with either of them (through systems settings > displays). Aproximately 3 inches is cut off from each side of the monitor that is not being used. Monitors are Samsung 23 inch which use 1920 x 1280 resolution, 1080p HD, and I think 70 hz (or was it 75 - doing this from memory). They are both connected through dvi. My graphics card is an evga gt 440 (nvida/ dual head card) with 1024 gb ddr3 and (I think, twinview). I actually have two of those monitors (dual monitor) but my primary concern right now is the resolution.

I'm not sure if the problem lies in the virutualization or the vm and I don't know where to look to find out. Can anyone help me diagnose this problem?

Thanks for taking the time to read this.

Jake

PS: The host system is Ubuntu 12.04 Server (so 12.04 server as host, a 12.04 desktop vm, and a fedora 16 vm with the same problem). Also, I should note that I have attempted to change the vm to use spice instead of vnc but get an error message and kvm/ virt-manager is unable to do it. I was just guessing that switching to spice might help my cause but that's all it was is a guess (maybe it wouldn't). I also have looked for drivers in additional drivers but nothing comes up. On a normal ubuntu install (not vm) drivers always come up during the install but they didn't with the vm install or the host install and there is nothing coming if I go to additional drivers through the dash.

Thanks
---------------------

Edit:

I should make a correction because I'm not sure if it's relevant or not. There are a grand total of 3 vm's on the machine. Windows 7 is the third but I've had no resolution problem with it. Just to note that it does exist on the machine.

---

### Post by rstonehouse on 2012-09-22
I had this problem (screen resolution in ubuntu 12.04 VMs as well)

This has been fixed for the up-coming ubuntu 12.10 as tracked in
  [https://bugs.launchpad.net/bugs/1022222](https://bugs.launchpad.net/bugs/1022222)

For 12.04 I had success in updating just the "vgabios" package to this new version. Get it from
  [http://packages.ubuntu.com/quantal/all/vgabios/download](http://packages.ubuntu.com/quantal/all/vgabios/download)

Hope this helps.

---

