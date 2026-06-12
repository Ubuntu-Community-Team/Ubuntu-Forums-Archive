---
title: "Adobe Flash Player"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by ewm on 2013-10-28
I have just discovered that Adobe Flash Player ver 11.2 is the last version that will be available for Ubuntu. My Tax efiling needs Ver 11.3.300 to work properly any solution apart from dumping Ubuntu and very reluctantly going back to Windows.
Sorry if this is not the right forum for this subject.

---

### Post by fantab on 2013-10-28
Dual boot Windows and Ubuntu. Install Windows alongside Ubuntu, use windows for your Tax eFiling. 

OR

Install Google Chrome for linux. Google Chrome comes with built in latest flash. See this [HOW TO]("http://tutorialforlinux.com/2013/10/09/how-to-install-google-chrome-on-ubuntu-13-10-saucy-i386amd64-linux-visual-guide/").

---

### Post by monkeybrain20122 on 2013-10-28
Install Chrome if you need the latest flash.  

Dualboot just to use flash seems completely unnecessary, not to mention going back to Windows. If worse comes to worse you can always put Windows in Virtualbox and fire it up just for your taxes.  

P.S. flash 11.2 works for 99% of the sites, I have chrome installed but seldom use it.

---

### Post by Impavidus on 2013-10-28
> **ewm said:**
> I have just discovered that Adobe Flash Player ver 11.2 is the last version that will be available for Ubuntu.Try chrome. For a virtual machine you need a genuine Windows install disk, but you may have one lying somewhere. Dual booting seems overkill, dumping Linux is not necessary.> My Tax efiling needs Ver 11.3.300 to work properly any solution apart from dumping Ubuntu and very reluctantly going back to Windows.
Sorry if this is not the right forum for this subject.I'm so happy my tax service supplies a .deb file.

---

### Post by craig10x on 2013-10-28
Yes...Google Chrome is the answer (not Chromium that is offered in the software center)....Adobe has an agreement to provide the latest flash for Chrome (for Chrome's built in pepperflash plug in)....if you are using firefox, they don't have that and you are using the old flash that was installed on your system when you added Ubuntu Restricted Extras (you are only getting security updates for that)....it's because Adobe no longer makes new flash for linux...with the exception of the agreement that they have Google Chrome...

Just go to Google's website for Chrome, download the proper deb file (64 bit or 32 bit depending on your computer) and open it and click "open in Ubuntu Software Center" and it will install for you in less then 5 minutes...No offense to our firefox fans here, but Chrome is an EXCELLENT browser...;)  It also has a handy built in pdf reader as well...

---

### Post by kurt18947 on 2013-10-28
I bookmarked this just in case I need it.  I have not tried it, not really a Google fan

[Install Pepper Flash Player For Chromium In Ubuntu Via PPA ~ Web Upd8: Ubuntu / Linux blog]("http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html") 

A tax service that uses a program know for its INsecurity?  Hmmmm:rolleyes:

---

### Post by ewm on 2013-10-28
Thanks for all the advice, I do have the latest Flash Version in Chrome but have subsequently discovered that it was an Adobe Reader issue, I needed Adobe X1 for which there does not seem to be a Linux version.
For the time being I have installed Fire Fox and Adobe Reader XI under Wine and everything works. Adobe is only required for me to read feedback from the service.

---

### Post by Baldrick_NZ on 2013-10-29
> **kurt18947 said:**
> I bookmarked this just in case I need it.  I have not tried it, not really a Google fan

[Install Pepper Flash Player For Chromium In Ubuntu Via PPA ~ Web Upd8: Ubuntu / Linux blog]("http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html") 

A tax service that uses a program know for its INsecurity?  Hmmmm:rolleyes:

+1. This works great in Chromium too (from the repos). Current version is 11.9, so should be more than enough for your app. Might even work for Firefox too, as they tend to share same plugins.

---

