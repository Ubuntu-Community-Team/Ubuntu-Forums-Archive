---
title: "Bash: Please explain ${var##*.}"
date: 2011-09-05
forum: Programming Talk
---

### Post by jhonan on 2011-09-05
I'm using bash to find the last part of a string e.g. 'myfile.3' - I found a method which works, but I don't know why!

What should I be googling to find out more about this? reg exp or something else?

The code;
```
var=my.test.file.23.45
echo $(( ${var##*.} + 1 ))
```

That returns '46', which is correct (i.e. 45+1) - What I need to understand is the **var##*.** piece. How is that saying 'go to the end of the string, the part after the '.', and return that'

---

### Post by nothingspecial on 2011-09-05
Look at the bottom of this page, it explains it very well.

[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

In order to answer your question about what you should be searching for it's called parameter expansion.

---

### Post by jhonan on 2011-09-05
Nice link, thanks for the reply!

---

### Post by nothingspecial on 2011-09-05
No problem. Read the FAQs and bash pitfalls sections as well when you have time.:)

---

