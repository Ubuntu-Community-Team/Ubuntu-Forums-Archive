---
title: "Help me set up a networked printer"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2008-09-12
i just got a [Linksys PSUS4 Wired Print Server]("http://tinyurl.com/2dnkkl") and i've been trying to set it up all day. can someone please help me out?

this is a diagram of my network as far as the printing is concerned (i don't think my 360 or wii comes into play lol)
[IMG]http://img355.imageshack.us/img355/2672/screenshotic9.png[/IMG]

i can get the PSUS4's web UI from any computer on the router, so i don't think it's an IP conflict (that and the touch is on DHCP, and the 360 and wii are turned off)

all the guides i've found online don't cover what i'm looking for (most cover printing to a printer through a windows box, etc.)

i've got a vista PC hardwired to the router, and a dual-booting laptop (XP/Hardy) that can be hardwired or connected via wifi. the printer is a HP DeskJet 842C, the printserver is a Linksys PSUS4.

please help me get this working

---

### Post by skippuff54 on 2008-09-12
have u done anything in the router config? can u see the printer from either computer?

---

### Post by Sonic Reducer on 2008-09-12
> **skippuff54 said:**
> have u done anything in the router config? can u see the printer from either computer?

yeah, i've set it up to use 192.168.1.105 and i can reach the web UI from there

---

### Post by skippuff54 on 2008-09-12
u might need to install samba/cups. samba is for file sharing, cups is for printer sharing.

but first, what can u do? can u do any printing at all? does the Windows machine work? what options do u have in the UI? where are u hittin a roadblock? can u print a test page from the UI? can u add the printer from the UI?

seems like u would need to config the router as well as the print server...then goin back to the ubuntu machine, u might need to install cups to handle ur print services on the network.

---

### Post by Sonic Reducer on 2008-09-12
Test page works, i went to 192.168.1.105 (for the web UI) then to **Status/Printer/Print Test Page**

it printed out:
```
Hardware ID: 04D0558C28
Firmware Version: 6034
Protocol ID: 006E
Default Name: LKCF6080
Server Name: PRINT SERVER
MAC Address: 001310CF6080

AppleTalk Info:
  Printer Type:
  PRINT SERVER:HP DeskJet 842C

TCP/IP Info:
  IP Address: 192.168.1.105
  Subnet Mask: 255.255.255.0
  Gateway Address: 192.168.1.1
  Email Server IP Address: 0.0.0.0
  Printing Account Name: N/A
  Redirect Account Name: N/A

SMB Info:
  Domain Name: JONES WI-FI
```

can you make anything of it?

---

### Post by skippuff54 on 2008-09-12
it's obviously workin w/ your router. the SMB i'm 99% sure means server message block which is the protocol that SAMBA/CUPS use for file/print sharing.

it should just be a matter of configuring hardy to sent print jobs through the router to that IP address. 

when u say u access the UI, which computer are u usin?

did u try to set up your printer using system > administration > printing in hardy?

if that doesn't work initially, go to synaptic package manager and install CUPS.

---

### Post by Sonic Reducer on 2008-09-12
> **skippuff54 said:**
> when u say u access the UI, which computer are u usin?
any computer on my network. i have it open on both my desktop and laptop, which are connected over wi-fi to the router

> **skippuff54 said:**
> did u try to set up your printer using system > administration > printing in hardy?

if that doesn't work initially, go to synaptic package manager and install CUPS.

i've tried setting it up through **system > administration > printing** but i don't know what i'm doing. lets just say i haven't been successful.

i have cupsys and a couple other similar named packages already installed, how should i set them up?

---

### Post by skippuff54 on 2008-09-12
make sure u have cupsys client installed. normally u would use a protocol called ipp, but u may end up usin one called lpd.

both of these items are available in the printer config under system > printing. what u should try first is to add a new printer using Internet Printing Protocol (ipp). use the ip address assigned to the print server via ur router as the host.

if that doesn't work, try adding a new printer using LPD as the protocol. from the brief search i just did via google, i saw people using linksys and *nix were usin LPD - u might even wanna try that first.

if neither of those work, try puttin in ur router as the host ip address and then make sure ur router is forwarding print requests to the print server.

honestly ur issue is gettin beyond the scope of my knowledge, and i would advise u to search for setups specific to ur linksys device. sorry i can't give u the magic bullet! i know it's frustratin but i can say with near certainty that u aren't the first person to try it and if u mix up ur search terms on these forums and the web u should get some add'l leads.

---

