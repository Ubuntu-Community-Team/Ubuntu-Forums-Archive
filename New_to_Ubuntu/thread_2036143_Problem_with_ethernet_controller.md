---
title: "Problem with ethernet controller"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by NoGumption on 2012-08-01
I'm trying to use my laptop (running windows 7) as a wireless card for my desktop (running ubuntu 10.04). I already know how to do this.

My desktop isn't recognizing that a cord is plugged in to the ethernet port. I looked around for a driver, and along the way read something about a BIOS update fixing the same problem someone else had. I don't remember if I ever located the driver (this was about 5 hours ago), but I don't think I did. I did find the BIOS update and currently have it on a flash drive to install onto my desktop. This is where my frustration begins. The BIOS update is an .exe and I can't run it in Ubuntu. That is, without WineHQ. I can't get WineHQ without connecting to the internet, which I can't do without updating the BIOS (or driver... but that'll be an executable also...), which I can't do without the Wine thing. Messed around with that for awhile to no avail. Found a neat thing called Keryx which I couldn't get to work. Tried 1.0 public21 and the portable versions, couldn't get anything to happen on desktop computer (which is still offline) after clicking on it's name and then manage. 

Looked online for help, but nothing for the 1.0 release, so I tried the 0.92.4 which is what all the "help" I was finding was for. Could get it to come up on the offline computer and run as if to install, but at the end it said something about running apt-get update or something close to that. Went into the terminal and figured out how to get that to work, but that all failed and based on the little I understood I'd say it failed because it wasn't online.

I left out the more detailed parts because I don't remember everything I've done for the last 5 hours (and I wasn't taking notes... definitely will from now on...) If there's something I need to do (again) and post results I will. I'm pretty sure the ethernet controller would be helpful, but I don't remember what to put in the terminal to make it tell me. It's Intel for sure, 899db1 (something like this) with PRO/100 and something else at the end. The word "Ethernet" was capitalized and in red font in the terminal if that matters.

Please help me! I've been going in circles for hours!:(

---

### Post by westie457 on 2012-08-01
hi, ```
lshw -C network
``` will tell you the name of the ethernet port and any other network hardware.

Are you using a 'crossover' cable to connect the two computers?

---

### Post by NoGumption on 2012-08-01
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:c3:83:54
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:ff6fe000-ff6fefff ioport:dc80(size=64)

```

Not sure if I was supposed to get "the ethernet port and any other network hardware." from that, but I couldn't so there it is. If you mean physically, it's the only one in the back of my desktop and the only one in the side of my laptop. As for other network hardware, I'm guessing you mean in the desktop? I'm hoping you got the information you want/need from the stuff the terminal spit out.

I don't know what a " 'crossover' " cable is... on the cable in black text is "BETTER (UL) E302151 CM 75" (degrees celcius - not written but I don't know how to get that symbol) "4PR 24AWG   C (UL) CM FT4 ETL VERIFIED TO TIA/EIA 568B. 2 CAT. 5E PATCH CORD---UTP"

Hope that tells you something. It's an ethernet cord... same cord I'd plug a computer into a router with. If there's different kinds, I don't know.

---

### Post by westie457 on 2012-08-01
A crossover cable allows two computers to talk to each other without going through a router. if you are not sure one to check is look at the plugs. Cable colours the same from left to right in each plug is a normal cable. Colours running from outside edge in (symmetrical) is a crossover cable.

Though exactly why the cable is not detected am not sure at the moment.

I have to go for a while now (work) hopefully someone will be online soon to help you more.

---

### Post by NoGumption on 2012-08-01
Ok. It is a crossover cable then. Or at least definitely isn't a normal cable. From left to right, when looking at the bottom of the plug with the end pointing up, the wires are: orange and white, solid orange, green and white, solid blue, blue and white, solid green, brown and white, solid brown. The ones that are colored partially white have the color spiraling around the wire, like a candy-cane except not red.

---

### Post by NoGumption on 2012-08-01
The Ethernet controller is "Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)"

Found using ```
lspci
```

---

### Post by westie457 on 2012-08-03
> **NoGumption said:**
> Ok. It is a crossover cable then. Or at least definitely isn't a normal cable. From left to right, when looking at the bottom of the plug with the end pointing up, the wires are: orange and white, solid orange, green and white, solid blue, blue and white, solid green, brown and white, solid brown. The ones that are colored partially white have the color spiraling around the wire, like a candy-cane except not red.

Did you have the plugs side by side, you have only described one plug. If on the other plug the colours are in the same order it is a normal straight through cable - the type that is connected to a router or modem.

As stated earlier you need a cross-over cable to directly connect two computers together.

The cable is not being detected because the connection is not complete. ie the passing of information from one to the other is landing on the wrong terminals and neither computer can make use of it.

---

### Post by Paqman on 2012-08-03
> **westie457 said:**
> 
As stated earlier you need a cross-over cable to directly connect two computers together.


Actually you don't on any computer made in the last few years. You can just use a regular cable now, the network adapter [detects it and swaps the pins]("http://en.wikipedia.org/wiki/Auto-MDIX#Auto-MDIX"). 

Given that the OP stated his machine was originally Win7 it'll easily have a new enough network adapter for a crossover to not be required.

---

### Post by westie457 on 2012-08-04
@ Paqman

Thank you for that link, very informative. This is from the link you posted > The popular Ethernet family defines common medium dependent interfaces. For 10BASE5 connection to the coaxial cable was made with either a vampire tap or a pair of N connectors. For 10BASE2 the connection to the coaxial cable was typically made with a single BNC connector to which a T-piece was attached. For twisted pair cabling 8P8C modular connectors are used (often called "RJ45" in this context). For fiber a variety of connectors are used depending on manufacturer and physical space availability.
With 10BASE-T and 100BASE-TX separate twisted pairs are used for the two directions of communication. Since twisted pair cables are conventionally wired pin to pin there are two different pinouts used for the medium dependent interface. These are referred to as MDI and MDI-X (medium dependent interface crossover). [COLOR="DarkRed"]When connecting a MDI port to an MDI-X port a straight through cable is used while to connect two MDI ports or two MDI-X ports a crossover cable must be used[/COLOR]. Conventionally MDI is used on end devices while MDI-X is used on hubs and switches. Some network hubs or switches have an MDI port (often switchable) in order to connect to other hubs or switches without a crossover cable.

Given that the OP is trying to connect two computers without a router it is possible I was right in what I posted. However if proved wrong I will apologise to you and the OP for posting useless information.

---

### Post by NoGumption on 2012-08-06
> **westie457 said:**
> @ Paqman

Thank you for that link, very informative. This is from the link you posted 

Given that the OP is trying to connect two computers without a router it is possible I was right in what I posted. However if proved wrong I will apologise to you and the OP for posting useless information.

It is not a crossover cable. How do I know whether I need one or if a straight through cable would work? Do I just need to know if the computers are MDI or MDI-X? If so, how do I check that?

I've used this laptop the same way before (as a wireless card) with the same cord, but with a different non-wireless computer connected - if that answers anything.

---

