---
title: "[Python] extracting main contents off of webpage"
date: 2010-02-06
forum: Programming Talk
---

### Post by dracule on 2010-02-06
Basically I want to do something like this;

give a URL. And find the part of the webpage that has the main content. 

e.g. a main page of a blog should return the div that contains the posts and nothing more. (so that the children of the div are iterable)

a post article of a blog should return the div that contains only the main article. (not just the text, but the div that contains the author, title and other stuff)

a forum page should return the div that contains the list of forum threads

a forum thread page should return the container that holds all the posts. 

etc. etc. etc. 


Basically what I have worked out is a series of weights that weighs the size of the div's text, against the child elements of the div, etc. etc. etc. It works OK, but it isnt perfect (well I dont expect it to be). It grabs most things. I am using lxml (switched from beautiful soup for speed reasons). 

I was wondering if anyone heard of such a thing. 

Thanks

---

