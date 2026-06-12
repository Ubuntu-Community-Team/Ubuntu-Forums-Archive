---
title: "using curl or wget in a sricpt url contains wrong characters"
date: 2014-08-17
forum: Programming Talk
---

### Post by peter_brickles on 2014-08-17
hi guys looking for a heads up im writing a script to atomaticly downloada few web pages 

list of the end of the urls 

> 0082FA4B-DECF-4B1A-9F80-21DCFE05DC42



but when i use curl or wget the end of the url is 

> 

0082FA4B-DECF-4B1A-9F80-21DCFE05DC42%0D

it there any way to stop this happening ?

any help would be appreciated

---

### Post by peter_brickles on 2014-08-17
sorry found the solution it was a carridge return sorted with [QUOTE]tr -d '\r'[QUOTE]

---

