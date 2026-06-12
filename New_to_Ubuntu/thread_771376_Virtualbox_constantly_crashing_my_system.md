---
title: "Virtualbox constantly crashing my system"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by grazed on 2008-04-27
Hi, I'm using Virtualbox to run an XP installation from within ubuntu. The install goes smoothly, though once I log into XP, my entire system will crash randomly within 5 minutes.

Not exactly sure what is causing it, but here are the last sys.log entries before it happens..

Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>    address 192.168.1.2 
Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>    netmask 255.255.255.0 
Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>    broadcast 192.168.1.255 
Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>    gateway 192.168.1.1 
Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>    nameserver 208.67.222.222 
Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>    nameserver 208.67.220.220 
Apr 27 08:09:43 insomnia-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 27 08:09:43 insomnia-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 27 08:09:43 insomnia-laptop avahi-daemon[5159]: Withdrawing address record for 192.168.1.2 on wlan0.
Apr 27 08:09:43 insomnia-laptop avahi-daemon[5159]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.2.
Apr 27 08:09:43 insomnia-laptop avahi-daemon[5159]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 27 08:09:43 insomnia-laptop avahi-daemon[5159]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.2.
Apr 27 08:09:43 insomnia-laptop avahi-daemon[5159]: New relevant interface wlan0.IPv4 for mDNS.
Apr 27 08:09:43 insomnia-laptop avahi-daemon[5159]: Registering new address record for 192.168.1.2 on wlan0.IPv4.
Apr 27 08:09:44 insomnia-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr 27 08:09:44 insomnia-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr 27 08:09:44 insomnia-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Apr 27 08:09:44 insomnia-laptop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Apr 27 08:09:44 insomnia-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 27 08:09:45 insomnia-laptop ntpdate[6122]: step time server 91.189.94.4 offset 1.360425 sec
Apr 27 08:09:47 insomnia-laptop kernel: [   73.943995] wlan0: duplicate address detected!
Apr 27 08:17:01 insomnia-laptop /USR/SBIN/CRON[6196]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 27 08:19:38 insomnia-laptop kernel: [  899.610722] sr0: CDROM not ready.  Make sure there is a disc in the drive.

any help would be greatly appreciated.

thanks.

---

### Post by nowshining on 2008-04-28
remove the version that you installed from the repos and install the one from the main virtualbox site, [http://virtualbox.org/](http://virtualbox.org/)

---

### Post by grazed on 2008-04-28
I did. =/

the non free one.

---

### Post by nowshining on 2008-04-28
the non free one is just open source - if you don't look/modify, etc.. @ the code - it makes no diff. Plus that & the non-open source one incl. support for a lot more stuff not incl. in the open source versions. Also non-free is FREE to download & use. :) you don't have to pay anything.

---

### Post by southernman on 2008-04-28
> **nowshining said:**
> **the non free one is just open source** - if you don't look/modify, etc.. @ the code - it makes no diff. Plus that & the non-open source one incl. support for a lot more stuff not incl. in the open source versions. Also non-free is FREE to download & use. :) you don't have to pay anything.Sorry, but the bold text above is just WRONG! ;) Your a wee tab mixed up there sparky.

[http://www.google.com/search?q=non-free+software&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=non-free+software&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

Carry on...

---

### Post by skymera on 2008-04-28
I use VirutalBox in WinXP but Ubuntu i typically use Qemu.
It's a lot lighter and when used properly its a lot quicker.

Takes a while to figure it out but it's worth it.

---

