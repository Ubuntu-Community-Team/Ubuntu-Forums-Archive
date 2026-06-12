---
title: "Changing IP address without rebooting?"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by honeybear on 2012-12-15
Hi,


Let suppose that you are in DHCP in an intranet network (rj45, ifconfig on eth0). In addition, the router gives you an IP number, and let suppose that it is allowed to change it as you wish. You have 192.168.1.100, and you desire to change it to 192.168.1.105. You simply wish to make it non permanent, so you do not desire to modify the /etc/. Why? Because you are in an hotel with an intranet. Your travel is great, and tomorrow morning, you leave early.

So the command would be to use ifconfig and dhclient. There are actually many possibilities, and you might wish not to modprob again your eth0 or do /etc/init.d/networking restart. You also would like to avoid rebooting (sudo reboot), because your screen session is heavily compiling a program. 

you desire the 192.168.1.105, the command might be on the good direction but it is not sufficient.
```
sudo ifconfig eth0 192.168.1.105 
```

What is the best way to make your IP change, this without rebooting?

thank you

---

### Post by Zill on 2012-12-16
honeybear:  I have to ask the question *why* do you care what IP address the DHCP server allocates your client?  One address is very much like another!

While you can allocate fixed IP addresses within your own LAN, you have no control over, for example, a hotel LAN and therefore the DHCP server will define the IP address you receive.  Personally, I can't think of any way a client PC can define a DHCP IP address but I remain open to suggestions. ;-)

---

### Post by honeybear on 2012-12-16
> **Zill said:**
> honeybear:  I have to ask the question *why* do you care what IP address the DHCP server allocates your client?  One address is very much like another!

because.


Any further input about the thread eventual answer?

---

### Post by Paqman on 2012-12-16
> **honeybear said:**
> because.


The evasiveness of this answer makes me wonder if you're trying to circumvent something. It was a legitimate question. I think if you want assistance you should clarify that what you're trying to do is above board.

---

### Post by honeybear on 2012-12-16
> **Paqman said:**
> The evasiveness of this answer makes me wonder if you're trying to circumvent something. It was a legitimate question. I think if you want assistance you should clarify that what you're trying to do is above board.

I think that I have been sufficiently clear on the first post. 
Why the person would need to know why actually it is aimed? funny, is that it is a simple answer. I took an example to make it simpler.


If I dont give any answer, then, no help, right? I thought that people are all free and have right to refuse to tell all of their life. You want also my ip and root passwd? 


Great board. ;)

---

### Post by haqking on 2012-12-16
Change the IP address in your network manager or /etc/network/interfaces

then do following

```
sudo ifdown eth0
sudo ifup eth0

```or a ```
sudo service networking restart
```Or substitute eth0 for wlan0 where applicable if its your wireless interface

As for wanting to change your own IP i see no reason why it should be considered underhand in anyways

---

### Post by Paqman on 2012-12-16
> **honeybear said:**
> 
If I dont give any answer, then, no help, right? I thought that people are all free and have right to refuse to tell all of their life. You want also my ip and root passwd? 


You're free to provide as much or as little information as you want, and everybody is free to help you as much or as little as they want.

---

### Post by honeybear on 2012-12-16
> **haqking said:**
> Change the IP address in your network manager or /etc/network/interfaces

then do following

```
sudo ifdown eth0
sudo ifup eth0

```or a ```
sudo service networking restart
```Or substitute eth0 for wlan0 where applicable if its your wireless interface

As for wanting to change your own IP i see no reason why it should be considered underhand in anyways

Hi,

this is what I usually do but visibly I am not so sure that it is the most suited option.

```
ifdown eth0 
ifconfig eth0 192.168.1.105 
ifup eth0 
dhclient
```

there must be sthg better than that

---

### Post by haqking on 2012-12-16
> **honeybear said:**
> Hi,

this is what I usually do but visibly I am not so sure that it is the most suited option.

```
ifdown eth0 
ifconfig eth0 192.168.1.105 
ifup eth0 
dhclient
```there must be sthg better than that

I dont get what you mean in "better" better how ? does it work or not ?

---

### Post by honeybear on 2012-12-16
> **haqking said:**
> I dont get what you mean in "better" better how ? does it work or not ?

Most of the time yes, but I think that it is not suited and not the right way

---

### Post by steeldriver on 2012-12-16
I'd be leery of configuring a static client IP on someone else's network where you can't guarantee that the address is free

From reading around the subject a bit, I believe there *is *a mechanism within DHCP for this kind of thing (specifically, the DHCPDISCOVER packet allows for a dhcp-requested-address from the client) but I don't know if dhclient supports it - and obviously the server may deny the requested address either because it's unavailable or just as a matter of policy.

---

### Post by Cheesemill on 2012-12-16
What DE are you using?

If you are using Unity or Gnome shell can't you just use network-manager to make the adjustments or are you specifically looking for a CLI solution.

---

### Post by haqking on 2012-12-16
> **honeybear said:**
> Most of the time yes, but I think that it is not suited and not the right way


mmmm ok, well i dont know how to answer you then ;-)

---

### Post by honeybear on 2012-12-16
> **steeldriver said:**
> I'd be leery of configuring a static client IP on someone else's network where you can't guarantee that the address is free

From reading around the subject a bit, I believe there *is *a mechanism within DHCP for this kind of thing (specifically, the DHCPDISCOVER packet allows for a dhcp-requested-address from the client) but I don't know if dhclient supports it - and obviously the server may deny the requested address either because it's unavailable or just as a matter of policy.

this is my routers. not worries. I have 3 routers. Usually I can change my ip. my router is fine with it. It does not complain at all. I could tell it to fix the ip, but I prefer like that since I call the machines by their hostname. 

So, to return to the topic, I think that there is a way to do better than ifdown/ifup... I guess it cannot be working in all cases. 

For instance, when you fake the mac address, this really works well. When you change your ip, it is not so well working

---

