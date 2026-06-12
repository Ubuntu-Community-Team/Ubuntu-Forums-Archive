---
title: "special characters representation - linux vs windows: &quot;±&quot; and &quot;&#65533;&quot;"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-07-31
Hi Ubuntu Community:

I've noticed that when I transfer a text file from an windows xp machine that has a special character like "±" to my ubuntu machine, that special character becomes "&#65533;".

I'm using the text editor "Kate" to look at those files.

How do I get ubuntu or Kate to dispalay that "&#65533;" character as "±"?

Thanks!
Phil Smith
Duluth, GA

---

### Post by sharks on 2008-07-31
did u try gedit?

---

### Post by Bachstelze on 2008-07-31
You have to open it using the correct character encoding. Windows uses cp1252, so make sure you open the file with aht encoding in Kate, or change the encoding afterwards (Tools > Encoding).

---

### Post by Old Jimma on 2008-07-31
Sharks and HymnofLife:

Thanks for your postings. I tried gedit and it read that special character. However, gedit puts other characters like tab characters in the file that other applications don't like not like.

Hymn:

I restored the file with the character using archive, and opened it in Kate... all of the characters with CHINESE. I don't understand that. What did I do??

Phil

---

### Post by Old Jimma on 2008-07-31
Sharks:

I just noticed an option in gedit to treat tabs like spaces. I'll try that.

THanks,
Phil

---

### Post by alromh87 on 2009-04-29
I hope this is still usefull, or in case someone else gets here qith that question, you can use

kate -e CP1252  %file

---

