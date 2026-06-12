---
title: "a simple XPATH problem for a guru [includes PHP]"
date: 2008-06-14
forum: Programming Talk
---

### Post by the_nomad on 2008-06-14
hi there :)
Ok so here it goes: I have downloaded a PHP Class that extends the DOMElement class and allows me to do some useful operations on HTML tables...

the problem with XML is the following: when i do this query:
```
tr[string-length(td|th)>0]
```
it works great but when i add the second expression, and thus becomes:
```
tr[string-length(td|th)>0 and contains(td/text()|th/text(),'EUR')]
```
it wont show me what i want, and that is 
```
all the TRs from the table whose TDs or THs not only aren't empty but they also contain in at least one of them the string 'EUR'
```

---

