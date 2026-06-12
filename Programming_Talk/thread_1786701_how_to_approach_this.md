---
title: "how to approach this"
date: 2011-06-20
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-06-20
I'm an intermediate programmer (just for fun here and there) and was wondering how I would go about writing a program that (approximately) reduces a fraction that came from a decimal. 

Lets say I start with the decimal 0.82931. Then i could easily change that into 82931/100000. However, I need a fraction with a denominator <= 6. Therefore I'd somehow need to reduce that to 4/5. Should I just ignore everything after the 1st decimal place? Or is there a better way to do it.

---

### Post by uco on 2011-06-20
Hi,
I don't know if there is a better way, but here is mine.

Since you have a very limited number of denominators to select from (2, 3, 4, 5, 6),
do the following:
assuming the number you want to convert is X
- for each denominator n=2,3,4,5,6 compute An=X-int(X*n)/n;
- select the n that gives minimum An
- compute approxX=int(X*n)/n;

---

### Post by NovaAesa on 2011-06-20
There's a much easier way to do it. If you want the denominator to be 6, simply multiply the original decimal number by 6. I.e. 6 * 0.82931 = 4.97586. Then round that number to the nearest integer i.e. round up to 5. Then your final fraction is 5/6.

EDIT: nevermind, I mustn't be thinking well today, this is pretty much what uco above me said.

---

### Post by flyingsliverfin on 2011-06-22
ahh im feeling a little stupid now... simple little equation could have given me that so easily...

hopefully its just me having summer break now :)

---

