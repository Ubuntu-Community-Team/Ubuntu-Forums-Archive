---
title: "Wget questions"
date: 2012-11-29
forum: Programming Talk
---

### Post by graphicsmanx1 on 2012-11-29
Im trying to learn wget and I have only spent a week in it.  I have read many sites with different ideas on how to use wget but I mostly go to man wget for help.  However I am asking this question because I dont know how to code wget to deny certain file types and folders.  This [tutorial]("http://www.linuxjournal.com/content/downloading-entire-web-site-wget") so far is my favorite and is what I use to code my initial script to mirror a site.  I would like to be able to add a section for denying certain file types.  Ive tried to mirror a few Wordpress sites but I want to deny the feed and the reply html pages.  Any ideas or guidance would be great!

---

### Post by ofnuts on 2012-11-30
See [http://www.gnu.org/software/wget/manual/wget.html#Recursive-Accept_002fReject-Options](http://www.gnu.org/software/wget/manual/wget.html#Recursive-Accept_002fReject-Options)

Unless you have another criterion to recognize comments. Another strategy is to download everything and erase some specific files based on contents.

---

