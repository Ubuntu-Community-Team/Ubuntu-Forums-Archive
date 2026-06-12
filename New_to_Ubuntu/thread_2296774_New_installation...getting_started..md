---
title: "New installation...getting started."
date: 2015-09-28
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-09-28
Hello Ubuntu community.  I've officially made the leap and installed the current Desktop LTS over the weekend.  Dabbled with it a bit and have some tuning questions:

1) The sound, works just fine on both my speakers and headset.  The volume however is painfully low.  Within the GUI I have the setting maxed.  I even clicked the booster that adds (but distorts) the sound.  Is there a tip for adjusting sound more effectively?

2) I'm new to the command prompt (and Linux-Type OSs in general).  With regards to my mouse, I noticed it is FAR FAR too sensitive.  It moves way to fast and is very twitchy.  I researched that perhaps I needed to adjust the acceleration using xinput.  That worked just fine but I sense that after the reboot it didn't stick.  Is there a best practice for handling this?
 - an extra credit question.  Do these adjustments carry over into a game launched with wine?

3) I spent 2 hours trying to get my Brother 7360N MFC printer working.  I believe I even downloaded the correct driver since it didn't seem to be in the PPE/PPD (sp?).  Anyway, it's an older printer and connected direct to my router.  My windows os found it in the past.  I was bummed I couldn't get it squared away within Ubuntu.

I'm 99% confident my challenges thus far are directly related to my lack of expertise.  So I'm open and an patient with a strong desire to learn it.  =)

Appreciate the support!

---

### Post by yancek on 2015-09-28
You have three distinct questions, try keeping them separate, meaning a separate post for each.  Have you tried modifying things in the System Settings for your sound problem?  Same for the mouse problem.  Where did you get the driver for your Brother printer, can you post a link?

---

### Post by eddiefiggie on 2015-09-28
> **yancek said:**
> You have three distinct questions, try keeping them separate, meaning a separate post for each.   

I see your point.  Sure thing, I'll ensure to keep questions in their own searchable thread going forward.  Thanks.

> **yancek said:**
> Have you tried modifying things in the System Settings for your sound problem? Same for the mouse problem.   

Yes, I've definitely tinkered with the System Settings.  With regards to sound, it's maxed out and barely loud enough.  I mentioned there I even used the "boost" that increases it a little further.  With regards to the mouse, I have the mouse speed at 0% and it's still, way too fast.  I did some research and found the means to deactivate/adjust the mouse acceleration with xinput, but it didn't appear to retain that adjustment on a system restart.  I was curious as well, if the mouse and sound settings carry over to applications that are leveraging wine.



> **yancek said:**
> Where did you get the driver for your Brother printer, can you post a link?   

I ultimately found the driver here:

[http://support.brother.com/g/b/downloadtop.aspx?c=us_ot&lang=en&prod=mfc7360n_all](http://support.brother.com/g/b/downloadtop.aspx?c=us_ot&lang=en&prod=mfc7360n_all)

---

### Post by Geoffrey_Arndt on 2015-09-28
Here's a promising thread from "askUbuntu" . . . seems very doable but will involve a bit of upfront work (suggest you print the instructions).

[http://askubuntu.com/questions/491691/printer-brother-mfc-7360n-cant-print-on-lan](http://askubuntu.com/questions/491691/printer-brother-mfc-7360n-cant-print-on-lan)

As a side note . . . (for future reference . . . it's MUCHO easier to install drivers for all HP and 90% of Epson printers.   There are a ton of Brother drivers for Linux at "openprinting.org" but not for you specific model . . . although sometimes installing another Brother driver that's close in number series can work with some experimenting.   But best bet is to try the askubuntu link first.

---

### Post by cariboo on 2015-09-28
For your audio level problems, have a look at alsamixer, make sure the levels are set high enough. Once you are happy with the settings, store the setting using the following command:

```
sudo alsactl store
```

---

### Post by eddiefiggie on 2015-09-29
> **cariboo said:**
> For your audio level problems, have a look at alsamixer, make sure the levels are set high enough. Once you are happy with the settings, store the setting using the following command:

```
sudo alsactl store
```

That worked great!  Thanks so much.

----------------------------

Still struggling with the Printer.  I'll attempt round two with the recommendations made earlier in this thread.

---

