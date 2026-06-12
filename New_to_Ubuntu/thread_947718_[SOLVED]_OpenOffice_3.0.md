---
title: "[SOLVED] OpenOffice 3.0"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by motomick on 2008-10-14
I have been running Ubuntu over 6 months now and I am fairly familiar with figuring how to get it to work well and figure out problems on my own.  But I have run into a reoccurring problem with OpenOffice 3.0.  

I was so excited to get it installed and working, but to find out, the tool bars and menus have the shapes instead of the words.  I ran into this problem when I first installed OpenOffice, but fixed it somehow, but I cannot remember.

If I could read shapes, I would not complain, but I cannot.  

Any help would be greatly appreciated.

---

### Post by o.besner on 2008-10-14
Where did you get OpenOffice ? The way you obtained it might help. Thanks.

---

### Post by Elfy on 2008-10-14
Go to View - Toolbars - Customise - then the Toolbar tab - there is a toolbar button on the right of the customise page - drop down menu - icons, icon+text, text

---

### Post by motomick on 2008-10-14
From this link:

[http://www.openoffice.org/](http://www.openoffice.org/)

I choose the deb package from the US.

---

### Post by fballem on 2008-10-14
> **forestpixie said:**
> Go to View - Toolbars - Customise - then the Toolbar tab - there is a toolbar button on the right of the customise page - drop down menu - icons, icon+text, text

I've attached a screenshot that should show you what you will see in the Customise Page.

If this answers your question, please don't forget to mark the thread as solved. Please use the Thread Options at the top of the page.

---

### Post by motomick on 2008-10-14
forestpixie - 

um, the drop down menus have shapes, no words.  I am used to using "microcrap 2007", and I am not very familiar with this layout.

---

### Post by motomick on 2008-10-14
Thanks for screenshot, it helped alot.  I think I am going in the right direction, but I still have no results.

---

### Post by clive littlewood on 2008-10-14
Hi

It looks like you have a weird font from your screenshot.

Look on the toolbar at the top where the strange sybols are and there should be a menu button at the side.

Click on this button and alter the font.

Should be OK then

cl

OOps. Sorry got the wrong end of the stick !!!

Did you choose the correct language when you installed ?

---

### Post by Elfy on 2008-10-14
Yes, did you get the donwload over the last few days - wehn everyone else was doing so?

I wonder if the download was corrupted at all, anyway try to check that the system font is enabled for user interface - thanks to drs305:) Tools - options, OO.org, view, - you won't be able to read them but you can see which ones from the screenshot

Also check the the language packs are installed in synaptic - openoffice 3 might be under Installed (local or obsolete) look for Language Modules, make sure they are installed properly.

---

### Post by mc4100 on 2008-10-14
Try unticking the "Use System Font for user interface" box in:
```
Tools -> Options; Openoffice.org -> View
```

Edit: forestpixie beat me to it. ;)

---

### Post by motomick on 2008-10-14
here is a screenshot:

---

### Post by Keen101 on 2008-10-14
It is advisable if you are installing open office 3 that you remove older versions first. Maybe two different versions are clashing.

---

### Post by motomick on 2008-10-14
I removed open office 2.4 before even installing, and I checked to make sure it was uninstalled through synaptic.  I tried the options menu, and as you can see from the screenshot, it appears the font is enabled.I also have a second screenshot to show that the language pack is installed.

---

### Post by LowSky on 2008-10-14
might seem dumb but change your theme. i had this odd issue while using Sun's Nimbus Theme that the menues would go blank when I moused over them, maybe that might work Maybe change the font you are using for the system.

---

### Post by motomick on 2008-10-14
Low Sky-

I changed my fonts in System - Preferences - Appearances:Fonts Tab, and changed the application font to something normal like Ariel, I had it on Dingbats!

Guess what, it worked!

Thanks Low Sky!

---

