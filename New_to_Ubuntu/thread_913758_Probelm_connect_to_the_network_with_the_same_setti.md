---
title: "Probelm connect to the network with the same setting as my windows installation"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by WilhelmE on 2008-09-08
Hi,

I have recently installed Ubuntu Hardy onto my machine in a dual boot environment, I have given both operating systems the same host name as I am trying to connect to my network that has DHCP setting on the firewall, my problem comes in is that I can not seem to get my Ubuntu install to receive the same ip configuration setting as my windows installation. The strange thing thing is that a college of mine has kind of a similar problem in that he has both his windows and ubuntu installation with the same ip address yet he is still getting blocked on the fire wall. To be honest I think that this might be a problem on the firewall side but I was wondering if there is anything that I could do on my installation to make them look the same.

Regards

---

### Post by Efros on 2008-09-08
Set your router to apply a fixed IP address to your machines physical or MAC address.

---

### Post by WilhelmE on 2008-09-08
Thanks that has worked. :) Is there any particular reason why the dhcp did not do this on its own or does it just get marked of as two different OS doing slightly different things

Regards 
Wilhelm

---

### Post by Efros on 2008-09-09
No clue, but I have a number of machines that I have set up with static IPs purely for remote access reasons, and I have never had issues with them but I have had with the dynamic IP machines.

---

