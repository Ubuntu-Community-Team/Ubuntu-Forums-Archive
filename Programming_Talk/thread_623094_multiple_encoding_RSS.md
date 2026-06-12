---
title: "multiple encoding RSS"
date: 2007-11-25
forum: Programming Talk
---

### Post by DouglasAWh on 2007-11-25
I've got a situation where I have an RSS feed with Hebrew, Cyrillic, English, Greek, etc.  I can't seem to get it to validate.  Is there a way to have multiple encodings in an RSS feed?  I can't do the encoding at the webpage level because it's pulling in news from various different sites with various different admins.

Any help is appreciated.

---

### Post by LaRoza on 2007-11-25
I don't know anything about RSS, but can you use Unicode?

---

### Post by DouglasAWh on 2007-11-25
UTF-8 is unicode, no?

Feed can be found at [http://www.ibiblio.org/snkahn/feed/](http://www.ibiblio.org/snkahn/feed/).  Make sure you view source to see what is actually going on, cause part of the problem is that it doesn't actually show up...at least not in Firefox.

---

### Post by LaRoza on 2007-11-25
Can you give a link to the site which it is being pulled from? That way I'll be able to see if it is a browser issue.

---

### Post by DouglasAWh on 2007-11-25
The content is all being pulled from various collections hosted on ibiblio.org.  ibiblio hosts lots of stuff, like folkstreams and Groklaw.

As it turns out, the problem is that the HTML entities don't work in XML.  I don't really know how to fix that though.  

Appreciate the help!

---

### Post by horsey on 2007-11-26
Have you checked out HTML Tidy? Something like
```
tidy -xml -utf8 file.rss
```
should replace HTML entities for you.

---

### Post by DouglasAWh on 2007-11-27
Here are some things that have been tried by the primary coder (aka, not me):

utf8_decode() 
utf8_decode() 
html_entity_encode() 
html_entity_decode()

"i think the problem entities are primarily html. i also think the problem could be the way i was trying to feed the array into the functions- these functions all take a string as a parameter, so i appended the array fields all in one line: something like $x[0].$x[1].$x[2] etc"

Would it be helpful to post the code?

---

