---
title: "Metcharacters"
date: 2012-02-19
forum: Programming Talk
---

### Post by achuth on 2012-02-19
Sir,
Please give me the patterns for the following using metacharacters

1. All filenames consisting of two lower-case letters
2. All filenames beginning with **p** and having a **t** somewhere

---

### Post by ofnuts on 2012-02-19
> **achuth said:**
> Sir,
Please give me the patterns for the following using metacharacters

1. All filenames consisting of two lower-case letters
2. All filenames beginning with **p** and having a **t** somewhere

[LIST]
[*]looks like some homework assignment, which is explicitly forbidden here
[*]you don't even tell for which environment. If it's for bash see here: [http://www.gnu.org/software/bash/manual/bashref.html#Pattern-Matching](http://www.gnu.org/software/bash/manual/bashref.html#Pattern-Matching)
[*]what have you tried so far?
[/LIST]

---

### Post by achuth on 2012-02-19
i am a tutor. For the first question the following command is showing wrong results
ls *[a-z]*[a-z]*

please help me on first question only

---

### Post by Vaphell on 2012-02-19
in this case * means 'any sequence of chars including the empty one'
*<0+ chars>[a-z]<0+ chars>[a-z]<0+ chars>*
you get stuff that is **at least** 2 chars long because * will match anything over these two base characters. Drop *'s and you will get your 2chars long names

---

### Post by Arndt on 2012-02-19
> **achuth said:**
> i am a tutor. For the first question the following command is showing wrong results
ls *[a-z]*[a-z]*

please help me on first question only

I wonder if tutor means the same to you as it does to me,

---

