---
title: "Need to remote to 12.04 from Mac?"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by iamjoe on 2012-07-03
I have an amazon EC2 instance running that I want to remote to (via vnc I guess).  The IP that I ssh to is 172.129.**.**

The IP that I see when I run ifconfig is 10.211.**.***

Is the ifconfig IP a private IP?

Do I need to install anything via ssh in ubuntu in order to connect to it?

I'm kinda new to linux, but certainly have enough experience to take direction.

Thanks all.

---

### Post by teward on 2012-07-03
The IP you see in ifconfig is the internal, private IP of the machine as it exists in Amazon's setups. The traffic on the IP you connect to is forwarded to that private IP address.
 
To get a remote "gui" environment (graphical environment, like your Mac has), you'll need to set up VNC to allow for remote desktop stuff. You'll also need to install a graphical environment (which Amazon EC2 instances sometimes do not allow).
 
If I may ask, why do you need the "remote" desktop session, rather than doing everything via SSH?

---

### Post by cipherboy_loc on 2012-07-03
What are you hoping to use VNC to do? VNC on a server is not that good of an idea, especially because of security aspects (not encrypted for starters). Secondly, Amazon EC2 likely does not provide a GUI by default, much less GNOME or KDE, and thus would require installation of a GB or so of data. Also, by using SSH you are already connected to it. From there you can install a LAMP or RAILS stack. 

Cipherboy

---

