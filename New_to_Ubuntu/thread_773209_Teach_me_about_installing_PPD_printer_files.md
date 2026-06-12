---
title: "Teach me about installing PPD printer files"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by bday_cs on 2008-04-28
Hi... 

So I was playing around trying to get a Canon MX310 printer to install.  This isn't in the list of printers when you just look for drivers that come with Ubuntu 8.04.  This is just using the 
System->Administration->Printing built into Ubuntu, which I think is slightly different than the gnome-cups-manager version. (I'm totally new to admin/install of linux... only been user prior)

When googling around, I saw that some folks had good luck using a similar model (MP150) that is included "built-in", and when I do that, the printer prints okay.  I also noticed that it generates a PPD file in the /etc/cups/ppd directory for it.

I also grabbed a PPD file from Canon directly from the Mac OS X CUPS driver file.  I figured I could tweak it to use in Ubuntu.
Problem I'm having is that using a PPD file does not result in usable printer.  This is even using the PPD file generated after installing with the MP150 driver with the built-in approach.
It acts as if it installs okay, but printing test page doesn't do anything.

So basic question is... is there another step needed after pointing to a PPD file to get a printer to work from a PPD file?
Next question.. can you point me in a path/steps to debug why this is the case?

If I can get this figured out, there's a good chance this would apply to many of the Canon all-in-one printers, as long as there is a Mac OS X driver file available for it.

Thanks! 
Brian

---

