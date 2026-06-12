---
title: "troubles with remote desktop XP into Ubuntu"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by ijason on 2008-11-24
i'm trying to remote desktop into by ubuntu desktop from an XP laptop, and i'm getting stuck on what i presume are some really basic things that i can't quite find answers to. any help would be appreciated.

on my ubuntu box i would prefer to use the included Desktop Sharing application from the System>Preferences>Remote Desktop menu. i've already enabled it in-so-far as i've checked the boxes and created a required password. now the icon is in the little tray. it tells me users need to connect to jason-desktop:0

i've installed tightVNC on my laptop, but can't figure out how in the heck to get it to connect! i've tried typing in "jason-desktop" and "jason-desktop:0" to the server field and get "failed to get server address" for the error message. when i put in the IP address for the desktop i get a different error message "failed to CONNECT to server".

i can ping the ubuntu box from my laptop... i'm assuming the IP is the first address returned when i do 'tracert local', right? 192.168.1.1 for the ubuntu box and my laptop is 192.168.1.2, so it seems right. but when i try to ping my laptop from the ubuntu i get 100% packet loss. so i'm stumped.

both machines are served from a netgear wireless router

---

### Post by Titan8990 on 2008-11-24
This address: 192.168.1.1 is most likely your router.

To find you ip address:


ifconfig

---

### Post by razy60 on 2008-11-24
never sure which way round it is, but isn't the server the pc your on and the desktop the pc you wish to connect to. Assuming you have vnc on both that is.:confused:

---

### Post by Titan8990 on 2008-11-24
Actually, it is the other way around. The computer you are connecting to is the VNC server and the client is the computer that is connecting to the server.

---

### Post by ijason on 2008-11-24
ah. thanks titan. ifconfig returns 192.168.1.7

however, when i put that address into tightvnc i get the same error message "failed to connect to server"

i think the problem is revealed by my not being able to ping my laptop from the ubuntu desktop. while i can ping the desktop from the laptop. also, i can ping the local router from the ubuntu desktop. :confused:

---

### Post by Titan8990 on 2008-11-24
Do you have a firewall on the laptop that could be blocking the ping?

---

### Post by ijason on 2008-11-24
working on that now... it's apparently something with the laptop. i can't ping it from any of the computers on my network, while the ubuntu box can ping others just not my laptop.

weird thing is, when i went to check the settings for windows firewall it informed me that the associated service isn't running. so not only do i not have the firewall turned on, it's not even running.

---

### Post by Titan8990 on 2008-11-24
Could be that a second firewall was installed and the Windows firewall was not disabled properly.

---

### Post by halitech on 2008-11-24
lets confirm some things as well;

you can ping the router (192.168.1.1) from the desktop but you cannot ping the laptop

you can ping the router from the laptop

have you confirmed the ID of the router you are connecting to on the laptop?

---

### Post by ijason on 2008-11-24
@hali :
from the laptop, i can ping the router and all machines
from the ubuntu desktop, i can ping the router and all machines EXCEPT the laptop
from a third machine, i can ping the router and all machines EXCEPT the laptop

clearly, the problem is somewhere in my laptop.

@titan :
i know i didn't install any firewall program on the laptop, and that windows firewall is completely disabled. what i have no clue about is why my laptop refuses to be pinged. i can see other devices in the 'network neighborhood', so it's not completely blind to things on the LAN. and the internet works, so it sees WAN. i'm stumped, and sadly the ubuntu forum isn't going to be the best place for windows help

---

### Post by halitech on 2008-11-24
only suggestion I have is to check the subnet and gateway on the laptop and compare it to the ubuntu machine and the router just to make sure everything matches.

---

### Post by ijason on 2008-11-24
@ hali : yes, the mask/gateway are a match for all the machines. and, since i can see two others computers (oddly, not the ubuntu desktop) in the "my network neighborhood", i believe that the laptop sees the machines fine.

i'm just confounded by no obvious reason for the ping-ing to be blocked, and it is.

i'm almost certain that there'd be no way to remote desktop if my laptop refuses ping, how would the initial handshake even be accepted to start the process? interestingly, when i tried to enable windows firewall - figuring maybe if i enable it i could reset whatever is going on - it errored out saying windows firewall could NOT be started. maybe some component is missing.

---

### Post by Titan8990 on 2008-11-24
And a major downside to Windows is that you probably are not going to fix Windows Firewall without reinstalling the OS.

---

### Post by ijason on 2008-11-24
yeah, that's the habitual solution when windows eventually goes south on you. if it weren't for the last few programs i use refusing to port over i'd be done with windows et all. 

appreciate your help though. i'll be reinstalling windows and taking a new attempt at dual booting ubuntu/XP this time.

---

### Post by irpapabear on 2008-11-24
this has worked more times then not in winders...try uninstalling your network adapter the rebooting and let windows reinstall it.

---

