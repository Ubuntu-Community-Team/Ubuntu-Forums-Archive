---
title: "integrated system dashboard - Python/Django? OOo Base? Other?"
date: 2009-08-11
forum: Programming Talk
---

### Post by yekibud on 2009-08-11
I'm about to start a fairly large project for a mid-sized business with a lot of integration with other systems (POS, accounting, website, inventory, purchasing, etc.) The purpose of the system is to try to reduce current data siloing and give employees role-based access to the specific data entry and reports they need, as well as to replace some manual and redundant business processes. The system needs to be cross-platform (Windows/Linux), open source and is primarily for LAN use.

My experience is mostly PHP/web/app development, but I have developed a few LAN apps using Java/Servoy (like Filemaker). I am leaning towards Python/Django - but wondering whether this may be unnecessarily web-specific. I really felt Servoy development was very rapid, and it was cross-paltform, but it was not open source (not to mention that anything custom needed to be Java which I find too verbose/ slow to develop in). Or maybe Open Office Base and some scripting is sufficient to handle my needs.

So, my main question is: Does a web framework like Django sound like a reasonable platform to build a LAN Dashboard for a mid-sized company? Or am I thinking too much like a web developer?

Any tips or suggestions would be greatly appreciated.

---

### Post by PaulFr on 2009-08-12
While others may have better points in favor of their favorite development technology, I would urge you to consider:
[LIST]
[*]The skills the developer(s) have
[*]The timeframe this has to be developed in
[*]The skills the maintainer(s) / administrator(s) have
[/LIST]
Once these have been taken into account, any of the "modern" development technologies can be used for a dashboard.

---

### Post by yekibud on 2009-08-12
Hi, PaulFr.

Thanks for your reply.

[LIST]
[*]there is one developer (me) whose skills are strongest in PHP
[*]the maintainers would be my successors, so I wouldn't want to pick a "fringe" technology
[*]the time frame is somewhat flexible - the business is interested in making the best choice, even if that involves a longer development period
[/LIST]

At this point, the business is willing to consider some parallel development to make sure we are heading in the right direction.  So, I could leave the starting gate right now with a PHP/web-framework - but I have the opportunity to try out a different web-framework (e.g. Python/Django or RoR) to see if development turns out to be more rapid/ elegant/ maintainable.

But taking into account that I have the time/resources to try out a different technology - I was wondering whether a web-framework would really be appropriate for a the LAN dashboard app I described - or if I should try a different approach entirely?  The only requirement being that that technology be open source and cross-platform compatible.

---

### Post by yekibud on 2009-08-21
UPDATE

I've settled on the following answer(s) to this question:

- A web framework is appropriate for the application.  Just because your inside a LAN, doesn't been the technologies developed for websites do not still apply.  And the advantage of having a built-in cross-platform client (web browser) are huge.
- In terms of frameworks, I will have to modify Python/Django for my particular application, as it involves multiple DB/product connections.  RoR also doesn't offer any help in this regard.  But, I have encountered the web2py project - a framework based on Django and Rails, which has multi-db connectivity built in.
- I do not believe OOo is a real option.  It is too limited, from what I can tell.

---

