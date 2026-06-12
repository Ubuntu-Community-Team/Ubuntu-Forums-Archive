---
title: "Home Server build?"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by fredfillis on 2013-02-12
About to start a home server build, primary purpose will be to serve as a NAS to windows 7 network plus an XBMC based HTPC (yet to be built).

I'm planning on installing ubuntu server 12.04, create some samba shares and run FlexRAID. I want to store media files on this NAS primarily. Don't plan on doing much of anything else at this point. 

I'd like to poke this machine into a cupboard somewhere with no monitor, keyboard etc needed after setup.

I've read a bunch of stuff about "headless" setups and am now more confused than educated!

Seems that a preferred way to make headless work is to tweak BIOS to allow boot with errors. I'm ok with that, providing it is not going to be a problem if I need to access the machine for admin purposes.

So, what would be the recommended way to arrive at a headless setup? What is the best way to access the machine for admin purposes?

Thanks!

---

### Post by matt_symes on 2013-02-12
Hi
 
> What is the best way to access the machine for admin purposes?

 
I administor my server using ssh and keys. 
 
I also use mediatomb as that has a web front end. 
 
You may also find something like webmin useful.
 
Kind regards

---

### Post by fredfillis on 2013-02-12
> **matt_symes said:**
> Hi
 

 
I administor my server using ssh and keys. 
 
I also use mediatomb as that has a web front end. 
 
You may also find something like webmin useful.
 
Kind regards

Hey thanks Matt. I'm vaguely familiar with webmin, having chucked it on my ancient laptop "test box" a few days ago. Seems it has much more than a noob like me would ever want!

---

### Post by wlraider70 on 2013-02-12
I've played around a good bit with headless severs. The most reliable way is using ssh. I would just use a password if you are behind a firewall, Google Authenticator if you have open ports. 

Webmin is okay, I have it on one of my servers, but if you nothing about webmin or command line, it makes more sense to use command line than webmin. All the guides you find will be in command line. 

lastly, some people don't realize that ubuntu desktop and server are essentially the same other then the gui. You don't put a gui like x11 on a server. I tried this once with the hope of using VNC or and it was a nightmare that caused boot errors and what not.

In the bios you might not have to do anything. The most you should need it to tell not "halt" on errors.

---

### Post by collisionystm on 2013-02-12
Check out Plex while you are shopping around for HTPC set ups.

---

### Post by fredfillis on 2013-02-13
> **wlraider70 said:**
> I've played around a good bit with headless severs. The most reliable way is using ssh. I would just use a password if you are behind a firewall, Google Authenticator if you have open ports. 

Webmin is okay, I have it on one of my servers, but if you nothing about webmin or command line, it makes more sense to use command line than webmin. All the guides you find will be in command line. 

lastly, some people don't realize that ubuntu desktop and server are essentially the same other then the gui. You don't put a gui like x11 on a server. I tried this once with the hope of using VNC or and it was a nightmare that caused boot errors and what not.

In the bios you might not have to do anything. The most you should need it to tell not "halt" on errors.

Thanks for the tips. Not familiar with SSH at this point, somewhat like VPN from the little that I have read. Assume I remotely connect to the server via SSH then run terminal to access CLI. I have some "experience" with CLI so that is not a problem.

---

### Post by wlraider70 on 2013-02-13
Think of ssh as a remote terminal connection. 
All it is is text based. 

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by Maheriano on 2013-02-13
I run a headless server which sits at a client site, I use SSH to administer it. I just made sure to edit one of the files (don't remember which one) which tells it to get the same internal IP from the switch every time it boots up and set a reservation on the switch itself for that specific IP. I also set it up to install updates automatically so I don't have to do it manually. It's been running great for 6 months.

---

