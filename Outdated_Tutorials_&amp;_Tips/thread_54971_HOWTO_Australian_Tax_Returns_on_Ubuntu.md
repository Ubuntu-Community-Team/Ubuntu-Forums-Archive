---
title: "HOWTO: Australian Tax Returns on Ubuntu"
date: 2005-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by ltmon on 2005-08-06
The Australian Taxation Office supplies a piece of software called eTax to fill in your tax return.  It's a Windows only piece of **** that is written in Delphi.  Never mind that they could easily use Kylix to produce a cross platform version....

If you're like me and don't have a Windows installation to fill in your tax return, or if you just want to do it on Linux to prove a point, here's how:

1. Install msttcorefonts.  You'll find instructions for this on ubuntuguide.org.  It's very important that you do this... I didn't at first and my etax had no text displayed whatsoever, which made it very hard to fill in ;)

2. Install wine from apt repositories. 

*IMPORTANT* The latest version of wine (in backports) is 20050419-1~5.04ubp1.  This doesn't work.  You will have to use synaptic (or apt-get) to force install an older version such as 20050310-1~5.04ubp1.  In Synaptic use the Package->Force Version menu option to do this.

3. Go to the following address: [http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)
Download the latest version of this utility.  Extract it and run ./setup.  Answer the questions and choose "Silent Installation".  This will set up wine automatically and *shudder* install IE6, which is required to submit your tax return.

4. Go to [www.ato.gov.au](www.ato.gov.au) and download etax.  They will tell you to go get Internet Explorer, but you can ignore this if you find the "continue" button near the bottom of the page.

5. Open a terminal and type:

> wine etax2005_1.exe

This will install the software.

6. Type:

> cd ~/c/etax2005/
> wine etax2005.exe

This will launch etax.  The only thing that doesn't work with mine is the help functions.  To view the hlp file (~/c/etax2005/etax2005.hlp) you can use the viewer available at [http://www.kamasoftware.com](http://www.kamasoftware.com).  Once you load the help file in this viewer, press the "index" button to see the help topics.

7. Fill in the tax return.

8. Lodge it.  This bit fails if you haven't got IE installed with Wine, that's why we did step 3.

9. Remove wine and IE from Ubuntu.

10. Shower with soap.

11. Write a nice, polite letter to the ATO and possibly your federal representative explaining the uses of multi-platform software and asking for a Java version next year.  Snail mail is generally more listened to than email.  A phone call or personal visit might even help.

Cheers all.

Luke.

---

### Post by mctavish on 2005-08-07
Very nice. I'd only make one suggestion, to reverse steps 10 and 11.  :) 

In a similar vein I've been trying to gee up HSBC Australia over the telephone every now and then about their lack of support for internet banking for firefox on linux with limited success. A frustrating experience.

---

### Post by ltmon on 2005-08-07
[QUOTE=mctavish]Very nice. I'd only make one suggestion, to reverse steps 10 and 11.  :) 

In a similar vein I've been trying to gee up HSBC Australia over the telephone every now and then about their lack of support for internet banking for firefox on linux with limited success. A frustrating experience.[/QUOTE]

Is it just a user agent problem?

I had to change my user agent settings to get Konqueror to work with Commonwealth Bank -- it used to get into an infinite loop until I did this!!!  With the user agent changed it works perfectly.

L.

---

### Post by mctavish on 2005-08-07
Yeah, pretty sure I tried that a while back. Thanks anyway.  :)

---

### Post by [pl]ice on 2005-08-09
thanks, i was about to got to my mates pc to do the tax :0)

---

### Post by strikeforce on 2005-08-09
My understanding is that two problems exist.

1. You can't print the form afterwards.
2. You can't send the form afterwards.

Thats according to whingepool anyways.


*Edit NM I just read the above properly.

---

### Post by ltmon on 2005-08-09
[QUOTE=strikeforce]My understanding is that two problems exist.

1. You can't print the form afterwards.
2. You can't send the form afterwards.

Thats according to whingepool anyways.


*Edit NM I just read the above properly.[/QUOTE]


I didn't try getting printing to work.  Anyone who knows how to print from wine, and can test this please let me know.

L.

---

### Post by drummer on 2005-08-09
[QUOTE=ltmon]I didn't try getting printing to work.  Anyone who knows how to print from wine, and can test this please let me know.

L.[/QUOTE]
 sudo apt-get install libwine-print

never tried it, but it looks like what you need.

---

### Post by flabdablet on 2007-07-23
Just completed my 2006/07 tax return online using Feisty, and it was a lot more straightforward than it apparently was two years ago.  Here's what I did:

[LIST=1]
[*]Installed msttcorefonts (1.8ubuntu1) and wine (0.9.41-0ubuntu2~feisty1) with Synaptic.
[*]Downloaded the e-tax 2007 installers from the ATO website.
[*]Right-clicked on the main installer (e-tax2007_1.exe) in Nautilus and added wine as a custom Open With handler for DOS/Windows executables.
[*]Accepted all the installer defaults.
[*]Double-clicked the remaining installer modules (etax2007_2_docs.exe, etax2007_2_cgtdll.exe, etax2007_2_ftbdll.exe) in turn.
[*]Double-clicked the e-tax 2007 Wine icon on my desktop, and was up and running.
[/LIST]
I was able to complete and lodge my 2006/07 return, including rolling over last year's after browsing to find the archived copy in /media/stephen/e-tax/ST2006.TAX, with only one slightly disconcerting issue: at the point of lodgement, the main e-tax window becomes unresponsive right after clicking Next.  Turns out that there's a pop-under that should be a pop-up, reminding you to establish an Internet connection.  Revealing that, and dismissing it with OK, makes everything work (this pop-under occurs about three times, if I remember right).

Didn't have to install IE.

Didn't try to print my return (got no printers installed on this laptop) though the print preview works fine.

Full marks to the Wine team for this one! :KS

---

### Post by kvonb on 2007-07-23
Nice one ltmon, well done.

I'll give this a try in the next few days, I tried to use a vmware etax last year and it did everything but actually lodge right at the end......grr!

On a side note, are you the same ltmon on the node ET servers?  If so you might know me as (FKQ)Ubuntu-42 :)

---

### Post by hairywombat on 2007-10-31
> Just completed my 2006/07 tax return online using Feisty, and it was a lot more straightforward than it apparently was two years ago. Here's what I did:

   1. Installed msttcorefonts (1.8ubuntu1) and wine (0.9.41-0ubuntu2~feisty1) with Synaptic.
   2. Downloaded the e-tax 2007 installers from the ATO website.
   3. Right-clicked on the main installer (e-tax2007_1.exe) in Nautilus and added wine as a custom Open With handler for DOS/Windows executables.
   4. Accepted all the installer defaults.
   5. Double-clicked the remaining installer modules (etax2007_2_docs.exe, etax2007_2_cgtdll.exe, etax2007_2_ftbdll.exe) in turn.
   6. Double-clicked the e-tax 2007 Wine icon on my desktop, and was up and running.

I was able to complete and lodge my 2006/07 return, including rolling over last year's after browsing to find the archived copy in /media/stephen/e-tax/ST2006.TAX, with only one slightly disconcerting issue: at the point of lodgement, the main e-tax window becomes unresponsive right after clicking Next. Turns out that there's a pop-under that should be a pop-up, reminding you to establish an Internet connection. Revealing that, and dismissing it with OK, makes everything work (this pop-under occurs about three times, if I remember right).

Didn't have to install IE.

Didn't try to print my return (got no printers installed on this laptop) though the print preview works fine.

Full marks to the Wine team for this one!

I'm running Gutsy and just did exactly what 'flabdablet' did. I did have a brief look at printing but with 30mins to the ATO deadline and no real need to print it I didn't investigate.

I had the same issue with the pop-under.

e-tax + WINE + ubuntu.... I'm impressed

---

### Post by thrice_loved on 2008-01-24
Just 'thirding' the above posts.

I installed wine and the msttcore fonts, then downloaded E-tax from the site and right clicked on the .exe and opened in wine.

No problems, it installed and ran without glitching or stopping or anything like that. On the downside it was quite slow for such a little program and the occasional pop-ups did come up underneath (just move the main window and click ok).

E-tax was going to be the only reason that I would need a Windows comp this year - now I don't even need one for that.  Full points to WINE and Ubuntu for this!

---

### Post by zombiepig on 2008-07-02
I've been trying to use etax 2008 with Hardy & Wine 1.1. Basically it install without any issue, and loads up and looks to be working ok, but after a few pages of questions I can't proceed past the "pre-filing" page. Regardless of what options I select on this page, nothing happens. I'm curious to know other's experiences with 2008!

---

### Post by sml on 2008-07-04
> **zombiepig said:**
> I can't proceed past the "pre-filing" page.

Same problem for me!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12814&iTestingId=28039](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12814&iTestingId=28039)

---

### Post by pcjunkie on 2008-07-17
Use an accountant. You pay $90 for it, but get an extra 300....
etax does not allow for certain legal deductions that you can make regardless.

---

### Post by darkrose0510 on 2008-07-22
> **sml said:**
> Same problem for me!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12814&iTestingId=28039](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12814&iTestingId=28039)

If you go to that link it tells you that you need to install msxml4, and how to do it. Once you do you'll be able to get past pre-filling and finish your tax return...

---

