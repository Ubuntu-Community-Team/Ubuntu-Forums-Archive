---
title: "Need help to filter out all non-standard characters"
date: 2008-02-13
forum: Programming Talk
---

### Post by Noggenfogger on 2008-02-13
Hi

Does anyone have a bash/perl script or "one liner" that removes all "non" standard characters?
(I only want regular characters like a-z and 0-9 when filtering a file)

//Nogg

---

### Post by SledgeHammer_999 on 2008-02-13
you could check each character of the file if it is an a-z/0-9. if not remove. once you have a hit your loop should stop and go to the next character until you reach the end.

---

### Post by Zwack on 2008-02-13
tr -dc [a-zA-Z0-9] <inputfile >outputfile

Z.

---

### Post by Noggenfogger on 2008-02-13
That tr string did the trick.

your answers are much appreciated, thanks!

---

### Post by Zwack on 2008-02-14
Sorry about the brevity earlier, I was in a hurry...

tr is intended for "translation" of characters from one set into another.... -d says "delete characters that appear in the first set" and -c says "take the complement of the first set before you use it"  So this deletes characters that aren't in the first set.  [] in a regular expression mean any one of the characters inside, 0-9a-zA-Z means three different ranges of characters.  The second set to tr isn't used here.

tr can also be used easily for rot-13 by using tr [a-zA-Z] [n-za-mN-ZA-M] 

Another option might have been to use the strings command.

Z.

---

