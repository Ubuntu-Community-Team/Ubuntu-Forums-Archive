---
title: "trying to install ubuntu on Pentium 3 server"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by Andrew_Bishop on 2014-09-14
I just got some old (really old!) pentium 3 servers to experiment with and learn how to use. I have a copy of ubuntu on an external hard drive and I have been trying to boot from that, but the server doesn't recognize it. I have limited experience with Linux and command lines.

---

### Post by jimmy-frydkaer on 2014-09-14
Pentium 3 ? Guess you need to find a 2.6.x kernel for that beast

Which OS is installed on the server?

---

### Post by ibjsb4 on 2014-09-14
I am not so sure why it would be necessary to use the old 2.6 kernel, maybe jimmy will tell us.

If your trying to use the full featured Ubuntu iso, thats a problem with a server.  A server will not have the graphic capability for this.

I suggest trying either Lubuntu or Xubuntu.

---

### Post by grahammechanical on 2014-09-14
Please give more information about what happens when you try to load Ubuntu on that external hard disk.

When we run a Ubuntu live session it detects the hardware and uses appropriate hardware modules (drivers). Then when we install Ubuntu we get a system that fits the hardware we have. The driver modules in Ubuntu on that hard disk might not be suitable for the hardware in those servers.

The version of Ubuntu, is it a server version or a desktop version? If it is a desktop version then it is expecting a graphic adapter. Can you not see that there could be all kinds of reason why Ubuntu is failing to load? And without more information about what is actually happening it become impossible to diagnose.

Regards.

---

### Post by MartyBuntu on 2014-09-14
> **Andrew_Bishop said:**
> I have a copy of ubuntu on an external hard drive and I have been trying to boot from that, but the server doesn't recognize it.


Honestly, I'd just keep it simple and install Ubuntu to a hard drive attached to the server's native controller.

Having said that, even a virtualised server would run circles around a Pentium-III era machine...

---

### Post by pissedoffdude on 2014-09-14
Oh wow, now that is old!  That's definitely not strong enough to run Ubuntu.   Your best bet is running a distro like feather (it's discontinued, but considering your hardware it might be what you want).  DSL or puppy might work.  But considering the oldness of that machine, what are you planning to do with it? You won't be able to run any modern software, and it might be a better idea to delve into linux on your current machine with a flash drive if you don't want to install it

---

### Post by Vladlenin5000 on 2014-09-14
There are many "server" usages doable in that machine. 
It can run the latest Ubuntu server and it should even run acceptably some very lightweight desktop environment. As long as the server base - without DE - is already installed and running you can experiment with desktop environments.
However, it's much easier to run a live session and test how it performs and that seems to be the first issue.
Posting the make/model of those old servers surely helps to find out how to both some installation media in that machine. I seriously doubt it can boot anything from USB so I think it's a waste of time what you're doing with the external HDD.

---

### Post by ibjsb4 on 2014-09-14
All this P3 negativity, have you ever own one?  I have and they could run Lubuntu.  

They can come with up to 8 processors.  True, the FSB is low, but they use a large L2 to help make up for this.  Video is possible, just not in full screen on the ones I had.

> Your best bet is running a distro like feather (it's discontinued, but considering your hardware it might be what you want).
Recommend discontinued OS?  Considering your hardware?  I would think about editing that.  All we know is its a P3(s).  Could have several gig of ram, could have a video upgrade.

Old yes, but not hopeless :)

I agree with Vladlenin5000

If you can't run Lubuntu, there is Lubuntu-core or lighter yet is LXDE.

@Vladlenin5000
Agreeing with you actually hurt, whats with that :p

---

### Post by Vladlenin5000 on 2014-09-14
I implicitly agreed with you as well in your comment about the kernel. I don't see any advantage of using a 2.6.x either.

---

### Post by pissedoffdude on 2014-09-14
> **ibjsb4 said:**
> All this P3 negativity, have you ever own one?  I have and they could run Lubuntu.  

They can come with up to 8 processors.  True, the FSB is low, but they use a large L2 to help make up for this.  Video is possible, just not in full screen on the ones I had.


Recommend discontinued OS?  Considering your hardware?  I would think about editing that.  All we know is its a P3(s).  Could have several gig of ram, could have a video upgrade.



True.  In my experience, it's been far easier to go with an older distro than trying to get modern software working on an old system though.  But like you said, we don't know the full system specs, so post your system specs Andrew!.  That said, I still think it's unlikely he'll get unity working on that setup (only based on what I think he has).

---

### Post by claracc on 2014-09-15
Of course you can install some light flavour of ubuntu in your pentium III computer.

I have one, and it has lubuntu desktop flavour installed in it, so I think a server version will run better because there is no a graphics (a lot of resources consumption) part.

Please see: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by jimmy-frydkaer on 2014-09-15
> **ibjsb4 said:**
> I am not so sure why it would be necessary to use the old 2.6 kernel, maybe jimmy will tell us.

If your trying to use the full featured Ubuntu iso, thats a problem with a server.  A server will not have the graphic capability for this.

I suggest trying either Lubuntu or Xubuntu.

I meant the thing about the 2.6.x kernel as a joke, maybe a bad joke, but still, a joke

---

### Post by mastablasta on 2014-09-15
does P3 support PAE kernel? if not then you need to boto with non pae boot option. as i knwo p3 runs Windows 200o quite well. so it should riun Lubuntu nice as well. I think LXLE version (the 12.04 one) is with kernel for modified for older CPU.

server will run well on it. you could use it for file server. if you need a gui for server (you connect via browser to your server) there is Zentyal and Webmin and Ajenti and others...

you could install Openmediavault which has an interface that is ment for file servers only.

other desktop distributions for older PC/servers:
- AntiX
- Slitaz
- LXLE
- DSL (kernel here is not patched often)
- Crunchbang
- Debian (with LXDE or openbox)
- Bodhi - but this one is now being discontinued (unless someone picks it up)
...

---

### Post by mörgæs on 2014-09-15
Pentium 3's support PAE just like the 2 and 4 do, but there's no SSE2. 

Anyway, let's put the thread on hold until original poster returns.

---

