---
title: "Connecting wirelessly to an HP PSC 750 printer"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by mlnease on 2012-10-03
Hello,

I connect wirelessly to a Linksys 3100 router via a 3com pci card.  Another computer connects to the cabled router that connects to the Linksys.  That computer *also* connects--via usb--to an HP PSC 750 printer.  I'd like to be able to connect wirelessly to that printer from my computer.

Does this make any sense?  Sorry if this isn't well worded, I'm completely new to networking.

Thanks in advance.

---

### Post by rai4shu2 on 2012-10-03
So, what OS is the computer connected to the printer?

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by mlnease on 2012-10-03
> **rai4shu2 said:**
> So, what OS is the computer connected to the printer?

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
Thanks for the timely response and sorry about that--both computers are running Lucid.

---

### Post by mlnease on 2012-10-03
p.s.  I'm looking at the link you sent--very helpful (I think), thanks.

---

### Post by mlnease on 2012-10-05
Thanks again for [this link]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu").  The instructions seem quite clear but I'm stuck at "Specify the host IP address or name" (it doesn't work without, I tried)--I tried 192.168.1.1 and 192.168.2.1 as well as my IP address, to no avail.

A screenprint of the printer properties is attached below.

All policies, controls and options are grayed out.

[UPDATE]  I've been able to print a test page from the remote machine if I first disable UFW on the print server.  The remote machine can't find the printer with UFW enabled on the print server.

[UPDATE]  I can print normally via the print server after having set the following rules in UFW on both computers: 
```
515/tcp                    ALLOW       Anywhere
631                        ALLOW       Anywhere
```If this was inadvisable I'd very much appreciate any suggestions.

Meanwhile I'll mark this thread 'solved' for any others encountering these hurdles.

---

