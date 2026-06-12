---
title: "pfsense replacement"
date: 2017-11-10
forum: New to Ubuntu
---

### Post by Dreamerman on 2017-11-10
Hi, I run a dedicated pfsense machine (for internet gateway, proxy server, dhcp server, firewall, traffic shaping) and another Win7 machine for torrenting and file server. My Win7 is playing up and I wondered if a Ubuntu machine can do both as a headless machine? From bits of info I think I can but would like to know for sure before I do down this path. Any help is appreciated.

---

### Post by Tadaen_Sylvermane on 2017-11-10
Id personally keep using pfsense but virtualize it with kvm on an ubuntu host. Best of both worlds.

---

### Post by Dreamerman on 2017-11-10
> **Tadaen_Sylvermane said:**
> Id personally keep using pfsense but virtualize it with kvm on an ubuntu host. Best of both worlds.

Thanks for your reply but I mainly want to know if Ubuntu can do both.

---

### Post by ian-weisser on 2017-11-11
Ubuntu *can* do both...but don't discount Tadaen_Sylvermane's point that it's unwise to put all your services in one basket.

pfsense is designed (well) to do it's specialty job. You are likely to find Ubuntu less efficient and more cumbersome to manage at that specialty job. 
And, of course, it introduces unnecessary risk and brittleness into your network: A misbehaving torrent server on the same system can crash your network access.

---

### Post by Dreamerman on 2017-11-11
> **ian-weisser said:**
> Ubuntu *can* do both...but don't discount Tadaen_Sylvermane's point that it's unwise to put all your services in one basket.

Ok thanks, it is just that I find it cumbersome to manage 2 "extra" machines at home. Was exploring how to reduce it to just one.

---

### Post by Tadaen_Sylvermane on 2017-11-11
I run all my services bare metal. It can work and i haven't any problems. However keeping services isolated can do a great deal of positive. And you can script a bunch of things to make management of multiple machines easier.

---

### Post by Dreamerman on 2017-11-11
> **Tadaen_Sylvermane said:**
> And you can script a bunch of things to make management of multiple machines easier.
Well that is it. I am not an IT Man beyond the ability to setup Win machines. I got pfsense running at great time cost which I did it as a challenge just to see all the hype. I tried Linux of various flavours over past years but never got it into home-production

---

### Post by ian-weisser on 2017-11-11
See, now you're confusing.
You want pfsense because you want all the cool buzzword features (traffic-shaping)...but you don't like actually setting up and running all those cool features.
You run a Windows home server (well, okay, it's your life) using all that pfsense LAN-control power...but you're asking on an Ubuntu forum if it's comparable. You mention trying other distros.
Seems like you're dabbling and experimenting.

That's okay, Ubuntu is great for dabblers. 
Create a LiveUSB installer and start experimenting in the trial environment. Desktop and Server are just different mixes of packages, so you really cannot go wrong - installing server packages into a desktop is trivial; adding a Desktop to a server is just as simple.
Be patient - your Windows power-skills mean that you have much to unlearn. Neither Windows nor Linux is *better* - they are *different*.

---

### Post by Dreamerman on 2017-11-11
> **ian-weisser said:**
> See, now you're confusing.
Admittedly you are right. I do want control but want to spend less time controlling, know what I mean? I think I need to ponder a bit more before asking. Do appreciate your reply. Cheers.

---

