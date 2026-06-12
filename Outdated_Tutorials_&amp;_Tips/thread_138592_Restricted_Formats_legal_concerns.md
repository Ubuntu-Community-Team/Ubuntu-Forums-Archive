---
title: "Restricted Formats legal concerns"
date: 2006-03-02
forum: Outdated Tutorials &amp; Tips
---

### Post by thibaud on 2006-03-02
Hello everybody, I just read ubuntu's wiki on [Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats") and I have a few questions. 

First on USA's law. The Wiki says:> If you live in a country where it is legal, you can enable MP3 playback in the Ubuntu
Is it legal in the USA ?

Same questions with the win32codecs: is it legal in the USA ? Does having a windows license make any difference ?

Here is another question. I noticed that when you install Java by hand, you accept some kind of license. But if you just apt-get, you don't see any license.  So is it legal to offer Java through apt-get ?

I'd like to keep my Ubuntu legal. Please help.

---

### Post by towsonu2003 on 2006-03-04
[QUOTE=thibaud]I'd like to keep my Ubuntu legal.[/QUOTE]
no worries, ubuntu is legal in the rest of the world. 

as for the us worries, if u aren't sure about legality, better not installing packages you're suspicious of. if their distribution is illegal in the us, their maintainers will send a cease and desist letter to ubuntu -again, no worries.

---

### Post by Iandefor on 2006-03-04
[quote=thibaud]Hello everybody, I just read ubuntu's wiki on [Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats") and I have a few questions. 

First on USA's law. The Wiki says:
Is it legal in the USA ?

Same questions with the win32codecs: is it legal in the USA ? Does having a windows license make any difference ?

Here is another question. I noticed that when you install Java by hand, you accept some kind of license. But if you just apt-get, you don't see any license.  So is it legal to offer Java through apt-get ?

I'd like to keep my Ubuntu legal. Please help.[/quote] w32codecs are not legal in the US. If you pay for a legal codec, then yes, you can use mp3 on Ubuntu. And it's legal to offer Java via apt; it's in multiverse, which means it isn't Free. But the license it available through Java.

---

### Post by az on 2006-03-04
[QUOTE=thibaud]Hello everybody, I just read ubuntu's wiki on [Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats") and I have a few questions. 

First on USA's law. The Wiki says:
Is it legal in the USA ?[/QUOTE]
Yup.

[QUOTE=thibaud]
Same questions with the win32codecs: is it legal in the USA ? Does having a windows license make any difference ?[/QUOTE]

Those codecs are not licenced for redistribution.  In that respect, they are stolen.  They are free of charge, in general, but there are term to their redistribution that are not compatible with free-libre software.  

That's why some distributions distribute them and others don't.  Some pay the owners of the codec the licencing fees.  Ubuntu follows the Debian Free Software Guidelines - Ubuntu will never distribute those codecs unless they are licenced in a way which is compatible with the DFSG.


[QUOTE=thibaud]
Here is another question. I noticed that when you install Java by hand, you accept some kind of license. But if you just apt-get, you don't see any license.  So is it legal to offer Java through apt-get ?

I'd like to keep my Ubuntu legal. Please help.[/QUOTE]

You have to agree to the licence when you install j2re from apt.  Where did you get your java package?

Sun licences java in a way that prohibits you from redistributing it if you also distribute other java implementations (lie all the free-libre ones).  Again, that is against the DFSG and evil.  That's why there is no Sun java in the repos.

---

### Post by christooss on 2006-03-04
I hope new mp3 solution (news about new licensing was posted few months ago) will bring them in to Ubuntu.

But for me "advanced" user it really doesn't matter if support for mp3s has to be in multiverse.

But for now on use OGG

---

