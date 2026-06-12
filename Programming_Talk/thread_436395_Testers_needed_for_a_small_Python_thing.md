---
title: "Testers needed for a small Python thing"
date: 2007-05-07
forum: Programming Talk
---

### Post by Bachstelze on 2007-05-07
Hi, everyone :)

For school, I've done an implementation of the classic MasterMind game in Python. It is not finished yet but it's playable so I'd appreciate if some people could help me test it.

[http://fkraiem.free.fr/mastermind/mastermind.tgz](http://fkraiem.free.fr/mastermind/mastermind.tgz)

I don't give further instructions about how to run it, there's a README included and it's supposed to be as throughout as possible so if I forgot to mention something, please tell me here and I'll add it ;)

---

### Post by slash2314 on 2007-05-07
In your functions.py at line 231  you need to change

file.write("\t<entry ranking=\"%u\">\n" % i+1)
to
file.write("\t<entry ranking=\'%u\'>\n" % i+1)

---

### Post by Bachstelze on 2007-05-07
Yep, someone else reported that bug, I corrected it another way though ;)

---

### Post by FuriousLettuce on 2007-05-07
In mmNoGui/__init__.py, on line 113, that 'e' at the end of the line should be another quotation mark.

EDIT:

In addition, in mmNoGui/functions.py, on line 93, you need to make the b = raw_input.. call before the while loop, as you have an undefined variable error at the end of each round in text mode.

---

### Post by Bachstelze on 2007-05-07
All those stupid little mistakes (and a few others) are corrected.

---

### Post by Noah0504 on 2007-05-07
Well, I didn't really come across anything, but I can say thank you.  hehe, I love Mastermind, and I've been playing this game far too long.

---

### Post by FuriousLettuce on 2007-05-08
Don't know if you're interested in any more replies, but the initial "Would you like text, gui or to quit" prompt can't handle non-numeric characters - it interprets them as variables ('o' is OK, but o is not). Perhaps raw_input should be used?

---

### Post by Bachstelze on 2007-05-11
Are you sure you're talking about that prompt ? It works fine here.

Bump anyway, lots of new things added, especially to the GUI mode...

---

