---
title: "Virtual PS Printer"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by horizonuser on 2013-01-23
Hello,
      In Windows I could create a printer and point it to a file. I could then select any driver I wanted and apply it the printer. This was usful for printing Postscript (level) documents to file. Is this possible in Ubuntu? I have installed cups-pdf but this only allows me to output in PDF format. Similarly, the "Print to file" option in the printer dialog only allows me to select PDF as the output. Is is possible to printer to a virtual PS printer in Ubuntu 12.04?

---

### Post by HermanAB on 2013-01-23
Uhmmm, the CUPS print system turns any printer into a postscript printer.  So if your printer is otherwise working, then all you need to do is send the postscript (or PDF) file to the printer and it will print.

[http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

---

### Post by horizonuser on 2013-01-23
Thanks for the reply. I don't understand it though! Maybe I am explaining the problem wrong.
Printing on PC is working. However, I need to print to a file, in Postscript format. In Windows this was accomplished by setting up a printer with a Postscript driver but making the Printer Port by a filename. This would prompt to save the printed file as and the format would be Postscript. While I do get a "Print to file" option in Ubuntu I only get the option to save as PDF, not Postscript!

---

### Post by mcduck on 2013-01-23
Are you sure? The Print to File-option sure does have the option for both PDF and PS on my computer, and has had that in all the previous Ubuntu verions as well (as long as the print to file feature itself has been available...)

---

### Post by horizonuser on 2013-01-23
I'm sure.......see attached. Also, changing the output file to .PS still saves it in PDF format!

---

### Post by mcduck on 2013-01-23
> **horizonuser said:**
> I'm sure.......see attached. Also, changing the output file to .PS still saves it in PDF format!

That's interesting. I just noticed you are using Lubuntu, so perhaps it's a question of some library that's not installed by default in Lubuntu but is on Ubuntu...

Which program are you printing from? The available options change depending on what the program itself allows, for example printing from Evince adds the option fro SVG output... Although I don't think I've ever seen the dialog without both PS & PDF options at least.

---

### Post by horizonuser on 2013-01-23
I am using Ubuntu 12.04 , Gnome Classic, not Lubuntu - where does it look like I am using Lubuntu?

This options appears in Chromium. Funnily, I didn't try any other apps as my main goal is to do this from the command line - all looking improbable now!

---

### Post by mcduck on 2013-01-23
> **horizonuser said:**
> I am using Ubuntu 12.04 , Gnome Classic, not Lubuntu - where does it look like I am using Lubuntu?

This options appears in Chromium. Funnily, I didn't try any other apps as my main goal is to do this from the command line - all looking improbable now!

The thread is tagged as "Lubuntu".

Anyway, try some other program for starters, if that would add the missing options.

(And if it doesn't, I believe the cups-pdf package should also support printing to PS. I haven't sued it myself, though, as the built-in print-to-file support made it pretty much unnecessary. But it might be worth looking at if the default system doesn't give you the options you need)

---

