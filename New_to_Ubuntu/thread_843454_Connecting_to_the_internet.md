---
title: "Connecting to the internet"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by newbee. on 2008-06-28
Let me start by saying I'm a total newbee to linux in general. Today is the first time I've ever even see linux booted up. Before now, I've only heard of it.

I just installed kubuntu, and I'm trying to connect to the internet. I have a hardwired connection. How would I go about doing this? The network settings window always shows wireless. I don't want wireless.

---

### Post by wrtpeeps on 2008-06-28
> **newbee. said:**
> Let me start by saying I'm a total newbee to linux in general. Today is the first time I've ever even see linux booted up. Before now, I've only heard of it.

I just installed kubuntu, and I'm trying to connect to the internet. I have a hardwired connection. How would I go about doing this? The network settings window always shows wireless. I don't want wireless.

I assume you have checked to see that the internet isn't working straight after install?

---

### Post by newbee. on 2008-06-28
> **wrtpeeps said:**
> I assume you have checked to see that the internet isn't working straight after install?

Correct. I'm on my other desktop, which is connected to the same hub, and works fine. I've navigated to Network Settings and I see the interface "ra0". I gather that I'm supposed to see "eth0". Would that be a correct assumption?

---

### Post by newbee. on 2008-06-28
Please help. This is very frustrating.

---

### Post by defrex on 2008-06-28
open a terminal and enter: 
```
ifconfig
```

Post the output if you can.

---

### Post by newbee. on 2008-06-28
> **defrex said:**
> open a terminal and enter: 
```
ifconfig
```

Post the output if you can.

/bin/sh: ipconfig: not found

---

### Post by defrex on 2008-06-28
f not p

;)

---

### Post by newbee. on 2008-06-28
> **defrex said:**
> f not p

;)

Hah that was a typo on my part. I'm posting from my other computer now. It says the same thing.. /bin/sh: ipconfig: not found

---

### Post by defrex on 2008-06-28
are you typing ipconfig or ifconfig? ifconfig is the right one, and it should be in every ubuntu install. It confused me when I moved to linux because ipconfig is the command in windows to do pretty much the same thing.

---

### Post by newbee. on 2008-06-28
> **defrex said:**
> are you typing ipconfig or ifconfig? ifconfig is the right one, and it should be in every ubuntu install. It confused me when I moved to linux because ipconfig is the command in windows to do pretty much the same thing.

Doh!

Wow. It output a ton of stuff..
[IMG]http://i32.tinypic.com/72wxop.jpg[/IMG]

---

### Post by ethanklein on 2008-06-28
If you dont have the drivers installed for you eth0 connection. go to System>Admin>Software Sources and check all third part repos. It worked for me.

---

### Post by newbee. on 2008-06-28
> **ethanklein said:**
> If you dont have the drivers installed for you eth0 connection. go to System>Admin>Software Sources and check all third part repos. It worked for me.

I can't find admin :confused: Do I click the K logo (like the start menu in windows)?

---

### Post by defrex on 2008-06-28
Is your network card on your motherboard or no? What's the model. It's really bizarre to not have it work right away...

---

### Post by newbee. on 2008-06-28
> **defrex said:**
> Is your network card on your motherboard or no? What's the model. It's really bizarre to not have it work right away...

Yeah it's built in.

The pc is a mega 180

[http://www.tomshardware.com/reviews/msi-mega-180-mini,763.html](http://www.tomshardware.com/reviews/msi-mega-180-mini,763.html)

---

### Post by defrex on 2008-06-28
Heh, that was ubuntu instructions rather then kubuntu. I haven't used kubuntu myself, so I'm not sure where it is.

By the way, why did you chose kubuntu rather then ubuntu? Just curious.

---

### Post by newbee. on 2008-06-28
> **defrex said:**
> Heh, that was ubuntu instructions rather then kubuntu. I haven't used kubuntu myself, so I'm not sure where it is.

By the way, why did you chose kubuntu rather then ubuntu? Just curious.

Buddy of mine gave me the computer broken, I fixed it, and another friend had a kubuntu CD laying around. I usually use the pirated windows versions but I figured I could at least try this out.

---

### Post by defrex on 2008-06-28
You should try Ubuntu. It's much nicer, in my humble opinion.

As for you're network interface, I'm at a loss. Hopefully someone who knows more then me will jump in here. I don't know why the kernal nic drivers wouldn't work. WiFi, maybe, but I've never seen a problem with nic drivers..

---

### Post by newbee. on 2008-06-28
> **defrex said:**
> You should try Ubuntu. It's much nicer, in my humble opinion.

As for you're network interface, I'm at a loss. Hopefully someone who knows more then me will jump in here. I don't know why the kernal nic drivers wouldn't work. WiFi, maybe, but I've never seen a problem with nic drivers..

Is it easier to figure out for a beginner?

Also, how do I uninstall kubuntu? Boot from CD? Or is that just windows?

---

### Post by defrex on 2008-06-28
I don't want to insult KDE, but yes, yes it is. Plus it's easier to get help on these boards, too, since most people use it.

---

### Post by newbee. on 2008-06-28
How do I go about uninstalling kubuntu?

---

### Post by defrex on 2008-06-28
[Download]("http://www.ubuntu.com/getubuntu/download") an Ubuntu iso, and burn it to disk. Boot it up and install.

---

### Post by newbee. on 2008-06-28
> **defrex said:**
> [Download]("http://www.ubuntu.com/getubuntu/download") an Ubuntu iso, and burn it to disk. Boot it up and install.

I'll try it and report back with any problems.

Thanks!

---

