---
title: "Finding network printer, firewall issue?"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by jaxom98 on 2013-12-29
Hello, can anyone tell me where to find the firewall? 
OS Edubuntu 12.04.3  
It won't detect my printer. (works perfectly in ubuntu 8.04 and win7) I found another thread that was almost the same, the fire wall was set to block all incoming. Result , could not detect printer.
WHERE is the blasted firewall hidden.
There are a number of changes from 8.04 and they obstruct usability

---

### Post by r3dd on 2013-12-29
Try
```
sudo ufw status verbose
```
That will at least tell you what the firewall status is. It shouldn't be active unless you turned it on.

---

### Post by Rich53201 on 2013-12-29
You can use Synaptic (at least, in lubuntu 13.10) to install gufw, a simple graphical firewall manager.  That's how I solved my printer problem.

Without a graphical window, you can edit iptables, according to this page:  

[https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall)

---

### Post by deadflowr on 2013-12-29
As stated, the status command will tell what states it's in.
If using the default setup it will be inactive.
Try
```
sudo ufw enable
```
to activate.
Run 
```
man ufw
```
to get an overview of what parameter you can use to set things
Some more here
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Edit:I realize after re-reading the OP that this thread is about a network printer.
Try this in a browser address bar
```
localhost:631
```
which should open up the cups page for you.

---

### Post by r3dd on 2013-12-29
Also, the "gufw" program is just the graphical front end for "ufw", the default firewall.

Make sure you have cups installed too.

---

