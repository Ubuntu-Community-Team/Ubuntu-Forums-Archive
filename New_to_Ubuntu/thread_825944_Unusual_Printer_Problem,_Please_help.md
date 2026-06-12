---
title: "Unusual Printer Problem, Please help"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by valmorel on 2008-06-11
Hi everybody, and thanks in advance to anyone who can help. I am running Hardy H, fully updated on a dedicated Acer laptop. Everything works very well except for a printing issue I have been unable to solve. I have the pc on a wifi home network, and I print to a Canon Pixma IP 4200. I can print just fine when the printer is connected via USB, or when printing via Samba when the printer is hanging off one of my Windows pcs. However, because of space restrictions, my preferred option is to use a Belkin wifi print server attached to the printer which all pcs on my network can address. Thus far, I have been totally unable to set my Linux machine up to work with the Belkin, but then to be fair, I dont really know what I am doing. Could anyone give me a step by step instruction, or at least point me in the right direction? The IP address of the print server on my network is 192.168.0.7

---

### Post by valmorel on 2008-06-11
Anybody?????????????????

---

### Post by carl.davis on 2008-06-11
I don't know what protocol your print server uses but when I simply try to add a new printer in Hardy it auto-magically discovers all of the printers that are on my local network. 

[LIST]
[*]Does your computer currently have an IP within the 192.168.0.0/24 subnet? 
[*]What is the exact model of your Belkin print server?
[/LIST]

---

### Post by avtolle on 2008-06-11
I don't have a solution for your problem. I have read several threads on the Forum(s) which indicate problems with printing when the printer is attached to a print server, and as I recall, there has been a bug filed in Launchpad. You might want to search around to see if there's been any work around or solution found.

---

### Post by valmorel on 2008-06-11
> **avtolle said:**
> I don't have a solution for your problem. I have read several threads on the Forum(s) which indicate problems with printing when the printer is attached to a print server, and as I recall, there has been a bug filed in Launchpad. You might want to search around to see if there's been any work around or solution found.
Thanks. I have been searching forums and stuff for about a week now with no luck. I kind of hoped someone else might have come across this and solved it. Maybe it just cant be made to work.

---

### Post by dlmoak on 2008-06-11
I am at work so I am not on my Ubuntu computer to see exactly how mine is set up.  But as I recall, when specifying the printer in Ubuntu I specified a TCP/IP type connection and used the IP address and the number of the port on the wireless print server.  In my case, that number was 9100 (the first of 4 USB ports on the print server).  I can't remember now if my server is a Belkin or not, but I think so.  I DO remember that using the setup for an LDP printer did not connect.  I used a GUI to set it up, but I can't remember the name of the program right now.  Sorry to not have more detail.  I can fill in the blanks after I get home from work.

---

### Post by valmorel on 2008-06-11
> **dlmoak said:**
> I am at work so I am not on my Ubuntu computer to see exactly how mine is set up.  But as I recall, when specifying the printer in Ubuntu I specified a TCP/IP type connection and used the IP address and the number of the port on the wireless print server.  In my case, that number was 9100 (the first of 4 USB ports on the print server).  I can't remember now if my server is a Belkin or not, but I think so.  I DO remember that using the setup for an LDP printer did not connect.  I used a GUI to set it up, but I can't remember the name of the program right now.  Sorry to not have more detail.  I can fill in the blanks after I get home from work.
Thanks so much. Brilliant

---

