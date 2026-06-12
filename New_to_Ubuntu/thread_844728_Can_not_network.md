---
title: "Can not network"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by DavidLamp on 2008-06-29
Hello,

I have just installed 8.04 on an older 32bit eMachine.

I am unable to use the internet through ethernet (eth0)

When I try to configure device (etho) I get a message "the interface does not exist).

I have enabled automatic DHCP under the network tools. (etho) does not show as as a location in the Network Settings admin.

Please advise the procedure to remedy this situation.

Thank You,

David

---

### Post by untermensch on 2008-06-29
w00t go old emachines! ( I have a few and I'm not sure why =p) Umm, is this lan or wlan you're talking about?

---

### Post by neurostu on 2008-06-29
Do you know if the network card is even recognized?  Try running: 
```

lspci

```
and paste the comments below!

---

### Post by DavidLamp on 2008-06-29
It shows as a nVidia nForce2

---

### Post by neurostu on 2008-06-29
Is that all it shows? can you paste the entirety of the results?  Anything about ethernet?

---

### Post by DavidLamp on 2008-06-29
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2) 
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2) 
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2) 
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2) 
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2) 
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2) 
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4) 
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2) 
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1) 
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2) 
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1) 
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) 
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) 
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2) 
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

### Post by neurostu on 2008-06-29
> **DavidLamp said:**
> 
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1) 

So the ethernet controller is showing up. try googling:
nForce2 Ethernet Ubuntu

That should help you find a post of someone who has dealt with this issue.

---

### Post by DavidLamp on 2008-06-29
I could not find anything relative with google.

I had this problem before with an older install.

I remember I needed to enter some DNS infor then it worked fine.

---

### Post by untermensch on 2008-06-30
Do you have a home router? Was this machine set up on a different router at a previous time?

---

