---
title: "kill running script which start before login window"
date: 2017-10-31
forum: New to Ubuntu
---

### Post by testko on 2017-10-31
I have Ubuntu 16.04 LTS and connected to it via TeamViewer. I changed rc.local to run a script before login. The script runs OK but it never ends. Consequently, login does not start, so I cannot login to Ubuntu. How can I kill running script remote via connected TeamViewer and without using Recovery Mode as I am few thousand miles away from the machine?

---

### Post by TheFu on 2017-10-31
Welcome to the forums.

I would ssh into the machine or connect to an IP-console I'd setup previously.  Then look at the process table.  If you can't ssh or get to a console, you'll need someone there to fix the rc.local (or just delete it).

I wouldn't use teamviewer.  ssh is much more efficient.

---

### Post by testko on 2017-10-31
Can you suggest an IP-console to install on Ubuntu when I get to the machine physically?

---

### Post by TheFu on 2017-10-31
> **testko said:**
> Can you suggest an IP-console to install on Ubuntu when I get to the machine physically?

I don't know of any software-only solution for physical machines.  If you use virtual machines, then you can use virt-manager from anywhere in the world via a secured ssh connection and keys to manage the systems.  

The server should have a DRAC or IPMI card already.  Just be very certain to lock down access to those ports.  There have been bad, terrible, security issues with these. [https://www.us-cert.gov/ncas/alerts/TA13-207A](https://www.us-cert.gov/ncas/alerts/TA13-207A) One model allowed an empty password to gain console access even if a password had been set.  Putting that on the internet without locking down the client addresses with access would be foolish.  Where I've worked, we had a completely different management LAN just for admins.

If not, you can buy [https://www.amazon.com/1PORT-USB-Remote-KVM-Spider/dp/B000OH5MDO/](https://www.amazon.com/1PORT-USB-Remote-KVM-Spider/dp/B000OH5MDO/) for a single system. I've never used it, but they are reputable. Check out some reviews. Most places have 12-48 port console switches.  Of course, putting the OS into a VM would get around this, provided the hostOS isn't toast. VMs provide all sorts of other handy features beyond just this.  Since more servers use less than 10% of the CPU, virtualization really does make sense most of the time.

---

### Post by HermanAB on 2017-10-31
Log in from another machine over the network: 
ssh user@ipaddress
and fix the script

---

### Post by TheFu on 2017-10-31
The key to the remote access suggestions is to have already setup the ssh-server and ensured that you could ssh in from where ever you normally would be.  I setup ssh by default on all my systems with ssh-keys (only keys can be used over the internet for access with our settings). It is how the machines are managed.  Along with firewall rules and fail2ban to prevent the entire world from having access to the systems, it is considered secure.

Securing ssh is no joke.

---

