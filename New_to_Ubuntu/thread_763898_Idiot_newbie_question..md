---
title: "Idiot newbie question."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by iforgot123456 on 2008-04-23
I'm brand new (12 hours or less) to kubuntu and linux. I'm having a bit of trouble getting kubuntu to recognise the wireless card (IPN2220) on the old laptop (Acer travelmate 2300) I'm using.

I've followed this guide:

[https://help.ubuntu.com/community/WifiDocs/Device/ipn2220?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/ipn2220?highlight=%28WifiDocs%2FDevice%29")

And from what I can tell - using the command 

*sudo ndiswrapper -l*

the driver is installed and the device recognised. I however get no wireless options in the Knetwork manager menu. Hope somebody can shed some light.

Thanks

iforgot

---

### Post by StefAndrew on 2008-04-23
I don't know if this will help you out, but my wireless on my Dell laptop refuses to work unless I disable IPV6.  You can do so by editing the ALIASES file in the /etc/modprobe.d folder.  I'm not familiar with how to edit the file in Kubuntu, but in Ubuntu I run "sudo gedit" from the command line on the file, /etc/modprobe.d/aliases and then look for this line:

> 
Alias net-pf-10 ipv6
[/qote]

And change it to:

[quote]
Alias net-pf-10 off


I don't know if that will help, but I have to do that everytime I have to reinstall.

---

### Post by Zralou on 2008-04-23
> **StefAndrew said:**
>   I'm not familiar with how to edit the file in Kubuntu, but in Ubuntu I run "sudo gedit" 

In KDE it's "kdesu kate".

Sara Lou

---

### Post by Seisen on 2008-04-23
> **iforgot123456 said:**
> I'm brand new (12 hours or less) to kubuntu and linux. I'm having a bit of trouble getting kubuntu to recognise the wireless card (IPN2220) on the old laptop (Acer travelmate 2300) I'm using.

I've followed this guide:

[https://help.ubuntu.com/community/WifiDocs/Device/ipn2220?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/ipn2220?highlight=%28WifiDocs%2FDevice%29")

And from what I can tell - using the command 

*sudo ndiswrapper -l*

the driver is installed and the device recognised. I however get no wireless options in the Knetwork manager menu. Hope somebody can shed some light.

Thanks

iforgot

Did you do sudo modprobe ndiswrapper after that?

---

### Post by iforgot123456 on 2008-04-23
I did, but it appeared that nothing happened - it asked for my password and then I was presented with a new command line.

---

### Post by iforgot123456 on 2008-04-23
Ok I've just redone the modprobe command  - and undone my changes to ipv6 - and it appears to be working - but not detecting my network - how do I get it to detect a WPA network?

(Thanks for your help btw)

---

### Post by iforgot123456 on 2008-04-23
Ok Knetwork acknowledged briefly that I had a wireless card, but no  longer does - even after a repeat "sudo ndiswrapper modprobe"

---

