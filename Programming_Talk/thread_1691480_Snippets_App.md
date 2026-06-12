---
title: "Snippets App"
date: 2011-02-19
forum: Programming Talk
---

### Post by Ascension on 2011-02-19
Is there a snippets app for Ubuntu? 

On Window's I was running JCodeCollecor I believe. Looking for something to store my code snippets and such. Any help appreciated.

---

### Post by icodemonkey on 2011-02-20
google for pysnippet or Qsnippetsmanager (what i use)
but as i have found out grep is the best way to find snippets of code 
eg i have a folder of code organised this way:
 /snippets/<lang>/<catagory>/<snippet>.<blah>

in the snippet file:
```
##### title of snippet #######
<code goes here>


```to find it i use:
```
 grep -nHIirF -- "<title of snippet>"  /path/to/your/snippets
```

but as always YMMV

---

