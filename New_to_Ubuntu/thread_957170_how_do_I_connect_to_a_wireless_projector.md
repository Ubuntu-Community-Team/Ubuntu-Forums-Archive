---
title: "how do I connect to a wireless projector?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by benner on 2008-10-24
I have been playing around and googling etc... but I can't seem to get my ubuntu laptop (a compaq tc4400 tablet) to connect to any of the projectors in my school.  networking is fine and i have no trouble connecting to the Internet. Just the projectors.  

And from how it looks if I use the networking tool in the toolbar, I can only connect to one at a time.  Is that right?  Can I simultaneously connect to the Internet and to a projector?  The machine is a dual-boot with vista, whicVistah has no trouble doing connecting to both.  i power on the projector by putting the ip in a browser.  then I use a program called nec presenter that connects to the nec projector.

from ubuntu i can turn on the projector from my browser.  i just don't know how to get my desktop up there.

thanks in advance...

---

### Post by Hexagoon on 2008-10-24
Hi! You will have to have two wifi interfaces to connect to both the internet and a projector. About connecting to the projectors, its probably some issues with ad-hoc support in your network drivers. Do you know exactly what chip and driver you are using?

---

### Post by benner on 2008-10-24
the video chipset on my laptop is: Intel GMA 950 

the projector is NEC LT-380+

I don't know how to set up a second network interface.

Thanks

---

### Post by benner on 2008-10-25
Aren't there any Ubuntu users out there using wireless projectors? I figured this one for a no-brainer.

---

### Post by benner on 2008-10-26
bump

---

### Post by benner on 2008-10-27
anyone? i know the ip of the projector.  that's it.Hexagoon, you got me excited and then you never came back...

---

### Post by benner on 2008-12-29
still nothing?  from windows, i have to open a program called 'presenter' to connect.  from linux, still can't.

---

### Post by cariboo on 2008-12-29
A lot of it depends on what network protocol the projectors are using, is it a standard protocol, or is a proprietory protocol that MS has come up with.

You should be to see all the device on the network, if the network usues the standard smb network protocol by using a command like:

```
smbclient -L <hostname> -U%
```

where <hostname> is the hostname of the network the projector is attached to.

Jim

---

### Post by benner on 2009-01-05
that lists all the computers on the network but not the projectors.  i have the IP's and MAC addresses and so on but i can't figure out the network connection manager for ubuntu to connect to it.  in windows, i would use a program called 'presenter' but in ubuntu i have no idea.

---

### Post by benner on 2009-01-06
someone must use ubuntu through a wireless projector.  google is giving me nothing.  any information might be helpful.  this is the last step for me to make the transition complete...

---

### Post by benner on 2009-01-16
bump

---

### Post by handydan918 on 2009-01-16
Not a solution, but a path to start down in search of one, perhaps. Install nmap and do
```
nmap <ip-address_of_projector>
```and it should tell you what ports are open, which you can use to guess what the protocol is,

---

### Post by benner on 2009-01-19
here's what I got from running nmap:

Interesting ports on 10.1.13.55:
Not shown: 1712 closed ports
PORT     STATE    SERVICE
7/tcp    open     echo
80/tcp   open     http
1024/tcp filtered kdm

does this mean anything to you?

---

### Post by benner on 2009-01-22
bump

---

### Post by handydan918 on 2009-01-22
> **benner said:**
> here's what I got from running nmap:

Interesting ports on 10.1.13.55:
Not shown: 1712 closed ports
PORT     STATE    SERVICE
7/tcp    open     echo
80/tcp   open     http
1024/tcp filtered kdm

does this mean anything to you?

It means that port 80 is open for http business, which might be what you need. No idea how to go about it...maybe try <ip-address:80> in the address bar of impress?

---

### Post by lewmnik on 2009-03-16
We just got Epson 1825 wireless yesterday, i'll look into this tomorrow, will post quickly my findings..

---

### Post by benner on 2009-03-30
Any luck?

---

### Post by cslee@ubuntforums on 2010-10-01
As far as I can tell these projectors use RDP as the protocol so you need to find a way of sending your desktop via RDP to a remote host.
It would be great if they supported VNC but I have not seen any that do this.

There is at least one RDP library but I have not seen a user interface to forward your desktop to an RDP client.

Regards,
Chris.

---

### Post by Elfy on 2010-10-01
closing necro thread

---

