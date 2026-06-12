---
title: "Canon network printer"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by bennypr0fane on 2013-01-27
> **jtarin said:**
> Example Setup:

Installing Cannon Network ScanGear for _**scanning from the Photocopier**_

    The copier is configured to pull it's IP address etc. from the Institute's DHCP server.
    As of 7th November 2005, the copier is statically allocated the IP address 163.1.148.102 using the 
MAC address 00:00:85:0a:58:b4.
    IMPORTANT NOTE: The TWAIN driver will not work if the client is on a different subnet than that of the copier.
e.g. A machine on the 163.1.148.0/23 network with a asymmetric route to an RFC1918 network, although 
able to ping the copier, the drivers will fall over. Ensure they are both on the 163.1.148.0/23 network.
    Install the software from either CD or download the self extracting zip file. The TWAIN drivers will be installed
along with the ScanGear tool for selecting which copier to use.
    Ensure the photocopier is in network scan mode and it's network plugged in.
    Fire up the Network ScanGear tool and "Discover" the copier. Select the copier from the list and click Exit.
    You should now be ready to start up your favourite software and use the TWAIN interface to scan documents in using the copier.
    Save scanned UCAS forms to \\admindb0\socrates

Hello,
I've been using the scanner with Windows to initiate a scan from the machine, but now I really want to get this working in Ubuntu.
It seems to me that the instructions above are just for starting a scan from the PC Ubuntu, not from the scanner (except in this example, it's a copier).
2 things not clear to me though:
there is mention of this *Network* ScanGear tool. My scanner software is just plain "Scangear", so maybe there is another piece of software involved that I haven't discovered anywhere (yet).
Secondly, I don't know if the two devices are on the same subnet - and I don't know how to find out. I believe my router assigns IPs dynamically, hence there wouldn't be any static IPs in my network...

---

### Post by jtarin on 2013-01-27
> **bennypr0fane said:**
> 
Secondly, I don't know if the two devices are on the same subnet - and I don't know how to find out. I believe my router assigns IPs dynamically, hence there wouldn't be any static IPs in my network...I don't know your particular setup so try this first and look for your particular situation.
Do a Google search about "assigning static ip to printer ubuntu"

---

### Post by oldos2er on 2013-01-27
Posts moved to their own thread.

---

### Post by HiImTye on 2013-01-27
you only need the normal 'scangear' program to scan documents from a network printer. Ubuntu treats a network printer the same as a printer plugged into the box.

I didn't have any luck configuring the printer for the network on my Ubuntu box and ended up plugging in the printer to my girlfriend's Win7 laptop to do the initial configuration. I hope you have better luck than I did

---

