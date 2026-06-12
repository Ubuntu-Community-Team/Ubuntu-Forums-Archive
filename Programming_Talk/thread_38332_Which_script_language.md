---
title: "Which script language?"
date: 2005-05-31
forum: Programming Talk
---

### Post by kimes on 2005-05-31
ye.. I know.. It's sort of very long discussed topic..
but I wanna know you ubunbu guys' opinion..

and I also wanna focus only on 'Perl vs Python'..

Which is better to learn..?
Which can be more helpful for future?
(I really want to study about computer science deeply)

tell me ur opinions..
Many thanks to only ones who post reply  :razz:

---

### Post by SNo0py on 2005-05-31
[http://www.google.at/search?q=perl+vs+python&submit=Go](http://www.google.at/search?q=perl+vs+python&submit=Go)

---

### Post by vague- on 2005-05-31
Perl has a certain credibility and feel to it that makes it unique.  That said, Python is one of the easiest to use languages that I have ever learnt.  Python is a real boom for productivity (and is more maintainable than a lot of common Perl "styles") - so it wins.  To me Perl's "There's More Than One Way To Do It" is both it's crowning glory and it's downfall.  There was a time when I would have said CPAN still left Perl the more easily useful of the two, but I am no longer sure that Python does not rival CPAN with a blooming supply of third party libraries.

I still perceive Perl as the "faster" of the two languages - though I have no evidence either way, and I know improvements such as Psyco really helped Python long before it helped itself.  I am not sure where this stigma comes from.  I tend to think: Perl is unmaintable; Python hogs the CPU; Java hogs the memory.  Each of these is less true - except that Perl needs to be rewritten now people recognise the constructs that make it unmaintable, the other two just gain each time their VM is updated.

As a side note, I now use Awk to do what Perl has done for me in file processing - using Python for the other tasks.  I find Awk's stricter semantics to give me what I want of Perl, without the bits I don't like - though, I am not one of these people who will write a 10KLoC Awk script.  I also tend to still use Bourne Shell over Python for small tasks.

Anyway, sorry for the babble: Python!

---

### Post by jerome bettis on 2005-05-31
if you scroll down in this forum a little bit you'll find a thread "a casual talk on python"

in there there's a link to a good article by a guy who was using perl but ended up using python and was able to do stuff quicker.  i don't know perl but it looks like a PITA to program in ... lots of bizzare syntax and such.  python is nice and clean.

---

### Post by jdonnell on 2005-05-31
Your forgot ruby :)

---

### Post by nobodysbusiness on 2005-06-01
Right now, I believe most of the momentum is behind languages like Python and Ruby. I've played a bit with Perl, and I don't think it's going to be the tool of choice for most people a few more years from now.

---

### Post by wtd on 2005-06-01
[QUOTE=nobodysbusiness]Right now, I believe most of the momentum is behind languages like Python and Ruby. I've played a bit with Perl, and I don't think it's going to be the tool of choice for most people a few more years from now.[/QUOTE]

Perl will be around and popular for a very long time.  When I recently whipped up a dynamic site for a friend, I used Perl and SSI even though I'd much rather have used Ruby.  Why?  Because I know they can take that and use it with just about any host out there.

---

### Post by SNo0py on 2005-06-02
Yeah, I absolutely agree! The problem is that ruby and all that other exotic languages are not installed on the hosters out there - and they won't install it...

So you have to use Perl or PHP... and most of us have to maintain old web applications, which use Perl or PHP, so there is no chance of rewriting everything in Ruby, just because it's cool...

---

### Post by vague- on 2005-06-02
I do not do many web applications, so that is something I hadn't considered.  I by far prefer Perl over PHP.  Java web applications are probably some of the easiest to build, but suffer the support that Ruby and Python do.  Maybe people should be ranking the scripting languages...

---

### Post by SNo0py on 2005-06-02
[QUOTE=vague-]I do not do many web applications, so that is something I hadn't considered.  I by far prefer Perl over PHP.  Java web applications are probably some of the easiest to build, but suffer the support that Ruby and Python do.  Maybe people should be ranking the scripting languages...[/QUOTE]
Yeah, and that's now the religious war... because I prefer PHP over Perl *and* Perl over PHP. The question is why and when:

PHP over Perl: for Web applications, because PHP has been designed for the Web and therefore it's much simplere to create Web applications.

Perl over PHP: for scripts that run on the server, because Perl has been designed as a scripting language and then been extended to also be used as Web language.

Regarding Java I disagree - Java Applications are great, powerful and fast, but they are not really easy to build and it does not make sense to create a small Web page using Java. But for larger applications the Rational Application Developer is really great. And there is a lot of support available, as it is for all other languages...

---

### Post by vague- on 2005-06-02
To clarify, the support issues that I refer to meant the amount of providers of hosting that offer these services.  PHP and Perl are provided from the lowest, cheapest provider right through to enterprise.  Ruby seems particularly rare, and mod_python is doing that much better.  Obviously, you can run most of these through CGI if that is allowed.

Java does not suffer much from being unavailable, in as much as it suffers the cost of the hosting available.  Decent Java hosting tends to be more expensive than you could satisfy your needs elsewhere.

You say that Java (and I assume, JSP) is good for rapid application development - surely that supports my claim that it is fairly easy rather than contradicts it.  If you have rapid development at any level, then you can benefit largely at the lower levels.  With the taglibs available now, you can often write JSP sites without writing any actual Java - and the well-mandated system for application layout means that you are less likely to have a deployment issue.  JSP with taglibs is often little beyond writing the actual HTML - I cannot see how that does not at least compete with other languages that offer interspersed formats (PHP, Mason, PSP, etc.).

---

### Post by SNo0py on 2005-06-02
Hi vague-!

Yeah, you are right regarding the hosting providers. But this problem is clear for me -  PHP and Perl need much less CPU power compared to an Websphere Server and secondly the scripting languages are easier to learn. You can't really compare an enterprise system (Websphere) with a LAMP system - that's unfair. And it's clear that advanced technologies are more expensive because they are not used so much by private people to create their homepages. Really, which private user wants to invest the money to buy Websphere?

With Java I not only refer to JSP, but to the whole J2EE environment - Websphere or even the Tomcat application servers with servlets and all that stuff. JSP is just for displaying the data - I would not recommend writing an application with JSP in the style that you normally use with PHP. And here is the difference - as private person I want to have results very fast and I don't want to think about an architecture and how to structure my application... that's the reason why Java is not so popular and thus so expensive.

---

### Post by wulf on 2005-06-02
If you're just planning to learn in a speculative fashion rather than to solve any particular problem (and there's nothing wrong with that), why not delve into both. I've found the O'Reilly book, *Learning Perl* to be helpful in getting me to the stage where I can write simple but effective utility scripts in that language and I suspect they've got a comparable, Python based offering.

Try both and, once you've got the basic vocabulary for each, try to solve a few problems using both languages and gauge which one **you** prefer.

Wulf

---

