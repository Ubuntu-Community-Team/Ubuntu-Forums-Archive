---
title: "My &quot;supported&quot; printer doesn't work"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Dannyblueyes on 2008-05-25
Yesterday I bought an HP deskjet D2530 printer. According to other threads this printer should work as a plug-n-play with the Huron ubuntu my laptop uses without any problems.

Every time I try to print a page though it doesn't print. Instead the power light starts blinking on and off. 

I thought it might be a driver issue so I installed HPLIP. From what I can gather that's a multi model driver program put out by Hewlitt Packard. Tried printing a test page. This time my computer claims that the page has printed. In reality nothing has printed and the printer's power button is still blinking on and off the same as before. 

Does ANYBODY know how to make this bloody thing do what I paid nearly $100 to make it do?

---

### Post by asrai on 2008-05-25
Ok, I'm happy to try and help, lets start from the beginning.

Are you trying to print over a network or is the printer plugged into your computer by cable? (usb I assume)?

What happens when you type localhost:631 into the address bar of your web browser?

---

### Post by Dannyblueyes on 2008-05-25
I'm connected using a USB cable. entering 'http://localhost:631/' into my firefox address bar takes me to a page called Home - CUPS 1.3.7

I should also mention a new development. The last two items I tried to print, a test open office document and a HP test printing have been 'pending' for the last 11 minutes and 13 minutes respectively. I've rebooted both the computer and the printer and they are still there. I've even tried to cancel these printings and they are still 'pending'. The printer's power light is currently a solid green.

---

### Post by asrai on 2008-05-25
If you click on "manage printers" from the localhost:631 page, does it show your printer?

Is there an option to cancel all jobs? If so, click on it. Let me know what happens from here.

Did you install the printer from the prefs/printer menu or through the HP toolbox?  Can you also tell me if the HP toolbox shows your printer correctly?

---

### Post by sdowney717 on 2008-05-25
[https://answers.launchpad.net/hplip/+question/31209](https://answers.launchpad.net/hplip/+question/31209)
HP DJ D2530 support?

Will there be support for the DeskJet D2530 printer?

Thank you,
-jaime
 Aaron Albright said on 2008-04-29:

We will be supporting the DeskJet D2530 in a future release of HPLIP, however I can't give a specific time frame--although it will be in relative short time.

Thanks for your support of HPLIP.

Aaron

---

### Post by Dannyblueyes on 2008-05-25
> **asrai said:**
> If you click on "manage printers" from the localhost:631 page, does it show your printer?

Is there an option to cancel all jobs? If so, click on it. Let me know what happens from here.

Did you install the printer from the prefs/printer menu or through the HP toolbox?  Can you also tell me if the HP toolbox shows your printer correctly?

I clicked manage printers and yes, my printer was shown (or at least the series was shown) I clicked the option to cancel jobs and the jobs canceled. 

When I first connected the printer I went into preferences and selected it to be my default printer. Both the HP toolbox and the computer correctly identify the printer as the default.

---

### Post by asrai on 2008-05-25
Ok can you try and print a test page from [http://localhost:631](http://localhost:631) ?

There is method to my madness, I promise :)

---

### Post by Dannyblueyes on 2008-05-25
I clicked the 'manage printers' tab and then clicked the 'print test page' tab. The power light on my printer immediately started blinking. According to my HP device manager the print job is continuing. Other than the blinking light though there is no printer activity at all.

---

### Post by asrai on 2008-05-25
Hmm that is interesting.  Can you check which driver it is using (you can check by looking at localhost:631 / manage printers or in the system/admin/printers menu.

---

### Post by Dannyblueyes on 2008-05-25
Okay found it! The driver is HP DeskJet D2400 Foomatic/hpijs, hpijs 2.8.2

---

### Post by Dannyblueyes on 2008-05-26
I figured it out.

First I went into CUPS and canceled all the jobs. Then I went into the HP toolkit and uninstalled the printer. Next I re-installed the printer and asked the computer to autoselect a driver. I noticed that it used HP DeskJet D2500 Foomatic/hpijs, hpijs 2.8.2 which is slightly different from the previous one. I tried a test page and sure enough it worked. 

It's amazing what a stiff drink, a stroll around the block, and some great advice can conquer. Thank you very much for your help and insight. 

BTW, if you ever come to California look me up for a drink.

---

