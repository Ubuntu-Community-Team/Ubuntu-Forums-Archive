---
title: "Ubuntu in VM VirtualBox"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by davecompton on 2012-03-07
Hello

I've recently installed Ubuntu – via Oracle VM VirtualBox -  on my laptop which runs Windows 7 The laptop uses a wireless connection on my home network. 

However, the network settings in Ubuntu say that I'm using a wired connection. How can this be? And how can I change it so that it uses the wireless connection 

Thanks in advance :D:D:D

---

### Post by cbennett926 on 2012-03-07
I know this is mundane, but it perhaps could be where the problem lies, have you checked the network settings on the virtualbox?

---

### Post by snowpine on 2012-03-07
Welcome to the forums!

A "virtual machine" is exactly that; the "guest" operating system (Ubuntu in your example) does not know that it is running in a virtual machine, it is not aware of your actual physical hardware, it sees only the virtual hardware emulated by VirtualBox.

[http://en.wikipedia.org/wiki/VirtualBox#Hardware_device_emulation](http://en.wikipedia.org/wiki/VirtualBox#Hardware_device_emulation)

Are you having any actual trouble with connectivity, or just curious how it all works?

---

### Post by haqking on 2012-03-07
as mentioned above me.

as long as you have connectivity dont worry about it, a VM cannot see or use internal wifi hardware it can only virtualise it.

It can use a USB wifi device accessed directly from the VM but internal wifi will be seen as a internal ethx device and by default use NAT.

Peace

---

### Post by davecompton on 2012-03-07
> **haqking said:**
> as mentioned above me.

as long as you have connectivity dont worry about it, a VM cannot see or use internal wifi hardware it can only virtualise it.

It can use a USB wifi device accessed directly from the VM but internal wifi will be see as a internal eth device and by default use NAT.

Peace

thanks - much appreciated

---

### Post by davecompton on 2012-03-07
> **snowpine said:**
> Welcome to the forums!

A "virtual machine" is exactly that; the "guest" operating system (Ubuntu in your example) does not know that it is running in a virtual machine, it is not aware of your actual physical hardware, it sees only the virtual hardware emulated by VirtualBox.

[http://en.wikipedia.org/wiki/VirtualBox#Hardware_device_emulation](http://en.wikipedia.org/wiki/VirtualBox#Hardware_device_emulation)

Are you having any actual trouble with connectivity, or just curious how it all works?

Just curious I suppose, thanks for the reply

---

### Post by davecompton on 2012-03-07
> **cbennett926 said:**
> I know this is mundane, but it perhaps could be where the problem lies, have you checked the network settings on the virtualbox?

Doesn't seem to affect connectivity - so i guess it's not worth worrying about. Thanks for your response. I'm sure to be asking for a lot more help in future :D

---

### Post by davecompton on 2012-03-07
All you guys - thanks for the prompt response. I want to learn as much as I can and I'm sure there will be many more questions along the way. (most of them dumb questions)   :D:D:D

---

