---
title: "Please help new user!"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by thedude2008 on 2008-08-11
I'm a new user, having installed ubuntu after windows crashed. I have been trying to configure a VPN.I followed the instructions but no connection-what am I doing wrong? 

Also as there are many things I can't do on ubuntu which I used to do on Windows, is there a way of getting Windows back on my computer without killing ubuntu?

Many thanks

---

### Post by Bölvaður on 2008-08-11
Well because Im in such a good mood for doing complete reinstallations... would you consider doing one? It is possible to install windows but because windows isn't very friendly to other OSes perhaps a reinsatllation might be acceptable if you have no data or big collection of programs installed.

---

### Post by hyper_ch on 2008-08-11
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by Vishal Agarwal on 2008-08-11
Installing Windows will overwrite the boot section at HDD, and u will need to install grub boot loader again to recover the UBUNTU.

Perhaps it should be there and not over written by windows.

---

### Post by ByteJuggler on 2008-08-11
> **thedude2008 said:**
> I'm a new user, having installed ubuntu after windows crashed. I have been trying to configure a VPN.I followed the instructions but no connection-what am I doing wrong? 

Also as there are many things I can't do on ubuntu which I used to do on Windows, is there a way of getting Windows back on my computer without killing ubuntu?

Many thanks

What type of VPN are you trying to connect to?  Connecting to some types of VPN can be problematic (e.g. connecting to Cisco 3000 concentrator using PPTP doesn't work, although the Vpnc (or whatever) IPSec one does, with a bit of coaxing.)

As for your other problems, please start seperate threads, 1 for each problems, with a descriptive title, explaining the essence of the problem for that thread.

---

### Post by thedude2008 on 2008-08-11
Thanks for all your help and sorry for not following the correct posting conventions. I'll try and do it better in future!

Bölvaður-I would be happy to reinstall Windows-nothing to lose really-best way to do it?

---

### Post by thedude2008 on 2008-08-11
ByteJuggler

Just found VPN which said it would work in Linux-VPN gates it was called. They gave me a test run and it worked fine-but when I subscribed it didn't work

---

### Post by ByteJuggler on 2008-08-11
> **thedude2008 said:**
> ByteJuggler

Just found VPN which said it would work in Linux-VPN gates it was called. They gave me a test run and it worked fine-but when I subscribed it didn't work

At the risk of repeating myself :)  What type of VPN are you trying to connect to?  What have you tried so far, exactly, on Linux?   

I'm not familiar with the package you refer to (but googling "VPN gates" did turn up [this]("http://www.vpngates.com/").) Is this what you're trying to connect to? I might add that should not have to subscribe/buy anything, generally, just to get your VPN working.  Normally the VPN you're trying to connect to exists already (e.g. your company's VPN) and you just need to configure your client to connect to it.  VPN Gates provides a third-party VPN service.  Are you sure that's what you want?  You might look into "[Hamachi]("https://secure.logmein.com/products/hamachi/vpn.asp?lang=en")" for something that has a free (as in $$$ ) option.  That said, if you simply want to set up a simple VPN and you have some patience, you can run a VPN server yourself, on your own Linux box, without involving a third party.

If you're actually trying to connect to e.g. your work's VPN then I re-iterate that you need to tell us the type and then we can try to help you connect to it.

---

