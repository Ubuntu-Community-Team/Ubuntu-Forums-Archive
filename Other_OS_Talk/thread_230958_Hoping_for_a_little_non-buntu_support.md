---
title: "Hoping for a little non-*buntu support"
date: 2006-08-06
forum: Other OS Talk
---

### Post by basketcase on 2006-08-06
Okay, I've tried the latest release of Knoppmyth, Knoppix and Ubuntu 6.06 LTS.  

Computer is an Shuttle XPC SN41G2
Nvidia gforce 2 chipset
AMD 1800+ Processor
512 DDR333
40gb HDD

Using Onboard Vid and Nic
PCI slot has a PVR-350 Tuner Card

I want to run Mythtv....Knoppmyth is great, everything works, but I cannot get a network connection.  

Using the onboard NIC, I am able to run 'netcardconfig' assign a static IP address, able to ping 127.0.0.1 and the IP addreass of the NIC (192.168.1.250)..Successful replys....but I cannot ping the router (Linksys WRT54G).  I know the ports on the router is good, because I can use them with my notebook.  I know the cable is good because I use it on one of the other desktops in the house.  

When I try and ping the router (or any other address for that matter) I get a reply from the computer's IP address 'destination host unreachable'.  I get the same reply in Knoppmyth, Knoppix and Ubuntu Dapper.  

So I have a USB to Cat5 adapter (Linksys USB100M) -- Operating systems recognize it, able to assign an IP address to it, and ping it.  When trying to ping the router, I will get 'destination host unreachable'.  I disabled the onboard NIC and just used the USB NIC, same issue.  

Why do I not have any network connectivity on this box?  The box is used, recently purchased from a coworker.  Was running Windows XP SP2 on it.  Said he had a few issues with the NIC when he bought it, but he just put in a NIC in the PCI slot and didn't worry about it.  I need the available PCI slot for the PVR-350 card.  

Any ideas, suggestions, etc. would be greatly appreciated, as I'm considering e-baying the box, the card and anything else I have and just buying a Tivo.  

Thanks!!

My biggest question is I can understand that the Onboard NIC might be dead, and so be it, but why isn't the USB one working?  

Thanks again!

---

### Post by Archlyric on 2006-08-06
hmm, try running 
# dhclient

and give the output :D

---

### Post by basketcase on 2006-08-06
I ran that a couple of times....I think the general idea was it wasn't recieving any sort of dhcp offer per it's discover request.  

I'm at work now, here for another 7 hours, but I can verify when I get home tonight.

---

### Post by Archlyric on 2006-08-06
i do infact remember installing linux on this machine and having the same sort of issue... perhaps try updating the routers firmware?

---

### Post by basketcase on 2006-08-07
It's running Talisman 1.1.  I think 1.2 is still in beta.  

There are 6 computers attached (wired and wifi).  3 get dhcp addresses, 3 are statically assigned

---

### Post by encompass on 2006-08-08
I would try to see if it is the os and if it has issues with your network.  Sounds weird... but take the pvr card out pop a pci nic in and see if you connect...
If you can connect, you know it has something to do with that nic.
By a nice from somewhere like walmart and they should let you return it.  Thats what I always do. ¶:

---

### Post by basketcase on 2006-08-08
I purchased 4 nics a while back to build some linux routers using IPcop...I can part one of those boxes for their nics.  

I'll give it a shot and see what I can come up with.

---

### Post by basketcase on 2006-08-10
> **encompass said:**
> I would try to see if it is the os and if it has issues with your network.  Sounds weird... but take the pvr card out pop a pci nic in and see if you connect...
If you can connect, you know it has something to do with that nic.
By a nice from somewhere like walmart and they should let you return it.  Thats what I always do. ¶:
Took the DLink cards out of my IPcop box....

Same results.  I don't know why I'm getting the same results with 3 different network cards, and 3 different OSes.

---

