---
title: "Converting a string to a date in bash using date utility"
date: 2018-07-05
forum: Programming Talk
---

### Post by trilobite2 on 2018-07-05
Hi all - 

 I'm trying to convert a string to a date in bash using the date utility but it isn't working.  Unfortunately, the string is in double-quotes and the date uses slashes as the separators.  

I'm doing this (where $ is the prompt) - 
```
 
$  date -d  "28/06/2018"  +'%d/%m/%Y'   

``` 

This gives me an error -   "date: invalid date ‘28/06/2018’  "  

I hope someone can help!  Thanks very much -  
- trilobite2

---

### Post by The Cog on 2018-07-05
Although date can output a date in any format you like, "man date" says expects any input date to be in the format "[MMDDhhmm[[CC]YY][.ss]]" ., although it seems to accept MM/DD/YYYY which is that strange American way to write dates:
```
~$ date -d  "06/28/2018"  +'%d/%m/%Y'
28/06/2018
```

---

### Post by trilobite2 on 2018-07-05
Hi, The Cog -  thanks for that!  

Ok -  that shouldn't be a problem for me.  I can just chop the date into three parts and reassemble it in the desired format.  

I'm happy - I'll mark this as solved!  

Cheers -  thanks again....   :)    
- trilobite2

---

