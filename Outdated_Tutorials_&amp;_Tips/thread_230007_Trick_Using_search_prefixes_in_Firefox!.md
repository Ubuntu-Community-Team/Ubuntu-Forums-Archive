---
title: "Trick: Using search prefixes in Firefox!"
date: 2006-08-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Adrian_b on 2006-08-05
This is a little trick i found out for Firefox.
With this, you can search from the location bar by using a keyword to specify the search engine.

Surf to any search engine and search for a random, recognisable string. (ex: [www.google.com/search?hl=en&q=UBUNTU](www.google.com/search?hl=en&q=UBUNTU) ) and bookmark it.
Rightclick on that bookmark and select properties.
Replace the string UBUNTU with %s
In the keyword field, type the name you want to search with. (pick something short such as gg for Google, wp for wikipedia)

If you use google and the keyword gg, you can now type gg -string- to search for -string- using Google :D

Example URLs: (Do as i described above, surf, bookmark, keyword it.)
For Google:
[http://www.google.com/search?hl=en&q=%s](http://www.google.com/search?hl=en&q=%s)
For Wikipedia (searching WP):
[http://en.wikipedia.org/w/index.php?title=Special%3ASearch&search=%s&fulltext=Search](http://en.wikipedia.org/w/index.php?title=Special%3ASearch&search=%s&fulltext=Search)
For Wikipedia (go directly to a page):
[http://en.wikipedia.org/wiki/Special:Search?search=%s&go=Go](http://en.wikipedia.org/wiki/Special:Search?search=%s&go=Go)
For Yahoo:
[http://search.yahoo.com/search?p=%s&fr=FP-tab-web-t500&toggle=1&cop=&ei=UTF-8](http://search.yahoo.com/search?p=%s&fr=FP-tab-web-t500&toggle=1&cop=&ei=UTF-8)
For TorrentSearch.com:
[http://85.17.40.140/ts/develop/main.php?searchString=%s&searchCategory=all&do_search=search](http://85.17.40.140/ts/develop/main.php?searchString=%s&searchCategory=all&do_search=search)
For Youtube:
[http://www.youtube.com/results?search_query=%s&search=Search](http://www.youtube.com/results?search_query=%s&search=Search)
For Google News:
[http://news.google.com/news?hl=en&ned=us&q=%s&btnG=Search+News](http://news.google.com/news?hl=en&ned=us&q=%s&btnG=Search+News)

URL Masked sites:
Some sites have an URL which is masked all the time meaning you can't just see the actual search URL.
I've encountered this mostly on PHP sites.
A lot of the time, looking for your string in the source code (right-click on the page and select 'View page source') is enough to find out.
Sometimes, however, it's not enough (Torrentsearch.com for example).
Try using Ethereal(apt-get install ethereal) then to capture the packets sent trough when doing the search. (Ping the website first to find the ip so you know at what adress to look)

(I know nothing about PHP or whatsoever, so notify me of any mistakes please :) )

Hope it was useful :D
If you have any questions, ask.

---

