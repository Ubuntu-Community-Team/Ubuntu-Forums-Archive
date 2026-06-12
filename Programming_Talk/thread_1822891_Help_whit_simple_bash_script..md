---
title: "Help whit simple bash script."
date: 2011-08-11
forum: Programming Talk
---

### Post by JuanMadrid on 2011-08-11
I need a bash script where I move all Jpg files from /tmp/programming/practise to /tmp/programming/Juan.

Thank you for your help!

---

### Post by sisco311 on 2011-08-11
Homework?

---

### Post by JuanMadrid on 2011-08-11
homeschool^^....trying to get something good out of these summer breaks..any help?

---

### Post by sisco311 on 2011-08-11
Take a look at: [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

Also check out the BashGuide, BashFAQ and BashPitfalls at the same site.

---

### Post by JuanMadrid on 2011-08-11
cp /tmp/programming/practise/*.jpg  /tmp/programming/Juan

maybe?
:popcorn:

---

### Post by sisco311 on 2011-08-11
Yep, that's right.

---

### Post by JuanMadrid on 2011-08-11
Thank you! If I want to add additional condition, script would be like these:
#! / Bin / bash
cp /tmp/programming/practise/*.jpg&&/tmp/programming/practise/*music*  /tmp/programming/Juan

Is it correct,or whats right?

---

### Post by sisco311 on 2011-08-11
You have to separate them with a space:
```
cp *.jpg *music* /target/dir
```
This will expand to:
```
cp *file1.jpg file2.jpg file3.jpg ... foo_music_bar1 foo_music_bar2 ... /target/dir*
```

---

### Post by JuanMadrid on 2011-08-11
hmm...your statement is if Im in that folder?  Does it mean that I just replace && with a space? That means last location in row is destination? Then how can I have multiple destinations?
 #! / Bin / bash
cp /tmp/programming/practise/*.jpg /tmp/programming/practise/*music* /tmp/programming/Juan



Thankk you for your time!:popcorn:

---

### Post by sisco311 on 2011-08-11
> **JuanMadrid said:**
> hmm...your statement is if Im in that folder?  Does it mean that I just replace && with a space? 

Yes.

> **JuanMadrid said:**
> 
That means last location in row is destination? Then how can I have multiple destinations?


Yes, the last directory is the destination. You can't specify multiple destinations.

---

### Post by JuanMadrid on 2011-08-11
last question, this is correct?

#! / Bin / bash
cp /tmp/programming/practise/*.jpg /tmp/programming/practise/*music* /tmp/programming/Juan

---

