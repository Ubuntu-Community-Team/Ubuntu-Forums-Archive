---
title: "how to get number of strings in the given file"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by gennadiJ on 2008-06-22
Is there any simple way to get number of strings in the given file, using standard linux command?
Thanks!

---

### Post by sdennie on 2008-06-22
I'm not completely sure what you mean but, it sounds like you want the wc command:

```

wc some_file.txt

```

It will print 3 numbers it prints represent lines, words and characters in the file.

---

### Post by gennadiJ on 2008-06-22
thanks, this helped!

---

### Post by Xerp on 2008-06-22
You can also use the "strings" command and pipe that through wc

---

### Post by acidsolution on 2008-06-22
wc i.e wordcount must be the ans of your question 
wc textfile
 it gives three numbers
lines, words and characters

---

