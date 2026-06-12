---
title: "getting programs to use new modem"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Bob Heap on 2008-08-14
[SIZE="2"][/SIZE]I have installed and got working a 536EP modem, however
none of the programs using internet access find it.
Initially had access through network to win xp connection on startup or demand, now I want to use the modem on this computer without disabling network! Also, Modem Monitor is grayed out.( using Ubuntu 2.6.24-16.)

---

### Post by ellgor on 2008-08-14
Hi,

Switch the modem OFF for a minute, then power back up, hope this helps.

Regards, Ellgor.

---

### Post by Bob Heap on 2008-08-15
Thanks but this is an internal modem. I have booted with network unplugged, no joy.
Set Network manager to use modem as default connection to web, no joy.
I presume its a permissions thing, wvdial dials out, connects then loses connection.
Enabling 'point-to-point' dials out, connects, no problem, but programs do not find connection.Heres Hoping.

---

### Post by Crafty Kisses on 2008-08-15
What programs are you actually trying to use?

---

### Post by Bob Heap on 2008-08-15
> **Codename said:**
> What programs are you actually trying to use?
Any that use dialup connection i.e. firefox, evolution,Apt,Synaptic etc.

---

### Post by phidia on 2008-08-15
Presuming you have enabled the modem through linmodem.org or your pci slot modem is a controller type and recognized in linux open a terminal and enter > sudo pppconfig 
Complete that modem set up program which creates needed files and be sure to add a user that has dialout privledges. You probably want to install gnome-ppp too.

---

### Post by Bob Heap on 2008-08-15
thanks, gnome ppp now connects,firefox is fine, evolution is not. I'll try to sort it out

---

