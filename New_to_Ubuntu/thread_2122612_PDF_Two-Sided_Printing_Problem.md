---
title: "PDF Two-Sided Printing Problem"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by trogbot on 2013-03-05
I've been running 10.4 Lucid for quit a while.  Have applied updates regularly.  Just recently downloaded a PDF Service Manual & want to print it two sided; but even though my duplexer is enabled in CUPS & HP Toolbox says it's enabled; PDF Document Viewer will not allow two sided.  Can print two sided anywhere else.  Does anybody have any suggestions?  All help greatly appreciated.

---

### Post by trogbot on 2013-03-06
Since no one has any suggestions; I will mark this thread as SOLVED.
Thanks to the few who viewed the thread.


Update:  **_CANNOT MARK SOLVED._**  It appears there is no Thread Solved Option on Thread Tools.  Running Firefox 15 w/last Update if it matters.
             Only options shown are:  Show printable version; Email; Subscribe

---

### Post by schragge on 2013-03-06
Isn't it a bit too hasty to declare thread closed less than in 24 hours after it was opened? 

As to you question. Do you experience this only with this Service Manual, or with other PDF documents, too? 
> **trogbot said:**
> Can print two sided anywhere elseCould you please define *anywhere else* a bit better. *lp* on the command line? Another PDF viewing software? Web browser PDF-viewing plugin? Another Linux distribution using the same printer? Windows using the same printer? Another printer?

---

### Post by tgalati4 on 2013-03-06
Create another printer.  Give it a different name.  Sometimes the printer spools get messed up with updates.  Then try with a small, 2-sided document.  If that works, then try the larger document.

It could be a buffer problem with cups, or a printer memory problem, or a driver problem.  Look at the log files in /var/log/cups for clues.

---

### Post by trogbot on 2013-03-06
It happens with all PDF's.  *anywhere else* is:  Printing files; Web Pages; etc.; yes even lp.  The only place that does not respect my printing default setup is the PDF Reader/Viewer used in Lucid.  It only allows 1 sided.  It's a network printer on local network & works fine from Windows & my box with the exception of
above problem.  The reason I've not gone beyond 10.4 Lucid is because I don't care for the changes being made to the Ubuntu UI.  I'm an Old Timer (Pre-DOS days...Bit/Byte Programming via Toggle Switches; All OS's since.).  I'm happy with version running now.  Just disgusted with PDF Doc Printing right now.

---

### Post by trogbot on 2013-03-06
I've tried re-defining printer, etc.  No help.  I believe it's the PDF Viewer/Reader.

---

### Post by Zill on 2013-03-06
> **trogbot said:**
> I've been running 10.4 Lucid for quit a while.  Have applied updates regularly...
> **trogbot said:**
> ...Running Firefox 15 w/last Update if it matters.
I think you may not have not updated your system fully.  I am running Lucid here but also [Firefox 19]("http://packages.ubuntu.com/lucid/firefox").  This is using the standard Ubuntu repos - no PPAs involved!

You should be able to update Lucid with Firefox 19 by running the following two commands:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by trogbot on 2013-03-06
Didn't think it was the problem w/not seeing SOLVED under Thread Tools; but upgraded FF to 19 anyhow.  Still do not see way to mark thread SOLVED.
Thanks Zill for the suggestion.

---

### Post by trogbot on 2013-03-06
I found the problem with FF Thread Tools.  Not working correctly under vBulletin 4.  They're working on a fix.  
If anyone else is having the Thread Tools problem; see [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377).

As for the PDF Print problem;  I'm going to live with it as is.

Thanks to everyone for your help.

---

### Post by tgalati4 on 2013-03-06
Check out linux mint MATE 14 (based on 12.10).  You get the latest packages with a traditional Gnome2 interface.  I'm going to check out 2-sided printing with my HP network printers soon.

---

### Post by trogbot on 2013-03-07
tgalati4:  Did some snooping with the PDF Print problem & through your *Grab a fly swatter* link; I found a bug that's been out there since early days of Lucid concerning PDF Printing (Images in case of bug); but it's pointing to Evince.  I went the old cmdline way, printing the PDF Doc Two-Sided via:
"lp -o sides=two-sided-long-edge *filename.pdf*" & it worked fine.  I suspect that the problem lies within Evince.... just using the default setting of One-Sided within CUPS; even though it shows a selection pull-down for printing (Where 1-Sided is shown as Default); but fails to show Two-Sided as Option on pull-down.  Surely it can't be that simple?  Perhaps there's someone fighting the Evince bug that could glance in that area of Evince.  Also; I think I will Re-Open
the Thread & keep the problem alive if I can after marking it SOLVED.

---

### Post by schragge on 2013-03-07
For reference: LP#[lpbug]861493[/lpbug]

---

### Post by trogbot on 2013-03-07
Thanks schragge.  Appears they knew about the problem 2 yrs.+ ago & just dropped it to a priority that will never get worked.
What does everyone think?  Should I keep the thread ***Open***/***SOLVED***?

---

### Post by schragge on 2013-03-07
Irrespective of what you'll decide to do with the thread here, I'd recommend you subscribe to that bug in Launchpad, and click on the green link "[COLOR=green]Does this bug affects you?"[/COLOR]. The more affected users will do that the more are the chances that Ubuntu developers will pay some attention to this bug and do something about it.

---

### Post by gifford on 2013-03-07
Adobe reader has a range of printing options. You can print only even or odd pages. This will allow for printing on both sides of a page.

---

### Post by tgalati4 on 2013-03-07
I would not have guessed a bug in evince, but I'm glad that you found a work-around.  When you set the printer up in CUPS originally, there should be a "Printer Options" tab.  Look in [http://localhost:631/printers](http://localhost:631/printers) and see if you can find the printer options--"Set Default Options".  You have to manually set Double-sided printing, because it is off by default.  I think evince just uses the CUPS default settings, and if it isn't set on, then other applications can't see the option.

If that doesn't fix it, then by all means, add your experience to that bug listing.  Squeaky wheel gets the oil.

Here's a cut-and-paste from my CUPS page for an HP printer:

Description:	Color Injet Printer
Location:	Terry's Office
Driver:	HP Officejet 7300 Series, hpcups 3.12.6 (color, 2-sided printing)
Connection:	hp:/net/Officejet_7300_series?zc=Officejet7310
Defaults:	job-sheets=none, none media=na_letter_8.5x11in** sides=one-sided**

After setting in "Set Default Options":

Description:	Color Injet Printer
Location:	Terry's Office
Driver:	HP Officejet 7300 Series, hpcups 3.12.6 (color, 2-sided printing)
Connection:	hp:/net/Officejet_7300_series?zc=Officejet7310
Defaults:	job-sheets=none, none media=na_letter_8.5x11in** sides=two-sided-long-edge**

---

### Post by trogbot on 2013-03-08
tgalati4:  I've got the same set-up as yourself.  HP Officejet 7300 Series w/Duplexer installed & set for two-sided printing through CUPS.

BTW:  Can you open a pdf by double-clicking on it; so Evince gets kicked off & printing 2 sided via Print to your HP?

---

### Post by trogbot on 2013-03-10
Closing due to having work around.

---

### Post by Matt 6:27 on 2013-05-10
I'm seeing the same issue with 12.04, which I update faithfully.  It just started maybe a month ago.  Evince will not even give me the option to print double-sided.  I am able to print double sided with any other application, including Acrobat Reader, so my experience mirrors trogbot's.

---

### Post by Matt 6:27 on 2013-05-10
Apologies for not reading entire thread.  I see you've a workaround.

---

### Post by tgalati4 on 2013-05-10
I just printed a two-sided tax document (with color and lots of small print) on my HP7300 through evince 3.6.0 using poppler/cairo (0.20.4).  I'm using Linux Mint Mate 14 (64-bit, based on 12.10).  There is a tab on the far right side of the evince print dialog box (Advanced):  *Duplexer Installed*.  If this box is not checked, then you won't get the double-sided print option.

So, I am not having a problem with duplex printing on 12.10 with evince 3.6 and CUPS 1.6.1.

---

