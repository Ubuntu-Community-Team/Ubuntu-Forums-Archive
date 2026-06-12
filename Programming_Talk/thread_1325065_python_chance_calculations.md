---
title: "python chance calculations"
date: 2009-11-13
forum: Programming Talk
---

### Post by eragon100 on 2009-11-13
Hello guys!

I want to write a program in Python to do chance calculations, you know, like binomcdf and bimompdf functions on the TI calculator, and just general chances.

Example: "500 Ubuntuforums.org users get interviewed. 280 of them turn out to be Anime fans. What is the chance that if you select 60 people from the 500, at least 40 of them are anime fans?"

Are there any handy modules/functions in python for calculating chances? Google isn´t giving me any usefull hits :(

---

### Post by A_Fiachra on 2009-11-13
NumPy, StatPy and SciPy have way more than combinitorics and statistics, but they are a place to start.

There is a Python binding to R -- also overkill, but good to know.

---

### Post by eragon100 on 2009-11-13
> **A_Fiachra said:**
> NumPy, StatPy and SciPy have way more than combinitorics and statistics, but they are a place to start.

There is a Python binding to R -- also overkill, but good to know.

Thanx for the info! :popcorn:

---

### Post by A_Fiachra on 2009-11-13
Don't forget to look into weighted distributions (google will give you plenty of leads)

---

### Post by Can+~ on 2009-11-13
> **eragon100 said:**
> Hello guys!

I want to write a program in Python to do chance calculations, you know, like binomcdf and bimompdf functions on the TI calculator, and just general chances.

Example: "500 Ubuntuforums.org users get interviewed. 280 of them turn out to be Anime fans. What is the chance that if you select 60 people from the 500, at least 40 of them are anime fans?"

Are there any handy modules/functions in python for calculating chances? Google isn´t giving me any usefull hits :(

I would stick to only R, and learn it properly, although it's not the prettiest language.

Also, two strata, a population and a sample? That looks like a   [hypergeometric distribution]("http://en.wikipedia.org/wiki/Hypergeometric_distribution").

---

### Post by TheStatsMan on 2009-11-14
> **Can+~ said:**
> I would stick to only R, and learn it properly, although it's not the prettiest language.

Also, two strata, a population and a sample? That looks like a   [hypergeometric distribution]("http://en.wikipedia.org/wiki/Hypergeometric_distribution").

 I don't see how R is any more suitable than Python (or any other language for that matter) for this kind of problem.

---

