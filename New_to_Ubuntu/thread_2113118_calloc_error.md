---
title: "calloc error?"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by cdlam on 2013-02-06
Hi all. I'm trying to run a certain program and I'm getting an "error calloc failed" message. I've tried reading around and I'm still unsure of what it is.

```
./glimmerhmm phytophthora_infestans_t30-4_1_supercontigs.fasta -d /home/chris/Documents/IS/Bioinformatics-Software/IS-Part2/GlimmerHMM/train/TrainGlimmM2013-02-04D22:47:09

ERROR:  calloc failed
```

The thing is, the program works with the test data it comes with, however when using real input data I get this error. So something about the "TrainGlimmM2013-02-04D22:47:09" directory is messing it up to produce this error.

Is there a common reason for getting this error?

---

### Post by Impavidus on 2013-02-06
There's not really a common reason for it. Calloc requests memory for the application from the OS. If it fails, it returns NULL, if zero memory is requested, it also returns NULL. This means that either
a: Your program requests no memory with this input data and doesn't properly handle the return value (a bug).
b: Your program requests more memory than available on your system. Most likely this is caused by malformed data from which required memory is calculated.

Option b is the more likely of the two. Could be a data file where the program expects it to start with a line declaring the number of rows, so that it can allocate memory, but has the first line missing/commented, so that it uses the first line of the table as if it were the number of rows. If this is a 8 digit number your computer may not have enough memory. If it had, it would probably run into a different error.

Working on potato diseases?

---

### Post by cdlam on 2013-02-16
Ah, sorry I forgot to come back to this. Thanks for the info, I would say in this context the problem lay more with option B, although it's really my fault. My input dataset was too large, and the scores being generated were outside of the program's set limits. Used a smaller subset, worked out fine. I'll mark this as solved.

Yup, investigating gene structure in P.infestans, P. capsici, and P. sojae for my senior thesis. Definitely in a little over my head with anything computer science related though haha.

---

### Post by Impavidus on 2013-02-17
We all have our specialities. My grandfather used to work on P. infestans in the sixties. Not much genetics in those days though. Not so many computers either.

---

