---
title: "getting wget to work with javascript links"
date: 2008-07-19
forum: Programming Talk
---

### Post by charlie22 on 2008-07-19
i am attempting to mirror a website that has tutorials posted on the site. the tutorials have different chapters and anyone can access the Table of Contents for the tutorial and click on any one of the chapters which will redirect you to a different page that displays only that chapter.

wget wasn't recursively downloading all of the pages in each chapter, it would just stop at the table of contents. going to the actual website and rolling over the links reveals a syntax similar to this in the status bar:
javascript:tut_viewer('redirect.php?id=100');

i would guess that this is where wget isn't recognizing the link as an "<a href=.....></a>" tag.

is this the problem? if so, how can i get wget to recognize that as a link.

thanks in advance.

---

### Post by LaRoza on 2008-07-19
You can't. That is why inline JS is evil, and why graceful degradation is so important. 

My home page uses JS links also, but it degrades gracefully.

---

### Post by drubin on 2008-07-19
> **LaRoza said:**
> You can't. That is why inline JS is evil, and why graceful degradation is so important. 

My home page uses JS links also, but it degrades gracefully.

Never heard of it  being called Graceful Degradation.- Thanks for the name.  
[http://webtips.dan.info/graceful.html](http://webtips.dan.info/graceful.html)

---

### Post by nanotube on 2008-07-20
> **LaRoza said:**
> You can't. That is why inline JS is evil, and why graceful degradation is so important. 

My home page uses JS links also, but it degrades gracefully.

sure you can
just look at the javascript code, function "tut_viewer", and see what it does, and where it redirects.
then you can use those reconstructed urls to download the stuff (with a helping of a bit of bash or python script).

but yea, graceful degrade is nice. :) in most cases, though, there is not even a reason for the "href" contents to be javascript.

---

### Post by LaRoza on 2008-07-20
> **nanotube said:**
> sure you can
just look at the javascript code, function "tut_viewer", and see what it does, and where it redirects.
then you can use those reconstructed urls to download the stuff (with a helping of a bit of bash or python script).

but yea, graceful degrade is nice. :) in most cases, though, there is not even a reason for the "href" contents to be javascript.

Anything is possible of course, but not with wget ;)

---

### Post by nanotube on 2008-07-20
> **LaRoza said:**
> Anything is possible of course, but not with wget ;)

well, you use wget to download the reconstructed links, no? :)

---

### Post by LaRoza on 2008-07-20
> **nanotube said:**
> well, you use wget to download the reconstructed links, no? :)

I can also write an assembly program to download and parse it, but that doesn't make such poor design ok.

---

### Post by charlie22 on 2008-07-20
thanks for the replies.

so in order to work around this, correct me if i'm wrong, i will have to do what i already have which is have wget mirror the table of contents page. then i will have a script parse that file looking for a unique string such as "tut_viewer('redirect.php?id=100');" and then parse the string to pull out the redirect.php?id=100 and call wget with [http://domain.com/redirect.php?id=100](http://domain.com/redirect.php?id=100).

i can do this but it's unfortunate that wget does not have a built-in work around for this.

---

### Post by ghostdog74 on 2008-07-20
> **charlie22 said:**
> 

i can do this but it's unfortunate that wget does not have a built-in work around for this.

more info [here](http://wget.addictivecode.org/FeatureSpecifications/JavaScript)

---

