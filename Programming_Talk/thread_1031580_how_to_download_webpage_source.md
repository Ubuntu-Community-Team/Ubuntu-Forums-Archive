---
title: "how to download webpage source"
date: 2009-01-05
forum: Programming Talk
---

### Post by TCSnyder on 2009-01-05
i am thinking about writing a program for linux. i want to make a parental control webpage search. but i need to be able to download the html off of the webpage to search it. 

i know that i can view it in firefox, but i need it to be automatic.

i searched wget and it didnt work and i also searched around the web. 

any help would be appreciated.
Thanks.

---

### Post by scragar on 2009-01-05
wget is what you want:
```
wget [-t **tries?**] [-O **output_file**] **url**
```
the [] bit is optional.

---

### Post by amauk on 2009-01-05
wget is the way to go

in a bash script, you can do
```
HTML=`wget -q -O - "http://www.webpage.com"`
echo "$HTML"
```

---

### Post by pmasiar on 2009-01-06
Use libraries from language which you use to evaluate the page. Python would be good choice for that: urllib2 can fetch you the page, and BeautifulSoup helps to parse HTML, handling many quirks in invalid XML correctly (so you don't have to struggle with your own custom regex expressions).

---

