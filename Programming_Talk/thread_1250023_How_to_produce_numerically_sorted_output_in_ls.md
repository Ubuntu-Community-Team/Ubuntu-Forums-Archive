---
title: "How to produce numerically sorted output in ls?"
date: 2009-08-26
forum: Programming Talk
---

### Post by bilol on 2009-08-26
Hi all,
Within my *dd* directory I have 15 sub directories viz. d1,d2,d3,...,d15.I want them to be listed in sequence  mentioned above.
Unfortunately, I am getting the following sequence of listing: 
```
dhiman@dhiman-desktop:~/dd$ ls
d1  d10  d11  d12  d13  d14  d15  d2  d3  d4  d5  d6  d7  d8  d9
dhiman@dhiman-desktop:~/dd$ ls | sort -n
d1
d10
d11
d12
d13
d14
d15
d2
d3
d4
d5
d6
d7
d8
d9
```
How can I do this?

---

### Post by DaithiF on 2009-08-26
ls | sort -n -k1.2

1.2 indicates to start the search key at the 2nd character of the 1st field

---

### Post by bilol on 2009-08-26
CLOSE.
**Thank you very much DaithiF**

---

