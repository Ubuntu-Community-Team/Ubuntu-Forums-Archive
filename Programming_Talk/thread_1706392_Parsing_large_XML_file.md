---
title: "Parsing large XML file"
date: 2011-03-13
forum: Programming Talk
---

### Post by jbiggs12 on 2011-03-13
I'm trying to parse a large XML file so that I can successfully migrate my blog from Blogger to toto, which is a smaller and more lightweight solution that requires each individual post to be stored as a textfile, with specific properties. First, the file name must be written in a specific way,  like YYYY-mm-dd-then-post-title-like-so.txt. Then, specific properties of the post must be specified in the textfile itself, so once in the textfile you have to type

date: YYYY/mm/dd
title: "Title of Post"
author: "Name of Author"

et cetera. Is there a simple way to automagically create these files using a simple Perl or PHP-cURL script? Is there a function where I can just input the file and get values by going file(tagname)?

Your help is very much appreciated.

---

### Post by Shpongle on 2011-03-13
heres some links for perl xml parsing 

[https://encrypted.google.com/search?ie=UTF-8&oe=utf-8&q=perl+xml+parser](https://encrypted.google.com/search?ie=UTF-8&oe=utf-8&q=perl+xml+parser)

most languages have xml parsing libs , so you should find one handy enough

---

### Post by jbiggs12 on 2011-03-13
what would be a simple way to create new files for each post, using the date and post title as the filename?

---

