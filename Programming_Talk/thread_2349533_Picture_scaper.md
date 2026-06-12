---
title: "Picture scaper"
date: 2017-01-15
forum: Programming Talk
---

### Post by kingpenguin on 2017-01-15
I know that there is picture scrappers already on the Internet but i am wanting to build one my self. I will post my code that i have so far but i am not understanding why this is not working correctly.
```

#!/usr/bin/env python3
import urllib.request
from bs4 import BeautifulSoup

page = BeautifulSoup(urllib.request.urlopen(r'https://images.search.yahoo.com/search/images;_ylt=AwrBTzzxFXxYY6sA1GZXNyoA;_ylu=X3oDMTE0bmoxZWYwBGNvbG8DYmYxBHBvcwMxBHZ0aWQDQjI5MTNfMQRzZWMDcGl2cw--?p=penguins&fr=yfp-t&fr2=piv-web'),'lxml')
all = page.findAll('a', {"class":"image"})
for i in all:
    print(i)

```
If i change the var all to all = page.findAll('img) Then i can loop through all in a for loop and get all of the image tags but with all the tags and extra stuff as well. I really just want the url. everything I have tried just seems to make it go from printing the <img> tags to printing nothing. Some help would be really awesome

---

### Post by howefield on 2017-01-16
Not an answer but there is also the discussion group [https://groups.google.com/forum/?fromgroups#!forum/beautifulsoup](https://groups.google.com/forum/?fromgroups#!forum/beautifulsoup), just in case you weren't aware.

---

