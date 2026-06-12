---
title: "Make FireFox Protocol Handler call Second Life from an SLURL"
date: 2007-09-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Mark_in_Hollywood on 2007-09-23
Clicking a out-world SecondLife link in Firefox should open Second Life. We will do this by configuring Firefox specifically to handle that particular protocol. This modification has a "universal" effect — clicking on a Second Life link in any application will call up the associated program. 

Now, to configure Firefox to handle the SLURL, you'll need to go into Firefox's configuration settings. Do the following:

1. In a blank tab, type about:config. You will be shown a page with a list of Firefox's configuration variables.

2. In the filter field, type network.protocol-handler. This will show a list of protocols handled by Firefox. You may or may not see the secondlife protocol in the list. If it's there, it would look something like network.protocol-handler.external.secondlife. The protocol is probably not there, though, in which case you'll need to add it. First create a Boolean protocol, then a String protocol.

3. To create the configuration setting, right-click on any item in the list and select New > Boolean. In the preference name, type **network.protocol-handler.external.secondlife**, and set the value to true. This tells Firefox to use an external program to handle the secondlife SLURL.

4. Next, create a new string item by right-clicking anywhere on the list and selecting New > String. In the preference name, type **network.protocol-handler.app.secondlife**, and in the value field, type the path to the program you want to use for that protocol (e.g. /home/mark/SecondLife_i686_1_18_3_5_RELEASECANDIDATE/secondlife). Do not use the parenthesis or the punctuation mark following the closing parenthesis.

n.b., I am waiting for the SecondLife Linux programmers to tie the Release Candidate updater to the downloader, so that I don't have the problem of not being able to update the Release automatically. Which means that with each succeeding Release, I have to add another String protocol line to about:config.

5. Restart Firefox and you should be set. If not, reboot and try it again. I had to reboot.

6. Try [http://slurl.com/](http://slurl.com/)
When it's finished loading, click the Orange colored radio button. Firefox should put a menu on the screen asking you if you want to run Second Life. Select Launch Application, if it works by running your SecondLife program, the next time you try it, you can check the "Remember my choice for all links of this type" button.

====================================
Lines needed for copying for this How-To:

network.protocol-handler.external.secondlife

network.protocol-handler.app.secondlife

the path to where your Second Life directory is. Again, by example: /home/yourname/SecondLife

================
URLs Used in this How-To

Explains how to edit about:config

[http://kb.mozillazine.org/About:config#Adding.2C_modifying.2C_and_resetting_preferences](http://kb.mozillazine.org/About:config#Adding.2C_modifying.2C_and_resetting_preferences)

Explains SLURL and about:config
[http://technopaideia.blogspot.com/2007/06/firefox-and-slurls-and-troubleshooting.html](http://technopaideia.blogspot.com/2007/06/firefox-and-slurls-and-troubleshooting.html)
====================================
Thanks to:
[http://basecamphq.com/forum-archive/viewtopic.php?id=1758](http://basecamphq.com/forum-archive/viewtopic.php?id=1758)

Additons and corrections welcomed!

---

### Post by Tsu Dho Nimh on 2007-10-26
Could you link to a loader instead? 

Call the loader, it calls SL? Or wold you lose the TP linking?

---

### Post by Mark_in_Hollywood on 2007-11-10
I have no idea as to how to respond to your post. I'm not a programmer. I came across the instructions and gave credit. If you find that poster, he may be able to answer your questions.

---

