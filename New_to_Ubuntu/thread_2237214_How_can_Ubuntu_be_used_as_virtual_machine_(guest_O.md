---
title: "How can Ubuntu be used as virtual machine (guest OS) to access the internet securely?"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by Eric_Feder on 2014-07-31
I want to useVirtualBox to install Ubuntu as a guest OS (virtual machine) with XP as the host. I want to use Ubuntu as virtual machine (guest OS) to access the internet securely. Originally, I was going to install Ubuntu as a second OS in a new partition on the hard drive, but is too inefficient to re-boot from XP to Ubuntu and back. Also, there is a risk I might tank XP when I install Ubuntu, and I understand that there is very little risk if Ubuntu is installed as a virtual machine instead. Unfortunately, it is not in my budget to upgrade to Windows 7, and I have numerous forms with reference fields in Word 2003 and Excel 2003 spreadsheets with extensive macros I wrote. It is not practical to switch to Ubuntu as my primary OS.
 
**However, I understand that if you have an ethernet cable plugged into the computer, it will automatically connect to the internet during the boot up.** It doesn't matter whether you don't use it, the connection will be there and attacks can be delivered against your machine. However, if you disable the lan adapter in XP there is very little chance of and attack on XP.
 
My question is whether, if I disable the lan adapter in XP, I can nevertheless enable a lan adapter in Ubuntu operating as the guest OS so I can install and use Google Chrome in Ubuntu so securely access the internet. 
 
Will this work, and will it be relatively secure?
 
What, if any, features of XP does Ubuntu used when it is operated as virtual machine use? I read that the virtual machine cannot directly access the hardware.

---

### Post by JKyleOKC on 2014-07-31
> **Eric_Feder said:**
> My question is whether, if I disable the lan adapter in XP, I can nevertheless enable a lan adapter in Ubuntu operating as the guest OS so I can install and use Google Chrome in Ubuntu so securely access the internet. 
 
Will this work, and will it be relatively secure?
 
What, if any, features of XP does Ubuntu used when it is operated as virtual machine use? I read that the virtual machine cannot directly access the hardware.No, it will **not** work as you describe -- but it would be very secure since it would not connect to the outside world.

Specifically, the virtualization program must use the physical hardware, so if you disable the LAN adapter itself, there's nothing available to make the connection. On the other hand, it's (barely) possible that if you leave the adapter itself enabled and disable the connection in XP's control panel/network connection applet, the virtualization program could still access it and make your plan work. The only way to know for certain, I suspect, will be to try it and see what happens.

I have a situation similar to yours (production systems using Word 2000 and Publisher 2003) but am running Xubuntu as the host system with XP in virtual machines. In my systems, when I create a new VM I must specify the host interface to use for its network connections. This implies that the host networking **must** be active before the guest can work; I don't know whether the same would be true with host and guest roles reversed but I believe it would be. That would make your plan impossible to implement.

As for automatically connecting during boot-up, that may happen if you have the Windows "automatic updates" feature turned on, but I've never seen it happen with any of my Windows host systems going back to Win95 days. In any event a good router or firewall that can block outgoing traffic can easily defeat such an action. Even the Windows firewall that's part of XP can offer quite a bit of protection!

While the VM itself does not (normally) access the host hardware **directly**, the virtualization program that makes the VM work at all **does** do so. And in certain cases, the VM can do direct access -- it's called "passthrough" operation and is most often applied to disk storage situations.

---

### Post by Vladlenin5000 on 2014-07-31
> **Eric_Feder said:**
> My question is whether, if I disable the lan adapter in XP, I can nevertheless enable a lan adapter in Ubuntu operating as the guest OS so I can install and use Google Chrome in Ubuntu so securely access the internet. 

No, it won't work. AFAIK WiFi USB dongles (and other USB devices) can be added to the guest OS, consequently disabling it in the host, and then a separated and independent network connection can be configured in the guest.

---

### Post by monkeybrain20122 on 2014-07-31
You should do it the other way around. Install Ubuntu in your hard disk and then install XP in VB and disable networking if you must keep XP. XP is dead, Ubuntu is a much better OS.

---

### Post by Eric_Feder on 2014-07-31
Thank you for your very informative reply. I think I will just disable automatic updates I Windows XP and accept whatever risk there may be. By the way, is there a way to prevent files on the external hard drive used to back up XP from being destroyed by a virus that infects XP, or by a hacker? It seems as if XP gets hacked, the hacker gains access to the external hard drive. I don't know if a virus can do that.

Eric Feder in Rochester New York

---

### Post by Eric_Feder on 2014-07-31
I just saw Vladlenin5000's reply.
 
I think I found a solution without a WiFi USB dongle. Put a fixed IP address on my host PC running XP and then block that IP address in the access restrictions page of my router. The host still has full access to the office network, but is cut off from internet access. The guest has a different IP address, so it is able to access the web.

I don't want to install Ubuntu as the host and XP as the guest because I have too many specialty programs installed with XP not compatible with Ubutu. and it would be a very time consuming project. Eventually I will upgrade to Windows 7. Perhaps at that point I should install Windows 7 as the guest, so when support ends I can still safely use the internet as monkeybrain suggested. I am afraid I am stuck with Windows because of the software I need that only works with windows.

---

### Post by ian-weisser on 2014-07-31
> **Eric_Feder said:**
> [I]s there a way to prevent files on the external hard drive used to back up XP from being destroyed by a virus that infects XP, or by a hacker?

No.
If your XP is compromised, you also have no way to prevent it from damaging or destroying the VM


> **Eric_Feder said:**
> I have too many specialty programs installed with XP not compatible with Ubu[n]tu.

Then you have a risk issue. Are you willing to put those specialty applications at risk by installing complexity (Ubuntu VM) or exposing your system to known vulnerability (by continuing to use XP)? If so, I would recommend good backups.


You _can_ use an Ubuntu VM to access the internet (using a different IP than the host). However, your hardware must be quite robust for XP-era systems, or you may find it to be a slow, inconvenient, and unsatisfying solution.

And, of course, none of your XP applications will be able to use the Ubuntu network connection.

---

### Post by mastablasta on 2014-08-01
> **Eric_Feder said:**
> Thank you for your very informative reply. I think I will just disable automatic updates I Windows XP and accept whatever risk there may be.
windows XP is still receiving updates for it's malicious software removal tool. you should strat planning on migrating oyur data and such.

BTW Word & Excell  2007 work well in wine.

> 
 By the way, is there a way to prevent files on the external hard drive used to back up XP from being destroyed by a virus that infects XP, or by a hacker?

unplug the drive when it is creating backups. use versioned backup or use Linux live CD to do manual backups to ext. partition (which windows can't read without 3rd party tools.

> **JKyleOKC said:**
>  In any event a good router or firewall that can block outgoing traffic can easily defeat such an action. Even the Windows firewall that's part of XP can offer quite a bit of protection!


this! use router's firewall to protect LAN computers. adiditonaly you can use Comodo or Zonealarm firewall to protect windows computer and to add another layer use a descent antivirus. all these still get patches and updates for XP.

this would give you enough time to plan on a migration. either as one said to stick windows XP inside virtual box or something else completely. I am not sure if you tried your files in libre office. as I know files made with 2007 and 2003 should be compatible. you can also try Kingsoft (WPS) office where compatibility is said to be even better.

if you use virtualbox only to access internet you may want to look at minimum install and just run some basic light desktop (e.g., xfce, lxde) or even just a windows manager (icewm, jwm...) and browser in it. it would start fast that way or restore from snapshot (even faster).


Ubuntu minimal install: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Ubuntu virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

If your system specs are not too good it will be much better to install Lubuntu or Xubuntu in it if you go down the full DE path...

---

### Post by JKyleOKC on 2014-08-01
> **Eric_Feder said:**
> I think I found a solution without a WiFi USB dongle. Put a fixed IP address on my host PC running XP and then block that IP address in the access restrictions page of my router. The host still has full access to the office network, but is cut off from internet access. The guest has a different IP address, so it is able to access the web.

I don't want to install Ubuntu as the host and XP as the guest because I have too many specialty programs installed with XP not compatible with Ubutu. and it would be a very time consuming project. Eventually I will upgrade to Windows 7. Perhaps at that point I should install Windows 7 as the guest, so when support ends I can still safely use the internet as monkeybrain suggested. I am afraid I am stuck with Windows because of the software I need that only works with windows.Unfortunately your solution won't work quite like you expect. If you block all incoming access to your guest, at the router, then you might as well totally disconnect from the network since that block will prevent ANY connection from completing. The network protocols use "handshakes" to confirm connections, so blocking incoming traffic stops them.

It's possible to set up firewall rules that prevent incoming packets from initiating connections while still allowing responses to requests that you have initiated yourself, but most consumer routers don't have such rules and don't provide access to their internal rules.

Even if you had such a setup, it still would not protect against the most tricky forms of malware, which do "drive-by" infection. That is, a perfectly good web site can become infected, and then when you access that site, the malware "rides piggyback" on your browser's connection to infect your system. Many, if not most, of the current malware problems seem to be propagated in this fashion -- and as fast as the "good guys" come up with a defense, the "black hats" find new vulnerabilities.

Unfortunately, no really good solution seems likely in the foreseeable future. All we can do is remain aware of the risk, and take whatever steps we can to minimize it. These steps include, but aren't limited to, keeping up-to-date backup copies of everything, including full disk images of the entire system so that in case of infection, you can blow away the entire system and restore it from a known good disk image. Once an infection takes place, that's the only way to restore confidence that the system is clean again.

---

### Post by 3rdalbum on 2014-08-02
Vladlenin's approach is probably the best one I can think of. Disable your internal LAN adapter and instead use a USB LAN adapter (you can get them pretty cheaply from eBay). Set up "passthrough" in the virtual machine software so the guest OS can access the USB adapter directly. Don't install the driver in Windows. This is exactly what you are asking for.

I'll just remind you of something, though, which may make things easier for you: If you have a firewall blocking all incoming connections, and you don't actually start up Internet Explorer and go surfing the web, you will not pick up any viruses. If you ONLY open an internet program on Ubuntu, and have a firewall on Windows or inside your modem, you'll be absolutely okay.

---

### Post by Rob Sayer on 2014-08-03
> **monkeybrain20122 said:**
> You should do it the other way around. Install Ubuntu in your hard disk and then install XP in VB and disable networking if you must keep XP. XP is dead, Ubuntu is a much better OS.

That's exactly what I was thinking.  100%.  Run XP in a VM for tools you can't get a substitute for in linux (which for me is only ripping DVDs, YMMV) and never connect Windows to the net again on that machine.

Even if you could do it as described you'd still have all the XP security problems.  And quite possibly get your linux partition destroyed by a virus along with the windows one.

---

