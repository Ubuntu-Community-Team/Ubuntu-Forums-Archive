---
title: "HOWTO: Fix Gaim character misrepresention problem - Change unicode encoding"
date: 2006-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Sammi on 2006-05-28
Many people use different characters encoding than the one found in UDF-8, which Gaim uses as standard. Especially those of non-english origin. For many people changeing it to ISO-8859-1 will fix the problem.

The problem is sometimes restricted to sertain messaging protocols and accounts.

Do this:
Right click on the Gaim system tray icon -> 
click on "Accounts" -> 
choose the account which is giving you troubles ->
Click on "Modify" ->
Click on "Show more options" ->
Paste this text "ISO-8859-1" over "UTF-8" in the option line named "Encodings:" ->
Press save ->
Reinitialise the windows that use the account in question
Done!

This should fix most peoples problems, but not everyones.

---

### Post by Sammi on 2006-05-29
No replies. It doesn't seem that many people have been experiencing this problem - lucky bastards :-D 

Anyway if this doesn't solve your problem, then you might need to use a different unicode string. The one I provided is standard english encoding, but has many extra characters, so it is compatable with many other languages. To find a different unicode string just do a searce for something like "unicode" on this forum and on any search engine, that should fix you up.

---

### Post by enaut on 2009-06-12
btw... your Post just helped me ;) so thanks

---

