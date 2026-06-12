---
title: "[SOLVED] Subversion. Is it right for me?"
date: 2008-05-16
forum: Programming Talk
---

### Post by null-cipher on 2008-05-16
Now, the title might be a spot misleading... but anyway...

I'm a bit of a hobbyist web-developer, and I was thinking to myself "Hmm, these fantastically talented KDE chaps use SVN for all their source code stuff... perhaps it would be helpful for me keeping track of my PHP website?"
It probably sounds nuts, but I'd like to get myself familiar with SVN as I'm looking at getting into software engineering, and I figured it might be a good way to familiarise myself with that sort of stuff.

So, any suggestions/tips/what-are-you-bats**t-insanes/reference-material?
As always, all your help is much appreciated.

P.S. Sorry if this is the wrong place to ask this sort of stuff, but I figured the programmers of Ubuntu might be the best to ask about Version Control Systems.

---

### Post by Delever on 2008-05-16
I used subversion back on Windows with apache, and really liked it. I think you are not nuts (:)), it's great way to learn it, and you will also have complete backup with every single change.

---

### Post by null-cipher on 2008-05-16
Wicked cool!
Thanks, now I know I'm not trying anything too weird! Haha!
After a bit of an "apt-cache" I have however confused myself as to which packages I'm looking for to put on my server. 0.o
Any pointers?

Thanks

---

### Post by escapee on 2008-05-16
I don't have Ubuntu running at the moment, but check the description and dependencies under the svn package  - I think svnserve is included with it as it is with some other package managers but I'm not too positive.  Otherwise, try downloading svnserve as it's own package.  Hopefully that helps out some :)

---

### Post by null-cipher on 2008-05-16
Yep yep! I found under the subversion meta-package, all the other ones I need.
So, when I have some spare time *cough*, I'll install it on my server and check it out!

Also, I've nabbed myself a copy of the SVN book off of the site, so hopefully that should have all my answers.

I'll still leave this thread open though, cause I'd be very interested to hear some "testimonials". Also, I'm probably going to need more help along the way... haha!
Thanks guys.

---

### Post by slavik on 2008-05-16
If you want to use subversion for the sake of using it (even if you don't need it), go ahead. It's one more thing you can learn about and know when you really do need it. :)

---

### Post by JudgeFudge on 2008-05-16
Have you considered CVS? It is the older and more widespread version control system. Personally, I find it easier to use (though that could be because I am used to it).

---

### Post by null-cipher on 2008-05-17
As was said before, I'm kinda using it for the sake of using it. I'm looking to get into KDE-devel later on in my life, and those guys use it for just about everything! So it's my wee experiment.

I have, installed the *subversion* meta package, and it's installed all the stuff I need.
I'm going to try and get through most of the SVN book, but if anybody has any quick-start tips, I would be all ears! Haha!
Rearing to go! :D

---

### Post by jdonnell on 2008-05-17
I find git to be a better choice for my personal projects, but subversion  is more common at this point (git is used for the linux kernel and was created by linus).

if you stick with subversion you'll probably want to check [this]("http://svnbook.red-bean.com/") out. Subversion basics are really easy to learn, maybe an hour or two.

---

### Post by null-cipher on 2008-05-18
I had actually considered git also, but seeing as git has the (as I discovered on Planet-KDE) git-svn function, I figured I may as well start with a SVN repo first.
I've got myself a little Socket A server that has had so many things I've been trying out on it, it's not even funny!:D
But git will be on my list.
Also, I've been reading the SVN-book (acquired from the link) and being a complete noob to Revision Control, I'm finding it very insightful.

---

### Post by Modred on 2008-05-18
I've personally started migrating all of my personal projects to [bazaar](http://bazaar-vcs.org/), which is a distributed revision control in a similar vein to BitKeeper or git.  It seemed a bit more friendly to someone like myself coming from a subversion background.  And the fact that it recently became a GNU project doesn't hurt, in my opinion.

Anyway, subversion is good when it does what you want; so if it's doing what you want, then great.

---

