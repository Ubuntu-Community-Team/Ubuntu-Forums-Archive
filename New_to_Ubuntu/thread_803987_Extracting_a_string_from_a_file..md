---
title: "Extracting a string from a file."
date: 2008-05-22
forum: New to Ubuntu
---

### Post by madu on 2008-05-22
Hello,

I tried Googling up but couldnt find the exact solution to my problem. I hope somebody could help me out with this.

What I want to do is to extract strings within two constant strings from a file. I think it is possible with AWK but couldnt figure out how to do it for the entire file.

For example I have the following file;
> 
<h2><a href="NAME-1" title="NAME-1-TITLE"></a></h2>
<h2><a href="NAME-2" title="NAME-2-TITLE"></a></h2>
<h2><a href="NAME-3" title="NAME-3-TITLE"></a></h2>
<h2><a href="NAME-4" title="NAME-4-TITLE"></a></h2>


What I need is to extract the strings NAME-1-TITLE,...,NAME-4-TITLE, which will always be between the strings > href="and> "> 

Any suggestion is appreciated.
Thank you very much.

---

### Post by Monicker on 2008-05-22
man egrep


Also look at the -e, -E, and -P options for grep

---

### Post by madu on 2008-05-23
Thanks mate.
Will have a look in that.

---

### Post by Monicker on 2008-05-23
If the url format you gave is consistent, you could also do
```

awk -F'"' '{print $4}' foo.txt
```

Where foo.txt contains ONLY the lines you gave.


If you need to pull out just lines like you gave, it could be

```
grep h2 foo.txt | awk -F'"' '{print $4}'
```

There are a number of ways to accomplish this. It really depends on exactly what is in the file you want to parse.

---

### Post by madu on 2008-05-23
Monicker thank you very much.
The code worked like a charm. I just have to make sure that the format in the file will be consistent.
Thank you again mate.

Cheers!

---

