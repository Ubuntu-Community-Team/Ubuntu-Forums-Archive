---
title: "Fast file scanning in C"
date: 2009-06-08
forum: Programming Talk
---

### Post by xr82 on 2009-06-08
Hi all, 
So I was at a party the other night and we were playing boggle and I got this seed of an idea that it would be cool to "crack" boggle. 
So I started writing the program and so far I've got it to output all the possible word combinations (including those which aren't necessarily words, e.g akvckzis). 
Now I want to use those results to see if I can find a match in /usr/share/dict/words.
The method I am currently using is slow! Every time I get a new word combination I open the dictionary and search through the whole thing, report if their was a match and then close the dictionary. 
Repeat ad nauseum. Who has a better idea on how I can speed this up? 
(Maybe I could load the file into memory... still the linear fashion in which I'm searching is the real bottle neck).

---

### Post by ghostdog74 on 2009-06-08
you can use a database to store your dictionary. remember to create indexes on your tables...

---

### Post by Mirge on 2009-06-08
> **ghostdog74 said:**
> you can use a database to store your dictionary. remember to create indexes on your tables...

Yeah, import the dictionary into a mysql table... id & word. add an index for word. Will be MUCH faster.

---

### Post by xr82 on 2009-06-08
I think I'll attempt to load the dictionary into a hash table since I don't know how to do that magic in databases. I'll look into that method if the hash table fails.

EDIT:
Hash table worked great (using the one included with search.h) and it now takes about 10 seconds instead of 10 years! 
P.S Thanks for the suggestions with the database. I'll have to look into that in the future.

---

