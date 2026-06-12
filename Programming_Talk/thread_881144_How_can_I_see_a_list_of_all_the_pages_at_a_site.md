---
title: "How can I see a list of all the pages at a site?"
date: 2008-08-05
forum: Programming Talk
---

### Post by tc101 on 2008-08-05
How can I see a list of all the pages at a site?  I can use Firefox/tools/Page Info/Links to see all the links from a site, but I want to actually see all the pages.  I think there is something in google to let me do this but I can't find it.

---

### Post by pytheas22 on 2008-08-05
Are you thinking of a Google search like:
[URL="http://www.google.com/search?q=site%3Aubuntu.com&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a"]
site:ubuntu.com[/URL]

I think that shows all of the pages of ubuntu.com that Google knows about (note that there could be other pages that Google doesn't index because they're blocked by robots.txt or whatever).

Also, you could use wget to download the whole site, although that's not the most efficient way to figure this out...although maybe wget has an option to only list site directories, not actually download the stuff.

Finally, there are some online [sitemap generators]("http://www.xml-sitemaps.com/") that could help you.

---

### Post by pmasiar on 2008-08-05
Google (or any other spider) knows only pages linked from other pages. Is it what you want?

Apache can be IIRC set to show list of all files in a directory, but it is most often disabled (for security reasons).

---

### Post by dileepm on 2008-08-07
Try this [http://www.garagegames.com/index.php?sec=mg&mod=resource&page=view&qid=4587](http://www.garagegames.com/index.php?sec=mg&mod=resource&page=view&qid=4587)

---

