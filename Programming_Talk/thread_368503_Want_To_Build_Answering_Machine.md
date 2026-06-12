---
title: "Want To Build Answering Machine"
date: 2007-02-23
forum: Programming Talk
---

### Post by SuperMike on 2007-02-23
I want to take Ubuntu Server on an old PC, put a modem card in it, and turn it into an answering machine that does voice recognition and then serves it up on a mail server. I take it that I'll need to glue together some components with programming scripts. How would I achieve this?

---

### Post by PilotJLR on 2007-02-23
TrixBox can do all of this except the voice recognition. I have no idea how that would be accomplished.

[http://www.voip-info.org/wiki/view/Asterisk%40Home+Handbook+Wiki+Chapter+8#812VoiceMail](http://www.voip-info.org/wiki/view/Asterisk%40Home+Handbook+Wiki+Chapter+8#812VoiceMail)
[http://asteriskathome.sourceforge.net/](http://asteriskathome.sourceforge.net/)

---

### Post by Tomosaur on 2007-02-23
Think you should forget about voice recognition - it's an incredibly complex challenge. Surely you've seen the Microsoft demonstrations - and how badly wrong it can go?

---

### Post by SuperMike on 2007-02-23
Well, the voice recognition thing would be a best effort and only on my house line. I'd like to at least attempt it. I could take like three trained versions of it -- one for kid, adult woman, adult man -- and see which one generates the largest count of recognized words from it when filtered through ispell. Then, I could use that particular interpretation on that particular message. Whatever drops off, oh well. Over time I could tweak it to increase accuracy.

---

### Post by Tomosaur on 2007-02-23
Well, it's up to you :P
I don't know of any libraries or tools which could provide you with the flexibility you'll require for this, but I'd certainly be interested to see how you progress. If you can find an open-source library for this, even better - I'm sure many people here would be interested.
Best of luck :)

---

### Post by SuperMike on 2007-02-23
This link looks useful:

[http://www.voip-info.org/wiki-Sphinx](http://www.voip-info.org/wiki-Sphinx)

---

### Post by Tomosaur on 2007-02-23
Thanks for the link, I'll take a look.

---

