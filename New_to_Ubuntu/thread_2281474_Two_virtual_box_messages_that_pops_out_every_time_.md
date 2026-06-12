---
title: "Two virtual box messages that pops out every time I turn on a virtual machine?"
date: 2015-06-07
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-06-07
The first one is: 
 The virtual machine window is optimized to work in 32 bit color mode but the virtual display is currently set to 16 bit.
 Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
 Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color mode to see if this message disappears or you can simply disable the message now if you are sure the required color mode (32 bit) is not available in the guest OS.
The second one is: 
The Virtual Machine reports that the guest OS does not support mouse pointer integration in the current video mode. You need to capture the mouse (by clicking over the VM display or pressing the host key) in order to use the mouse inside the guest OS.
Can you guys please tell me why this thing happened in the first place and then help me to solve it.
This is my very first time with VirtualBox.

---

### Post by CharlesA on 2015-06-07
Sounds like you need to install the Guest Additions.

See here:
[https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html)

---

### Post by v3.xx on 2015-06-07
Yep, sounds like guest additions is needed.
> select a 32 bit color mode
I had this problem on a previous box.  It had poor built in graphics and did not get resolved.  However performance was good without it.  My current box does not get this warning, but I have optional graphic driver installed and tend to think this helps.  Plus I have the option to use 128M for video ram. Have you been here?
[https://www.google.com/search?client=ubuntu&channel=fs&q=select+a+32+bit+color+mode+virtualbox&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=select+a+32+bit+color+mode+virtualbox&ie=utf-8&oe=utf-8)

---

