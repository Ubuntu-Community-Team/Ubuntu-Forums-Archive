---
title: "Posting system's file management"
date: 2010-08-23
forum: Programming Talk
---

### Post by ZaHACKieL on 2010-08-23
Hi everyone, I was wondering something. Let's say you have a website where you can post stuff...now, assume I work with PHP/MySQL so my first basic approach to the system would be to have a file that inserts the post in to the database, let's call it post.php and another one that shows the posts, call it showpost.php

Now, to show a specific post I would do something like:

[www.mywebsite.com/showpost.php?id=637](www.mywebsite.com/showpost.php?id=637)

The same way they do here in ubuntuforums.

Now, I've seen that a lot of websites don't use this type of approach but instead they have, for each post, a url structure like in the case of Digg:

[http://digg.com/comics_animation/The_Best_of_Marvel_Comics](http://digg.com/comics_animation/The_Best_of_Marvel_Comics)

That makes me think that each post has its own directory...am I right?

So what is the difference of having a separate directory for each post and using just one file to directly extract your info from the database using an ID parameter.

I would REALLY like to know your experience with this stuff. At least for me, I've just worked with the one-file method but I'm very intrigued about the second way.

Thanx!!!

---

### Post by ZaHACKieL on 2010-08-23
I'm going to partially answer my question...I think the advantage of using a separate directory for each post would be that, when someone posts a message/story, you save that info in your DB and create a new static html file with the story so when someone reads that post you don't have to connect again to the DB to retrieve that information, you just show a static html file.

Well, maybe you can connect to the DB to show the comments or so but you save some code and DB time.

What do you guys think? Am I right or I'm just talking crap?

=]

---

### Post by slavik on 2010-08-23
they use mod_rewrite to change the URL to a real request

---

### Post by ZaHACKieL on 2010-08-23
Oh didn't know that! so with mod_rewrite you get a cool URL. Thanx a lot slavik!

---

