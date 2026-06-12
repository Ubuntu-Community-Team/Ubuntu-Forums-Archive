---
title: "Printing to a shared printer?  Test page yes, other docs no."
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Ansible on 2008-06-13
I have a USB printer connected to a desktop, and I'm able to connect to it and print a test page from my laptop.  However, I can't print from firefox or evince (the pdf reader).  The jobs just stack up in the queue with status 'pending'.  

A friend was over at the house yesterday with her mac and we were able to print just fine.  I guess that means the problem is on the client side, but maybe I need to do something special on the server to enable ubuntu clients?

On the server, I checked the box for sharing, and for sharing over the internet, and for allowing users to change all the jobs not just their own.  Doesn't seem to help!

---

### Post by avtolle on 2008-06-13
First, which release of Ubuntu are you using? Second, there was, for a good while, a problem with printing from Evince, which, via the various updates, etc., to 8.04 been "cured". For printing from a pdf, install xpdf from the repositories, load a pdf to it, and try to print, this to check on the general printing setup and to narrow possible problems. Note: if you are able to print from xpdf, be aware the page might have some funky margins (at the top, especially) but again, the purpose of trying xpdf is to check printing setup for now.

---

### Post by avtolle on 2008-06-13
Just had another thought; when trying to print from Evince, are you selecting the usb printer attached to the desktop as the printer to use, rather than the default selection?

---

### Post by Ansible on 2008-06-13
Ok, thanks for the suggestions.  I guess I'm a little further along, although it still doesn't work.  I've used this printer directly over USB with the laptop before, and so it was present among the printers but inactive.  Although I selected the remote ip4000@<ip address> from firefox/whatever program, they were all queued up for the local printer.  I deleted the local printer from the printers list, and then all those jobs went away.  

So it looks like a printer with the same name as the remote printer takes precedence, even though it isn't connected.

Now when I print to the remote printer, the job is not queued locally.  It doesn't appear on the remote machine either though.  

I didn't try xpdf yet - I just tried printing plain text from Text Editor.  

BTW both machines are on 8.04.

---

### Post by stchman on 2008-06-13
If you are in US make sure you select US Letter instead of A4.

---

### Post by avtolle on 2008-06-13
> **stchman said:**
> If you are in US make sure you select US Letter instead of A4.
He beat me to it. :-) 

Another thing to check; open Firefox, in address bar input localhost:631 which will get you to the home page for CUPS (the printing system "manager"). Be sure the deleted local printer isn't still hanging around there. But try the paper size change first.

---

### Post by Ansible on 2008-06-14
When I go to print on the laptop, the print dialog has Paper type and Paper source.  Paper type has these choices:

Plain paper
Transparencies
Tshirt transfers
Glossy photo paper
.... etc ....

And then paper source has these:
Selected by paper select key
auto select
casette
CD
Automatic Paper Source Switching

Nowhere else on the dialog is paper type mentioned.  I didn't see A4 or US Letter as choices.  

When I go to [http://localhost:631/printers/](http://localhost:631/printers/), I get this (pasted from web page):

iP4000@100.100.100.95 (Default Printer)
	Description: Canon iP4000
Location: Location Unknown
Printer Driver: Canon PIXMA iP4000 - CUPS+Gutenprint v5.0.2 Simplified on 100.100.100.95
Printer State: idle, accepting jobs, not published.
Device URI: ipp://100.100.100.95:631/printers/iP4000 

Plus there's a PDF option.

---

### Post by Ansible on 2008-06-14
Ok, found the US letter option under Page Setup in the pdf app.  It was already US Letter.  Also tried it from gedit.

---

### Post by Ansible on 2008-06-17
bump

---

### Post by Ansible on 2008-06-20
Ugh... stupid solution to this!!  I changed two variables at once, so I'm not sure which one it was.  One thing I did was to log in to my server first through Nautilus.  Not sure if I'd done that in previous tries.  

But what I think was real culprit was the fact that one of the ink tanks on my printer is low.  Under windows (local printing through USB) you get a dialog announcing that fact, then you have hit an 'override and go ahead' button on the printer.  I forgot all about this with remote printing, which gave no dialog.  I got it to print from windows, then rebooted into linux and was able to print there as well without hitting the override button - presumably because I'd already done it once since turning on the printer.  Whatever, now it works.

---

