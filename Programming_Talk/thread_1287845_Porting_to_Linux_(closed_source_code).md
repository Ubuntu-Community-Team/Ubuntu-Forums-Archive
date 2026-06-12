---
title: "Porting to Linux (closed source code)"
date: 2009-10-10
forum: Programming Talk
---

### Post by Marco A on 2009-10-10
.

---

### Post by napsy on 2009-10-10
If the program is proprietary or closed source it doesn't necessary mean it's bad software.

The problem with closed-source programs is that it's hard to create a community around it and you have to provide binaries for Linux distributions yourself and make sure that they work.

---

### Post by stinger30au on 2009-10-10
some people think its some kind of cardinal sin if hey use closed source programs

others are more educated and have no real issues with it

---

### Post by Can+~ on 2009-10-10
The question is, what does it do?

Also, if you're going to port, check out the different libraries available in the repository, so you don't end up reinventing the wheel.

---

### Post by shadylookin on 2009-10-10
most distro repos won't distribute it because it's closed source and this poses ethical and legal issues. 

People will use closed source software(assuming they are aware of it) if there is no alternative or the alternative is poor.

I would say the biggest hurdle isn't that it's closed source per say, but that since it's closed source it won't be seen by most linux users since it won't show up in the places they usually look for software(repos, sourceforge, freshmeat, launchpad) 

I would consider just making your windows code compatible with wine and give them the option to use that

---

### Post by dwhitney67 on 2009-10-10
I personally would not use an application on my system that is not open-source.  I would want, or better yet others, to be able to discern whether the application is "safe" for my system.

If one little facet of your application is dependent on some closed-source functionality, I would suggest that you reverse-engineer it so that it can be open-source and available for Linux.

Of course, that may be considered illegal (for all, except those living in Norway?), but once the cat is out of the bag, there's no stopping it.

---

