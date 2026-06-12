---
title: "Disable Skype Supernode in ubuntu Hardy"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by cool_penguin on 2008-08-14
Hi Guys,

I was wondering if there is a way to disable Skype supernode feature in Ubuntu Hardy. I do not want my computer to act as a node in serving other calls since I have a relatively low bandwidth. 

Any help will be greatly appreciated. 

Thanks a lot.

Cheers,
Harry

---

### Post by brian_p on 2008-08-14
> **cool_penguin said:**
> Hi Guys,

I was wondering if there is a way to disable Skype supernode feature in Ubuntu Hardy. I do not want my computer to act as a node in serving other calls since I have a relatively low bandwidth. 


You can't. See [www.skype.com](www.skype.com).

---

### Post by starcannon on 2008-08-14
The windows client allows this, some poking around in skype forums confirms that its coming to mac and linux clients eventually as well.

Until then creating firewall rules can do the job, but can cause some transfer rate issues.

[http://snapvoip.blogspot.com/2006/10/how-to-be-or-not-to-be-skype-supernode.html](http://snapvoip.blogspot.com/2006/10/how-to-be-or-not-to-be-skype-supernode.html)

[http://chris.pirillo.com/2007/10/23/are-you-a-skype-supernode/](http://chris.pirillo.com/2007/10/23/are-you-a-skype-supernode/)

If your behind a nat router your already disabled as a supernode

---

### Post by cool_penguin on 2008-08-14
Thanks for your prompt response. How would I know if I were to be behind a NAT server?

---

### Post by starcannon on 2008-08-14
I'd likely do a search on the model of the router combined with the term NAT. See what pops up. Most consumer grade routers, linksys, netgear, etc... are NAT routers by default.

If you built the router yourself I'm not sure how one would know, I actually keep meaning to do this project, but... hehe, my specialty is procrastination.

---

### Post by cool_penguin on 2008-08-14
Thanks. Shall give it a shot on Google. I use a FON Wireless router (Which I want to flash with another open source firmware) and a Motorola Cable Modem.

Shall give you a feedback soon.

Cheers,
Harry

---

### Post by cool_penguin on 2008-08-14
Hey starcannon. You mentioned you would wanna build your own router, right? May be u could help me with this. How could I replace the existing firmware of my FON Wifi router by an Open Source Firmware like DDW or something like that?

---

### Post by starcannon on 2008-08-14
Don't know, sorry, I currently use a linksys router, not the one that can be made into a super router. On my consumer grade stuff I generally flash it with the updates released by the manufacture. If I build one from scratch I'll do so using an old laptop or computer that is too slow to do much of anything else, say an old PII 133mhz or something of that nature, and put coyote linux, or freesco on it or something like that.

---

### Post by binary.koala on 2008-08-14
in fact it's only upnp that will make your skype be supernode behind nat router. many routers (linksys included) have upnp by default. 
you can have a nice visualization of your udp skype traffic with 'etherape',
just run in on your active iface and wait a while (see attached picture).
im eager to be able to turn supernode off within skype.

---

