---
title: "Word Processor"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by Kevin McCready on 2014-03-07
I've been happy with Linux for a couple of years now.

But now I find myself needing to do more serious word processing than I've done for a while.

Something is going wrong when I try to cut and paste pictures from one place to another (please don't tell me to save the pic file separately and insert it, as that wastes too much time).

The problem occurs with abiword and libreoffice.

I tried lyx, but that doesn't suit. A while ago I also tried kword which crashed all the time.

Any suggestions?

---

### Post by Rex Bouwense on 2014-03-07
Give us some details about your problem and perhaps someone can provide you with a solution or a work around.

---

### Post by Kevin McCready on 2014-03-07
While browsing the web, if I right click and copy a picture, it is saved in the buffer. 

I can paste it into Pinta
I can't paste it into abiword.
I can paste it into libreoffice, but for some reason, occasionally libreoffice also doesn't allow me to paste it.

---

### Post by nunecas123 on 2014-03-08
What's the popup when you try to paste it into Libreoffice? I never had similar problems with Libreoffice.
Try SoftMaker FreeOffice. ;)

---

### Post by Vladlenin5000 on 2014-03-08
... or Kingsoft Office ;)

---

### Post by kurt18947 on 2014-03-08
I was using SWMBO's machine with 12.04.3 installed.  I noticed the same behavior with LibreOffice.  I couldn't right-click-copy an image from a web page and paste it into a libreoffice page.  Saving an image via screenshot, save to clipboard then paste does work on her machine.  So did clicking on an image, saving as a .jpg file then importing into LibreOffice. 

 I'm running 14.04 Ubuntu-Gnome on this machine, the office suite is LibreOffice 4.2.1.1.   I just tried right-click-copying an image from a few different web sites and pasting the image  into a libreoffice writer page.  The images have pasted as expected.  I wonder if something in the most recent version of one or both has made the image copy/paste function work as expected?  Of course this may fail tomorrow, one of the 'joys' of using developmental software.

---

### Post by Kevin McCready on 2014-03-08
In libreoffice there is no message at all when it fails to paste. It just doesn't paste. It's a variable fault. If I shut the system and restart, it works OK for a while. Abiword just crashes. Kingsoft? Joke? Not in repos.

---

### Post by Vladlenin5000 on 2014-03-09
No, not a joke. Kingsoft Office is probably the best alternative office suite - actually it could be argued that the (in)famous suite from Redmond is the alternative one because the guys from Beijing and Zhuhai Kingsoft Office started this project back in 1988 :guitar: - and it's the one with the best compatibility with the new proprietary formats. Here's some news from their recent incursion on Linux: [http://www.omgubuntu.co.uk/?s=kingsoft](http://www.omgubuntu.co.uk/?s=kingsoft)

---

### Post by mastablasta on 2014-03-09
it doesn't seem like the issue is with wordprocessor. if could be something with "clipboard" tool in lubuntu. so i would say rather than going through and trying all available office programs i woudl say try a different clipbaord tool. somethign from gnome or KDE perhaps.

---

### Post by Vladlenin5000 on 2014-03-09
> **mastablasta said:**
> it doesn't seem like the issue is with wordprocessor. if could be something with "clipboard" tool in lubuntu. so i would say rather than going through and trying all available office programs i woudl say try a different clipbaord tool. somethign from gnome or KDE perhaps.

I agree entirely. I just mentioned the alternative following the previous post but without much regard to the actual problem.

---

### Post by Kevin McCready on 2014-03-09
Thanks Guys

I'm at a bit of a loss as to which program/s to try.
Here is my system:
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux k-Presario-CQ57-Notebook-PC 3.2.0-60-generic-pae #91-Ubuntu SMP Wed Feb 19 04:14:56 UTC 2014 i686 i686 i386 GNU/Linux

How can I discover what clipboard tool my system uses? In Synaptic when I search for clipboard I notice that some libfm programs are installed.

When I search Synaptic I get programs such as:
glipper, xclip, xsel, parcellite, klipper, clipit etc

Where should I start?

When I install such a program does it automatically takeover from what's already installed? Or does it become the default and If it fails the system moves to the next in line?

---

### Post by mörgæs on 2014-03-09
You are using an unsupported version of Lubuntu.
I suggest a clean install of 13.10 and after that the version of Libre Office found in the repository. Using that I am able to copy and paste without errors.

---

### Post by Kevin McCready on 2014-03-09
thanks

---

