---
title: "[SOLVED] Creating PDF's from a web page"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Jacdeb6009 on 2008-05-12
Hi there, this has probably been asked before, but I don't seem to find a simple answer.

If I want to print a webpage (say a form that I filled in, for example) then doing so generates a PS file.  In Windows (sorry...) I used Acrobat as a printer to directly create a PDF file.

Is there a simple way to do this in Ubuntu? The people that I need to send info to, can easily view and print PDF's, but have no clue how to deal with PS output.

I've tried the Ghostview route, but this does not work for me. At the moment, I transfer the PS file to a Windows box and convert it using Acrobat, bot a nice solution and inconvenient, especially as I am trying to kick the Windows "habit".

Any help would be appreciated...

---

### Post by HotShotDJ on 2008-05-12
> **Jacdeb6009 said:**
> In Windows (sorry...) I used Acrobat as a printer to directly create a PDF file.Print the web site as you normally would.. but choose the PDF printer rather than your default printer.  It should have been installed by default.

---

### Post by lazyart on 2008-05-12
Control-P, then select CUPS/PDF as your printer.

---

### Post by Jacdeb6009 on 2008-05-12
Mmm, seems to be a problem, this is what I have been looking for all along, a "PDF printer". When I hit the print command in Firefox, the printer comes up as "Postscript/Default".  If I click on the little arrows next to it, there are no other options for printers (I have also not installed any physical printers yet).

So now what ? ...

---

### Post by shuttleworthwannabe on 2008-05-12
It seesm you do not have [COLOR=Red]cups-pd[/COLOR]f installed. Check in synaptic if you could install it there, then try again. (I am not sure if you have reboot or restart Firefox?? Hardy (actually gutsy) have this pre-installed by default as the previous poster mentioned.

---

### Post by Jacdeb6009 on 2008-05-12
Correct! :) As I read the previous post, I realised this was clearly the problem...

I've installed CUPS-Pdf printer.  This is linked to an HP 2200 Laserjet.  It appears that you cannot install the PDF as a stand-alone?

After installing CUPS-Pdf using Synaptic, I still had no printer. I then went to System-Admin-Printers and added a printer.  Here the system detected the PDF virtual printer but then insists on installing a printer together with it... (Is this actually required, or did I screw up somewhere?)

I selected the HP 2200 Laserjet as I have an old one kicking around the office.  So far so good.

I then printed a page from the forums. The printer creates a PDF file in the appropriate directory (/home/PDF) but the files is empty...  Printing a "test" page generates the same result.

I am ten steps closer, but still one step away :) 

Anyone know what the obvious error is...

Thanks for the help so far!!

---

### Post by inportb on 2008-05-12
Hm... the procedure sounds way too complicated. You should not have had to do anything to get the default PDF printer. Are you running Gutsy/Hardy?

---

### Post by Jacdeb6009 on 2008-05-12
Fiesty... :)

---

### Post by NikoC on 2008-05-12
Perhaps the following link can help you on the way?
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_a_virtual_PDF_printer]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_a_virtual_PDF_printer")

---

### Post by Jacdeb6009 on 2008-05-12
Thanks all!! Problem solved... RTFM :) as always, only need to know where to look...

Works a treat, thanks a lot!

---

### Post by richmod1 on 2008-05-21
Hello!
I have installed the UBUNTU CUPS virtual PDF printer and it works. I wish to use it to convert a web page to an E-mailable file. But there is a problem in that it takes a small webpage of about 1 -2 MB and converts it to a giant PDF file of 80 or more MB! Absolutely unmailable. The PDF file opens OK on my desktop. Apparently it takes a web page containing many small (50KB or so) photos and enlarges them by default to giant size! How do I configure this to make photos smaller? I would like to set it so each photo is limited to about 50KB in size.
Richmod1

---

