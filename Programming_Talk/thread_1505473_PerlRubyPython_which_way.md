---
title: "Perl/Ruby/Python which way?"
date: 2010-06-09
forum: Programming Talk
---

### Post by eroomydna on 2010-06-09
Hey guys,

I'm a DBA by trade using Ubuntu Desktop and administering RHEL5.4, Windows 2008, SQL Server and MySQL5.1. I'm developing my BASH skills day-to-day and I've been curious about other languages namely Ruby, Perl and Python.

I'm not really sure of the direction to take but am leaning more towards Ruby or Perl. As a linux based DBA, Perl would be a great feather in my cap as there's lots of tools written in perl but I also use Ruby on Rails so a deeper understanding of Ruby would also be advantageous. 

Please let me know your opinion.

Andy

---

### Post by Bachstelze on 2010-06-09
You've pretty much answered your own question. ;) If you have to work with a lot of Perl and Ruby tools, then it would probably be best to learn those langues, so you can for example modify those tools to better suit your need.

It really depends on what you want to do with it, for example Perl is mostly geared towars text manipulation, while Python is more of an all-around language, with a very extensive library to do a lot of things (network-aware, graphical or multithreaded applications, for exmaple).

---

### Post by shawnhcorey on 2010-06-09
I use Perl; here's why:

```
$ ruby -v
ruby 1.8.7 (2010-01-10 patchlevel 249) [powerpc-linux]
$ irb
irb(main):001:0> 1/2
=> 0
irb(main):002:0> exit
```

```
$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 15:32:38) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 1/2
0
>>> 
```

```
$ perl -ple '$_=eval'
1/2
0.5
exit

```

Perl is the only one that gets it right.

If you're interested in Perl, then check out the following:

[perl.org]("http://www.perl.org/") -- the official site for Perl.  Especially, look at their mailing lists.

[Perl Programming Documentation]("http://perldoc.perl.org/") -- an online resource of all the standard Perl documentation.

[CPAN]("http://www.cpan.org/")  -- Comprehensive Perl Archive Network, many, many modules for Perl

[PerlMonks]("http://perlmonks.org/")  -- for the really tough questions and very good answers

---

### Post by trent.josephsen on 2010-06-09
> **shawnhcorey said:**
> I use Perl; here's why:

<code snipped>

Perl is the only one that gets it right.


I find that floor division is much more useful with integers than floating point division.  In fact, my last Perl script had a "use integer" line in it for just that purpose.  YMMV.  Python3 is introducing a floor division operator // and making / do mathematical division, if I recall correctly, so no more complaints there (and you can do "from __future__ import division" to use this functionality in current Python versions).

On the whole, Perl is the most usefully expressive language I have ever used.  Python is probably suited to a wider range of applications.  Robotics comes to mind.  Ruby seems to be appealing to the same areas Perl dominates, but I don't know it myself.

But you won't know which one matches your style and needs best until you know them all.  Start with any of them, it doesn't matter, but learn all three and use them where they are most useful.

To shawnhcorey's links, I add [the Camel book](http://oreilly.com/catalog/9780596000271).

---

### Post by ja660k on 2010-06-09
> **shawnhcorey said:**
> I use Perl; here's why:

<code snipped>

```
$ perl -ple '$_=eval'
1/2
0.5
exit

```

Perl is the only one that gets it right.


your joking right?

Perl does alot of things auto-magically
In other languages; Ruby, Python
You need to tell it your using floating point numbers.

```

john@ubuntu:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 1.0/2.0
0.5
>>> 
john@ubuntu:~$ irb
irb(main):001:0> 1.0/2.0
=> 0.5
irb(main):002:0>
john@ubuntu:~$

```

---

### Post by Barrucadu on 2010-06-09
```
Python 3.1.2 (r312:79147, Apr  1 2010, 09:12:21)
[GCC 4.4.3 20100316 (prerelease)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 1/2
0.5
```

---

### Post by Bachstelze on 2010-06-09
Successful troll is successful.

---

### Post by ja660k on 2010-06-09
> **Bachstelze said:**
> Successful troll is successful.
:lolflag:

---

### Post by shawnhcorey on 2010-06-09
> **ja660k said:**
> your joking right?

Perl does alot of things auto-magically
In other languages; Ruby, Python
You need to tell it your using floating point numbers.

No.  Perl does it the way you were taught in elementary school.  You should have to do something different to get different results, not the other way around.  In this case, Perl is not auto-magical, Python and Ruby are.

---

### Post by ja660k on 2010-06-09
Ive got nothing against perl. But you made out such an example on why perl is so sweet...most languages are like the ruby python output.

java
```

System.out.println(1/2);
System.out.println(1.0/2.0);
0
0.5

```
C
```

printf("%d\n%0.1f",(1/2),(1.0/2.0));
0
0.5

```
i would do more, but i have no desire to keep arguing over something so trivial.

All im saying is dont choose a language because it outputs 0.5 instead of 0... when we tell it to return an integer.

---

### Post by shawnhcorey on 2010-06-09
> **ja660k said:**
> i would do more, but i have no desire to keep arguing over something so trivial.

All im saying is dont choose a language because it outputs 0.5 instead of 0... when we tell it to return an integer.

And I'm saying to choose a language that is based on the way you think, not on some artificial criteria.  Many of the "modern" languages come from a time when not every CPU had a built-in floating-point arithmetic process.  Integer math was used as default in those languages.  The question is why do modern languages like Python and Ruby carry this legacy?

Yes, integer math is a trivial example but it reflective of the design philosophy; that the programmer must conform to the language, not the language to the programmer.  Perl's motto is There Is More Than One Way To Do It.  And Perl does its best to allow you to do it your way.

And yes, I know Perl has its flaws, the sigil being the worst offender.  Of course, if your background is in shell programmer, you at least are familiar with it.  But of the three languages mentioned, Perl is the one that will easily conform to your programming style.

---

### Post by Luke has no name on 2010-06-17
Came in to say that perl is not a fun language to look at. The poster complaining that integer division isn't "natural" is a troll, too lazy to type a ".0" for floating point division, and in any case, chooses languages for the wrong reasons.

Read some perl code, read some python code, and read some ruby code.

IMO, Ruby is a nice language to look at, and is just as capable as a language (with std libs) as Python or Perl as a system language. I want to get our Unix scripting tasks on Ruby.

---

### Post by DanielWaterworth on 2010-06-17
I really like python and I use it all the time, but I think ruby has some good features too. Perl's ok, but I wouldn't use it for anything bigger than 100 lines.

---

