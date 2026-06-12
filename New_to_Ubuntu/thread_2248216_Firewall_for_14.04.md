---
title: "Firewall for 14.04?"
date: 2014-10-13
forum: New to Ubuntu
---

### Post by logie on 2014-10-13
I have just started with 14.04.  Can anyone suggest a good firewall program for this distro?

---

### Post by slickymaster on 2014-10-13
[UFW - Uncomplicated Firewall]("https://wiki.ubuntu.com/UncomplicatedFirewall"), is available by default in all Ubuntu installations after 8.04 LTS.

You can install [Gufw]("https://help.ubuntu.com/community/Gufw"), which is a very user-friendly way to manage your Ubuntu Firewall.

---

### Post by SeijiSensei on 2014-10-13
By default, Ubuntu has no ports open to the outside world.  If you install something like the Apache web server, it will open ports (80 and, perhaps, 443 in this case), but a vanilla desktop installation really doesn't need a firewall.

The "[Do I need a firewall?]("https://help.ubuntu.com/community/DoINeedAFirewall")" help page is worth reading on this subject, but I think it's a bit too paranoid.  
> One, if you do not utilize a firewall on the basis that you have no open ports, you are crippling your own security because if an application that you do have is exploited and code execution occurs a new socket can be created and bound to an arbitrary port. The other important factor here is that if you are not utilizing a firewall you also have no outbound traffic control whatsoever.
For most users who run nothing but mainstream programs from the Ubuntu repositories, the possibility for such exploitation is remote.  Note the examples given for potential exposures are things like Apache, FTP, SSH, and other servers.  Ordinary desktop users rarely run such programs.  Even then, Ubuntu usually configures server software to listen only on the "localhost" interface, 127.0.0.1. That interface is visible only on the local machine and cannot accept remote connections. Apache is an exception, but both MySQL and Postfix, to take two common examples, are confined to localhost by default.  You can reconfigure these programs to accept remote connections, but it doesn't sound like you're likely to be doing any of this.  If you do want to run servers that are open to the outside world, then you most assuredly need a firewall.

Also if you're behind a firewall router, you have an additional layer of protection there as well.

---

### Post by sammiev on 2014-10-13
Here is the basic settings I use with GUFW with a few extra ports for my printer and VPN.

I deny all in and out except the ones I use for out going.

---

### Post by logie on 2014-10-13
Many thanks.  I probably don't need it, but now I know where to find it.:mad:

---

### Post by pfeiffep on 2014-10-13
> **logie said:**
> Many thanks.  I probably don't need it, but now I know where to find it.:mad:

Follow the link in post from slickymaster and you'll find complete guidance ... here's a snip

> [COLOR=#333333][FONT=Ubuntu Beta]Getting started with ufw is easy. For example, to enable firewall, allow ssh access, enable logging, and check the status of the firewall, perform:[/FONT][/COLOR]
$ sudo ufw allow ssh/tcp
$ sudo ufw logging on
[SIZE=4]**$ sudo ufw enable**[/SIZE]
$ sudo ufw status

---

### Post by craig10x on 2014-10-13
I just install GUFW and turn it on...with no extra special settings...does the job for me ;)

---

