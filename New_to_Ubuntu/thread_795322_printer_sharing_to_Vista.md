---
title: "printer sharing to Vista"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by tone33 on 2008-05-15
I have ubuntu 8.04 on my desktop with an HP 2100 printer and I can print fine.  I have Vista Enterprise x64 on my laptop and would like to send print jobs to the same printer.  The printer is connected via  parallel port to the desktop.  I've played around with the System->Administration->Printing but can't get my Vista machine to see it.  Can someone please point me to a guide on how to do this? or perhaps provide a little insight?

---

### Post by stchman on 2008-05-15
> **tone33 said:**
> I have ubuntu 8.04 on my desktop with an HP 2100 printer and I can print fine.  I have Vista Enterprise x64 on my laptop and would like to send print jobs to the same printer.  The printer is connected via  parallel port to the desktop.  I've played around with the System->Administration->Printing but can't get my Vista machine to see it.  Can someone please point me to a guide on how to do this? or perhaps provide a little insight?

You need to share the printer attached to the Hardy machine.

After you share the printer you need this line for your Vista machine:

http://<IP address>:631/printers/<Exact Printer Name>

<IP address> - the IP address of the machine the printer is attached to the Hardy machine.
<Exact Printer Name> - The EXACT name of the printer attached to the Hardy machine.

---

### Post by tone33 on 2008-05-15
ok so I have a dumb question.  How do i get the ip address in ubuntu?  what's the ipconfig equivalent?

ok I got it...  it was the local ip inside my network.  it works!  Thanks for the help.

---

