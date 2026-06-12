---
title: "sed to replace text"
date: 2007-02-12
forum: Programming Talk
---

### Post by Greslore on 2007-02-12
Short, sweet, and quick question:

contents of /etc/blah.conf:
blah1
blah1
blah2
blah2
blah1

How do I use sed to change all the blah1 in /etc/blah.conf with the word scoobie?

---

### Post by LotsOfPhil on 2007-02-12
sed -i 's/blah1/scoobie/g' /etc/blah.conf

The -i makes it edit the file in place.

---

### Post by Greslore on 2007-02-12
Bingo.. that did it.  I was using: 

sed 's/blah1/scoobie/g' /etc/blah.conf

That -i did the trick.  Thank you kindly good sir =)

---

### Post by jblebrun on 2007-02-12
> **LotsOfPhil said:**
> sed -i 's/blah1/scoobie/g' /etc/blah.conf

The -i makes it edit the file. It's the same as sed '...' /etc/blah.conf > /etc/blah.conf

CAUTION! No, it's not the same!!

 The second command will obliterate your blah.conf file, turning it into an empty file. I've been bittern by that one before.

---

### Post by LotsOfPhil on 2007-02-12
True, true. I meant in a pseudocode kinda way. I edited the post to remove the offending (damaging :)) passage.

---

