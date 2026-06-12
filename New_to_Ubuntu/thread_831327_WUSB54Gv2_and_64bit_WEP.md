---
title: "WUSB54Gv2 and 64bit WEP?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by lockerhaxor on 2008-06-16
Hey everybody,

I'm a fairly new Ubuntu user (but I love Ubuntu soooo sooo much ^_^) however I'm having one issue. I have to have Wireless, as this is a laptop, and I have a USB adapter: Linksys WUSB54Gv2. 

I have wine installed on this computer, however I don't think it would be a good idea to install a .exe for a driver.

Does anyone have, or know where to get, or how to install the drivers for this certain model? I would appreciate it, as I want to run Ubuntu on this Laptop permanently.

ALSO:

MY current network is configured for a 64bit WEP key. On another computer where I got the wireless running, it was unable to connect to the 64bit WEP key, it only prompted me for a 128bit key. Is there any way around this, or something I need to change?

Thanks,
Lockerhaxor

---

### Post by RequinB4 on 2008-06-16
Hey!  Welcome to ubuntu.  Try in order:

1)  Go to system - administration - hardware drivers

2) What is the output of
```

lspci | grep Linksys

```

3) "ndiswrapper" is a program that will allow you to do windows drivers, but the specifics depends on the output of 2

---

### Post by Old_Grey_Wolf on 2008-06-16
The WUSB54G should work with 7.10 or 8.04 without installing drivers. They should already be installed.

> **lockerhaxor said:**
> 
MY current network is configured for a 64bit WEP key. On another computer where I got the wireless running, it was unable to connect to the 64bit WEP key, it only prompted me for a 128bit key. Is there any way around this, or something I need to change?

I'm not sure what the above means. Your network is set up for 64bit WEP, yes/no?
The other computer you used would not connect using the same WUSB54G, yes/no?
The other computer is running what OS?

---

### Post by stchman on 2008-06-16
> **lockerhaxor said:**
> Hey everybody,

I'm a fairly new Ubuntu user (but I love Ubuntu soooo sooo much ^_^) however I'm having one issue. I have to have Wireless, as this is a laptop, and I have a USB adapter: Linksys WUSB54Gv2. 

I have wine installed on this computer, however I don't think it would be a good idea to install a .exe for a driver.

Does anyone have, or know where to get, or how to install the drivers for this certain model? I would appreciate it, as I want to run Ubuntu on this Laptop permanently.

ALSO:

MY current network is configured for a 64bit WEP key. On another computer where I got the wireless running, it was unable to connect to the 64bit WEP key, it only prompted me for a 128bit key. Is there any way around this, or something I need to change?

Thanks,
Lockerhaxor

My advice is to not use WEP as it is easily defeated.  Go with WPA or WPA2 with at least a 30 character passphrase consisting of uppercase, lowercase, numbers, and symbols.

---

### Post by DirtDawg on 2008-06-16
Drivers are included with Hardy that do work, but they are not great, IMO. I had serious problems with the signal strength of the provided driver as well as occasional lockups. If you also have problems, follow the first post on [page 13 of this thread]("http://ubuntuforums.org/showthread.php?t=588045&page=13") (by Pavlick), it will give you step by step instructions about how to install the Windows drivers on your Ubuntu machine(64bit WEP supported) . 

There are a few small mistakes in these instructions that I address in the [very last post]("http://ubuntuforums.org/showthread.php?t=588045&page=19") of the same thread.

EDIT: I just realized you are using WUSB54Gv**2** when the instructions I pointed you to are for WUSB54Gv**4**. Sorry for the mixup.

---

### Post by Old_Grey_Wolf on 2008-06-16
I agree with WPA being better than WEP; however, if the OP has been running a network with WEP for a while then a few hours will not matter. 

After the OP gets connected then the OP can figure out how to switch to WPA. 

The OP may have a reason for running with WEP, like a game console that does not supporting WPA or another computer with a Netgear WG111 USB adapter for example.

Edit: Yes, if WEP is necessary a DMZ could be set up, but lets getting him working first.

---

### Post by Old_Grey_Wolf on 2008-06-16
> **DirtDawg said:**
> I just realized you are using WUSB54Gv**2** when the instructions I pointed you to are for WUSB54Gv**4**.

I may give the instructions a try. When my neighbor turns on his repeater I have trouble staying connected. We have large houses, and some people use repeaters to get the signal to remote areas. I was going to buy a repeater; however, if the instructions work I can save a few $.

---

### Post by DirtDawg on 2008-06-16
> **Old_Gray_Wolf said:**
> I may give the instructions a try. When my neighbor turns on his repeater I have trouble staying connected. We have large houses, and some people use repeaters to get the signal to remote areas. I was going to buy a repeater; however, if the instructions work I can save a few $.

It's likely the instructions are nearly identical for the v2 model. Just make sure you have the right drivers for ndiswrapper and blacklisting. Goodluck.

---

### Post by lockerhaxor on 2008-06-16
The OS of the system I use for everything right now IS windows, however I need Ubuntu to read a 64bit WEP which it doesn't seem to be doing. I'm not to worried about security where I am, but then again it's best to have some. 

I appreciate all the help, and I will be trying these solutions.

---

