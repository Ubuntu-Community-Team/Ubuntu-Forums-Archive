---
title: "print to Shared laserjet connected to XP on windows domain."
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Garmuar on 2008-08-19
I am very new to Ubuntu Network administrations.

I have connected my first Ubuntu workstation to our microsoft network using Likewise-open. I joined it to the domain.
We use shared printers on the network.
I can see machines and file shares browsing the domain, but no printers.
Can someone point me in the right direction? What needs to happen to use a printer attached and shared on a xp machine on the domain?

Also, there appears to be a default smb server running on the ubuntu machine. When I open "places/network/windows networks" in the GUI, I see our windows domain, and a "MSHOME" domain listing the Ubuntu machine?

Shouldn't SMB have been joined to the MS domain also by Likewise-open?

---

### Post by guardsman85 on 2008-08-20
Have you tried the following?
Go to System -> Administration -> Printing
Select "New Printer"
Select "Windows printer via SAMBA" (it will show you an example of what to type)

As far as the workgroup/domain issue is concerned, could someone else chime in here?  I'm not really familiar with likewise-open or adding Ubuntu to a Windows domain.

---

### Post by Garmuar on 2008-08-21
When I try that, it can't find the printer.  And when I browse,  I can see every machine in the domain, but no shared printers under them on the list.

Is using a shared printer on an XP machine possible with out having some kind of linux drivers installed on the linux machine for that printer?  When a microsoft PC connects to a network shared printer, the drivers get pushed down to the PC and installed automaticly.

I can see microsoft file/folder/drive shares on the network and access them , but no printers?

Likewise-Open IS allowing domain users to authenticate with SMB2000 AD server.  However, the Machine is not JOINED to the domain?  It is sitting in a MSHOME domain separately.  This is confusing the hell out of me.  Why does the machine not show up in the joined domain? It was successfully joined according to Likewise-open.

When I look in AD Users and Computers,  the Ubuntu machine is listed in the "Computers" folder in the tree.

---

### Post by guardsman85 on 2008-08-21
> **Garmuar said:**
> Is using a shared printer on an XP machine possible with out having some kind of linux drivers installed on the linux machine for that printer?

At home I have a printer shared on a Windows XP machine, and yes, I had to install a Linux driver (luckily, my model had a driver in Linux).  You may be able to find out if your printer is supported or get a needed driver at:
[http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)

Here are some other resources I saw that might be helpful...

Debian / Windows shared printer how-to
[http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html](http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html)
Section 3 has instructions on how to connect using smbclient.  I haven't ever tried doing it this way, but it's an option you could try.

This is a commercial, for-pay option, of which I really know NOTHING about.  However, if the above resources don't work for you, then it may be worth researching.  There is a free tiral.
[http://www.brooksnet.com/unix-lprlpd-networkprinting.html](http://www.brooksnet.com/unix-lprlpd-networkprinting.html)

Finally, one other for-pay option I found, but again, I really haven't gone this route. Hopefully you'll have your printer working without needing to resort to it.
[http://www.printfil.com/english.htm](http://www.printfil.com/english.htm)

I know I'm only offering partial answers to your problem, but hopefully it brings you a little closer to where you want to be!

---

### Post by Garmuar on 2008-08-21
Thankyou Garudsman85.

The tutorial from [www.linuxfoundation](www.linuxfoundation) was priceless. 
I finally was able to reach the printer and found drivers for it.
Now if I can solve this Windows Domain Authentification problem I'll be set.

I cant install the printer logged in as a domain user because ubuntu will not accept the domain password for that account still.  

If I log in as sudo user (not NT domain user) and install printer, can I make it available to other domain user accounts on this machine?

---

