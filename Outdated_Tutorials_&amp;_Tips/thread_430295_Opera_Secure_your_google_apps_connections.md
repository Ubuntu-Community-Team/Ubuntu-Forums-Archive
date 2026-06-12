---
title: "Opera: Secure your google apps connections"
date: 2007-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by wildkarde on 2007-05-02
After the release of Speed Dial feature on the new Opera, i dumped FIrefox for it.  One of my favorite features of Firefox was Greasemonkey.  Opera has a very similar feature called Userjs.

This greasemonkey script will work on Opera and will redirect all http connections from gMail, gCal, gReader and gDocs to https.

Just thought I'd share this. :)

[http://userscripts.org/scripts/show/5951](http://userscripts.org/scripts/show/5951)

---

### Post by derekguy on 2007-05-14
Sorry I am a bit of a n00b but I use Opera as my browser of choice. How do you use the greasemonkey script? Opera's User JS is in 

[CENTER]Tools > Preferences > Advanced > Content > JavaScript Options[/CENTER] 

right? Where should I save the script files and what filetype should they be? The firefox script is .xpi but I figured it might be .js or .java 

Cheers for any help,
Derek

---

### Post by Colonel Kilkenny on 2007-05-15
> **derekguy said:**
> Sorry I am a bit of a n00b but I use Opera as my browser of choice. How do you use the greasemonkey script? Opera's User JS is in 

[CENTER]Tools > Preferences > Advanced > Content > JavaScript Options[/CENTER] 

right? Where should I save the script files and what filetype should they be? The firefox script is .xpi but I figured it might be .js or .java 

Cheers for any help,
Derek
I use my own config as an example.
I created a directory /home/*username*/.opera/jscripts and told Opera to use it as UserJS-dir (you mentioned the correct place for this setting in your post). And then just download scripts (.js-files) to /home/*username*/.opera/jscripts. I'm not quite sure if it requires opera restart after downloading script to make it work, I think plain refresh is enough and no restart is needed.

---

