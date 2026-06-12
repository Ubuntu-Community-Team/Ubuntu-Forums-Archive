---
title: "Using a USB to Ethernet Adapter"
date: 2019-10-02
forum: New to Ubuntu
---

### Post by kevinuulong on 2019-10-02
I am running ubuntu server LTS and am trying to hook my device up to the internet. As my device does not have an ethernet port, I am trying to use a USB to Ethernet adapter. Both of these devices are working on Windows, but when I try to plug it in to my device running ubuntu server it does not recognize it. I have searched all over and tried just about everything I can find, but have had no luck, how can I configure this adapter to work with my device.

Thanks,
Kevin Long

---

### Post by TheFu on 2019-10-02
So ... I use a USB3-to-GigE adaptor from my laptop to connect to the world.  I've been using something like this since my first chromebook in 2013.  IME, Ubuntu Server expects a well known, wired, ethernet card and doesn't have all the same drivers pre-loaded that the desktop versions have.

With the desktop version install, my USB3-to-GigE adaptor was recognized.  The challenge is getting the correct driver onto the system, with is a chicken/egg problem for network devices.  Normally, to get a list of network devices, you'd need something like these commands:
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
sudo lsusb -v  |egrep 'Ether|Network'
lsmod |grep usbnet
sudo lshw -C network
```
The first two only show wifi devices on my laptop.  The last three give more data, but only because the driver is loaded and working.

Thinking about this a little, you might try booting from a desktop install flash drive, then running the last 3 commands, finding the correct package(s), copy that package(s) off to other storage, then do a server install and use the just copied packages to install the driver needed.  If going this route, beware that every dist-upgrade might require something similar.  Also, be certain that the kernel line used for the server release and desktop release are the same.  If you are running a 4.15 kernel on the server, then you want to use a desktop install ISO on the flash boot running that same kernel version.

That's my theory about this.  No guarantees.

I wimped out and installed a very lite Ubuntu Desktop, then removed all the GUI stuff, network-manager* ... and lots of other GUI tools until no GUI login was presented.  I call it a "server" now.  ;)  Close enough?

---

### Post by rsteinmetz70112 on 2019-10-03
If your device has WiFi you could go to Starbucks and download what you need over WiFI. :p

---

### Post by kevinuulong on 2019-10-03
Is there a way I could connect my device to wifi? I was under the impression the server install of ubuntu was unable to connect to wireless networks.

---

### Post by cruzer001 on 2019-10-03
The server.iso will automatically hookup to wifi during the install.

---

