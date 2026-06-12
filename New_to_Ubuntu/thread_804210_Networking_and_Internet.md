---
title: "Networking and Internet"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Vigh on 2008-05-22
Hi I am new to Ubuntu, just put a fresh install on my machine seems to be going okay. I was just wondering how can check if there are drivers already installed for my network card and if there are drivers already installed how can I set up my network so that I can connect to the internet through linux. The network card is plugged directly into the modem via ethernet. Thanks Anthony

---

### Post by Nessa on 2008-05-22
If your network card is built into the motherboard, it usually detects it automatically. Check your hardware list if your lan card shows up there with the right brand/model/etc.

---

### Post by Vigh on 2008-05-22
Need more info, its not an on-board lan cards, its 10/100 pci lan card, not sure of the model and make, how do i check the driver list? I am noob. Sorry! LoL! Anthony

---

### Post by oedha on 2008-05-22
open terminal :==> applications - accessories - terminal
type :==> sudo lshw -short  { this will display your HW and see your NIC there }
after that
go to system - administration - hardware testing { to test your hardware }

---

### Post by Vigh on 2008-05-22
Don't I have to be connected to the internet to test the hardware? It says could not connect to server when I try to test the hardware. In the hardware list under network it says Gammagraphx, Inc. Does this mean the driver and hardware are working properly? Or will I need to install a driver for the network card still.

---

### Post by MaindotC on 2008-05-22
Yes you should have the 10/100 card plugged into "the internet".

---

### Post by Vigh on 2008-05-22
It is plugged in to the internet, it connects directly to the adsl modem via ethernet but the internet does not appear to be working on ubuntu. Any suggestions on how I can get it going.

---

### Post by MaindotC on 2008-05-22
Yes - try restarting your computer with the ethernet cable still plugged in.  You don't have to do this all the time, just this once.  If it's still not working, go to System -> Administration -> Network and see if you see a "Wired Connection" setting.

---

### Post by oedha on 2008-05-22
have you set the ip address and dns address ?

---

### Post by MaindotC on 2008-05-22
I'd rather he just use DHCP - this doesn't sound like a user that should be dealing w/ addresses.  Just trying to keep it as simple as possible.

---

### Post by Vigh on 2008-05-22
Still not working, no wired connection appearing under network. It says the network interface is not connected.

---

### Post by thisiam on 2008-05-22
i like the roaming option myself. what do you get from ifconfig ?

---

### Post by MaindotC on 2008-05-22
Do you see lights around the ethernet port on your machine?  Should be a constant green light and a blinking amber light.

---

### Post by thisiam on 2008-05-22
try this in terminal found it [here]("http://www.linuxguide.it/commands_list.php?Commands_by_Argument:Networking")
```
sudo mii-tool eth0
```

---

### Post by Vigh on 2008-05-23
trying to put a different network card in see if that works, working now thanks everyone

---

### Post by MaindotC on 2008-05-23
Yeah - unfortunately that doesn't really solve your problem, you just put a "band-aid" on it.  It could be that your system didn't have the necessary drivers for the card - highly doubt it but just in case - after you download all your updates, stick that card back in and see if Hardy recognizes it.

---

