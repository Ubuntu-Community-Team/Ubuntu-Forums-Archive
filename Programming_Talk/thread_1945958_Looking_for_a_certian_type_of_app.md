---
title: "Looking for a certian type of app"
date: 2012-03-23
forum: Programming Talk
---

### Post by ClientAlive on 2012-03-23
Hi,

I was wondering if there's an app for planning/ designing/ organinzing/ tracking a development project. Somthing that would help with the initial planning as well as folowthrough for a piece of software you wanted to create. What do they call that type of app and are there any specific names of apps I could check out?

Thanks
---------------

Edit:

I just thought of another thing too - totally different thing, but...

Sometimes when I'm writing a program I have it at a point where 'everything is working so far;' then, after making a few changes, it's like the whole thing just blows up in my face. It would be great if there were an ide with something like a snapshot feature. Does anyone know of one that has that? Mostly I've used Geany, but have dabbled a tiny bit with CodeBlocks and eclipse - don't know if they have a feature like that though.

---

### Post by satsujinka on 2012-03-24
Koffice kplanner (may be named something else now) can be used for planning projects and tracking progress.

Your other request is satisfied by revision control software. Git and mercurial are good examples. As for ide support... I don't know which if any have built in support for something like that.

---

### Post by MG&amp;TL on 2012-03-24
*Planner* is quite a nice app for that sort of thing.

---

### Post by ClientAlive on 2012-03-24
Right on. I'm reading about mercurial right now. Seems interesting. I also saw something last night called Taskjuggler. It seems a little interesting too. I'll look at koffice klanner too. Thanks for the tips.

---

### Post by Habitual on 2012-03-24
Personally, I can't live without TaskCoach.
I use it for my timecard, but that's about 1/100 of it's features.

---

### Post by BertN45 on 2012-03-24
Eclipse a very complete development tool.

---

### Post by ClientAlive on 2012-03-25
I'll have to take a deeper look at stuff like eclipse (possibly even CodeBlocks). I only fiddled around with them before so I never really discovered all they're capable of.

@Habitual

Nice signature man. I'll check that other thing out too. Thanks.

---

### Post by fct on 2012-03-26
You can also look at server-side development tools. Projects like trac ([http://trac.edgewall.org/](http://trac.edgewall.org/)) allow you to track features and bugs for defined milestones in development, and integration with version control like subversion or git.

---

### Post by ClientAlive on 2012-06-13
At the time I started this thread, I really didn't know how to  communicate what my questions were. It was just some fuzzy notion of a  problem I needed to solve. I recently found out about some things and  thought I'd share what I've discovered.

(1) As for the first part: "an app for planning/ designing/ organinzing/ tracking a development project."

There's this stuff, it's been around for quite a while from what I  gather, called "modelling languages". UML (Unified Modelling Language)  is one that is pretty main stream, but there are many (and for many  various disciplines as well).

[http://en.wikipedia.org/wiki/Modeling_language](http://en.wikipedia.org/wiki/Modeling_language)
[http://en.wikipedia.org/wiki/Unified_Modeling_Language](http://en.wikipedia.org/wiki/Unified_Modeling_Language)

There's also something called "design patterns." Been around since the 80's I hear.

[http://en.wikipedia.org/wiki/Design_pattern](http://en.wikipedia.org/wiki/Design_pattern)

I'm not very knowledgeable about any of them yet (since I've only  just found them); but, in addition to the languages/ concepts  themselves, I believe there are computer programs around for using them  (I think).

(2) As for: "...when I'm writing a program I have it at a point where 'everything is  working so far;' then, after making a few changes, it's like the whole  thing just blows up in my face. It would be great if there were an ide  with something like a snapshot feature."

[satsujinka]("http://ubuntuforums.org/member.php?u=914974") - you hit the nail squarely on the head with that one. Thank you.



Revision control. There are a number of revision control software  available, a few are most popular (as satsujinka mentioned, git and  Mercurial are examples). I chose Mercurial. It's a "distributed"  revision control system and one of it's main purpose (any revision  control) is to keep track of changes to the code you write. (It also  makes sharing code amongst one another simpler).

[http://en.wikipedia.org/wiki/Revision_control](http://en.wikipedia.org/wiki/Revision_control)

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

hih someone


):P

---

### Post by PaulM1985 on 2012-06-13
I find that design patterns are definitely worth knowing.  However, I have seen cases where they have been abused.  It is as if the person writing the code was determined to stick in as many patterns as they can.

UML is also very useful as a quick graphical tool to describe code.

For source control I use Bazaar.  It is only for personal projects where no-one else is going to commit code.  I don't know what it would be like if I put it on a server, but I think it supports it.

Paul

---

### Post by ClientAlive on 2012-06-13
> **PaulM1985 said:**
> I find that design patterns are definitely worth knowing.  However, I have seen cases where they have been abused.  It is as if the person writing the code was determined to stick in as many patterns as they can.

UML is also very useful as a quick graphical tool to describe code.

For source control I use Bazaar.  It is only for personal projects where no-one else is going to commit code.  I don't know what it would be like if I put it on a server, but I think it supports it.

Paul


Right on  ;)   Super cool stuff - I'm excited!

I found an interesting example. Whether one chose to delve deeper into this particular one or not there's still a lot of interesting stuff to note.

[http://c2.com/ppr/catsfate.html](http://c2.com/ppr/catsfate.html)

---

### Post by MG&amp;TL on 2012-06-13
> **PaulM1985 said:**
> 
For source control I use Bazaar.  It is only for personal projects where no-one else is going to commit code.  I don't know what it would be like if I put it on a server, but I think it supports it.


Correction: most of launchpad, including projects like Unity, use bazaar. You can definitely put it on a server and have multiple people commit.

Good suggestion though. :)

---

### Post by trent.josephsen on 2012-06-13
Thanks for coming back to the thread and adding what you've learned. It will probably save more than one person who stumbles across this thread by Googling. That and it's always nice to know when the community has been helpful. :D

---

### Post by |{urse on 2012-06-13
Don't know about current gnu project management software but I've used Openproj before and it does what you're asking for :)

[http://sourceforge.net/projects/openproj/](http://sourceforge.net/projects/openproj/)

---

