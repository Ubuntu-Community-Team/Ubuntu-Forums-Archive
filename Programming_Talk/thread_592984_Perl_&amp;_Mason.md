---
title: "Perl &amp; Mason?"
date: 2007-10-26
forum: Programming Talk
---

### Post by ThinkBuntu on 2007-10-26
The number of [big-time websites on this list ]("http://www.masonhq.com/?MasonPoweredSites")that run primarily on Perl and the Mason framework is staggering. Why is it that we seldom hear about Perl in the web development world? It's always PHP, .NET, Java, and Ruby or Python, but never Perl. And it's not as if most small shared hosts offer a proper environment for any of these but PHP (on occasion, Perl or ASP are offered).

---

### Post by skeeterbug on 2007-10-26
> **ThinkBuntu said:**
> The number of [big-time websites on this list ]("http://www.masonhq.com/?MasonPoweredSites")that run primarily on Perl and the Mason framework is staggering. Why is it that we seldom hear about Perl in the web development world? It's always PHP, .NET, Java, and Ruby or Python, but never Perl. And it's not as if most small shared hosts offer a proper environment for any of these but PHP (on occasion, Perl or ASP are offered).

Probably because Perl was old faithful when the web came out. .NET didn't even come around until, what, 2001? When Java came out it wasn't a really a web framework. So why would they switch? They have teams of Perl devs and a huge community for support.

On that note, it is much easier for people to get started with Django, Ruby on Rails, or PHP than it is with Perl. Perl gives so many choices (Mason is one of the many template systems) that it can be hard for a newcomer to pick something and stick with it.

---

### Post by ThinkBuntu on 2007-10-26
[http://del.icio.us/](http://del.icio.us/)

founded in 2003

---

### Post by ThinkBuntu on 2007-10-27
Craigslist also runs almost entirely on Perl. I'm beginning to take Perl as a serious alternative for Java and .NET on the enterprise level...

[http://www.craigslist.org/about/thanks.html](http://www.craigslist.org/about/thanks.html)

---

### Post by pmasiar on 2007-10-27
Perl is past prime now. 8 years ago, Perl was the duck tape which hold Internet together, but not any more. Most new projects skip over Perl and use Python or Ruby. Because those languages are much cleaner and better designed, programming in them is much simpler. FOr Perl, you need real guru. In ruby or Python, average programmers can be productive too.

Java, as statically typed, is completely different game.

---

### Post by slavik on 2007-10-27
PHP is "Perl made for web programming"

Slashdot is also in Perl, so is bash.org

I started doing some PHP programming (for learning purposes) and I find that with docs it is easy, except for the difference between isset() and defined() (so far). But some things are much simpler, like using a database.

---

### Post by arist0tle on 2008-07-11
I am a Perl web developer and I will say this....people who say that perl is old and past its prime are out of their minds. pmasiar has no idea what he/she is talking about and ripped that 'duct tape' line straight off another site. Perl has something that none of those other languages have....CPAN. CPAN will ensure that Perl is around for a long time. Not to mention Perl is faster than Python, Ruby, and PHP; more flexible; and more expressive.

---

### Post by pmasiar on 2008-07-12
> **arist0tle said:**
> people who say that perl is old and past its prime are out of their minds. pmasiar has no idea what he/she is talking about

I was founding member (back in 2002) and first host for "Best Practices of CGI::Application", yet another (more lightweight) CGI framework for Perl, so I might have a little clue :-)

> Perl has something that none of those other languages have....CPAN.

Python has CheeseShop module repository. Perl people forgot to patent the concept of code repository, so anyone can do it - and any project does, so... you IMHO just proved that it's **you** who has no idea what he/she is talking about :-)

>  CPAN will ensure that Perl is around for a long time.

CPAN cannot do that - only people prefer to use Perl in production applications do. They are less and less abundant these days - many new people look at Perl and say "yuck". Python has almost the same features, less quirks, and cleaner OOP and exceptions.

> Not to mention Perl is faster than Python, Ruby, and PHP; more flexible; and more expressive.

Irrelevant: Perl is dead, because Perl6 is dead. Most new developers moved to Python and Ruby, because those languages (and web application frameworks for them) are easier to learn and more productive.

Of course Perl projects would be maintained for decades, COBOL is even more obsolete and yet COBOL code still runs, and even more is added. Perl is dead in sense as COBOL is dead: there are better tools to solve those problems now.

Our own Perl project is being reevaluated as old server is being retired after 7 years; rewriting in Java is probably too expensive, so we just upgrade server and do minimal changes, but boss will never ever let Perl be used in any project, and what is worse, Python got the bad rap too and Java was selected as standard. In our dept, Perl is as dead as it can be.

Perl makes sense for experienced sysadmin who knows bash, awk and other system utilities (who were first Perl audience). For a person without this experience, Perl is ugly and quirky - and not OOP enough.

Show me a company supporting new development in Perl? Supporting development of the language?

I would prefer further discussion about current and future status of Perl to continue in context: in [ Why I love/hate Perl](http://ubuntuforums.org/showthread.php?t=577596) to avoid repeating same arguments again and again

---

### Post by myrtle1908 on 2008-07-12
Perl is a fantastic tool and very good at what it does best ie. munging text, statistical analysis, getting simple things very quickly, one-liners etc. 

It once was the king of the internet and, as *pmasiar* has pointed out, was touted as the "duct-tape" that held the world wide web together.  To some degree it still does.

Those of us are that were fortunate enough to learn this tool many moons ago will always have a use for Perl.  I'm a Java programmer but use Perl almost every day.

Perl is used very heavily today in the medical/scientific world and I doubt this will change.  It is brilliant at statistical analysis of arbitrary data.

Perl6 development I have not followed for some time so cannot comment on this.  What ever happened to Parrot?

Anyone remeber $Bill, Jenda, Randall etc from the old perl boards/lists?  Are those guys still around?  Ahh the memories.

---

