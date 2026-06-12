---
title: "SQL Question"
date: 2007-07-19
forum: Programming Talk
---

### Post by 008325 on 2007-07-19
i have two column , start day and  end day
i would like to check the date while i insert a new record
i tried between function , however , it is useless for "Date Range"
for example 

Record 1 . 7/1 to 7/9

while i insert record two,

7/2 to 7/7

how can i use SQL to check the date is conflict ?

---

### Post by peppy.ch on 2007-07-19
hey
wen ever I have to deal with date I use the [Unix timestamp]("http://en.wikipedia.org/wiki/Unix_timestamp") it makes the hole thing easier.
you can then use syntaxes like "SELECT * FROM aTable WHERE dateA<dateB" 
I don't know if I got your problem right but I hope it helps ;)
regards

---

