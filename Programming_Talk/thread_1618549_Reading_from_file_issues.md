---
title: "Reading from file issues"
date: 2010-11-10
forum: Programming Talk
---

### Post by JeremiahS on 2010-11-10
Im writing an encryption program in Python 3.1.2. But when i use f.read() it uses escape characters(ex. \n) and that interferes with my encryption. Now if I could get it to read like this '''My name's Jeremiah''' instead of 'My name\'s Jeremiah'. It'd be perfect. Thx

---

### Post by cipherboy_loc on 2010-11-10
Read: [http://diveintopython3.org/regular-expressions.html](http://diveintopython3.org/regular-expressions.html)

If I under stand it correctly:

```

s = 'This is a test: \' for the \' character...'
s.replace('\', '')

```

But I am not sure, not having worked in Python a lot.


Cipherboy

---

### Post by JeremiahS on 2010-11-10
That looks right... I'll try it out. I didnt think of using regular expressions..

---

### Post by cipherboy_loc on 2010-11-10
The only reason I thought about using them was because my native language is Perl. Not English, Perl. (It actually is English, but Perl is better ;) ). Perl has easy-to-use Regular Expressions. Unlike other languages where you have to import a library or some other things...


Cipherboy

---

### Post by trent.josephsen on 2010-11-10
What do you mean?  read() should yield the exact text read from the file.  Escape sequences are only used for display purposes and not stored with the string.

Should you actually need to interpret escape sequences, look into the eval built-in.  Removing '\' everywhere it occurs will bite you.

---

