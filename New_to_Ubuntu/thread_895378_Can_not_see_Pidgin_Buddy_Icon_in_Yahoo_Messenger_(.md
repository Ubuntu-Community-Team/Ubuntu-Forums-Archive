---
title: "Can not see Pidgin Buddy Icon in Yahoo Messenger (WIndows)"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-20
I use Pidgin in Hardy Heron. I would like to share my buddy icon with my friends who use YM in Windows but I don't know how to do that. Do I need a plugin to do it? Btw, I already set buddy icon in Pidgin.

---

### Post by freak42 on 2008-08-20
I am not sure if this is the problem, but give it a try if you haven't done so already:

in Pidgin under Accounts->[your yahoo account (aim??)]->edit account-> basic
be sure to select the checkbox next to Use this buddy icon for this account (and your buddy icon should be in the image next to it).

hth

---

### Post by fauzie on 2008-09-08
This is a bug in Pidgin. The only thing you can do is to wait for the next version. The team had worked on it and found a solution, but it had not been released yet. You can also try Kopete (The devs use Kopete's code to fix the problem)

---

### Post by natrik on 2008-10-04
> **fauzie said:**
> This is a bug in Pidgin. The only thing you can do is to wait for the next version. The team had worked on it and found a solution, but it had not been released yet. You can also try Kopete (The devs use Kopete's code to fix the problem)

I'm looking at the [Pidgin Changelog]("http://www.pidgin.im/ChangeLog") (and here's the [google cache version]("http://72.14.205.104/search?q=cache:www.pidgin.im/ChangeLog+Setting+your+buddy+icon") -- i can't access pidgin.im right now)  

It looks like this is a libpurple fix that was released in version 2.4.3 (07/01/2008), but it looks like it hasn't yet made it through to the Debian Hardy packages just yet. 

To the first poster:  Your windows friends probably have a more recent pidgin (and libpurple).  You can always try going to the website and updating directly.  Whenever the website comes back online, that is.

-- Nate

---

