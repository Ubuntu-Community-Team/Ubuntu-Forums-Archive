---
title: "Old ubuntu laptop as print server"
date: 2020-09-27
forum: New to Ubuntu
---

### Post by rev9ers on 2020-09-27
Hello everyone,

I have an old ubuntu laptop that I would like to set up as a print server.

Here's the scenario: I have two printers which not wireless (Cat45/USB only) that I would like to make available wirelessly to the home network (two windows, one mac) by connecting them by USB to my old Ubuntu laptop and using that laptop for the computers to access the printers.

Is it the correct thing to do to try and set up the laptop as the printer server and will that work? I'd like to just be able to print to either of those two printers from any of the laptops via wifi.

Any help is most appreciated.

Thank you!

---

### Post by TheFu on 2020-09-27
Networking is networking. Wired or wifi should work fine, provided the laptop has a static IP, runs CUPs, and the laptop can print to the printers.  I have a desktop doing the same thing. I just point any client machines at the CUPS server (631/tcp) on that desktop, choose the correct printer driver, choose IPP as the protocol and printing works.  I only have 1 printer setup that way, but can't see why CUPs can't handle 500 printers provided they have a unique identifier/name.

---

### Post by SeijiSensei on 2020-09-27
Attach one printer to the laptop and install it. I often choose to use the web-based management tool that comes with CUPS by pointing a browser at [http://127.0.0.1:631/](http://127.0.0.1:631/). Go to a client and see if you can connect to and install the remote printer. On a Linux client, you can use that same web-based client. In Windows, install the printer using IPP as TheFu suggests.  I'd also give the laptop a static IP address rather than letting it be assigned by DHCP. Anything that operates as a server should have a static address.  

If all this works, attach the other printer, rinse and repeat.

---

### Post by TheFu on 2020-09-27
Server guide how to: [https://ubuntu.com/server/docs/service-cups](https://ubuntu.com/server/docs/service-cups)
There is almost always some step that I forget.  Common things like setting up printers are covered in the desktop and server guides.

---

### Post by rev9ers on 2020-09-27
This is great, thank you! I will give it try and report back!

---

