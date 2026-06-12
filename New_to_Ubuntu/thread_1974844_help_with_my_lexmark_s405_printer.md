---
title: "help with my lexmark s405 printer"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by dsos30 on 2012-05-06
Hi everyone,
 
I'm a newbie Im using ubuntu 12.04 and Im trying in install my lexmark s405 printer, but there's no drivers for it? please can you help me anyone........................?:confused:

---

### Post by Cheesemill on 2012-05-06
Try the drivers for Ubuntu 11.04 and see if they work:
[http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_INTERPRET_S405](http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_INTERPRET_S405)

---

### Post by dsos30 on 2012-05-06
Thanks mate I will try it.........:)

---

### Post by Rulius on 2012-09-20
I have installed the drivers for 12.04 from support.lexmark.com, but they don't seem to work. 
I went to system settings > printing and followed the steps, the printer was identified but when I right click > properties it doesn't let me press the "print test page" button. Also, I tried printing a pdf and a doc file with no success.

Finally, I tried to update the firmware from support.lexmark.com, but their page doesn't seem to work properly: the necessary Firmware Download tool doesn't appear on the page.

 ](*,):???:

---

### Post by pissedoffdude on 2012-09-20
> **dsos30 said:**
> Hi everyone,
 
I'm a newbie Im using ubuntu 12.04 and Im trying in install my lexmark s405 printer, but there's no drivers for it? please can you help me anyone........................?:confused:

Did you try the PPD for cups?  Make sure you download the correct PPD (either 32-bit or 64-bit), then open up the printing preferences, add a printer, and when it asks for a driver, manually select the PPD, and a test page should print afterwards

Since it comes in a deb file, see if you can extract the deb, then extract the data.tar.gz.  The PPD is in usr>local>lexmark>v3>etc

---

### Post by Rulius on 2012-09-29
Hi pissedoffdude and thanks for the reply,

I followed your advise to manually direct to the ppd and now I'm able to click on the print test page, but still nothing prints. I open the print queue and it says "Processing" for a few secs and then "Stopped". Same thing when I try to print a doc.

So now I get "Stopped" instead of "Canceled" that I was getting before and I'm still not able to print.

Any ideas?

---

### Post by samataz on 2012-12-30
> **Rulius said:**
> Hi pissedoffdude and thanks for the reply,

I followed your advise to manually direct to the ppd and now I'm able to click on the print test page, but still nothing prints. I open the print queue and it says "Processing" for a few secs and then "Stopped". Same thing when I try to print a doc.

So now I get "Stopped" instead of "Canceled" that I was getting before and I'm still not able to print.

Any ideas?
Dear all,
Drivers and printing seems to work ok on kubuntu-12.04 though.  I had the exact problems when working on linuxmint nadia.
I'll get back to check on another version.

---

### Post by Rulius on 2012-12-30
The problem still remains for me.
I print rarely, but when I do the only thing that works at the moment is virtual box and win7. :oops:

---

### Post by Rulius on 2013-02-05
I finally managed to make the printer work in the following way:

Used  a windows pc to update the firmware of the printer. (I couldn't update  the firmware with ubuntu as there was no communication between the  system and the printer and with virtual box: even though I could print,  when running the update firmware exe file the printer couldn't be found -  I only use usb connection)

Anyway after updating the firmware of the printer and reinstalling the drivers from Lexmarks site, it is now working.

---

### Post by base808 on 2013-06-29
Which firmware version did you use? I've tried a couple, but still no luck. It says processing but never does, then stopped.

---

### Post by base808 on 2013-06-29
Sweet!!!! So i was able to get it to print to doing a search from terminal (find / -name "*400*.ppd" -print) for .ppd file and once i found (lxS300-S400.ppd) the location, I created a new printer setup and used the option to select that .ppd file (thanks pissedoffdude!!!). Saved it and printed a test page and it worked!!!! Didn't do at first when i saw that Rulius and I had the same issue, but selecting the .ppd file didn't seem to help him solve his issue.

Note: You may find more than one lxS300-S400.ppd file. Try them all. The first one i used worked for me, but try all of them.

---

### Post by Rulius on 2013-06-30
[http://support.lexmark.com/index?page=product&locale=en&productCode=LEXMARK_INTERPRET_S405&segment=SUPPORT&userlocale=EN](http://support.lexmark.com/index?page=product&locale=en&productCode=LEXMARK_INTERPRET_S405&segment=SUPPORT&userlocale=EN)

I think it was type r. The version difference is related with the wireless feature, which I'm not using anyway.

Cheers

---

### Post by elatre on 2014-06-16
Could you please share the file lxS300-S400.ppd? I can't find it at lexmark.com anymore.
Thanks!

---

