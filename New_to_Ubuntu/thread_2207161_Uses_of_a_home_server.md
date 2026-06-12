---
title: "Uses of a home server"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by niall.stronge on 2014-02-22
Hey folks,

I'm still fairly new within the community here, but I've been playing around with Ubuntu 13.10 for the last few months now, and I'm really getting on with it. I've also been studying towards an IT Apprenticeship and have been learning about networking and the like (hopefully in preparation for going off to do my CCNA somewhere down the line.). Basically, as a way to try and keep everything that I've been learning fresh in my mind, I've been toying with the idea of setting up a home server on my old windows box. 

Now, aside from the traditional server roles (DC, DHCP, File Server, etc.) what could a home server be used for to actively improve the service on a home net? I've been thinking of using it as a central media/torrent storage unit, but surely I could just rig up a NAS for the same role? Also, I work and study away from home a lot of the time and I would like to be able to have access to this store remotely (especially as torrenting and the like has been blocked in my accomodation). Would I be able to remotely join the network through an IP service (telnet?) and be able to transfer files from the server?

This would be my first real IT project and I'm trying to do my homework before I go diving right in, so any advice you all might be able to give would be amazing!
Thanks!

---

### Post by Lars Noodén on 2014-02-22
> **niall.stronge said:**
>  Also, I work and study away from home a lot of the time and I would like to be able to have access to this store remotely (especially as torrenting and the like has been blocked in my accomodation). Would I be able to remotely join the network through an IP service (telnet?) and be able to transfer files from the server?

The package openssh-server provides access with both SSH and SFTP (which operates over SSH).  Telnet was replaced by SSH many years ago, being incurably insecure.  Anything you can do over the local terminal you can also do over SSH.  If you configure your router / modem to forward a port to your server, then you can access it securely even from abroad.  The only hard part there will be knowing the external IP address to contact, if you do not have a static one.  You can look that up before leaving the house and hope that it does not change during your trip or you can use a [dynamic DNS](https://help.ubuntu.com/community/DynamicDNS) service to access it via a host name.  

For file transfer over SSH, you have SFTP.  There is a built-in text client, sftp, in your system and most file managers (Nautilus and others) also have built-in SFTP support.  Press ctrl-L in the file manager and then enter the URL:

```

sftp://user@server.example.org/home/user/

```

There are also other SFTP clients like SSHFS which allows you to mount the remote system as a local directory and do file transfers just like working with a local directory.  

```

mkdir /home/user/remote
sshfs user@server.example.org:. /home/user/remote/

```

That would make the home directory of *user* from the remote server available in the local directory *remote*

---

### Post by niall.stronge on 2014-02-22
That sounds a little over my level at the minute I think, but only because of the acronyms! Another issue with my home net is that there are a number of different OS in use. My main concern with this plan is that I'm not sure if all the devices will be able to talk to one another (i.e. a Win7 client attempting to connect to an Ubuntu server). Would that really be a problem or am I just worrying over nothing?

---

### Post by TheFu on 2014-02-22
IT happens as needed in most organizations. Your home won't be any different. You have limited budget and want to use the existing hardware for as many purposes as possible.  **You will not do it right.**  Get over that.  Expect to make mistakes and LEARN FROM THOSE.

a) NEVER use telnet for anything besides checking connectivity for HTTP, SMTP, things like that. It is NEVER appropriate to use anywhere for remote connections - even on a LAN or within virtual machines on the same physical hardware - NEVER really means NEVER this time. ;)  Use **ssh**.
b) Learn about ssh, rsync and 1 good backup solution that works without a GUI.  ssh is the center of all UNIX/Linux administration.
c) Do whatever else you like.  A few options:
* VPN Server (openvpn)
* backup storage
* Plex
* NAS for the LAN (prefer NFS, but CIFS is ok ONLY for Windows boxes)
* Remote Desktop Server (FreeNX)
* gnump3 server

In real IT systems, we'd not have mp3s, plex, and probably not a NAS on a server like this.  We've setup:
* authentication (logins/passwords)
* RADIUS for WiFi Authentication 
* openvpn for remote access to the network
* project management (redmine)
* DHCP
* Remote Access (FreeNX, xrdp, ...)
* Desktop Screen Sharing and collaboration
* VoIP (FreeSwitch or Asterisk)
* Document Management (Alfresco)

Knowing how to backup all these things following the "[Best Practices for Backups]("http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups")".

What is a "DC?" Never heard of that before in 20+ yrs doing this stuff.

---

### Post by niall.stronge on 2014-02-22
A Domain Controller? We've been learning about servers using Win Server 2003/8 and before you do anything, you have to promote at least one server on the net to a DC. It's bacically where you'd host your DHCP and DNS.

---

### Post by Lars Noodén on 2014-02-22
It's easier than it sounds.  Don't worry about the acronyms much.  They are there to make it easier to look up information on the net.  These are industry-standard tools so there is a lot of material.   As for SSH/SFTP, it works out of the box.  Just install the package openssh-server on the machine you wish to connect to and then point your client, such as the file manager Nautilus, which is the default for Ubuntu, at it using the ctrl-L method above.  

On legacy systems, you can connect using FileZilla for file transfer.  To log in and run things via the terminal, you have PuTTY.  Both are available for download in the repositories for Ubuntu.  For legacy systems, you can get either one from the corresponding project's web site.

---

### Post by niall.stronge on 2014-02-22
Awesome, thanks for the advice so far. But what would you use a home server for, rather than just a glorified NAS?

---

### Post by Lars Noodén on 2014-02-22
Any of the uses suggested by TheFu work.  Data backup is useful.  Probably the easiest is using it as a web server for local experiments.  With port forwarding on your modem/router you can even access the web pages ove the net.  What are you interested in trying?  The sky is the limit.

---

### Post by Iowan on 2014-02-22
> **niall.stronge said:**
> Awesome, thanks for the advice so far. But what would you use a home server for, rather than just a glorified NAS?
I have an antique acting as DHCP/DNS/Samba server.  I have another as a LAMP server. I don't have a mail server, yet, nor an LDAP server. They're on my "To-do" list, but the "Due" date seems to be getting further away. I unsuccessfully tried a media server - need to look into that someday, too...

And... Let's not forget the Raspberry Pi and BeagleBone Black - one of which should become a home automation server.

---

### Post by niall.stronge on 2014-02-22
Well, I'm still putting the concept down on paper, but what I want to do with the server is this:
I work and study away from home a lot of the time, and the internet connection where I stay when I work is heavily restricted (i.e. We are unable to torrent, are restricted to the amount of devices we can connect at any one time, etc.). What I would like to do is configure my old gaming tower (which has recently had a few upgrades) into a media/file server that the folks at home can use locally on the domain and, ideally, I will be able to log on remotely to access torrents, stored media and to maintain.

So, in all honesty, I just want to try and get around work's "no torrent" policy without getting into trouble if I get caught ;)

---

### Post by Iowan on 2014-02-22
> **niall.stronge said:**
> So, in all honesty, I just want to try and get around work's "no torrent" policy without getting into trouble if I get caught ;)Is it really worth it? 
Not in my book...

---

### Post by niall.stronge on 2014-02-22
Well, there are other reasons, but that is what started me thinking about how to go about it. For example, it would be useful to have access to all my music and films without having to carry round an external drive with me. It would also give me something to do to keep my mind active while I'm waiting to get loaded onto my next course, and (hopefully) give me a bit more experience in real time networking, rather than just using virtual machines.

---

### Post by Lars Noodén on 2014-02-22
As mentioned, you can use SSH to control what your server is doing just as if you were typing at the local terminal.  So what runs there, stays there, just your control is done from the remote machine.

Also, if you want to monitor your torrents running at home you can use Transmission's web interface and tunnel access to it over SSH.  Tunneling, aka port forwarding, is one of the extra things which SSH can do which is very helpful.

---

