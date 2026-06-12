---
title: "Network Name of Linux Server"
date: 2014-08-21
forum: New to Ubuntu
---

### Post by sam64 on 2014-08-21
I'm trying to connect to a network from my Ubuntu virtual machine using PuTTY on my Windows host:

[SCREEN SHOT SHOULD GO HERE. HOW DO I UPLOAD AN IMAGE FROM MY COMPUTER INSTEAD OF A URL LINK?] 

Since I'm learning this from home, what so-called network should I try to connect to?

---

### Post by nerdtron on 2014-08-21
Upload the screenshot as an attachment.

You would like to connect from your windows host using putty to the Ubuntu machine right?

Be sure that openssh-server is installed on the Ubuntu machine. Then on Putty, connect using ssh and provide the IP address of the Ubuntu machine.

---

### Post by sam64 on 2014-08-21
> **nerdtron said:**
> You would like to connect from your windows host using putty to the Ubuntu machine right?
I think so. I'm still trying to grasp a full understanding of how to use a linux server (and more importantly, what to use it for).

> **nerdtron said:**
> Be sure that openssh-server is installed on the Ubuntu machine.

Where do I find an open ssh-server? Do I have to download it?

> **nerdtron said:**
> Then on Putty, connect using ssh and provide the IP address of the Ubuntu machine.
How do I find out the IP address of my Ubuntu machine?
[ATTACH=CONFIG]255705[/ATTACH]

---

### Post by nerdtron on 2014-08-21
Fastest way, on the Ubuntu machine, open a terminal, type: sudo apt-get update && sudo apt-get install openssh-server

Wait for it to finish the installation.
To determine the IP address of the Ubuntu machine, on the command line type: ifconfig

---

### Post by sam64 on 2014-08-21
> **nerdtron said:**
> To determine the IP address of the Ubuntu machine, on the command line type: ifconfig
So where is the IP address in the following screen shot?:
[ATTACH=CONFIG]255709[/ATTACH]

---

### Post by lisati on 2014-08-21
> **sam64 said:**
> So where is the IP address in the following screen shot?:


The line that begins "inet addr:" shows the IPv4 address on your local network.

---

### Post by mastablasta on 2014-08-22
also is this a virtualmachine? in that case you need to bridge the network to VM. for server use you do not need the desktop. if you need a GUI to administer the server then look at webmin, zentyal or many others.

in this case you installed desktop Ubuntu which doesn't have many server packages. they can still be installed via software center (as well as synaptic or terminal).

---

### Post by sam64 on 2014-08-30
> **nerdtron said:**
> Fastest way, on the Ubuntu machine, open a terminal, type: sudo apt-get update && sudo apt-get install openssh-server

Wait for it to finish the installation.

It's an installation, is it? So how do I access the openssh-server that I already installed next time I log onto my Ubuntu VM? I didn't finish configuring it with PuTTY on my host last time.

> **lisati said:**
> The line that begins "inet addr:" shows the IPv4 address on your local network.
Which "inet addr:"?
[ATTACH=CONFIG]255989[/ATTACH]
What are "eth0" and "lo" short for?

---

### Post by nerdtron on 2014-08-31
> It's an installation, is it? So how do I access the openssh-server that I  already installed next time I log onto my Ubuntu VM? I didn't finish  configuring it with PuTTY on my host last time.

Yes you need to install it because it is not installed by default on the desktop version. Just follow the on screen prompts during the installation.
Just open Putty on windows, choose SSH, and input the 10.0.2.15 ip address, then connect.

Note: if you can't connect can you ping 10.0.2.15 from your windows command line?

> Which "inet addr:"?
[Attachment 255989]("http://ubuntuforums.org/attachment.php?attachmentid=255989")
What are "eth0" and "lo" short for?

eth0: first network interface - 10.0.2.15 - the ip address of the first network interface
lo: the loopback interface - all linux have this in their system, do not disable or change settings on this interface

---

### Post by mastablasta on 2014-09-01
install server edition in the virtualmachine and many things will be preconfigured and preinstaleld for you.

if you want to use specific service on the server look at the servers I proposed before or use something like Turnkeylinux or Bitnami stack which provide ready to use virtual disks and are much easier to configure.

---

### Post by sam64 on 2014-09-01
> **nerdtron said:**
> 
Just open Putty on windows, choose SSH, and input the 10.0.2.15 ip address, then connect.

Why did I get this error message:
[ATTACH=CONFIG]256060[/ATTACH]
> **nerdtron said:**
> 
Note: if you can't connect can you ping 10.0.2.15 from your windows command line?

Ping couldn't fufill my connecting request either:
[ATTACH=CONFIG]256061[/ATTACH]
I had my VM running when I attempted to connect, but didn't do anything in the Terminal. Am I supposed to type a command or something in my Ubuntu VM Terminal before I am able to connect with PuTTY?

---

### Post by nerdtron on 2014-09-01
> I had my VM running when I attempted to connect, but didn't do anything  in the Terminal. Am I supposed to type a command or something in my  Ubuntu VM Terminal before I am able to connect with PuTTY?

Nope. As long as the ssh process is running on the ubuntu machine you shouldn't have any problem. I assume you don't edited firewall rules on Ubuntu yet. The first thing to do here is to fix the network issue. Start by finding out why you can't ping the VM from your windows host.
My initial suggestion would be to try using Bridge mode instead of NAT in the network configuration of virtual box. Then start your VM again and you'll notice that the IP address changed. Now try to ping the VM again from your windows host and see if it is successful.

---

### Post by mastablasta on 2014-09-02
you need bridge mode or host only network to eb abel to connect to virtual server.

---

### Post by sam64 on 2014-09-12
> **mastablasta said:**
> you need bridge mode or host only network to eb abel to connect to virtual server.

Ok, I changed the Virtual Box network settings from NAT to Bridged Adapter. Then, on my host, I generated and saved SSH keys:
[ATTACH=CONFIG]256415[/ATTACH] 

But now what? I still intend on connecting my VM to my host (assuming my host is the server). But my host is NOT just a server, it's an operating system. If I am going to get this silly SSH connection project to work, how do I synchronize the public and private SSH keys?

And judging from this documentation:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#keys-with-specific-commands](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#keys-with-specific-commands)

Was I supposed to generate the PuTTY SSH keys on the VM instead?:confused:

---

