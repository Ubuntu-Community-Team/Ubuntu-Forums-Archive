---
title: "Installing ASUS USB N-10 for VirtualBox OS only since wifi already works on host"
date: 2015-11-17
forum: New to Ubuntu
---

### Post by newone3 on 2015-11-17
Hello,

I am new to Ubuntu and VirtualBox, and have just picked up an ASUS USB-N10 wifi adapter so that I can have wifi on VirtualBox. 

I have tried to install it and I am not sure if it is working. 

I have followed various threads and tried installing it, but when I go to USB on VirtualBox for my guest OS  can't find the device.

I recently fixed the wifi on the laptop so it works fine, it just does not transfer to the virtual box. I read this was an issue with virtual box. 

Any help is appreciated.

Thanks.

---

### Post by Vladlenin5000 on 2015-11-17
Hi and welcome.

First of all, terminology: Virtualbox is a virtualization software, not an operating system.
That said, for most (home) usage scenarios, the VM (virtual machine) does not require a separate network connection, wifi or otherwise. The guest OS simply uses a bridged connection from the host OS seamlessly managed by Virtualbox. When it doesn't there's something wrong with that VM's settings.

Now, forget about the WiFi dongle for a moment and focus on the VM's network settings. 
What OSs are you running? Host and guest.
Which Virtualbox version? VM's network settings?

PS - When requesting help please provide all the relevant details.
The thread title is misleading. Albeit understandable - you explained where it comes from - the title doesn't point to the actual problem.

---

### Post by mastablasta on 2015-11-17
would be good if you posted a screenshot of virtualbox networking and network adapter that is set up.

otherwise: [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

---

### Post by newone3 on 2015-11-17
[COLOR=#DD4814][COLOR=#000000][Vladlenin5000]("http://ubuntuforums.org/member.php?u=1468732"): I am running Ubuntu 14.04 installed alongside the original Windows Vista. I have a Kali guest in Vbox. 

I am using VirtualBox 5.0.10 for Linux installed and running in Ubuntu. 

I have tried all different network connections: NAT, Bridged Connection, and all the others to no avail. 

Thanks for the help and tips.
[/COLOR][/COLOR]

---

### Post by cariboo on 2015-11-18
If Kali doesn't support your builtin wifi adapter, you are never going to get it to work in Kali installed in vbox. VirtualBox works on virtual hardware, not actual hardware. If you want to use Kali, I suggest installing directly on your hard drive. For support for Kali go [here]("https://forums.kali.org/"), as we do not support it here.

---

### Post by mastablasta on 2015-11-18
or try Backbox Linux instead which is Ubuntu based.

Kali is debian. and debian has issues with proprietary drivers :)

---

### Post by newone3 on 2015-11-18
[COLOR=#000000]mastablasta: [/COLOR][COLOR=#000000]cariboo: [/COLOR]Thanks yea i just tried using Iceweasel on Kali for the first time and it worked! I had wifi all along!

thanks!

---

