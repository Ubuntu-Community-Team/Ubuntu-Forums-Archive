---
title: "[SOLVED] Cleaning strings in bash"
date: 2008-02-11
forum: Programming Talk
---

### Post by dedtr9 on 2008-02-11
I am writing a scipt to download a certain web page that requires authentication, and it is going fine except for one problem. In the code they have two strings that are needed to pass to the page that you submit to and change every load, but I don't know exactly how to get those cleaned up, as in just the data I want from the line. Finding the line is no problem. 
They are formatted like this:
```
var pskey = "2D2012350FBA0AAB0A7252FC3D4B29BB4BE406561F40550D6449107703055F07";

```
and 
```
<input type="hidden" name="pstoken" value="2517">
```

In this case I would want out 2D20... from the first one and 2517 from the second. 
From searching I've found that i need to use Regular Expressions, but i cant seem to understand enough to be able to get the data out. 

On a side note, is there a good way to call a JavaScript function from their .js file or just from their code? It would be a lot of work to re-write theirs.

---

### Post by ghostdog74 on 2008-02-11
> **dedtr9 said:**
> 
In this case I would want out 2D20... from the first one and 2517 from the second. 

don't know what you mean. I will assume you want to get 2D20 and 2517?
```

awk 'BEGIN{FS="[=\"<>]"}
/var pskey/ {   
 print substr($3,1,4)
}
/pstoken/{print $(NF-2)}'  htmlfile

```

otherwise, describe more clearly what you want, best if you have sample input, and your expected output.

---

### Post by dedtr9 on 2008-02-11
I meant the whole of the string, as in 2D2012350FBA0AAB0A7252FC3D4B29BB4BE406561F40550D6449107703055F07, but I was able to get it with 
```

awk 'BEGIN{FS="[=\"<>]"}
/var pskey/ {   
 print substr($3,1,64)
}
/pstoken/{print $(NF-2)}' index.html

```
Thanks

---

