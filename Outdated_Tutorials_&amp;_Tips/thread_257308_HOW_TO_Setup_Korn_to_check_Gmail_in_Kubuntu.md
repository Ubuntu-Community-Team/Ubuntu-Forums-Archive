---
title: "HOW TO: Setup Korn to check Gmail in Kubuntu"
date: 2006-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Obor on 2006-09-14
I have recently decided to get rid of the Gmail checker and start using Korn for both my email accounts. I had a bit of trouble getting it work and I couldn't find much info either. So here is a simple little HOW TO.

1. Install Korn (email checker for KDE)

2. Alt-F2 and run korn

3. In Korn Configuration:
Add name for your box i.e. Gmail in the screenshot.
[IMG]http://ubuntuforums.org/gallery/data/500/configurationbox1.png[/IMG]
Highlight Gmail and click Edit
[IMG]http://ubuntuforums.org/gallery/data/500/configurationbox2.png[/IMG]
Choose icons and behavior when a new email is received. i.e In my screenshot - different icons for no mail and mail plus number of new emails will be written over the icon.

Change tab to Events
[IMG]http://ubuntuforums.org/gallery/data/500/configurationbox3.png[/IMG]
Make it look like the screenshot and paste the following to the Command text box: 
```
/usr/bin/mozilla-firefox http://mail.google.com/mail/
```
Replace /usr/bin/mozilla-firefox with a path to your browser of choice.
This will open your gmail box (if autologin is setup in your gmail) in your browser. You can change the address to the login page if you preffer.

Change tab to Accounts
[IMG]http://ubuntuforums.org/gallery/data/500/configurationbox4.png[/IMG]
Add account Gmail, highlight it and click Edit

Make the Server tab look like this and fill in your login name and password
[IMG]http://ubuntuforums.org/gallery/data/500/configurationbox7.png[/IMG]


In the Account tab change the timing to suit (i.e. 120 secons on mine)
[IMG]http://ubuntuforums.org/gallery/data/500/configurationbox6.png[/IMG]

OK your way out and you almost done.

You should go to your Gmail account settings into Forwarding and POP and enable POP.

Hope this works for you. Screenshots are on Kubuntu 6.06 with KDE 3.5.2 and Korn version 0.4

---

### Post by shanepardue on 2006-12-22
Cool! Any idea how to stop korn from notifying me when I send out emails?

---

### Post by RagonichaFulva on 2008-08-30
The images of the How-To don't appear. Can you write down the data we must put in events and in acount or re-upload the images?

---

