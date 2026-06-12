---
title: "remote desktop (vinagre) via ssh"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by digitography on 2012-02-03
I have got to the frustrated as hell stage with this.

all computers referred to here as 11.04 Ubuntu.d

I have a ddns setup and have opened the port of the router.

I can use the command

ssh [email]user@ddns...com[/email]

it connects fine and I can use command line stuff, even ssh into other computers on the same network.

Looking online I found ssh 5900:127.0.0.1:5900 [email]user@ddns...com[/email] instructions said set vinagre to localhost::5900 and it should be good to go. However it is flakey as hell, connects sometimes sometimes not.

So is there a better more reliable way.

As always thanks for your time, and efforts, and hope I get an answer before I lose what little hair I have left.

---

### Post by lkraemer on 2012-02-03
digitography,
**WARNING:**  If you are just accessing your ddns.....from your LAN
**DO NOT FORWARD (OPEN) your router port**, as you will be attacked
by others over your WAN.   You will be able to access all IP's
on your LAN with the Port not Forwarded, saving you all the headaches.
(Check your LOG FILES and you will see the numerous attempts on
your system!)

If you must FORWARD the router port, the best thing to do is set up some
IPFW rules to ONLY allow your specific IP address to access that
Port.

Here is some information you need to read BEFORE FORWARDING any Ports!

Hopefully you can correct the situation before your system gets penetrated!
(CHECK your LOG FILES Immediately!)

REF's:

[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11500](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11500)
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11496](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11496)

lk

---

### Post by digitography on 2012-02-03
When I wrote opened the port, I only port forwarded the port for ssh, havent' opened anything else.

The router is a broadband router, for small office use, and the ddns (one of those freebies) simply directs to the external IP of my broadband router.

Is this still a bad idea?

All the stuff I have read says that's the way to do it.

---

### Post by fsLori on 2012-02-03
You can forward specific remote X applications to your computer with:

ssh -X username@remotehost

When logged on, just try e.g.

xeyes &

In my experience, this works a lot quicker than forwarding whole desktops with VNC.

---

### Post by lkraemer on 2012-02-03
Any time you FORWARD a port, you need to make sure that it's access
is LIMITED to EXACTLY those who need access.  Your LOG FILES will
tell the tale as to who is attempting to gain access, or have gained
access.  That limiting has to be done by you via IPFW rules.

It's always best to error on the side of caution......

You ONLY need to forward a port, if you are accessing your ddns
via the WAN.

lk

---

### Post by d4m1r on 2012-02-03
> **lkraemer said:**
> digitography,
**WARNING:**  If you are just accessing your ddns.....from your LAN
**DO NOT FORWARD (OPEN) your router port**, as you will be attacked
by others over your WAN.   You will be able to access all IP's
on your LAN with the Port not Forwarded, saving you all the headaches.
(Check your LOG FILES and you will see the numerous attempts on
your system!)

If you must FORWARD the router port, the best thing to do is set up some
IPFW rules to ONLY allow your specific IP address to access that
Port.

Here is some information you need to read BEFORE FORWARDING any Ports!

Hopefully you can correct the situation before your system gets penetrated!
(CHECK your LOG FILES Immediately!)

REF's:

[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11500](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11500)
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11496](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=11496)

lk


I would disagree. I have my local static IP set to DMZ mode in my router (all ports open) for YEARS and I have not experienced any negative effects....Some random IPs have been reported as "attacking IPs" according to my antivirus or other local programs, but again, nothing has happened.

Depending on your OS, I would say opening up all ports for SSH access isn't a bad idea..Manually managing ports is a HUGE pain in the *** for me anyway when I used to do it.

---

