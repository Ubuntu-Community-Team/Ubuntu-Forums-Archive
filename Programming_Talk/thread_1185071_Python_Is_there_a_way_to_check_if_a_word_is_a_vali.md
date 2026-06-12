---
title: "Python: Is there a way to check if a word is a valid one based on a dictionary?"
date: 2009-06-11
forum: Programming Talk
---

### Post by superpink99 on 2009-06-11
Hi, i was wondering if there was a way in python on checking if a certain word is an accepted word based on a dictionary?

example if i typed a word, is there a library where i can cross reference it if it is an acceptable word?

thanks..........

---

### Post by ghostdog74 on 2009-06-11
get the dictionary to a list. use the "in" operator
eg
```

if "word" in list_of_dictionary_words:
   print "ok"

```
otherwise, use a database

---

### Post by benj1 on 2009-06-11
why are you starting multiple threads asking the same question?

you had the answer in the last thread.

---

### Post by superpink99 on 2009-06-11
sorry benj1, your right i should haver rephrased my first post.:)

ghostdog74: you said put the dictionary on a list? does that mean typing every word from the dictionary? where can i find a database of all the words?

thanks............:)

---

### Post by benj1 on 2009-06-12
as was answered in the other post
/usr/share/dict
contains the dictionarys

you need to learn about working with files

so

```
text = open("/usr/share/dict/british-english",'r').readlines()

for lines in text:
    if lines.find("word") == 0:
        print "word is in the dictionary"
```

---

### Post by benj1 on 2009-06-12
as was answered in the other post
/usr/share/dict
contains the dictionarys

you need to learn about working with files

so

```
text = open("/usr/share/dict/british-english",'r').readlines()

for lines in text:
    if lines.find("word") == 0:
        print "word is in the dictionary"
```

---

