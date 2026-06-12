---
title: "Building an Ubuntu based home file server"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by PandaMadness on 2012-07-16
Hi everyone. I've got an issue: as the thread name suggests, I want to build a  home file server running Ubuntu desktop. The server will have my internet router connected to it, and it will share internet with my main workstation via LAN. I want to be able to control files on the server via my main workstation (it runs on windows 7, I'm a gamer) with remote desktop (I believe in Ubuntu that is VNC), and also via my notebook (also windows 7) via wifi (router has wifi). Can you please explain what software I should use to make this  dream  a reality, and how to also make this little network secure (i.e. no external machine can access my files)?

Also, potentially in the future, I was thinking of a way to connect to my home network from outside (perhaps via VPN?).

Any help will be appreciated, thanks in advance.

---

### Post by PandaMadness on 2012-07-16
Greetings.
As the thread name suggests, I want to build a  home file server running Ubuntu desktop. The server  will have my internet router connected to it, and it will share internet  with my main workstation via LAN. I want to be able to control files on  the server via my main workstation (it runs on windows 7, I'm a gamer)  with remote desktop (I believe in Ubuntu that is VNC), and also via my  notebook (also windows 7) via wifi (router has wifi).

After researching a bit on the subject I have come to this:

On my server (Ubuntu), I will need to install and configure SSH, port forward port number 22 to the ip address of my server on the local network. Also enable VNC (my guess is its pre installed in ubuntu).

After that, on my client computers I will have to install putty for establishing an ssh connection and any free VNC viewer (I picked TightVnc). With putty i establish an ssh connection to my server via a certain port, and connect to localhost with the vnc viewer (this part I don't understand, why do I connect to localhost instead of the ip address of the server?).

These actions should result in a secure connection between server and client PC's with shared desktop.

Please correct me if I'm wrong anywhere.
Thanks in advance.

---

### Post by mastablasta on 2012-07-16
why would a server be running a desktop?
why do you need remote desktop access to it?
 
if it's only file server there are other ways. if you dont' like CLI there are GUI's for server management available.
 
also what exactly is your question? you stated what you wnat , so why not just do it?

---

### Post by PandaMadness on 2012-07-16
Remote desktop is needed because I plan to run some applications (downloads and such) on the file server rather than it being idle all the time.

After researching a bit on the subject I have come to this:

On my server (Ubuntu), I will need to install and configure SSH, port  forward port number 22 to the ip address of my server on the local  network. Also enable VNC (my guess is its pre installed in ubuntu).

After that, on my client computers I will have to install putty for  establishing an ssh connection and any free VNC viewer (I picked  TightVnc). With putty i establish an ssh connection to my server via a  certain port, and connect to localhost with the vnc viewer (this part I  don't understand, why do I connect to localhost instead of the ip  address of the server?).

These actions should result in a secure connection between server and client PC's with shared desktop.

Please correct me if I'm wrong anywhere.
Thanks in advance.

---

### Post by mastablasta on 2012-07-16
good reasearch :-) seems like you got it covered. you do not need desktop for those funcitons. it can be done via command line. or browser based gui.
 
or you can simply use a gui and control server via browser.
 
have a look at Zentyal (Ubuntu based). it's GUI based server for home use and small busiinesses. there might be other options out there that fit your need. for example some are more focused more on files (such as openmediavault -based on super stable debian and similar such as freenas)
 
edit: it seems Zentyal options are not as free as they used to be however i believe a similar option exists that is red had/centos based. with things done via GUI. you will save electricity power/CPU power... by not loading desktop.

---

### Post by prshah on 2012-07-16
> **PandaMadness said:**
> 
On my server (Ubuntu), I will need to install and configure SSH, port forward port number 22 to the ip address of my server on the local network. Also enable VNC (my guess is its pre installed in ubuntu).

After that, on my client computers I will have to install putty for establishing an ssh connection and any free VNC viewer (I picked TightVnc). With putty i establish an ssh connection to my server via a certain port, and connect to localhost with the vnc viewer (this part I don't understand, why do I connect to localhost instead of the ip address of the server?).

These actions should result in a secure connection between server and client PC's with shared desktop.

Please correct me if I'm wrong anywhere.

Most important point: Ubuntu server does not have a GUI installed out-of-the-box. So either install a GUI manually, or use xubuntu desktop (recommended).

Your idea of remote access is pretty much correct, but glosses over certain aspects. For example, you will have to consider wether you want to use passwordless (public key) or password authentication.

About using VNC to connect to localhost: When you create a "tunnel", it means that you are attempting to map a local port (say 5901) to a remote port (again, say 5901 for simplicity). Subsequently, to use the port, you command your client to connect to localhost:5901, which in turn securely connects to the remote port 5901. The advantage of doing this, rather than connecting directly to remote port 5901 is that on the server, you can set the VNC server to accept ONLY LOCAL CONNECTIONS. That way, requests to 5901 port that originate either on the LAN or the WAN are dropped. Only the server's localhost is allowed to use port 5901; and the "tunnel" that you have created makes the VNC server believe that you are connected to the server's localhost, rather than the client's localhost.

Please post back if you need more details.

---

### Post by nothingspecial on 2012-07-16
Threads merged.

Please do not create duplicate threads, it dilutes community effort.

---

### Post by PandaMadness on 2012-07-18
> **prshah said:**
> Most important point: Ubuntu server does not have a GUI installed out-of-the-box. So either install a GUI manually, or use xubuntu desktop (recommended).

Your idea of remote access is pretty much correct, but glosses over certain aspects. For example, you will have to consider wether you want to use passwordless (public key) or password authentication.

Please post back if you need more details.

Thanks for clarifying the localhost issue for me.

If I choose to use passwordless auth. will it still be safe, considering that the file server will be connected to the internet?

And  how do I properly set up auth. with passwords?

Also, I thought about it and decided to buy an adsl router modem (my current one has only 1 lan port) and connect both the workstation and the server to it, rather than setting up workstation->server->modem. Will it severely affect connection speed between these two PC?

---

### Post by mastablasta on 2012-07-18
> **PandaMadness said:**
>  
Also, I thought about it and decided to buy an adsl router modem (my current one has only 1 lan port) and connect both the workstation and the server to it, rather than setting up workstation->server->modem. Will it severely affect connection speed between these two PC?
 
that's a much better/simpler solution. no it won't really slow down LAN connection. mostly we are limited with internet speed rather than LAN speed. which is why "LAN parties" used to be very popular as they provided higher speeds and lower pings.

---

### Post by prshah on 2012-07-18
> **PandaMadness said:**
> If I choose to use passwordless auth. will it still be safe, considering that the file server will be connected to the internet?

And  how do I properly set up auth. with passwords?

Also, I thought about it and decided to buy an adsl router modem (my current one has only 1 lan port) and connect both the workstation and the server to it, rather than setting up workstation->server->modem. Will it severely affect connection speed between these two PC?

Your idea of using a adsl modem + LAN router is a good one, and an easy and simple solution, especially when adding more clients to the LAN in the future.

However, for Port Forwarding to work, please ensure that your "server" is setup with a static LAN ip address; your clients can use the router's DHCP.

Passwordless authentication is safer and recommended over passworded auth. However, you have to ensure the safety of your  self-created public and private keys. 

Please see the [community documentation for SSH server]("https://help.ubuntu.com/community/SSH/") for full details. You can post back here if any part of it is not clear.

I suggest you avoid connecting your server to the internet (or disable port forwarding) until you have installed, tested and strengthned SSH server access.

---

