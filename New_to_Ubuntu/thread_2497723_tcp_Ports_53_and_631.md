---
title: "tcp Ports 53 and 631"
date: 2024-05-15
forum: New to Ubuntu
---

### Post by bhubunt on 2024-05-15
Hi,
I typed the cd ss -lntu into the terminal and noticed tcp port 53 and tcp 631 are open, listening. Both are potential liabilities, it seems. Port 631 is for cups, which I don't use.

How can I block port 631 in ufw and why do I need port 53. What happens if you block it?

---

### Post by currentshaft on 2024-05-16
pdo

---

### Post by ActionParsnip on 2024-05-16
If you don't print then you can stop and disable the cups service. I do this myself. Printing is something I never do

---

### Post by bhubunt on 2024-05-16
I have uninstalled cups several times but it keeps coming back. I also receive updates through the Ubuntu Software Updater.


> **ActionParsnip said:**
> If you don't print then you can stop and disable the cups service. I do this myself. Printing is something I never do

---

### Post by bhubunt on 2024-05-16
> **currentshaft said:**
> Use "sudo lsof -Pni" to see which processes are listening on those ports.

Port 53 is most likely used by your local domain resolver agent. If you don't use cups, you can simply uninstall it with apt.

However, there is virtually no risk in having either of these ports exposed, because they are most likely bound to localhost in the first place.


Uninstalling Cups doesn't work.

---

### Post by Rubi1200 on 2024-05-16
Start by showing the output of this command:
```
sudo systemctl status cups
```

If the service is running, stop it like this:
```
sudo systemctl stop cups
```

If you want to prevent it from running at startup, do this:
```
sudo systemctl disable cups

```
If you want to also prevent it from being manually started, use this command:
```
sudo systemctl mask cups


```

Not sure why you are going to so much effort to get rid of it when 3 commands can stop and disable the service.

The output of the command **currentshaft **asked for would have been helpful.

---

### Post by bhubunt on 2024-05-16
> **Rubi1200 said:**
> Start by showing the output of this command:
```
sudo systemctl status cups
```

Here you go: please explain what you see in the code below. It says cups is running, but what about the scheduling? Why is the scheduling active? 
I'd appreciate it if you could unpack what you see

```

cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: >
     Active: active (running) since Thu 2024-05-16 21:06:35 CEST; 32min ago
TriggeredBy: &#9679; cups.socket
             &#9679; cups.path
       Docs: man:cupsd(8)
   Main PID: 1185 (cupsd)
     Status: "Scheduler is running..."
      Tasks: 4 (limit: 4385)
     Memory: 8.6M
        CPU: 117ms
     CGroup: /system.slice/cups.service
             &#9500;&#9472;1185 /usr/sbin/cupsd -l
             &#9500;&#9472;1307 /usr/lib/cups/notifier/dbus dbus:// ""
             &#9500;&#9472;1308 /usr/lib/cups/notifier/dbus dbus:// ""
             &#9492;&#9472;1312 /usr/lib/cups/notifier/dbus dbus:// ""

Mai 16 21:06:34 XXX-ThinkPad-X240 systemd[1]: Starting CUPS Scheduler...
Mai 16 21:06:35 XXX-ThinkPad-X240 systemd[1]: Started CUPS Scheduler.  
```

---

### Post by The Cog on 2024-05-16
> **bhubunt said:**
> Here you go: please explain what you see in the code below. It says cups is running, but what about the scheduling? Why is the scheduling active? 
I'd appreciate it if you could unpack what you see

It's being scheduled because the service is enabled - you can see it's enabled on the Loaded line.

But cups only listens on on the loopback address, so it's not accessible from over the network. I'm not sure how much would stop working if you stopped it. Probably printing of any sort would stop, even print to a usb printer or print to PDF. Cups is the system print spooler.

```
~$ sudo ss -lntup | awk 'NR==1||/cups/'
Netid State  Recv-Q Send-Q Local Address:Port  Peer Address:PortProcess                                   
udp   UNCONN 0      0            0.0.0.0:631        0.0.0.0:*    users:(("cups-browsed",pid=1126,fd=7))   
tcp   LISTEN 0      128        127.0.0.1:631        0.0.0.0:*    users:(("cupsd",pid=809,fd=7))           
tcp   LISTEN 0      128            [::1]:631           [::]:*    users:(("cupsd",pid=809,fd=6))           
```
But notice there is also a cups-browsed process listening on UDP 631. This is listening on all addresses, for printer advertisements from remote printers. Although I think the risk is low, you may want to disable this service. I wouldn't uninstall it though - it doesn't take up much space and you may find you want it one day.
```
sudo systemctl stop cups-browsed
sudo systemctl disable cups-browsed
```

---

### Post by bhubunt on 2024-05-16
Can you pls explain what you mean in the following line: 

This is listening on **all addresses, for printer advertisements from remote printers.**

---

### Post by The Cog on 2024-05-17
> **bhubunt said:**
> Can you pls explain what you mean in the following line: 

This is listening on **all addresses, for printer advertisements from remote printers.**

It's listening on udp 0.0.0.0:631. That's UDP protocol port 631 - suitable single messages like just announcing the existence of an available printer. And 0.0.0.0 means listening on all interfaces and for any destination address. These adverts are usually broadcast rather than directed to a single destination address anyway, but if the computer receives the packet then it will be processed and the browser daemon will note that another printer is available for use. 

It's like the printer occasionally shouts out "Hey everybody, I'm a printer and I'm here if you want me.". A single packet addressed to a broadcast address, meaning all devices on the local network.

---

### Post by bhubunt on 2024-05-17
OK 

So the idea is that CUPS is useful if you are on a local network?  Other people on your local network can print out files that you send them, to give but one practical example?  

However, I'd still like to hear more about why various websites warn about liabilities associated with CUPS and port 631 (which is why I started this thread). Even if chances are slim. 

What are the security risks, including in cases when you are not on a local network?

---

### Post by ActionParsnip on 2024-05-17
If you don't use a service and it is listening then it is offering you no benefit and exposes your system (in some way) to attack. This is part of basic hardening. I believe the CUPS packages are part of the "ubuntu-desktop" meta-package which is probably why they are being reinstalled occasionally.

---

### Post by currentshaft on 2024-05-17
cupds

---

### Post by The Cog on 2024-05-17
It is possible to reconfigure the cups print spooler process to listen for external connections instead of just local processes (listen on 0.0.0.0 instead of 172.0.0.1). This allows other computers to send prints to your printers, read printer properties, ink levels, print queue properties etc. If you wanted other 'puters to be able to do that, you might want to limit which addresses can do that even though the service is password protected. 

On top of that, any service that outside folk can connect to just might have a vulnerability that can be abused to hijack your computer.

---

### Post by bhubunt on 2024-05-18
Thanks for the heads up and your explanation that a listening service like CUPS, unused, might expose one's system to an attack.


> **ActionParsnip said:**
> If you don't use a service and it is listening then it is offering you no benefit and exposes your system (in some way) to attack. This is part of basic hardening. I believe the CUPS packages are part of the "ubuntu-desktop" meta-package which is probably why they are being reinstalled occasionally.

---

### Post by bhubunt on 2024-05-18
[> **The Cog said:**
>   On top of that, any service that outside folk can connect to just might  have a vulnerability that can be abused to hijack your computer.  


Thanks for this helpful addition to ActionParsnip's comment about unused services like CUPS posing a potential security risk. 

I have no intention of using CUPS now or in the future -- my system is a personal Lenovo laptop that is not part of a network of computers. Any rare printing I do is for personal use, on paper, on a Brother printer. 

I just entered the disable-cups command that Rubi1200 suggested in a post above. 

Can you or someone else explain to me if the return output looks right? 

What does "multi-user.target.wants" stand for? 

And does this mean that cups won't be coming back, not even through an ubuntu update?

```
 sudo systemctl disable cups
[sudo] password for XXX: 
Synchronizing state of cups.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install disable cups
Removed /etc/systemd/system/multi-user.target.wants/cups.service.
Removed /etc/systemd/system/multi-user.target.wants/cups.path.
Removed /etc/systemd/system/sockets.target.wants/cups.socket.
Removed /etc/systemd/system/printer.target.wants/cups.service.
  
```

---

### Post by The Cog on 2024-05-18
Yes, that disabled the cups service. Which was not accessible over the network anyway. If you can't print to a local printer or to pdf files any more, you know why.

What about cups-browsed, the one that **is** accessible across the network? Did you disable that or is it still listening?

---

### Post by bhubunt on 2024-05-18
> **The Cog said:**
> Yes, that disabled the cups service. Which was not accessible over the network anyway. If you can't print to a local printer or to pdf files any more, you know why.

What about cups-browsed, the one that **is** accessible across the network? Did you disable that or is it still listening?

Thanks for the reply.

For future reference: 

If I change my mind and want to enable CUPS again at boot startup, what is the command line?  

I disabled cups-browsed

```
 Synchronizing state of cups-browsed.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install disable cups-browsed
Removed /etc/systemd/system/multi-user.target.wants/cups-browsed.service.

 
```

---

### Post by Rubi1200 on 2024-05-18
If you change your mind and want to enable CUPS at boot this is the command:

```
sudo systemctl enable cups
```

Can I suggest something?

Keep a text document with a list of commands you used with enable and disable parameters. Good as a handy reference tool.

---

### Post by currentshaft on 2024-05-18
D>

---

