---
title: "no sound for flash videos"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by Rfdp on 2012-12-23
I use Firefox 17.0.1 and Chromium [COLOR=#303942][FONT=Ubuntu]20.0.1132.47[/FONT][/COLOR] on a Ubuntu 12.04 64-bit version.

Until yesterday all flash videos worked fine, but after I followed these [https://sites.google.com/site/easyli...roject/firefox]("https://sites.google.com/site/easylinuxtipsproject/firefox") instructions, I have no sound on either Firefox or Chromium.

I tried to install gnash instead, which didn't help, and used Flash-aid 2.2.3, but the problem remains the same.

about:razz:lugins shows shockwave as well as Java, VLC an  QuickTime plugin. Should I remove any of these? How (if Flash-aid didn't do it)?

What else could I try to get the audio working again for flash?
Thanks for the help


Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-35-generic
GNOME 3.4.2

---

### Post by Rfdp on 2012-12-23
"dpkg -l | grep -i flash"   shows even more plugins installed - how do I get rid of those?



ii  adobe-flash-properties-gtk             11.2.202.258-0precise1                  GTK+ control panel for Adobe Flash Player plugin version 11
ii  adobe-flashplugin                      11.2.202.258-0precise1                  Adobe Flash Player plugin version 11
ii  browser-plugin-gnash                   0.8.10-5ubuntu1                         GNU Shockwave Flash (SWF) player - Plugin for Mozilla and derivatives
rc  flashplugin-installer                  11.2.202.258ubuntu0.12.04.1             Adobe Flash Player plugin installer
ii  flashplugin-nonfree-extrasound:i386    0.0.svn2431-3ubuntu1                    Adobe Flash Player platform support library for Esound and OSS
ii  gnash                                  0.8.10-5ubuntu1                         GNU Shockwave Flash (SWF) player
ii  gnash-common                           0.8.10-5ubuntu1                         GNU Shockwave Flash (SWF) player - Common files/libraries

---

### Post by Open and Sourced on 2012-12-23
Did you configure your speakers? This may be a disturbance with something else. Not the web browser.

---

### Post by Rfdp on 2012-12-23
Thought so too, but I can hear music/ movies with VLC Media Player

---

