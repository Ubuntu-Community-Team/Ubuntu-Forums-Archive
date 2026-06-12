---
title: "options for 2 computers 1 monitor"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by s1wood on 2012-05-25
I now have a second old P4 computer with Windows XP installed to use for a few things that don't run on Linux (Windows never worked very well on Virtualbox - not enough spare capacity).
I would like to be able to manage them with one monitor/mouse/keyboard, using the Ubuntu as the main computer.
They are in the same room and could be put side by side.
They both have wireless internet and connect to a wireless modem/router.
Teamviewer works but my internet is a bit  slow  and videos don't play properly via the remote.
A KVM switch looks like my best bet but before I get one I would just like to ask whether I could do this through the network without losing internet speed, perhaps with crossover cable? I don't quite understand what can be done through the network connection, I don't need to file share, it is just for 'remote' access.

 I can't try it out because I have never managed to set up a network - I get lost in all the different addresses whenever I try, the same with RemotedesktopViewer, I just don't know what to put in the boxes - if the network is the best solution I shall have to appeal for someone to talk me through it, I have already read plenty of instructions.

Advice would be much appreciated.

Susan
PS these are both old machines - Bios defaults to around 2002.

---

### Post by sudodus on 2012-05-25
I'm using an ATEN KVM switch for 4 computers and I have used an ATEN KVM switch for 2 computers.

Both use VGA video connections to the monitor, and they work without any problem independent of the operating system (Windows or Linux). The KVM switches are only connecting the monitor screen, keyboard, mouse and load-speakers, so they are independent of the LAN or WLAN [wireless] local area network.

The easiest way to connect several computers to the internet and to each other is via a router (wired or wireless). It is described in the user manual of the router how to set up the LAN or WLAN.

---

### Post by s1wood on 2012-05-25
So, IF I manage to connect them via the router do I get control of  the windows machine from the linux or do I need to set up a remote desktop as well? Like I said,I've never succeeded in setting up a network and don't really know what result to expect.

Susan

---

### Post by kanikilu on 2012-05-25
I use a simple KVM switch to go between my Ubuntu machine and Mac mini at work, but once upon a time, I got synergy to work to accomplish the same task:

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

It wasn't particularly easy to setup, especially since I had to figure out how to tunnel it over SSH because it's not secure. On a home network, though, this probably wouldn't be a big concern...

---

### Post by s1wood on 2012-05-25
Synergy seems to require separate monitors, which I haven't got space for.
What about connecting by crossover cable? I've read this is the fastest connection is it possible to set up the remote desktop this way?

Susan

---

### Post by kanikilu on 2012-05-25
Oops, you're right, that was when I had dual monitors. I think a KVM switch is going to be your easiest option. A cross-over cable could be used to directly connect 2 computers, but I don't think that really helps you in this case.

The only other thing I'd suggest is if you have both computers on your home network, just enable remote desktop connection on the Windows computer, and connect to it from the Ubuntu machine with a client like Remmina. If using the Windows computer name doesn't work, you can always set a static IP address and connect to it using that.

---

### Post by s1wood on 2012-05-25
Perhaps I should have another attempt at setting up the home network and then try the remote desktop if I succeed. what do you mean about setting a static IP address?

Susan

---

### Post by Dave_in_MD on 2012-05-25
> **s1wood said:**
> Perhaps I should have another attempt at setting up the home network and then try the remote desktop if I succeed. what do you mean about setting a static IP address?

Susan

Another member here has a step by step on a windows Ubuntu network
[http://www.europe.eclipse.co.uk/Ubuntu/1010%20on%20Win%20Network.htm](http://www.europe.eclipse.co.uk/Ubuntu/1010%20on%20Win%20Network.htm)
It was written around 10.10 but works for 12.04 as well, just different screen shots

I concur a KVM

---

### Post by s1wood on 2012-05-25
That tutorial assumes I can set up the network which has always been my problem.
KVM switches seem to be quite cheap on ebay though!

Susan

---

### Post by sudodus on 2012-05-26
> **s1wood said:**
> That tutorial assumes I can set up the network which has always been my problem.
KVM switches seem to be quite cheap on ebay though!

Susan
Yes, I think you should divide your task into two subtasks and solve them independent of each other.

1. User interface via a KVM

2. Internet and LAN via a router

---

### Post by s1wood on 2012-05-26
Yes,
I'll have another go at the network and scream for help if needed. Could my router firewall be the problem do you think - I've never attempted to do anything with it.

Susan

---

### Post by Old_Grey_Wolf on 2012-05-26
I prefer the KVM switch when working with only a few desktop computers. 

If I don't need more than one computer powered on; then, I don't need to power on a computer with a keyboard, mouse, and monitor just to ssh or remote desktop into the other computer.

Remote Desktop (RDP) is slow on a Wireless-G network anyway. You really want a Wireless-N or hard-wired connection if you are going to use Remote Desktop on a regular basis.

---

