---
title: "2 Questions: WINE and FACEBOOK"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by mattywarr on 2008-04-22
Hey peeps :)

Got a couple more questions after playing with Ubuntu some more last night.

1. I was trying to play Poker last night using Ladbrokes Poker through WINE. Some of the interface is based upon HTML, and it prompted me to install the WINE Gecko plugin (Or something like that). It installed to 100% then hung, so I exited it. However, the HTML interface in the ladbrokes software still doesn't work, and it doesn't prompt me  to install Gecko again! is there a way I can manually install Gecko for WINE?

2. I tend to use Facebook a lot. One of the things with it is the Image uploader, which is a Java based browser control. I have Java 6 installed but still this won't load. Any ideas?

Thanks guys :)

Matt

---

### Post by SDL on 2008-04-22
For the Facebook uploader, go to:
applications->internet->sun java web start

Leave the Java control panel open whilst you're uploading images and it should be ok.

---

### Post by mattywarr on 2008-04-22
> **SDL said:**
> For the Facebook uploader, go to:
applications->internet->sun java web start

Leave the Java control panel open whilst you're uploading images and it should be ok.

Interesting... Is there any way this can be done to run in the background, or on startup?

---

### Post by billgoldberg on 2008-04-22
Sure.

Go to "system -> preferences -> sessions" and add a new entry.

Give in these thins:

- Java Web Start
- /usr/lib/jvm/java-6-sun-1.6.0.03/bin/java -jar
- java web start

(note the second one can change a bit depending on the version, this is from my computer wich is fully updated, so if yours is to, it should be the same)

That will start java web start on startup.

---

### Post by mattywarr on 2008-04-22
Cheers mate!

---

### Post by Trail on 2008-04-22
Yes, there was a way to install gecko manually. I don't have a link handy though, but you could google it.

If all else fails, I think you can install ie4linux and it includes gecko.

---

### Post by mattywarr on 2008-04-22
Found it!

[http://ohioloco.ubuntuforums.org/showthread.php?t=634464](http://ohioloco.ubuntuforums.org/showthread.php?t=634464) <-- The link in case anyone else has a similar problem.

---

