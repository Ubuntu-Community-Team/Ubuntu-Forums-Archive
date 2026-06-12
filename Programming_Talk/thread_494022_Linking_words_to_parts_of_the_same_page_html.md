---
title: "Linking words to parts of the same page: html"
date: 2007-07-06
forum: Programming Talk
---

### Post by b0ng0 on 2007-07-06
Basically I would like to know how to get a word or words to take you down to a specific section on the same page (wiki/ubuntu guide style). So I have my contents at the top of my webpage and if someone clicks on for example "1D Analysis" I would like the page to then go down to that section on the web page. Hope this all makes sense, thanks for any help.

---

### Post by Mr. C. on 2007-07-06
Like this:

```
<a href="#my_title">Go to My Section</a>
...

<a name="my_title">My Section</a>
```

MrC

---

