---
title: "Telnet with VMware"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by vulcaninvt on 2011-09-26
Hi,

I have Ubuntu 10.10 installed in VMware (7.1.4 build-385536). I installed telnettd within ubuntu, my host is MS7 and I made sure to turn on the telnet function.  I shut off avast and MS firewalls as well. 

When attempting the telnet command I am receiving the following errors.  I am very new to this, any help would be greatly appreciated. 
[IMG]http://i85.photobucket.com/albums/k72/luvinvermont/School/Screenshot.jpg[/IMG]

---

### Post by Dangertux on 2011-09-26
Telnetd stands for telnet daemon (it is the server for the telnet connection) so you didn't need to install it on the Ubuntu machine if you are trying to telnet to the Windows host.

However, you are probably using the wrong ip address since it's a VM, it is more likely something like 172.16.16.1 (this is the default ip address for the VMware host)

Double check your ipconfig (windows) and get the ip address of the virtual adapter it should end in 1.  Like I said it will likely be 172.16.16.1

---

### Post by vulcaninvt on 2011-09-26
Thank you for the quick response.

When running ipconfig I get two VMware network adapters.  VMnet1 and VMnet8  with IP addresses.

 192.xxx.xx1 and 192.xxx.xxx.1

I attempted both of those with the same result as above.

---

### Post by Dangertux on 2011-09-26
Did you run netstat on the windows host to ensure that telnet is running, it should be listening on port 23, also make sure it is actually listening on its default port and not 2323 or something like that.

---

### Post by vulcaninvt on 2011-09-26
I ran netstat but I am not sure where I would see the ports or telnet.  Where would these be indicated.  Thanks for being patient with me and my learning curve :) 

I see quite a few 127.0.0.1:xxxxx addresses  and then the 192.168.2.x addresses as well.

---

### Post by Dangertux on 2011-09-26
You can try this command on the Windows machine

```

netstat -an | find -i / "listening"

```

That should show you all listening connections on the windows box. 

you'll be looking for something like 0.0.0.0:23

---

### Post by vulcaninvt on 2011-09-27
I ran the command and the response I got was,  FIND: invalid switch

---

### Post by The Cog on 2011-09-27
What are you trying to telnet to? I see that you are trying to connect from a machine called school-virtual-machine. But you are trying to telnet to a machine called Ryan-PC. Is Ryan-PC an Ubuntu box or a windows box? Assuming that it is an Ubuntu box, then the following should be performed on Ryan-PC. If Ryan-PC is a windows box, then you need to ask someone who knows windows and the following is not relevant:

Try ```
netstat -lnt
``` and look for something listening on port 23. FYI, the flags are:
l - listening
n - numeric output (rather than names)
t - TCP ports
Hope to see either **0.0.0.0:23** or **:::23**. Either of those means that it's listening for telnet connections.

If you see either **127.0.0.1:23** or **::1:23** then it is only listening for connections on the loopback address and is not reachable from outside the machine. You will need to reconfigure the telnet service and restart it. The ocnfiguration file is probably in /etc/default/telnet or /etc/telnet, or something very similar to one of those (I don't have telnet installed).

If you don't see any of the above addresses, then the telnet daemon is not listening for connections, probably not running.

---

### Post by Dangertux on 2011-09-27
Sorry OP it should be the below command, but I'm confused are you running the telnet services on the Windows machine or the Linux Guest?

```

netstat -an | find /I "listening"

```*note : this command is for Windows. If you are trying to run telnetd on Ubuntu use the command in the post above or more simply

```

netstat -anl | grep :23

```Hope that helps.

---

### Post by vulcaninvt on 2011-09-27
Sorry for the confusion.  I am running telnet on the guest Linux machine in VMware. 

I give the commands a shot and let you know what I get.   

This is for a Linux Admin I class that I am taking.

Okay, I ran the command in Windows and didn't find :23  I have a bunch of 127.0.0.1: xxxxx the other addresses end in :139

In my linux machine I get the following: tcp        0      0 0.0.0.0:23              0.0.0.0:*               LISTEN

---

### Post by The Cog on 2011-09-28
> **vulcaninvt said:**
> In my linux machine I get the following: tcp        0      0 0.0.0.0:23              0.0.0.0:*               LISTEN
That's good - it i slistening for incoming telnet connections. 

But you talk as though there is only one Linux machine. I see you trying to connect from school-virtual-machine to Ryan-PC. Do you have two different Linux machines, or is something else going on?

---

### Post by Dangertux on 2011-09-28
> **vulcaninvt said:**
> Sorry for the confusion.  I am running telnet on the guest Linux machine in VMware. 

I give the commands a shot and let you know what I get.   

This is for a Linux Admin I class that I am taking.

Okay, I ran the command in Windows and didn't find :23  I have a bunch of 127.0.0.1: xxxxx the other addresses end in :139

In my linux machine I get the following: tcp        0      0 0.0.0.0:23              0.0.0.0:*               LISTEN

In the linux machine the telnet daemon (server) is listening for incoming connections. This means you can telnet to it  from the Windows host. If you want to telnet to the windows host from the linux guest you will need to install a telnet server on the Windows host.

Does this make sense?

@The Cog - OP is using Ubuntu in a virtual machine running on WIndows. The Windows machine is Ryan-PC, the Ubuntu vm is school.

The part I am not sure is whether the OP is trying to telnet to the windows machine or to the ubuntu guest.

---

### Post by The Cog on 2011-09-29
> **Dangertux said:**
> @The Cog - OP is using Ubuntu in a virtual machine running on WIndows. The Windows machine is Ryan-PC, the Ubuntu vm is school.

The part I am not sure is whether the OP is trying to telnet to the windows machine or to the ubuntu guest.

Ah, that makes sense. Maybe he doesn't realise that both the host and the guest machines will have their own IP address, so that when you want to telnet to the guest in the VM, you have to telnet to the guest's IP address, not the host's IP address.

Also, I'm not familiar with vmware, but if it's like virtualbox then you have different options for networking. Virtualbox allows the guest's network connection to be fully isolated from the real net, fully connected, or separated by a NAT gateway.

Also, I would note that ssh is the preferred protocol these days - telnet is regarded as an old and insecure legacy protocol.

---

