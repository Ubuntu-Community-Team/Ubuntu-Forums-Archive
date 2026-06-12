---
title: "Change last field to upper-case with awk"
date: 2009-09-10
forum: Programming Talk
---

### Post by kaibob on 2009-09-10
I have an awk question that I have been unable to answer. I have a text file with 3 to 5 space-separated fields per record. For example,

> one two three four
one two three
one two three four five

I want to capitalize the last field of each record. Using the above example,

> one two three FOUR
one two THREE
one two three four FIVE

If all of the records had 4 fields, I could use either of the following. 

```
awk '{ print $1,$2,$3,toupper($4) }' file
awk '{ print $1,$2,$3,toupper($NF) }' file
```

How can I do this with the varying number of fields. This seems simple, but I spent quite a bit of time in research and couldn't get anything to work. 

Thanks.

---

### Post by DaithiF on 2009-09-10
Hi,
hmm, not so sure about awk, but like so in sed:
```
sed 's/ \([^ ]*\)$/\U&/' testfile
one two three FOUR
one two THREE
one two three four FIVE
```

---

### Post by DaithiF on 2009-09-10
i guess in awk you could use a for loop, something like:
```
awk '{ for(i=1; i<NF; i++) printf $(i) " "; printf toupper($NF) "\n" }' testfile
one two three FOUR
one two THREE
one two three four FIVE

```

---

### Post by unutbu on 2009-09-10
I don't know if this is proper awk, but this seems to work:
```
awk '{ gsub(/.*/,toupper($NF),$NF) }1;' file
```

---

### Post by kaibob on 2009-09-10
Thanks everyone for the help. I tried the suggested solutions, and they all worked great. Before posting, the only one that occurred to me was the for loop, but I used print rather than printf, which of course did not work well.

Thanks again.

kaibob

---

### Post by ghostdog74 on 2009-09-10
am i missing something?
```

# awk '{$NF=toupper($NF)}1' file
one two three FOUR
one two THREE
one two three four FIVE


```

---

### Post by kaibob on 2009-09-11
Thanks ghostdog74. It can't get much simpler than that. I appreciate the help.

---

