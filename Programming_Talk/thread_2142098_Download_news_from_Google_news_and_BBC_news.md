---
title: "Download news from Google news and BBC news"
date: 2013-05-04
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2013-05-04
Hi

I've never done something like this, I mean I'm preatty good at programming but never done something with web.
Now I need to download articles from google news and bbc news ... . All I need is a title and the content (article) and save this in file. I need to download as much articles as I can (I'm doing a research), let say every article published from 2005 - 2013. Now since I have never done something with web nor was interested in web I have no idea how to do this. Any explanation how to do this would be great, also I should do this in C# but a general solution would also be helpful. 

Thanks

Please help me.

---

### Post by BluNova on 2013-05-04
I would suggest looking at the RSS feeds for both and finding a parser for c#

---

### Post by tgalati4 on 2013-05-04
I would install *curl* and look for RSS feeds from both sites.

So here is the BBC News website:  [http://www.bbc.com/news/](http://www.bbc.com/news/)

Here is the BBC News RSS feed:  [http://feeds.bbci.co.uk/news/rss.xml](http://feeds.bbci.co.uk/news/rss.xml)

Write a script to capture the article titles using *curl* then recurse over the titles to get the actual articles.

You may have better luck with simply using the "site:[www.bbc.com/news](www.bbc.com/news) search-term" within google.

---

### Post by Mr.Pytagoras on 2013-05-05
would it be possible to download articles from some past period of time through the RSS?

---

### Post by Mr.Pytagoras on 2013-05-05
Right now I'm using httrack to download the news from bbc, however it is slow and also it is downloading other files as well, currently I have downloaded 71 000 files, but in the news directory there is only 25 000 files. I need 75 000 more ](*,) so far it took one day :) if anybody know a better way please share, also those pages that I have downloaded are not only the title and the article, its a compleate html file with scripts ... so I need to parse every and get the actual article from it.

---

