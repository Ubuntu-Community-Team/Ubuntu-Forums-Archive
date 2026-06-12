---
title: "Javascript simple lightbox question"
date: 2009-03-22
forum: Programming Talk
---

### Post by fredscripts on 2009-03-22
Hi!

I'm playing with lightbox ([http://www.lokeshdhakar.com/projects/lightbox2/#download](http://www.lokeshdhakar.com/projects/lightbox2/#download)) to show some images in my website. It works fine, for example:

```
//in the head include all required js files
...
...
<a href="im0.png" rel="lightbox[csubj]" title="Desc0"><img src="im0_thumbnail.png" alt="" /></a>

<a href="im1.png" rel="lightbox[csubj]" title="Desc1"><img src="im1_thumbnail.png" alt="" /></a>

<a href="im2.png" rel="lightbox[csubj]" title="Desc2"><img src="im2_thumbnailn.png" alt="" /></a>

...

```

That presents the images pretty well when I click on them (even with this collection presentation that you can navigate within the collection).

What I would like is to have the possibility to , instead of leftclicking the thumbnail and the image appears (with lightbox cool effect), just right-click the thumbnail, then open in a new tab, without lighbox doing anything (so I can see the image in the new tab without any effect).

As I've done it, when I right-click the thumbnail, the lightbox effects appear (also I can select open in a new tab, but of course I don't want that lightbox do nothing when I right-click the thumbnail).

Curiously, for example in this website: [http://www.theater.htwg-konstanz.de/?q=node/4#program](http://www.theater.htwg-konstanz.de/?q=node/4#program) , I can do what I want without any problems (right-click that Die-Hamlet picture). I've checked the source code and doesn't do anything special different than mine. 

in my website: [http://www.fredsampedro.com/misc.html](http://www.fredsampedro.com/misc.html) , try right-clicking on that little brain.


Anyone knows what I should do to get that behavior? or maybe is the lightbox version?


Thanks so much in advance.

---

### Post by fredscripts on 2009-03-22
I've kind of guessed where the problem is, looking at js code of lightbox, it calls the function to show the image when:

```
document.observe('click' , ...)
```

and 'click' means either right or left click. I cannot find what to put instead of 'click' to get only left click response.

---

### Post by fredscripts on 2009-03-22
solved:

[http://www.huddletogether.com/forum/comments.php?DiscussionID=2990&page=1#Item_0](http://www.huddletogether.com/forum/comments.php?DiscussionID=2990&page=1#Item_0)

---

