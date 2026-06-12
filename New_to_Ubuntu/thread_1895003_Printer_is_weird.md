---
title: "Printer is weird"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by Foobarz on 2011-12-13
Ok, so whenever I print through my network printer, this is what happens

When I print my essays from Libreoffice, the printer prints the first page. Then stops and cools down. Then it prints the second page. Stop and cool down. Same pattern for all the pages

This is unlike using windows on the same machine. Whenever I print through windows (same machine, same printer) it prints smoothly.

I have a Brother HL-2270DW and I installed it by finding it in the network, putting that address into the Device URI, and I used the Generic PCL 6/PCL-XL ppd file. 

Everything else is normal, so why does my printer print in such an erratic way?

---

### Post by N00b-un-2 on 2011-12-13
what method do you use to connect to the printer?  I have a Brother printer and depending on what method I use to connect to the printer, I have experienced erratic behavior.
For my printer, sharing it using Samba caused all sorts of headaches but configuring it to use Jet Direct protocol (the one that uses port 9100 by default) clears up the connectivity problems.  I think ipp (internet printing protocol) works as well.

---

### Post by Foobarz on 2011-12-14
I don't connect with samba (I think), i just added a new printer using the add printer function

It's a wireless connection, and uses a Device URI and ppd
Should I install CUPS and an lpr and use that instead?

---

### Post by N00b-un-2 on 2011-12-15
CUPS should be installed by default on any linux distro.  However, that being said I would check to see that it is in fact installed.  Its my understanding though that you wouldn't be able to print at all without the common unix printing system.
Brother provides the drivers for your printer on their support website here
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2270DW]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2270DW")
you need to install both the LPR drive and the CUPS wrapper.  Then you should be able to add your printer via the printer configuration dialogue.
Out of curiosity, have you assigned the printer a static IP in you router?  If not, you should do so now.

---

