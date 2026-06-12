---
title: "Print from Windows 7 through samba"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by clvrfsh on 2013-04-17
I'm fairly new to Ubuntu and I'm trying to print from a Windows 7 box to a printer connected to an Ubuntu 12.10 machine. The Ubuntu box is connected to the internet and is connected to a printer (HP LaserJet P4015) I have installed Samba and Cups but haven't configured them and now I'm at a loss of what to do. The Windows 7 machine doesn't have internet access and they are both Dell Optiplex 745. Does the Win7 one need internet or can it be connected directly to the Ubuntu box?

---

### Post by TheFu on 2013-04-17
The the machines are on the same LAN, then no internet connectivity is needed.
I'd suggest that you 
* Verify printing works locally from the Ubuntu machine
* Setup the printer to be shared on the network using the CUPs web admin interface.
* Load the printer driver on the Windows machine
* Test from the win7 machine while watching the cups logs on the Ubuntu machine.

There is a web page to help setup CUPs at http://{insert-ubuntu-hostname}:631/ and login using your local Ubuntu account. This account should have full administrative control over CUPs.  You will need to enable the printer to be shared on the network. I think it is a check box.

There is a samba share setup for printing. I don't remember if that is really needed or not. From Windows, you can print using IPP and skip the entire Samba part. There are logs of how-tos for network printing - search for "ubuntu network printing" to find them.

---

### Post by clvrfsh on 2013-04-17
The thing is I'm not allowed to print straight from the win7 machine to the printer. I have to be able to go from the windows machine, find a file on the ubuntu machine, and then print it from the Ubuntu machine to the printer. I've tried installing and configuring samba and cups before and when I try to "Find a network printer" on the Win7 machine it tells me that I'm not putting in the name right. I named the printer on the Ubuntu machine LaserJet and when I try to network it on Win7 I use [http://Ubuntu:631/LaserJet](http://Ubuntu:631/LaserJet) and I keep getting an error. And I can't even explore the Ubuntu machine from windows.

---

### Post by TheFu on 2013-04-17
> **clvrfsh said:**
> The thing is I'm not allowed to print straight from the win7 machine to the printer. I have to be able to go from the windows machine, find a file on the ubuntu machine, and then print it from the Ubuntu machine to the printer. I've tried installing and configuring samba and cups before and when I try to "Find a network printer" on the Win7 machine it tells me that I'm not putting in the name right. I named the printer on the Ubuntu machine LaserJet and when I try to network it on Win7 I use [http://Ubuntu:631/LaserJet](http://Ubuntu:631/LaserJet) and I keep getting an error. And I can't even explore the Ubuntu machine from windows.

I think we have a misunderstanding. Maybe?  If both machines are on the same subnet (that is a local network), then you can tell Windows7 that the printer exists under the Ubuntu server and can use the IPP protocol from Windows to print via the Ubuntu machine, but directly to the printer.  LP and LPR protocols can also be used.  I have never gotten a printer working from Windows by  "browsing" for the printer or using an HTTP URL to auto-configure it.  Perhaps that works for some people. I've never seen it.

If the Windows machine is not on any network, then you'll be either
* connecting it to the network
* copying a file (probably a PDF) to the Ubuntu machine somehow - perhaps using a USB flash drive - then printing it.

If you really need to print by copying a file, the only way I see that happening is with a script that monitors a specific directory on the server for a PDF file (that you would create from Windows) and then print it using the PDF printing module that CUPS supports.

Using IPP or LP or LPR over the network would be much more convenient. Definitely.

---

### Post by clvrfsh on 2013-04-17
OK here is what I have so far. I have enabled the printer to be shared over the network using cups. But when I go to the win7 machine and install the driver for it I can't find it. I can ping the Ubuntu machine and it can ping back. I can even ping the printer but I can't find the printer. I read this [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) and tried it but it didnt work. Every time I put in the ip and printer name ( in 'the printer I want isn't listed' ) I get an error.

---

### Post by TheFu on 2013-04-18
You can't find the driver?  Does the vendor not provide Windows printer drivers?

I've asked a few questions that haven't been answered yet. Could you please review and answer those? We really do want to help, but lacking that information, our view is extremely limited.

---

