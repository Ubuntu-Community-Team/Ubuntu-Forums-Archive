---
title: "PCI Express driver for ubuntu 12.04"
date: 2012-06-05
forum: Programming Talk
---

### Post by billybob567 on 2012-06-05
We are developing a product with a PCI Express interface, the h/w guys are putting an FPGA in the box that I'll need to talk to.
 
We plan to plave a prototype card in a PC running Ubuntu 12.04 so as to debug the FPGA and the host driver.
 
I've set up a PC with the Ubuntu and I've read about the PCI Express design in the Documentation folder and in blogs on the web. I started with example code for a PCI Express service and got compile errors that don't make sense.
 
According to the HOWTO in the Documentation folder (something I found on the web), the source code should contain the following struct:
 
[SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]static struct pcie_port_service_id service_id[] = { {[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000].vendor = VENDOR_ID,[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000].device = DEVICE_ID,[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000].port_type = PCIE_RC_PORT,[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000].service_type = PCIE_PORT_SERVICE_AER,[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000]}, { /* end: all zeroes */ }[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000]};[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#008000][COLOR=black]The compiler complains about the struct name. I checked the header file, pcieport_if.h, and it does not contain the struct that I'm supposed to use. I looked around and apparently, this struct was removed in a patch. [/COLOR][/COLOR][/SIZE][COLOR=#008000]
 
[SIZE=2][COLOR=black]So now, I'm not sure how to code the service because my tutorial may have been based on an old design and I cannot seem to find a tutorial for the new design approach.[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#000000]Any ideas would be welcome.[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#000000]Sincerely, [/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]More confused than ever :KS[/COLOR][/SIZE]
[/COLOR][/COLOR][/SIZE]

---

### Post by billybob567 on 2012-06-07
[COLOR=red]SOLVED[/COLOR]

[COLOR=black]According to our part-time Linux consultant, I was led astray by the info that I read at [http://www.kernel.org/doc/ols/2005/ols2005v2-pages-9-18.pdf](http://www.kernel.org/doc/ols/2005/ols2005v2-pages-9-18.pdf).[/COLOR]

[COLOR=black]I can write a driver just like I've done in the past but register it as a pci driver whereas in the past, I registered as a platform driver.[/COLOR]

[COLOR=black]I was pointed towards /drivers/net/3c59x.c for an example of how to write a driver.[/COLOR]

[COLOR=black]Thx, Bill. [/COLOR]

---

### Post by sammiev on 2012-06-07
> **billybob567 said:**
> [COLOR=red]SOLVED[/COLOR]

[COLOR=black]According to our part-time Linux consultant, I was led astray by the info that I read at [http://www.kernel.org/doc/ols/2005/ols2005v2-pages-9-18.pdf](http://www.kernel.org/doc/ols/2005/ols2005v2-pages-9-18.pdf).[/COLOR]

[COLOR=black]I can write a driver just like I've done in the past but register it as a pci driver whereas in the past, I registered as a platform driver.[/COLOR]

[COLOR=black]I was pointed towards /drivers/net/3c59x.c for an example of how to write a driver.[/COLOR]

[COLOR=black]Thx, Bill. [/COLOR]

Hi billybob and welcome to the forums. Hope you can go up to " 	Thread Tools" and mark this thread as "solved". It will only help the next person on a search of such a topic. Thanks.

---

