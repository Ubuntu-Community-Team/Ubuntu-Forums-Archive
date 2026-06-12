---
title: "How do I convert Lotus Smartsuite (2000) files to LibreOffice?"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by bwallum on 2011-11-23
Hi

I have some old files that go back to the year 2000. They were created in Lotus Smartsuite Millenium Edition.. The file suffixes are:-

.ADX
.APR
.dbf
.lwp

I have found a utility called kvlot32.exe which handles Lotus file formats up to 1998 but won't do the 2000 vintage.

Anybody have any experience in converting these files?

I would be happy to get them as text documents but would prefer them somewhere near laid out as created.

Thanks in advance

---

### Post by coffeecat on 2011-11-23
I have one suggestion, which may or may not work, and I hope others may have a better one.

A couple of years ago I used Lotus Symphony to convert a couple of old Lotus word processor files from about 1999. The words sledgehammer and nut come to mind, but at least Lotus Symphony is free. You can download it here:

[http://www-03.ibm.com/software/lotus/symphony/home.nsf/home](http://www-03.ibm.com/software/lotus/symphony/home.nsf/home)

The bad news is that the newest version of Ubuntu listed as supported is 8.04, so I have no idea whether that will install on current versions. If it doesn't, you might have to use (whisper is softly!) the Windows or MacOS version. And I have no idea whether it will cope with all those file formats.

Good luck anyway.

---

### Post by qamelian on 2011-11-23
Documents from Lotus 1-2-3 and Lotus WordPro should just open in LibreOffice, as LO already supports those formats. I'm not sure if there is an easy way to use or convert Lotus Approach databases for use in LO.

---

### Post by crazy bird on 2011-11-23
Can this be helpfull:
[http://www.google.nl/search?q=%22convert+Lotus+Smartsuite+files+to+LibreOffice%22&btnG=Zoeken&hl=nl&gbv=2&gs_sm=e&gs_upl=1734l8390l0l8656l20l19l1l7l0l0l281l1907l3.3.5l11l0&spell=1&sa=X&oq=%22convert+Lotus+Smartsuite+files+to+LibreOffice%22&aq=f&aqi=&aql=](http://www.google.nl/search?q=%22convert+Lotus+Smartsuite+files+to+LibreOffice%22&btnG=Zoeken&hl=nl&gbv=2&gs_sm=e&gs_upl=1734l8390l0l8656l20l19l1l7l0l0l281l1907l3.3.5l11l0&spell=1&sa=X&oq=%22convert+Lotus+Smartsuite+files+to+LibreOffice%22&aq=f&aqi=&aql=)

---

### Post by bwallum on 2011-11-24
I've found half the answer! 

.lwp and .dbf can be opened by LibreOffice 3.3 +. You may be asked for character set. I chose Western Europe (ISO-8859-15/EURO) and it worked for me. I live in Scotland. That is the joy of 'standards', there are so many to choose from!

...and bonus, .wks (that's M$ Works files) are said to be openable in 3.3+. 

I tried Lotus Symphony which is free from IBM but it did not recognise .lwp or .dbf files (or any of the old 'Approach' files either which I find very odd). It also relies heavily upon network connectivity and seems to be a full client office suite but auto hooks up to a cloud server. Not too sure who was in charge of my computer so I removed it.

Now, .APR and .ADX anybody?

EDIT
quick overview of import functions can be found here 
[http://www.libreoffice.org/download/new-features-and-fixes/](http://www.libreoffice.org/download/new-features-and-fixes/)

---

