---
title: "Wildcards in python?"
date: 2010-01-30
forum: Programming Talk
---

### Post by HalfEmptyHero on 2010-01-30
I want to scan an html file, looking for images, and add the url of the image to a list, however I am not sure how to do this. Is there any way to do wildcards in python, such as:

if 'http://www.'*'.jpg' in file:
  list.append(item)

or something that works to that degree. Or some other way to do this.

---

### Post by nvteighen on 2010-01-30
You need a regular expression. Look at the re module.

---

### Post by ricegf on 2010-01-30
You might also want to check into Beautiful Soup ([http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)), a Python library useful for efficiently and usefully dissecting web pages. It's particularly adept at handling badly-coded pages such as you often find on the open web.

---

### Post by HalfEmptyHero on 2010-01-30
Excellent thanks for the help.

---

