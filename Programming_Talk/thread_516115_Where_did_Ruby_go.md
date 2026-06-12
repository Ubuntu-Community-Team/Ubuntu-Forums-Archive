---
title: "Where did Ruby go?"
date: 2007-08-02
forum: Programming Talk
---

### Post by Garou on 2007-08-02
Has Ruby's popularity, or should I say hype, dissipated?

A year ago all you could read about was ruby this, and ruby that. Ruby on Rails and 37signals. Now we hear... crickets.

A year ago I was very active with Ruby, but have since almost forgotten about it.

Who here uses Ruby?

---

### Post by Geekkit on 2007-08-02
What's Ruby?

*hops in time machine, goes back to 1993*

Ohhh ... Ruby. Sorry guy, Ruby didn't make it. They forgot to unplug life support.

---

### Post by pmasiar on 2007-08-02
2 years ago Ruby was the only game in the town for rapid web app frameworks. Not anymore. Python has 2 or 3 (Django, Turbogears, and maybe Pylons - but Pylons is different) frameworks as good and rapid as Ruby ever was. Even Java is making noises that not all frameworks needs be oversomplicated monsters like Struts 1.0. Rails has couple very radical ideas ("convention instead of configuration" is truly brilliant) but Python was able to repurpose them - and Python community is huge, hackers are smart, and need for better solutions was dire.

Another way to make nicer, more responsive web apps is AJAX and friends (JSON, AHAH etc). To avoid handling javascript idiosyncracies and quirks in implementations in different browsers, you need to generage JS instead of hand-crafting it. So JS libraries were created: Yahoo, Google have their own, and many more. ZK framework for Java is brilliant idea in this area - let's process JS events on server, in Java! 

People realized that even with RoR, someone needs to write code, and it is lots of learning how.

---

### Post by Note360 on 2007-08-02
Ruby is good all around I like some rubisms compared to pythonisms, but i find my self drawn to python for some reason. I don't know why.

---

### Post by skeeterbug on 2007-08-03
> **Garou said:**
> Has Ruby's popularity, or should I say hype, dissipated?

A year ago all you could read about was ruby this, and ruby that. Ruby on Rails and 37signals. Now we hear... crickets.

A year ago I was very active with Ruby, but have since almost forgotten about it.

Who here uses Ruby?

If you check out the official RoR blog it is pretty dead with comments too (only a handful). I think their problem is they touted everything in the framework as being so easy and fast to develop. When you run into the special needs of application you suddenly don't know what to do, or it doesn't work for crap.

At my day job we do C#/ASP.NET (Yes I know, the devil made it). We were looking to do rails for a web service API, sitting on top of SQL Server. Just because they have an adapter for SQL Server doesn't mean it works right! You can't upload binary objects larger than 50k into the database, along with a few other problems, like failing to handle reserved names. We ended up doing it in .NET using LLBLGen (old faithful for us).

If you take a look at DJango, it offers the same as RoR, plus more. The admin section is brilliant, and can be used in production, you can't say the same about rails scaffolds, can you? Plus like someone said, the Python community is bigger. The rails framework also got people started in the framework without actually learning ruby first (I am sure this made for some great maintainable code).

---

### Post by pmasiar on 2007-08-03
And another half-bit :-) of info about community. Big part of Ruby deep development discussion is on mail-list in Japanese :-( (which will obviously limit access :-) for many free software developers ) because [Matz](http://en.wikipedia.org/wiki/Yukihiro_Matsumoto) likes it so. Compared to that, Python's Guido is Dutch, much easier to learn :-)

---

### Post by elst on 2007-08-05
I suspect that part of the reason that the buzz has fallen off is that Rails is the only really big app for Ruby. Rails hasn't had a release in a while as the devs are working on Rails 2.0, and many early adopters have now tried Rails and come to a conclusion about it - either that it was right for them or it wasn't. So the Rails hype period is over, and there isn't so much to talk about there right now. Ruby 2 is still in development and  won't be out until December.

Python is semi-officially the development language for Ubuntu, and I think that these forums reflect that. Not a bad thing at all, but it does mean that there is more discussion of Python here. Ruby and Rails folks have their own hang-outs, and you can probably gauge the health of those projects better by asking in those places. I get the impression that it's good - new projects are still being delivered in RoR and the conferences are still filling up.

---

