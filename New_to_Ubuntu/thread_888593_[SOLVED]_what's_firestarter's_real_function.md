---
title: "[SOLVED] what's firestarter's real function?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by macvr on 2008-08-13
hi, i'm new to ubuntu 8.04.1 ,have just shifted from XP, 
i read in a few sites that said a firewall was good for keeping away unwanted intrusions>>> so i installed FIRESTARTER

when i checked the events tab it had a few blocked events when i had clearly turned off the program[in pic i have highlighted the events]

so is it just a simple GUI to the inbuilt UBUNTU firewall ?

_if its just a GUI_ , other than to allow the blocked events does it have any other purpose? is the ubuntu firewall enough?

i use torrent downloads so was considering a firewall.
is it safe to use torrents with just the ubuntu firewall?

---

### Post by pparks1 on 2008-08-13
Firestarter is just a GUI to the real behind the scenes firewall...which is iptables.

With Ubuntu 8.04, you can also use UFW...uncomplicated firewall wall.   It's a more simplistic command line system to setup firewall rules...which is often easier for people than writing the actual iptables lines.

---

### Post by Oldsoldier2003 on 2008-08-13
Iptables was very difficult for new users, so firestarter filled a void. More experienced users would build their rules manually, but in my opinion firestarter is better than not using your firewall at all.

As to your question about the blocked events, once you have configured iptables it will do its job without further need for interaction. Firestarter is NOT the firewall, its just an easy way to interface with iptables.

---

### Post by macvr on 2008-08-13
> **Oldsoldier2003 said:**
> Iptables was very difficult for new users, so firestarter filled a void. More experienced users would build their rules manually, but in my opinion firestarter is better than not using your firewall at all.

As to your question about the blocked events, once you have configured iptables it will do its job without further need for interaction. Firestarter is NOT the firewall, its just an easy way to interface with iptables.

so it doesnt matter if i dont have it running or not, i just need to check it if my connections are not working?

---

### Post by Nepherte on 2008-08-13
Exactly, you don't need to start up firestarter for your firewall to function. The firewall starts during the boot process.

---

### Post by Malac on 2008-08-13
> **macvr said:**
> so it doesnt matter if i dont have it running or not, i just need to check it if my connections are not working?
 That's right. You only need to run Firestarter if you need to adjust something. i.e. open a port, allow inbound access from an IP address or that sort of thing.

---

### Post by Oldsoldier2003 on 2008-08-13
You can turn off firestarter and you will still be protected by iptables. (as long as your rules were saved).

edit: unless you want to delve into the command line, it doesn't hurt to run firestarter on occasion to verify everything is as you want it.

---

### Post by macvr on 2008-08-13
thank you

---

