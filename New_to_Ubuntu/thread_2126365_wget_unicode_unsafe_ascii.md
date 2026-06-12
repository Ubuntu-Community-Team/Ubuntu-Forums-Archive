---
title: "wget unicode unsafe ascii"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-03-16
I used wget to download some stuff from a website.
Unfortunately it downloaded everything in ascii.
When I check the info page it said something about safe mode.
But a search of the info and man files for wget doesn't show the word "unicode".


Can anyone help me? How do I force wget to save stuff in the original unicode or code of the website being saved?

---

### Post by schragge on 2013-03-16
You should have searched for "UTF-8" instead :).

---

### Post by Kevin McCready on 2013-03-16
Thanks for the hint schragge, but could you help me a bit more.

In info I found 
 --remote-encoding=encoding
           Force Wget to use encoding as the default remote server encoding. 
but this seems not to apply to my system

When I tried
wget -r -remote-encoding=encoding [website]
I got an error.

Maybe I should edit the .wgetrc  file, but I can't find it

---

### Post by schragge on 2013-03-16
You should specify the actual encoding, e.g.
```
wget -r --remote-encoding=UTF-8
``` The encoding is what you see in the HTML sources in the line [html]<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />[/html]

---

### Post by Kevin McCready on 2013-03-16
Thanks again.
I tried it but I'm still getting:
ç¬¬åå&#8250;&#382;ã&#8364;&#8364;å°½æ&#339;&#8240;ç&#8249;&#8218;è¨&#8364;å®¹æ&#8226;°å* æ¯ä»&#381;é«&#732;ä¼&#353;å&#381;&#8226;è¯¸å&#8230;¬
instead of unicode.

---

### Post by Kevin McCready on 2013-03-17
I tried
 wget -r --local-encoding=UTF-8
but that didn't work either.
Still hoping someone may be able to help.

---

### Post by Impavidus on 2013-03-17
The linux default is Unicode in UTF-8 encoding. That one is backwards compatible with ascii in the sense that any 7-bit ascii text will be encoded in exactly the same way in UTF-8, such that any ascii text will be loaded correctly when interpreted as UTF-8.

If the stuff you download is not ascii but, for example, windows-1252 or UTF-16 encoded Unicode, it is unlikely that you get valid UTF-8. It would probably produce boxes or question marks. Maybe the program you use for viewing your stuff is misconfigured to interpret it as an 8-bit encoding, like latin-1, whilst your stuff really is Unicode in something else than the latin alfabet. That would give you valid gibberish.

The problem may be in your viewer. Try to reconfigure it.

---

