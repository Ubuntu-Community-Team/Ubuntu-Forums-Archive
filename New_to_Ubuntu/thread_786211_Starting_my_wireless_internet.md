---
title: "Starting my wireless internet"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by tori on 2008-05-07
I just installed ubuntu on my desktop, and I'm trying to get my wireless Internet to work. I have no idea what to do, can someone please walk me through it? 

PS, I went to the network admin tool and it only shows wired connections and point to point connections. No wireless. 

Even a link to a good walkthrough of the system I'm looking for would be fine.

Thanks :)

---

### Post by daimaru on 2008-05-07
> **tori said:**
> Even a link to a good walkthrough of the system I'm looking for would be fine.
what kind of wireless adapter are you using ? for future reference, just go to "UserCP" in the forums menu select "Edit signature" and add your system details like (desktop/laptop, graphics card model, sound card, wireless adapter, anything else that might be usefull) to the signature. That makes it easier for people reading your post to give imidiate and relevant feedback, instead of asking you what kind of wireless adapter your using. As I did above ;)

---

### Post by Brightbelt on 2008-05-07
Hi, Welcome to Ubuntu. :)

It would help to know what kind of card your wireless card is... I'm not good at the command line, but try running
```
sudo lspci
```
and you can maybe find out what it is. This link can be a resource for you possibly:

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=wireless&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=wireless&titlesearch=Titles)

Good Luck!
Frank B.

---

### Post by tori on 2008-05-07
It's a dimension 8200 desktop. That's about all I know... 

As for the wireless card, I typed lspciand got "ethernet controller: realtek semiconductor, Co., Ltd." Is that my card? If not then, I don't know and will have to wait until the owner of the network comes around. Unless you can tell me to figure out what it is. NVIDIA is the only thing recognized by my hardware drivers. 

And the only CD I've uncovered so far from the depths of my desk is for a Wireless LAN PCI card, v 2.0. So.........?

---

### Post by tori on 2008-05-07
*delete*

---

### Post by daimaru on 2008-05-10
hi tori sorry for the long wait. its not the ethernet controller. there should be something saying wireless in it. do this from the terminal:
```
lspci |grep Wireless
```for my computer it gives me
```
Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection
```If you get no output at all try this.
```
lshw -C network
```that should give you a list of all your network controllers including wireless. No matter what could you please paste the output of the lshw -C network thx

---

