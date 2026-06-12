---
title: "[SOLVED] complete newbie -setting up ad hoc wireless cnx to printer"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by phoenixrosebud on 2008-06-22
I am trying to wirelessly connect a new printer directly to my computer, and I desperately need help.

Both my computer and my printer are able to see the other wireless networks, so it seems that the problem is setting up the peer to peer connection.

Please help-I am very confused!!!


Ubuntu: Gutsy
Printer: HP Photosmart C8180
Wireless Card: Broadcom 4303
(The firmware for the Broadcom 43xx chipset family is enabled and in use and I am able to see other wireless networks.)
Internet connection through wired modem connection.

---

### Post by KenBW2 on 2008-06-22
I'm not sure what you want from it but this is how I did it with my HP printer:
Shared the printer on a samba share and used System > Administration > Printing to add the printer from there on my eeepc across the network to my main PC, which has the printer plugged into it.
Hope that helps

---

### Post by phoenixrosebud on 2008-06-22
Thanks for your response! I actually only have one computer, and no network really set up. I thought I could try directly connecting my printer and computer wirelessly. 

I don't know how to do a samba share, but I tried going through the other steps you indicated, but it doesn't seem to be finding anything...

---

### Post by starcannon on 2008-06-22
I just used the printer wizard found in 

System-->Administration-->Printing

Chose my HP 4385 wireless printer from the list of found printers, followed the wizard, and it works perfectly.

Let us know where its not going as expected and perhaps we can get you up and printing.

GL

---

### Post by phoenixrosebud on 2008-06-22
When I try to add a new printer, it asks me to select a connection type... I don't know what to chose. 

I tried going through the steps with the AppSocket/HP JetDirect option, and used the appropriate ppd that I downloaded from openprinting.org, but the test page didn't print.  

It seems like the printer that I "added" doesn't really connect with my actual printer-like it is a figment of my computer's imagination or something. :)

---

### Post by phoenixrosebud on 2008-06-22
> **phoenixrosebud said:**
> When I try to add a new printer, it asks me to select a connection type... I don't know what to chose. 

I tried going through the steps with the AppSocket/HP JetDirect option, and used the appropriate ppd that I downloaded from openprinting.org, but the test page didn't print.  

It seems like the printer that I "added" doesn't really connect with my actual printer-like it is a figment of my computer's imagination or something. :)

I should clarify - there were no listed printers when I went to System->Administration->Printing, when the system searched for printers.  So  when I tried to add a printer I had to go through the above steps.

Also, I didn't enter a Hostname when I set it up as a AppSocket/HP JetDirect and I left the port as the default 9100

---

### Post by brian_p on 2008-06-22
> **phoenixrosebud said:**
> Also, I didn't enter a Hostname when I set it up as a AppSocket/HP JetDirect and I left the port as the default 9100

The LPD/LPR option may be the one you want. AppSocket/HP JetDirect is for dedicated print servers (I think). The cups documentation is at

[http://localhost:631](http://localhost:631)

---

### Post by phoenixrosebud on 2008-06-22
When I try the LPD/LPR option, the only thing that shows up is localhost, and that doesn't show any printers. When I hit "probe" nothing happens.

I've never used CUPS before, but I'm trying that now.

---

### Post by phoenixrosebud on 2008-06-22
I have no idea what to put for the "Device URI".

I printed out the HP Network Configuration Page, is there anything that I should be looking for on it?

Should I use the Hostname and MAC that the printer shows?

Thanks!

Okay- so it looks like from [http://localhost:631/help/network.html]("http://localhost:631/help/network.html") that I need to use the MAC address to configure an IP address.

Here's a really dumb question: On the page they say to use DHCP or BOOTP I haven't used either before, I just do things in terminal... how do I do what they are telling me to do?

---

### Post by phoenixrosebud on 2008-06-22
Please help! 

I am trying and failing to figure out how to assign an IP address to my printer.

---

### Post by phoenixrosebud on 2008-06-22
I just bought a USB cable to wire my printer to my computer. That is working just fine.

:KS

---

### Post by starcannon on 2008-06-23
Look for its ip address, that's all I needed from that page, I can't remember where, but somewhere in that wizard, if it doesn't auto locate the printer you can specify its ip

---

