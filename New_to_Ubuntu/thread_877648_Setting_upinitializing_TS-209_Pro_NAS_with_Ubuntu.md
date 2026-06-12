---
title: "Setting up/initializing TS-209 Pro NAS with Ubuntu"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by infinitejones on 2008-08-02
I've bought a TS-209 Pro NAS unit and I've plugged in a hard drive. I'm trying to get it all set up but it assumes you've got either Windows or a Mac to run the set-up software and I've got neither!

I'm trying to run the Windows software on the disc using WINE but QNAP Finder keeps saying it can't find it on the network, even though my router has given it an IP address and I can ping it from my Ubuntu machine.

Also when I type the IP address into a browser I get System Information screen telling me "The system is not configured" in loads of different languages so clearly there's no problem with my Ubuntu machine and the NAS being able to see/talk to each other.

Installing Windows on my Ubuntu machine isn't an option (even in a virtual machine) because I don't have a valid Windows licence, which is why I'm running Ubuntu in the first place!

It seems crazy that all the marketing material and reviews on the internet make a big thing about the fact that it runs Linux and you can't even set it up without using Windows or OSX!

Any suggestions?

---

### Post by gmalac on 2008-09-04
This page gives information I hope can help
[URL="http://www.qnap.com/pro_features_server.asp"]
[http://www.qnap.com/pro_features_server.asp](http://www.qnap.com/pro_features_server.asp)[/URL]

Guy

---

### Post by infinitejones on 2008-09-05
Thanks for the link but it doesn't really add much - it's just instructions on how to use the (Windows only!) installation app.

I eventually got it all working by borrowing a friend's Windows laptop. The application is just a VB app (not even a very well written one!) that runs a load of installation scripts. This is very annoying because I would imagine that porting it to GTK wouldn't be difficult at all! It's a linux machine that the scripts are running on, after all...

---

### Post by fixeon on 2008-09-11
Bump, Looks like weird to have to run windows to initialize a linux operated device....

So far no answer found.
Anyone can help?

---

### Post by con on 2008-10-20
I'm in the same position as the original poster was. 
I installed a virtual copy of Windows XP using Virtual Box and tried to use this to set up the NAS. In order for the finder app to work it needs any firewall/virus software to be turned off. Its a base install of windows and I've turned off the windows firewall but I still can't get QNAP finder to work. The Windows machine is able to access the network and is even able to get to the "This system is not configured" page on the NAS.

So my question, is there something funny involved with networking with a virtual machine that would stop the QNAP finder app from connecting to the NAS, like a firewall might do.

By the way QNAP actually claim Linux support, TUX is on the front of the retail box and the back says Linux/UNIX client support.

---

