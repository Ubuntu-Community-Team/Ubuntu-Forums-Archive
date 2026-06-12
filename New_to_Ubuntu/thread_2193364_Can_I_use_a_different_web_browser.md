---
title: "Can I use a different web browser?"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by tomwethern on 2013-12-12
Help - here is what I have - HP Pavillion Chromebook 14 2gig, Intel, NOT 4G.  Installed Ubuntu via Crouton and use XFCE.
  
Here is my problem..  I want to use this machine for a job search.  Thus I need (and have up and running) libreoffice (google docs does not play nice with microsoft office and don't want to send resume etc., from google docs).  The default web browser in XFCE is not to my liking.  Sure, I could just ctrl alt < to get to chrome but my docs in Libreoffice are not in my google drive (maybe I should focus on getting the libreoffice to talk to google drive perhaps a better solution??  Or dropbox for that matter - have DBox and GDrive but don't know how to save from LOffice in Linux xfce to such).

Thinking I need a different broswer in my xfce setup so I can navigate to my libreoffice files and attache cover letter / resume to online job applications I make at different websites.

Installed firefox (sudo apt-get install firefox).  Seemed to work but I can't find Firefox anywhere or make it my default browser.

Thanks for any suggestions or help with either (firefox solution in xfce - or libreoffice save docs to dropbox / google drive).

TW

---

### Post by newbie-user on 2013-12-12
You could open a terminal and type "firefox" at the prompt to start firefox. Otherwise you can download and install chrome. I haven't touched xfce in a few years, but I believe you can edit the menus and add your own launcher for firefox.

---

### Post by philinux on 2013-12-12
Xfce change default apps.

[http://docs.xfce.org/xfce/exo/preferred-applications](http://docs.xfce.org/xfce/exo/preferred-applications)

---

### Post by tomwethern on 2013-12-12
Thanks for replying...  even though I installed firefox without error message via terminal using sudo apt-get install firefox, I can't find it on my machine.  Pluged in external drive for storage of libreoffice docs - then switch to chromebook - chrome browser and go on my way.  Still learning.  TW

---

### Post by Frogs Hair on 2013-12-12
Open the main menu from settings > main menu and see if the box next to Firefox is checked . This would be in the Internet category. Once the box is checked it should be viable in the application menu, but  you may have to logout-in. Check for it under Internet on the application menu as well.

---

### Post by nothingspecial on 2013-12-12
This is linux, you can use whatever you like ........................ so long as it is compatible .....

---

### Post by ptn107 on 2013-12-12
[URL="https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb"]_Google Chrome 64-bit_
[/URL]
[_Google Chrome 32-bit_]("https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb")

---

### Post by berninghausen on 2014-02-06
Software Center, remove Firefox.  Google Chrome, install google-chrome (not the same as chromium).  Assign Chrome as default or preferred app.  Problem solved.

---

### Post by Votlon on 2014-02-07
I found that google chrome was more responsive on webpages when i was using "Inspect Element" which makes me sad :( but whats the real difference between chromium and google chrome?

---

### Post by SeijiSensei on 2014-02-07
Chrome is proprietary and closed-source; chromium is open.  Chrome is chromium with the proprietary bits added and distributed as a binary blob without source.

Some people are concerned that Chrome might be sending their personal information to Google  Here is the [official description](https://www.google.com/intl/en/chrome/browser/privacy/) of how Chrome treats your privacy.

---

### Post by Votlon on 2014-02-07
Well that's eye opening ill look into use chromium instead.

---

