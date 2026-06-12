---
title: "can Ubuntu &amp; Windows 7 software co-exist on same wireless router?"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by s1baker on 2012-03-21
hi,
I bought a Linksys wireless router ( WRT54GL ) and now I am going to try to set it up. I have a laptop that has Windows 7 on it, and in the near future I am going to put a dual boot Ubuntu 11.10 on it.
I have a set-up CD for the router ( for Windows ) and I was going to run it to install the router, but I don't want to overwrite anything already in the firmware of the router that will not let me use the router with 11.10 if I install the Windows CD.
Question:
Can I use the same router on both OS's on the laptop, 11.10 & Windows 7, or will installing the Windows software from the CD screw up my router when I go to set 11.10 up for the router ?

Here is a cnet website that has some specs on the router:
[http://reviews.cnet.com/routers/linksys-wireless-g-broadband/4507-3319_7-31639659.html](http://reviews.cnet.com/routers/linksys-wireless-g-broadband/4507-3319_7-31639659.html)

Thanks

---

### Post by Paqman on 2012-03-21
Routers don't care what OS connects to them, the communicate using internet protocols that are common to all systems.

Your "setup CD" that you've been given is probably superfluous. You can set up a router from any web browser just by going to the IP of the router and entering the password (the router will normally assign itself an IP like 192.168.1.1 or similar). Your setup CD just automates some of this process, but you don't have to use it if you don't want to. It doesn't actually install anything on the router, it just points your browser to the right place.

Bottom line: set up your router using the Windows CD if you like. Make sure you change the admin password for the router and the wifi SSID. Make note of the wifi password. When you install Ubuntu later all you'll need to do is enter the wifi password to get connected. You won't need to set the router up again.

---

### Post by Rex Bouwense on 2012-03-21
I know of no reason why computers using Microsoft Windows 7 and Ubuntu cannot both use the same router.  As a matter of fact I just set one up for a friend.

Sorry Paqman.  You beat me to the draw.  I only use two fingers to type so I'm a bit slow.

---

### Post by wildmanne39 on 2012-03-21
Hi, should be no problem I have 2 ubuntu machines and my wife has 2 window machines all on the same router, and I help with wireless networking issues and I have never heard of that being a problem.
Thanks

---

### Post by HiImTye on 2012-03-21
I use Ubuntu and Windows 7 (well, my girlfriend uses Win7) on the same network with no issues. if you are going to share files with Samba then make sure that the Win7 PC is set to a work network and enable lower level encryption. also, her computer has issues detecting mine to get share names, to fix that I just went to my computer by name (on the workgroup) and made a network drive.

hopefully this will help you with whatever future issues you may encounter

---

### Post by ccrs8 on 2012-03-21
Paqman is right - the default IP address for that particular router is 192.168.1.1.  You definitely won't have a problem connecting multiple OSs to the router.  Heck, my current router has two GNU/Linux machines (one hard, one wifi), two Windows machines (one hard, one wifi), two ROKUs (one hard, one wifi), and two Android phones (wifi, obviously).

One suggestion I do have is to get familiar with and use the web-based configuration interface reachable via that IP address above.  That way no matter what computer you have now or in the future, the interface will be the same and one you are familiar with (as opposed to always needing a windows machine with the CD at your disposal).  Also, if my recollection is right, sometimes you can't do everything with the CD...some of the "Advanced" features of the router are only accessible via the web interface.

---

### Post by s1baker on 2012-03-21
Then having 2 different OS's dual booting off of the same laptop and using the same router doesn't make any difference? 

Thanks guys, will call this one solved soon.

---

### Post by PapaGary on 2012-03-21
> **s1baker said:**
> Then having 2 different OS's dual booting off of the same laptop and using the same router doesn't make any difference? .
Nope, I'm doing it right now. Oh, I can confirm that you can log on to your router from a Ubuntu box. I just did it with mine.

---

### Post by Mark Phelps on 2012-03-22
To calm your fears ... the Linksys (or Cisco, these days) software supplied with the router doesn't actually install anything to the router itself.  It just installs software on the PC that helps you maintain the router.  In the case of newer Linksys routers, this is usually Cisco Connect.

You don't really need that software, for if you enter the router's IP address in any browser, it will bring up screens in the browser -- you can do any maintenance that way.

The router itself has no knowledge of the OS the PC is using to connect to it, it's only getting data packets from across the network.

---

