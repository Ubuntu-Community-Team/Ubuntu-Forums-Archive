---
title: "Evolution changes mail encoding"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Chinjuu on 2008-06-05
Hey guys. I'm new to Ubuntu (and the forum) and I'm loving it already. :)

I'm having a bit of a problem with the Evolution mail client. When I try to send e-mail in the ISO-2022-JP charset, Evolution _sometimes_ (not always) changes the encoding to UTF-8 without notifying me. This is frustrating because many mobile phones are unable to decipher UTF-8.

The reason for this misbehaviour may be that Evolution detects in the e-mail message a character which is not present in the selected charset. In practice, however, I have not been able to identify the offending character(s) even after sending the message.

Should I file a feature request (how?) to rectify the problem?

---

### Post by ZabiGG on 2008-06-05
This post is very old, but it might help you solve your problem. 

[http://ubuntuforums.org/showthread.php?t=162084](http://ubuntuforums.org/showthread.php?t=162084)

I sincerely hope it helps,

Z.

---

### Post by Chinjuu on 2008-06-06
Hi ZabiGG and thanks for replying!

In the thread to which you kindly linked, the OP had missed the Character set option in Composer preferences. My problem is somewhat different.

I do have the Character set in Composer preferences set to ISO-2022-JP, which is the way I want it. The problem is that in some cases Evolution **overrides** this setting and sends the message in UTF-8.

---

### Post by ZabiGG on 2008-06-06
Did you also set the default encoding in Edit > Preferences > Composer Preferences > Character set?

---

### Post by Chinjuu on 2008-06-06
> **ZabiGG said:**
> Did you also set the default encoding in Edit > Preferences > Composer Preferences > Character set?

Yes, that's the setting which I have set to ISO-2022-JP.

---

### Post by ZabiGG on 2008-06-06
Sorry, did you also set it in Mail Preferences? (same place, 1 icon above)

---

### Post by Chinjuu on 2008-06-07
> **ZabiGG said:**
> Sorry, did you also set it in Mail Preferences? (same place, 1 icon above)

Tried that just now. Unfortunately the problem persists.

---

