---
title: "Remote access"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by fneergaard on 2011-11-21
I want to allow someone to access my ubuntu 10.11 server. The one is supposed to help me with some installation and also to move around some stuff. Basically I want to give him root access.

Which ports should I open / redirect in my firewall. Right now I have opened 80, 20-21 and 23. I have a static IP number and the server is installed behind the firewall with an ip number assigned by the dhcp server.

Someone was suggesting to open 25, 465 and 562, - but I don't if those has anything to do with it.

---

### Post by sadaruwan12 on 2011-11-21
For me I use TeamViwer it's easy and works great no need to open ports or any thing it works on it's own merit and fairly secure as well for your primary setup you can use that he can work through that just like being in your computer.

---

### Post by Lars Noodén on 2011-11-21
You only need to open port 22 (SSH) for the work to be done.

---

### Post by lifeboy on 2011-11-21
> **fneergaard said:**
> I want to allow someone to access my ubuntu 10.11 server. The one is supposed to help me with some installation and also to move around some stuff. Basically I want to give him root access.


You should not use root willy nilly to "move things around" via a gui.  Open port 22 and let him/her login with SSH.  It's secure and whatever that user is allowed to do, can be done.

If you want to use a gui, install nomachine.  [http://www.nomachine.com](http://www.nomachine.com)
It's very fast, access the machine remotely via ssh (port 22) and is thus secure.  Two users can use it for free.

> Which ports should I open / redirect in my firewall. Right now I have opened 80, 20-21 and 23. I have a static IP number and the server is installed behind the firewall with an ip number assigned by the dhcp server.

Someone was suggesting to open 25, 465 and 562, - but I don't if those has anything to do with it.

Would that person be using a Windows machine?  Nomachine runs on Windows and Macs too.  If you want network file access, investigate SAMBA.

---

### Post by fneergaard on 2011-11-21
Do I download nonashine for both windows and ubuntu and the can talk together...?

If I should not give root access then how should I do?

Is /var/www/site1 the right place to put a site?

Thanks

---

### Post by fneergaard on 2011-11-22
Now I can access my IP ([http://188.178.104.174/](http://188.178.104.174/))... and I can see that something is working...!!!

On the ubuntu I cannot modify files in the directory?

I tried CuteFTP! It is opening a connection but I cannot transfere files...

putty is getting "network error connection refused"?

Any ideas?

---

### Post by lifeboy on 2012-06-14
Did you ever get your problem resolved?  Did you read the how to's on the nomachine.com site?

---

### Post by quarkhirad on 2012-06-14
I used to use vnc viewer to log into my student file server at college from my laptop.Its simple and gives you full access.

---

### Post by sammiev on 2012-06-14
Just came across this thread. Think I will try nomachine in the next few days. Thanks

---

