---
title: "Printing over Internet"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by lledurt on 2011-09-09
I have a printer on my network at home (also usb connected to a ubuntu machine), and when I am on the road I would love to be able to print over the Internet in both windows and Ubuntu to this printer.  Isn't cloud supposed to do this?

Right now I just print to a pdf, do a scp then ssh in and print.  There has to be an easier way.  I think a windows vpn would make this work, but again there must be an easier way.

Thanks for your help

---

### Post by ubudog on 2011-09-09
Hi!  I would recommend this:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

And also getting a DynDns account so that you can print while on the go.  
[http://www.dyn.com](http://www.dyn.com)

Hope that helps, if you need any help with the setup, we are here!  :-)

---

### Post by tgalati4 on 2011-09-10
Poke a hole in your firewall at port 631 and you can print to most printers directly.

You just need to find out what the printer is called, for example: (go to localhost:631)

[http://localhost:631/printers/HP-OfficeJet-7110](http://localhost:631/printers/HP-OfficeJet-7110)

Substitute localhost with the IP address or web address of your machine hosting the printer or the printer itself (if it hangs directly off of the network).  It works well, but could be a security hole so I would only open the ports when you really need to use them.

You could redirect some random port (12000 to 65000) to 631 using a firewall rule--security by obscurity.

Set up a new printer and put the address in the IPP dialog box and choose the correct printer driver.

---

### Post by ubudog on 2011-09-10
> **tgalati4 said:**
> Poke a hole in your firewall at port 631 and you can print to most printers directly.

You just need to find out what the printer is called, for example: (go to localhost:631)

[http://localhost:631/printers/HP-OfficeJet-7110](http://localhost:631/printers/HP-OfficeJet-7110)

Substitute localhost with the IP address or web address of your machine hosting the printer or the printer itself (if it hangs directly off of the network).  It works well, but could be a security hole so I would only open the ports when you really need to use them.

You could redirect some random port (12000 to 65000) to 631 using a firewall rule--security by obscurity.

Set up a new printer and put the address in the IPP dialog box and choose the correct printer driver.

+1!  Never knew you could do that.

---

