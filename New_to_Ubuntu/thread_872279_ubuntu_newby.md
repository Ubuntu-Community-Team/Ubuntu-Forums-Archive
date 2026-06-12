---
title: "ubuntu newby"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by lrisner on 2008-07-27
I have just downloaded and installed Ubuntu on a previously working Desktop I am going to give to a economically disadvantaged friend. I did not want to "give away" my bought and paid for version of XP so I opted for Ubuntu for the Box.

Everything went fine until Internet time. It will not see the network. I have tried Network Manager, Manual config, and terminal. It does not see the network enough to hook up. I say "not enough" because it does list "belkin", the name of my network, in the domains list in network Manager.

I am at a lose about what to do. This box worked fine with XP  and I even went as far as swapping out the NIC in case it went bad overnight.


Please help. I do not what to buy another copy of XP.

Thanks

Larry

---

### Post by The Titan on 2008-07-27
> **lrisner said:**
> I have just downloadeed and installed Ubuntu on a previously working Desktop I am going to give to a economically disadvantaged friend. I did not want to "give away" my bought and paid for version of XP so I opted for Ubuntu for the Box.

Everything went fine until Internet time. It will not see the network. I have tried Network Manager, Manual config, and terminal. It does not see the network enough to hook up. I say "not good enough" because it does list "belkin", the name of my network, in the domains list in network Manager.

I am at a lose about what to do. This box worked fine with XP  and i even went as far as swapping out the NIC in case it went bad overnight.


Please help. I do not what to buy another copy of XP.


Larry
What kind of network card is it?  Have you checked to see if it is compatible with Ubuntu?

---

### Post by lrisner on 2008-07-28
bump

---

### Post by SunnyRabbiera on 2008-07-28
Do as The Titan suggested, give us your specs so we can help you better.

---

### Post by jamesrfla on 2008-07-28
Is Ubuntu having trouble interfacing with the card or Ubuntu detects the card but you can't hit the web?

---

### Post by lrisner on 2008-08-07
As I stated before,  tried two cards with the same result. no network detected.

Current card: Linksys #LNC100tx.

Everything else on the install seems great, but I am building for a friend to surf the Internet so it is not done!

I also tried a wireless NIC with the same result.

There clearly is no problem with the network as it has three other Comps on it with all working fine. I have tried swapping ports on the switch and swapping cables. No stone has been left unturned.

---

### Post by lrisner on 2008-08-07
bump

---

### Post by LowSky on 2008-08-07
did you mean LN**E**100tx?

What are the rest of the computer's specs?

open a terminal and type or copy this command

```
lspci -v
```

then please post here

---

### Post by ace007 on 2008-08-07
You need to systematically troubleshoot.


1). Does lspci -v list an ethernet card? If not its not recognized in the system.

2). In a terminal, is there a device listed other than "lo" such as "eth0"? Is there an assigned IP address to that devicee? If not it the router's fault.

3). Did you change the router settings to manual IP configuration? Is it still using DHCP?  Did you change the computer's IP configuration to manual or is it still in roaming mode?

---

### Post by lrisner on 2008-08-08
> **ace007 said:**
> You need to systematically troubleshoot.


1). Does lspci -v list an ethernet card? If not its not recognized in the system.

2). In a terminal, is there a device listed other than "lo" such as "eth0"? Is there an assigned IP address to that device? If not it the router's fault.

3). Did you change the router settings to manual IP configuration? Is it still using DHCP?  Did you change the computer's IP configuration to manual or is it still in roaming mode?


Great response! 

  Clearly, I may not be ready for Ubuntu. This is far too tech for me, to be honest. 

To clarify my situation,I am putting this box together and have no OS for it. It had XP, but I am unwilling to give the License away as this computer is a freebie for someone. It was on my net with XP pro on it, but my son got a new gaming computer and I offered his old one with a OS other than my XP Pro. to a boarder.

I have a win98 license and may just have to give them that.


My network is ad-hoc with a Belkin router and 
I don't want to mess with it as it works fine right now. The "green" party will be using my network and I'd rather not change due to the other 4 computers working fine.

I will post the result, as I am willing to  learn.


Thank You all!

---

### Post by scotcella on 2008-08-08
Hey mate, 

You said you were learning..  and open to learning, that's great!! Welcome!!! It'll be great to learn something new. Since you are learning, and no doubt you will run into snags.

This is a great forum, no question is a stupid question- only stupid users!
Please feel free to post questions when ever you need to.

If you have multiple questions, it's best to post one question at a time (eg you're having trouble with Firefox and something else, do two separate posts unless they're connected).


Okay lets start with the terminal.....

Do you know what the Terminal is? It's the command thingy.. when someone asks you to post the output of something, this means you need to type in a command in the terminal to find out some information and copy and paste it back onto here...

To open the Terminal, go to Applications -> Accessories -> Terminal.

Type in the commands EXACTLY.. (or copy and paste). 
> 
lspci -v

The command above will list your computer specs.. so if you can type or copy and paste it into the terminal. The terminal will ask you for your password, do not panic if you can't see it showing up, just type it once and then press enter... 

Then copy and paste the response onto here, we might be able to help you out.

Try and be persistent and keep learning!!
Good luck and I hope everything works out for you!!

:o)

---

### Post by pparks1 on 2008-08-08
> **ace007 said:**
> 
1). Does lspci -v list an ethernet card? If not its not recognized in the system. Think of this like the behind the scenes Device Manager under Windows.   We need to know whether Ubuntu sees the card or whether it doesn't.   This command will provide that answer.

> **ace007 said:**
> 2). In a terminal, is there a device listed other than "lo" such as "eth0"? From a terminal window, ***sudo ifconfig*** will tell you whether your operating system is attempting to use your card.  The lo is the loopback adapter or 127.0.0.1...which is the computer itself.   The eth0 is the ethernet interface and thus should be the one that gets the IP address.

Let's start there and see what we get.  You might be surprised with how much information we can provide with the outputs of those 2 commands.

---

