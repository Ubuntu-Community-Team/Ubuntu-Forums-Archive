---
title: "Good modern web framework, for a quick but fairly fully functioning site?"
date: 2015-01-02
forum: Programming Talk
---

### Post by F.G. on 2015-01-02
Hi All,

I'm planning to start a small project, and am looking for a new webframework to get stuck into. I'm familiar with ruby on rails, groovy on grails, Spring 3 and a couple of others. I was wondering what current new-ish web frameworks people would recommend?

Project will need:
 - unit testing
 - MVC type architecture
 - support for either postgres or mySql
 - out of the box boiler plate code to kickstart the thing
 - to be based around a scripting language (ruby/python/php/perl, etc)
 - CMS

Project won't need to be scalable, won't need that much functionality, i'm going to have registration and messaging to the administrator, I'd ideally like the option to include a paypal payment method at a later date (not essential), but that's about it. Basically looking for something interesting that also wont be too absorbing / take too much of my time. Thanks for any suggestions.

regards,
FG

---

### Post by TheFu on 2015-01-02
RoR is hard to beat in terms of productivity, if you don't need to scale too much or need it on the internet where security matters.
Python has a few nice frameworks, I hear. I don't do python, so no personal experience. [https://wiki.python.org/moin/WebFrameworks](https://wiki.python.org/moin/WebFrameworks) has a list. If you  ask about any specific one listed, someone might respond.

Serious Perl devs use Catalyst, but that is a 6 month commitment to come up to speed.  Perl Dancer is much quicker to get started, if a little slow (slow perl is still faster than most others).   Perl frameworks don't include a ORM, but you can use any that you like. There are a few other Perl frameworks - some are self contained, Mojolicious, to minimize CPAN dependencies. Be certain to use perlbrew. It is like RVM in Ruby-land.  A simple, 1-table, CRUD app is about 10 lines with SimpleCRUD.  I'd used Dancer and Dancer2 for the last few years. Dancer2 isn't quite ready for production use. Dancer is fairly easy to get started with if you already know Perl. I love how the request can get XML, JSON, HTML or whatever other filter you create. The 1st 3 are built-in.  
With CPAN, anything can be accomplished without re-inventing the wheel. Almost all modules there are extremely high quality, tested on thousands of deployments, across many different platforms and perl versions.  Perl has migrated to OOP over the last 5 years, so most of these frameworks require using Moose or Moo - if you don't know Perl already, it can be a steep learning curve [TIMTOWTDI ]("http://en.wikipedia.org/wiki/There%27s_more_than_one_way_to_do_it")can be frustrating to new mongers.  It that is an issue, go with Python.  Perl is designed as a language, so there are different ways to accomplish different tasks, sometimes many, many, different ways.

CMS?  Uh - that doesn't have anything to do with any web frameworks that I know. You'd write a CMS using these. None come with a CMS.

I'd avoid php for now and the foreseeable future due to security.  Posted an interesting internet study yesterday in "OS Chat" that [shows 78% of all php websites are not secure.]("http://ubuntuforums.org/showthread.php?t=2259060")  Perl and Python have much better showings - still too many, but ... 

Most folks are using [TDD]("http://en.wikipedia.org/wiki/Test-driven_development") these days.  Both Perl and Python have embraced that method, so there are many tools available that work well in support. Ruby does too, for any lurkers, though I find that maintaining ruby gems on a deployment to be hard due to huge RAM requirements (why is that?).

Anyway - have fun.  There are local [perl]("http://www.pm.org/") and python groups who want to help people learn.  Lots of online help too.

---

### Post by F.G. on 2015-01-02
Hi TheFu,

Thanks for your comments, i'll certainly give perl dancer a look. I don't really know perl, but have hacked together a few scripts in it before (for work), so this could be a good oportunity fo consolidate that knowledge. Otherwise I might just stick with RoR, as while I know it better it's been a few years since i did any rails development. Regarding CMSs I had thought that various modern frameworks had plugins (like [this]("http://en.wikipedia.org/wiki/Refinery_CMS") kind of thing for rails) for writing a CMS into your web pages. I have not used anything like it though, so don't know how it works. Alas everything I do for work uses in house tools.

Most other code that i have looked at is legacy stuff, buggy, not clearly layed out, and without tests, i'm hoping that for this project i'm going to be able to keep it clean and maybe unlearn some bad habits! Now you mention it, I will steer clear of php, I do recall at least one recent exploit coming to light.

thanks again for your suggestions,
FG

---

### Post by TheFu on 2015-01-02
Modern Perl isn't something you can hack together without significant background learning first. There is a free book by Chromatic - **Modern Perl** - get it, read it, know it.  By following these idioms, you'll avoid most of the complaints about perl being a write-once language.  There are also many tools to help you write better perl code - the PerlCritic module is one.  It will point out when you've done something considered poor style or hard to maintain. There's a book on that too - **Perl Best Practices** which the perl critic module follows.  There are a few intermediate and advanced perl books out there too.  I can recommend Brian Foy's **Mastering Perl**.  Plus Brian is a great guy, had dinner with him a few months ago.

I assume you will be going with Perl 5.20-ish and not the base install perl on the system which is really, really, out of date or Perl6 which really is a completely different language and needs a beginner level intro when ready for production at Xmas (we just don't know which Xmas Larry will release it).

Perl is like English.  It can be terse or verbose.  The same thing can be said 20+ different ways. Sometimes pronouns are used, but not always.  I'm convinced that Shakespeare would use Perl, not Ruby, not Python, not Php. The choice of words in Perl is amazing, which can lead to frustration if for people unwilling to move to the master level of knowledge.  The perl language isn't there to tell you how to program - that is your decision.  OTOH, I can't think of anything which cannot be solve through a perl solution.  That doesn't mean that perl is the best answer always, just that it is very flexible.

There is always python, which is a great language too (except the whitespace dependencies drive me crazy).

Oh - and I've never heard of anything like RefineryCMS, but CMS isn't my primary area.  I worked in document management for years, but that is different from webCMS stuff.

---

### Post by dragonfly41 on 2015-01-02
To balance the picture you could look at laravel MVC framework (PHP).

[http://laravel.com/](http://laravel.com/)

---

