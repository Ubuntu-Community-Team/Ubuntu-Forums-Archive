---
title: "[SOLVED] Can't connect to the internet"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by the_Ben on 2008-06-14
My friend's Dell Inspiron 2650 was on it's last leg with Windows (massively infected with viruses and adware), so I offered to load Ubuntu to revive it.  I loaded heron successfully, but I'm having problems getting it online.

The laptop uses as Belkin wireless card (one of the plug-in dealies) model F5D7011.  I've searched around, and read something to the effect that if I connect to the internet via ethernet, I can install drivers to get the card to work.  However, whenever I connect to a wired network, it doesn't actually connect to the internet.

Any ideas?

---

### Post by phidia on 2008-06-14
With the ethernet cable plugged in open a terminal and type ifconfig press enter and see what's up with your connection.

---

### Post by the_Ben on 2008-06-15
Here's what I get from running "ifconfig" in the terminal:

```
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:e9:fb:28  
          inet6 addr: fe80::208:74ff:fee9:fb28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:724 errors:0 dropped:0 overruns:1 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45562 (44.4 KB)  TX bytes:6289 (6.1 KB)
          Interrupt:10 

eth0:avahi Link encap:Ethernet  HWaddr 00:08:74:e9:fb:28  
          inet addr:169.254.8.96  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137264 (134.0 KB)  TX bytes:137264 (134.0 KB)
```

Not quite sure what it's telling me here.  Suggestions?

---

### Post by momo07 on 2008-06-15
Go to System > Administration > Network and check wired connection. Hopefully this will solve your problem.
Cheers

---

### Post by the_Ben on 2008-06-15
> **momo07 said:**
> Go to System > Administration > Network and check wired connection. Hopefully this will solve your problem.
Cheers

Network Settings tell me I've got roaming mode enabled for the wired connection, so dead end there.

---

### Post by fwre01 on 2008-06-15
the "eth0:avahi" means your not getting an IP address. wheres the DHCP server? you could run ```
 sudo dhclient eth0 
``` to see if you can lease an address. or set it statically from within network manager

---

### Post by Xerp on 2008-06-15
The router needs to have its DHCP server on and dishing out addresses for roaming to work - is it?

---

### Post by the_Ben on 2008-06-15
The command "sudo dhclient eth0" tells me (among other things) "No DHCPOFFERS received" and "No working leases in persistent database".

As for the router, I've circumvented it by plugging directly to the cable modem.  Do I need to plug it in to the router and turn on the DHCP server?  And how do I go about doing that?

---

### Post by JordanH on 2008-06-15
Are you sure it's a cable modem and not a DSL modem?  If it's a DSL modem, you can plug the ethernet cable directly into the DSL modem and then use the following command to configure the connection:
sudo pppoeconf
After this is configured, you can do what you need to do.

---

### Post by the_Ben on 2008-06-15
After running sudo pppoeconf, I get this:

"Sorry, I scanned 3 interfaces, but the Access Concentrator of your provider did not respond.  Please check your network and modem cables.  Another reason for the scan failure may be another running pppoe which controls the modem."

This is with the laptop connected directly to the modem via ethernet.  Back to the drawing board, I guess.  Thanks for all the help so far, guys!

---

### Post by cariboo on 2008-06-15
If you are connecting directly to the modem you may need a crossover cable between the computer and the modem. Belkin crossover cables are yellow (at least thats what color the local staples sells). If you are trying it with a straight cable that may be why you are having trouble connecting.

My advice is to connect the router back up and make sure that it is getting an ip address from the internet provider. Depending on who manufacturer is you can access the router management interface with your web browser, get your freind to dig out the manual for their router and it will tell how to access it, if your friend dosen't have a manual, it is also located on the cd that came with it.

JIm

---

### Post by kennster on 2008-06-15
im having the same problem at right now. just mine happend outta no ware didnt change any setting nuttin just logged off of wow and aim to go out to eat. didnt even shut off computer left it on and came back to get on. and well i wasnt connected... if u fix it let me know

---

### Post by the_Ben on 2008-06-15
SUCCESS!!! :guitar:

I ran an ethernet cable from the router to the laptop, typed in the terminal command...

```
 sudo update-pciids; lspci grep Ethernet
```

and I'm online!  I'm currently installing updates and will post again to let everyone know the status of wireless browsing.  Cheers all around!

---

### Post by the_Ben on 2008-06-16
Huzzah, everything works!  As I wrote in the previous post, wired internet is working.  All I had to do after that was run updates (System->Administration->Update Manager for newbies), then I opened 3rd party drivers (System->Administration->Restricted Drivers Manager) and enabled the newly installed wireless driver.  After that, everything was a go!

Thanks to everybody for the help.  This thread is SOLVED! \\:D/

---

