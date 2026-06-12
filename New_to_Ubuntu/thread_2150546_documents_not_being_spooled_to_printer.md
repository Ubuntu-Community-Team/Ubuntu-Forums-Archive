---
title: "documents not being spooled to printer"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by arranskye on 2013-06-01
just set up my printer.  System settings/printer/ add/ generic drivers.

Ubuntu can see printer and has marked  with green tick to indicate ready but documents not showing in print qeue.

what have I missed please  thanks.

printer lexmark Z735 not available in ubuntu's driver's list. thats why I choose generic.

---

### Post by tgalati4 on 2013-06-01
Open the following link:  [http://localhost:631/printers](http://localhost:631/printers)

Describe what you see.

Choosing "Generic" might be problematic.  This thread is not optimistic either:  [http://ubuntuforums.org/showthread.php?t=812862](http://ubuntuforums.org/showthread.php?t=812862)  Someone started a driver project for this printer, but never got anywhere:  [http://linux-z735.sourceforge.net/](http://linux-z735.sourceforge.net/)

---

### Post by arranskye on 2013-06-01
[TABLE="class: page"]
 [TR]
[TD="class: body"] [TABLE]
 [TR]
 [TD][[IMG]http://localhost:631/images/left.gif[/IMG]]("http://www.cups.org/")[/TD]
 [TD="class: unsel"][  Home  ]("http://localhost:631/")[/TD]
 [TD="class: unsel"][  Administration  ]("http://localhost:631/admin")[/TD]
 [TD="class: unsel"][  Classes  ]("http://localhost:631/classes/")[/TD]
 [TD="class: unsel"][  Online Help  ]("http://localhost:631/help/")[/TD]
 [TD="class: unsel"][  Jobs  ]("http://localhost:631/jobs/")[/TD]
 [TD="class: sel"][  Printers  ]("http://localhost:631/printers/")[/TD]
 [TD="class: unsel, width: 100%"][/TD]
 [TD][IMG]http://localhost:631/images/right.gif[/IMG][/TD]
 [/TR]
 [TR]
[TD="colspan: 9"] Hi  your link shows this:
[/TD]
[/TR]
 [/TABLE]
   [h=2][Lexmark-730-Series]("http://localhost:631/printers/Lexmark-730-Series") (Idle, Accepting Jobs, Not Shared, Server Default)[/h]                               [TABLE]
 [TR]
[TH]Description:[/TH]
[TD]Lexmark 730 Series
[/TD]
[/TR]
 [TR]
[TH]Location:[/TH]
[TD]ubuntu
[/TD]
[/TR]
 [TR]
[TH]Driver:[/TH]
[TD]Generic text-only printer (grayscale, 2-sided printing)
[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]usb://Lexmark/730%20Series?serial=20M00014900036A
[/TD]
[/TR]
 [TR]
[TH]Defaults:
[/TH]
[TD]job-sheets=none, none media=na_letter_8.5x11in sides=one-sided


When asked to print a test page this shows.  Thanks

[/TD]
[/TR]
 [/TABLE]
  
 [h=3]JobsThere was an error during the CUPS operation: 'client-error-document-format-not-supported[/h] 
     **Search in Lexmark-730-Series:**   

     
  No jobs.

  [/TD]
[/TR]
 [TR]
[TD] [/TD]
[/TR]
 [TR]
[TD="class: trailer"]CUPS and the CUPS logo are trademarks of [Apple Inc.]("http://www.apple.com") Copyright 2007-2013 Apple Inc. All rights reserved.[/TD]
[/TR]
 [/TABLE]

---

