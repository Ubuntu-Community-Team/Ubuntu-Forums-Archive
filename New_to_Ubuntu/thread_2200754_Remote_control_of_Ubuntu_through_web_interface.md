---
title: "Remote control of Ubuntu through web interface?"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by marc13 on 2014-01-20
Can I access my Ubuntu 12.04 GUI interface at the login screen level from another computer? 

What I want to do is to leave my latop at home, connected to the internet and access it from around the world when I travel. This gives me a lot of flexibility as I can go a internet cafe, friends house etc. 

But I have a couple of questions regarding this being possible: 

- Can I access the GUI interface and log on if I sit on a Windows? 
- Does it require that the computer I connect from has Ubuntu One or is a Ubuntu environment itself? 
- Is there a web interface, online, that I can log into, and then access my desktop GUI that way? 
- Will I be able to setup access to enter my laptop from a phone/tablet as well? (I assume if web is possible, any device is then possible)
- Any ports to open? Do I need a fixed ip maybe? Other things? 

FYI: I do NOT want to use team viewer, it is very unstable through their web browser method.

---

### Post by madverb on 2014-01-20
Ubuntu has built-in remote desktop capabilities or you can use TeamViewer or similar. You will need to forward ports on your modem/router for the built-in remote desktop.

---

### Post by tgalati4 on 2014-01-20
It would take some work.  It's not real fast, but you can create a virtual private network (vpn) and use [port forwarding]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding") to push your desktop to a remote machine.  On Windows, it would require an xserver emulator.  On mac (with some work) and linux, the server is built in and running.  

You would need to sort out your IP address if it changes dynamically, then you would need to poke some holes in your router to allow the packets to flow.

There are better and easier ways to do this.  Put files that you need when you travel on Ubuntu One or Dropbox or Google Keep.  Then use your android phone or tablet to access them.

---

