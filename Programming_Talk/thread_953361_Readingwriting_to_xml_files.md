---
title: "Reading/writing to xml files?"
date: 2008-10-20
forum: Programming Talk
---

### Post by sch0009 on 2008-10-20
Programming language - Python

Hi there. I am currently trying creating a program in python which i want to allow users to add and remove rss feeds to a list (xml file), and then search these rss feeds title and description. The search feature is working but i am unsure on how to add/remove files using cgi. 

so basically i will be using cgi and have an input form where the user types in a rss feed url. There will be an add button next to this. When the add button is clicked the page will be refreshed and the rss url will be added to a list. If the user repeats this process then the list will be appended and a second url will appear below. This is what i am trying to achieve but cant find much about it. Any help would be greatly appreciated. 

Thanks

---

### Post by jespdj on 2008-10-20
Which programming language?

---

### Post by sch0009 on 2008-10-20
oops totally forgot about mentioning that. The language is in python. Thanks for pointing that out.

---

### Post by pmasiar on 2008-10-20
to parse (read) XML files, ElementTree is the best, and included in core since 2.5.

To write, any templating system will do. To generate valid XML try kid, or it's newer version Genshi, they focus on valid XML (ie it's runtime error to generate invalid XML). If it feels too complicated, you can either use plain string interpolation and join together valid XML snippets, or look at htmltml, the simplest templating arouund.

---

