---
title: "packettracer won't start or uninstall"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by Sir_melo on 2012-09-28
Hello
I have been trying to install Cisco Packet Tracer 5.3.3 on my recently installed Ubuntu 12.04 64bit. My school gave me a packet tracer file for linux and I tried to install it using these commands: 

Chmod +x Packet_Tracer_v533_i386_installer-deb.bin

and then

./Packet_Tracer_v533_i386_installer-deb.bin

Packettracer then got installed and when I tried to start packet tracer from the dash nothing happened. It looked as if it was installed however nothing happened when I clicked the icon. Then I tried to start it from the terminal with the use of this command. 

 /usr/local/PacketTracer5/packettracer

the terminal wrote : Starting Packet Tracer 5.3
however nothing happened after this. 

Then I tried to uninstall with the command.

Sudo dpkg -r packettracer 
 
dpkg: warning: there's no installed package matching packettracer

then I tried to uninstall with other names as packettracer5, PacketTracer, PacketTracer5 and so on but that didn't work either. 

Then I thought to my self if there's no installed package macthing, then I should be able to install it then. But when I tried that I was told to uninstall packettracer before installing it. 

If someone knows what to do here I would be very glad.

---

### Post by daslinkard on 2012-10-05
I found this [link]("http://kaslnetwork.com/articles/installing-cisco-packettracer-5-3-2-on-64-bit-ubuntu-or-debian/") and thought of you....I hope it helps you!

---

