---
title: "Please enable Java Message"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Splitshine on 2008-10-18
Hey everyone, 

Firstly: I'm very very new to Ubuntu and the whole linux scene. Decided to cross the border after getting fed up with Windows (not the first and I seriously doubt I'm the last!). So I've got Ubuntu 8.04.1 running and all seems well. 

The problem I'm having now is with Java. 

I've installed Java, as far as I can tell, and it's working with Firefox. If I go to [http://java.com/en/download/help/testvm.xml?ff3]("this test page") to check my Java version it says it's the latest.

I've been to Edit >> Preferences >> Content and checked the boxes to enable Javascript and Java.

However, upon running the Blizzard downloader for World of Warcraft, when the updates are being patched, instead of giving me patch notes, up comes the update box that says "Please Enable Javascript"

So (and you may think "finally..."), do I have to do something additional with Java or is this an issue with Wine (what I'm running for WoW)?

If you need me to post anything let me know!

Thanks in advance

---

### Post by tdrusk on 2008-10-18
Did you install Java for Windows with Wine?

IMO the best way to set up programs is with Wine-Doors.
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

It may even have installers for the game.

---

### Post by Zzl1xndd on 2008-10-18
> **tdrusk said:**
> Did you install Java for Windows with Wine?

IMO the best way to set up programs is with Wine-Doors.
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

It may even have installers for the game.

This is correct, WoW is looking for the Windows version of Java and is unable to find it.

---

### Post by Splitshine on 2008-10-18
That's brilliant guys. Thanks very much for the help and the quick response!!

---

### Post by nautilus on 2010-03-06
I know this is an old thread but... well first of all, Java and JavaScript are two entirely different languages.  JavaScript has almost nothing to do with Java at all, since it is basically a slang name for ECMAScript.

That said, I'm curious how to enable Javascript in the embedded mozilla docview which the Blizzard updater uses?  I'm certain I don't need to install an entire Java runtime, that would be ridiculous.

---

### Post by sandyd on 2010-03-06
> **nautilus said:**
> I know this is an old thread but... well first of all, Java and JavaScript are two entirely different languages.  JavaScript has almost nothing to do with Java at all, since it is basically a slang name for ECMAScript.

That said, I'm curious how to enable Javascript in the embedded mozilla docview which the Blizzard updater uses?  I'm certain I don't need to install an entire Java runtime, that would be ridiculous.
gecko (winetricks or wine-gecko package)

---

