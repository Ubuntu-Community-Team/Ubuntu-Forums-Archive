---
title: "Share PDF-printer"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by .nedberg on 2008-08-06
I want to share a PDF-printer from an Ubuntu server (8.04) to Windows clients (XP). Now I can make the printer available to the clients, and it prints fine. My problem is that I want the clients to save the PDF-file locally, not on the server.

I want it to work just like "Windows document writer". The client should get a pop-up asking where to save the file, and the file should be saved locally.

Is this possible?

I have samba and cups working on the machine.

---

### Post by thirdwheel on 2008-09-16
Hey,

To print PDF files locally in Windows, your best bet is to go with CutePDF Writer.  There's a freeware version that uses ghostscript in the background.

Hope this helps.

---

### Post by .nedberg on 2008-09-16
Hey, thanks for replying!

CutePDF requires installing on the client, something I would rather not have to do.

I had a look at [PDFCreator]("http://www.pdfforge.org/products/pdfcreator"). It can be installed on a Windows Server, and can save to a local folder using variables (username). So this is a better solution for me, but I still haven't installed it on my main server...

---

### Post by bab1 on 2008-09-16
> **.nedberg said:**
> I want to share a PDF-printer from an Ubuntu server (8.04) to Windows clients (XP). Now I can make the printer available to the clients, and it prints fine. My problem is that I want the clients to save the PDF-file locally, not on the server.

I want it to work just like "Windows document writer". The client should get a pop-up asking where to save the file, and the file should be saved locally.

Is this possible?

I have samba and cups working on the machine.

**Edit:**>  [COLOR="Blue"][B]Martin-Éric Racine  wrote on 2008-03-27:  (permalink)

Sorry guys, we've already answered this question MANY times already and no, CUPS-PDF cannot have a dialog, because it's just a printer backend for CUPS.

The dialog you see in GNOME applications comes from GTKPRINT, which offers PDF generation as a standard feature; it has NOTHING to do with CUPS-PDF.

It doesn't accept parameters either. It's not a command line tool.

Anyhow, AppArmor prevents anyone from changing the output path, even if you edit cups-pdf.conf, on Ubuntu.[/B][/COLOR]


**[COLOR="Red"]See below for the entire exchange:[/COLOR]**
[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/158406]("https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/158406")

I have seen your scripting skills with timekpr.  I'm sure you can make this work.  Good luck!

---

