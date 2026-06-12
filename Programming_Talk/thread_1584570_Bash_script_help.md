---
title: "Bash script help"
date: 2010-09-29
forum: Programming Talk
---

### Post by Diametric on 2010-09-29
I have created 10 directories; test{0-9}. I would like to, via a script, change the name of each directory by adding the number one (1) to each directory. So test0 becomes test01, test1 becomes test11 and so on. I do not want a full script as an answer, but can someone give me nudge in the right direction? I want to figure it out myself, I just want a little help in getting started.
 
I'm pretty sure I'm going to need to use a "for" statement and "ls" - would it need to be in back tics?

---

### Post by spjackson on 2010-09-29
```

for f in *
do
    mv "$f" "${f}1"
done

```

---

### Post by Diametric on 2010-09-29
I see that - thank you.  That's what I was looking for.  I appreciate your help.  I'll give it a try when I get home and post the results.
 
Cheers.

---

### Post by shawnhcorey on 2010-09-29
A somewhat safer method:
```
for f in test[0-9]
do
    mv "$f" "${f}1"
done
```

---

### Post by Diametric on 2010-09-30
SO, i went home and attmepted the first code - which appended the number one (1) to all of the files and directories.  
 
Shawn - would your example have appended ONYL those directories that beging with "test"?

---

