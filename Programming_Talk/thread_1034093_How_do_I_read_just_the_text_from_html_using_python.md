---
title: "How do I read just the text from html using python?"
date: 2009-01-08
forum: Programming Talk
---

### Post by agim on 2009-01-08
I would like to write a program that searches my bookmarks file, and downloads the html so I have a copy of them.
Ideally, I would like to be able to just scrape the Title, which isn't too difficult, and the text from the html.

I cannot figure out a decent solution to scrape the text. I have looked into beautiful soup. If it does this then I am looking in the wrong place.

Whether the answer is here or somewhere else, hopefully someone here can help.

Thanks
Andy

---

### Post by Ahadiel on 2009-01-08
This should probably be moved to the Programming forum.

---

### Post by mssever on 2009-01-08
> **agim said:**
> I would like to write a program that searches my bookmarks file, and downloads the html so I have a copy of them.
Ideally, I would like to be able to just scrape the Title, which isn't too difficult, and the text from the html.

I cannot figure out a decent solution to scrape the text. I have looked into beautiful soup. If it does this then I am looking in the wrong place.

Whether the answer is here or somewhere else, hopefully someone here can help.

Thanks
Andy
Beautiful Soup is the ideal tool for this job.

---

### Post by agim on 2009-01-08
Great, it seemed like it. Exactly what do I have to do? Each site uses their tags differently, is there something like a 'scrapeText' function?

---

### Post by mssever on 2009-01-08
> **agim said:**
> Great, it seemed like it. Exactly what do I have to do? Each site uses their tags differently, is there something like a 'scrapeText' function?
The best thing is to read the documentation. I've never used Beautiful Soup myself, so I don't know the details of how to use it. Just go to its website, and you'll find documentation.

---

### Post by ghostdog74 on 2009-01-08
you can use simple string manipulations just fine.
Another way is to use regular expression. Just a snippet
```

import re
for l in open("file"):
    if "<A HREF" in l:
        print re.findall("<A HREF=\"(.*?)ADD_DATE.*\">(.*?)</A>",l)

```

---

