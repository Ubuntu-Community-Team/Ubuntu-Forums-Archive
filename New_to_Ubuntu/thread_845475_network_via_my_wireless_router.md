---
title: "network via my wireless router"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-06-30
Is there a way that I can network my laptop via my wireless router so that I can access a printer scanner?

If so, how do I do it?

---

### Post by cariboo on 2008-06-30
First of all we need way more information, like does wireless work for you now? If not could post the results of Applications--Accessories-->Treminal:

```
lspci
```

Paste the output in your next post, this will give us an idea of what wireless card you have in your laptop.

Second is the printer scanner connected to another computer?

Third is your router also a print server?

Jim

---

### Post by saskatchewan on 2008-06-30
Ok
My wireless works but for using things like printer and scanner I have it pluged into the router via a hard wire.

The linux computer that I am using does not have a wirless card.

The printer/scanner is connected to a desktop running XP.

I don't know if the router is a print server.  Can I make it one?

---

### Post by stchman on 2008-06-30
> **saskatchewan said:**
> Is there a way that I can network my laptop via my wireless router so that I can access a printer scanner?

If so, how do I do it?

What kind of printer/scanner is it?

Does the printer have a network card?  If no print servers are not that expensive.  You can also try to use Samba to connect to the printer.

---

### Post by saskatchewan on 2008-06-30
I honestly do not know if the printer/scanner has a network card.  It is an Epson Sylus Photo RX 500.  I looked up Samba and it says that it is a network tool.  Would I just install that on the desktop computer and that would allow me to network other computers?

---

### Post by cariboo on 2008-06-30
You should make sure you have your printer is shared on the XP computer, then got to System-->Administration-->Printing-->New, then in the Select Connection Window, select Windows Printer via Samba(SMB). Then under SMB Printer click the Browse button, if you have your printer correctly set up for sharing it should show up in this window, Select youe printer and click Forward. Make sure Select printer from database is checked, then scroll down to Epson and click forward, in the left pane scroll down to RX500 and click on it. Use the recommended driver ahd click forward. Enter any info you want in the next window, it doesn't affect the operation of the printer and click apply.

Jim

---

### Post by saskatchewan on 2008-07-01
Do I have to install Samba on both the XP computer and the Linux computer or just one of them?

---

