---
title: "How do I set up a proxy on ubuntu? And other questions."
date: 2011-09-20
forum: New to Ubuntu
---

### Post by cetta on 2011-09-20
Hello all! I'm a genuine newb running the Ubuntu 11.04 distro -- classic view. I've come across a few problems in my terminal like trying to even install a proxy.

"cetta@cetta-Dell-DXP061:~$ sudo apt-get install tor proxychain
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Please help!

---

### Post by nothingspecial on 2011-09-20
Hi, it looks like you have either update-manager or software center running.

Close which ever one it is and try again.

---

### Post by cetta on 2011-09-20
I don't have either one running... At least I don't think so. How can I check?

---

### Post by nothingspecial on 2011-09-20
> **cetta said:**
> 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"


this error usually means that another instance of apt or dpkg is running.

Are you updating/installing/removing any other packages with any other process at the moment, even in another terminal?

---

### Post by sadaruwan12 on 2011-09-20
Got to System -> Administration -> System Monitor and when the window opens click the processes tab and scroll to see if the mentioned programs are running if they are select it and press end process button.

Do this if you're not doing a update or doing a software installation

---

### Post by ykanello on 2011-09-20
sudo fuser /var/lib/dpkg/

Check what process id is using the file
ps -aef |grep pid to see the application
kill -9 pid to kill the application :)

---

### Post by nothingspecial on 2011-09-20
> **ykanello said:**
> sudo fuser /var/lib/dpkg/

Check what process id is using the file
ps -aef |grep pid to see the application
kill -9 pid to kill the application :)

Unless you are in the middle of an update or there is the possibility something bad might happen.

---

### Post by cetta on 2011-09-20
Hey all! I'm not in the middle of an update and I couldn't find those processes in my System Monitor! Still stuck. D: I need to be walked through this one step at a time it seems...

---

### Post by ykanello on 2011-09-21
> **nothingspecial said:**
> Unless you are in the middle of an update or there is the possibility something bad might happen.

What is the worse that can happen if you break the apt?
reconfigure some packages? ok there are worse things can happen to an os :oops:

---

### Post by Lisiano on 2011-09-21
If you are 100% sure and triple-checked.
```
sudo rm /var/lib/dpkg/lock
```
This will remove the lock and allow you use apt. But ***_THIS IS POTENTIALLY DANGEROUS IF YOU HAVE AN UPDATE RUNNING_***. Sorry for the caps.

---

### Post by cetta on 2011-10-06
Thank you all for the help! The problem seems to be fixed. But I still need to get a proxy set up.

---

### Post by ykanello on 2011-10-10
proxy like squid, haproxy, reverse proxy (httpd-apache) or what kind of proxy exactly do you need?

---

### Post by Lisiano on 2011-10-10
As for how to install Tor. [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)
[quote=ykanello]proxy like squid, haproxy, reverse proxy (httpd-apache) or what kind of proxy exactly do you need?[/quote]
The OP, judging by the command he tried to issue, wanted to install Tor - The Onion Router. Basically P2P meets Proxy software.

---

