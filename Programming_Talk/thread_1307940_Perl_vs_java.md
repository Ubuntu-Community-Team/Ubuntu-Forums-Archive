---
title: "Perl vs java?"
date: 2009-10-31
forum: Programming Talk
---

### Post by JayKay3000 on 2009-10-31
Well, i'm currently browsing the net to try and answer for this as i'm writing and assignment for uni. Well. final year project.

So what is the advantage of writing a program in one or the other?


The program I am planning to write will keep a computerised backup of a plan of our uni network and where all ports are plugged in, etc. It will load data from flat files, compare files, create backups, enable users to log in and keep a paper trail of their usage so that other users can see who changed what while being able to revert to old working versions if someone changes something in the real network and breaks it.


So... your thoughts. To me there does not seem to be much difference, faster to make programs in perl and less strict but ive never used perl so... 

If anyone knows any links to any good articles or anything discussing this. I'll keep hunting though, infact I think i'll moove to a diff planning part as i've been on this point for quite a while.

I've been looking at

[http://oss.oetiker.ch/mrtg/index.en.html](http://oss.oetiker.ch/mrtg/index.en.html)

Which is designed to interrogate network switches via SNMP (which is the 2nd part to my project) and it written in perl so that's why i'm overall a bit stumped.

---

### Post by froggyswamp on 2009-10-31
Java will range from slightly slower to much faster depending on what exactly you're benchmarking, will scale better, but will take more memory and has a slower startup, amen.

---

### Post by 0cton on 2009-10-31
I would recommend Java as well for such a project.
perl is more of a scripting language isn't not suited for that type of project (not impossible thought)

---

### Post by slavik on 2009-10-31
if you're using flat files, Perl all the way. Perl also doesn't throw up like Java does on large inputs.

and always use strict in Perl.

---

### Post by myrtle1908 on 2009-10-31
> **0cton said:**
> I would recommend Java as well for such a project.
perl is more of a scripting language isn't not suited for that type of project (not impossible thought)

I disagree.  Perl is perfectly suited to system/network administration.  Far more so than Java.  There are countless Perl modules that deal with SNMP etc.  Search CPAN or look here [http://net-snmp.sourceforge.net/](http://net-snmp.sourceforge.net/)

For *any* kind of text parsing, Perl flogs Java hands down.  Trust me you don't want to do serious text parsing in Java it is a nightmare.

If you were to opt for Java here then be prepared to write *alot* of code.

And do take Slavik's advice, if you use Perl always use strict (and warnings).

---

### Post by A_Fiachra on 2009-11-01
> **JayKay3000 said:**
> ...

It will load data from flat files, compare files, create backups, enable users to log in and keep a paper trail of their usage so that other users can see who changed what while being able to revert to old working versions if someone changes something in the real network and breaks it.



Perl hands down.

There is a decent book, "Perl for System Administrators"

Doing system administration in java is like using a Winnebago to cut grass.

---

### Post by A_Fiachra on 2009-11-01
> **0cton said:**
> I would recommend Java as well for such a project.
perl is more of a scripting language isn't not suited for that type of project (not impossible thought)


What does Java offer for system administration that is even remotely close to Perl??

Perl has been called the Swiss Army Chainsaw of Unix utilities -- why would anyone use a quasi-compiled, typed, OO language that requires a VM for a basic set of system tools?

Did you think before you responded or are you just another fanboy?

---

### Post by albandy on 2009-11-01
I'm a java programmer and if I were you I'll use perl for this stuff.

Java should not be used for system administration, of course java brings you things as jpa and ejb, and thousands of classes for do what you want in an easy way, but you should realize of the requeriments of your project.

---

### Post by JayKay3000 on 2009-11-02
Cheers for the input guys. I was going to type 'i'm more confused than ever' oh wait. I just did :D. 

But seriousley I think based on what you say I think I better understand to what perl can be suited for and what java can be suited for.

Great to get some real feedback, articles on the net get a bit vague sometimes.

We learnt java in uni but I think I will have a look at perl in a bit more detail anyway. I nearly brought a book on it the other day. It definatley looks interesting but the 'you can do one thing a thousand ways scares me a little'

Without trying to start a flame war, i've read that everything you can do in perl you can do in java, then again they say everything you can do in java you can do in C++ so that may have been a throw away comment.

Again. Thanks for the input.

---

### Post by Shin_Gouki2501 on 2009-11-02
exactly the point, you have to choose what language/framework is appropriate for the problem and then also what you can learn/use easy.

That's not easy to decide since you have to code and not anyone who writes here.

Maybe look at sample implementations of important sub problems for your project and see where you can grasp concepts and such the best way.

regards Andreas

---

### Post by fiddler616 on 2009-11-02
Java's good at applications (for example, most of OpenOffice is written in Java).

Perl's good at quick and easy system administration, but (from what I understand) gets kind of hard to deal with for huge programs. ESR himself said that Perl was only good for <100 lines of code (although those hundred lines may be pretty packed).

---

### Post by Arndt on 2009-11-03
> **fiddler616 said:**
> Java's good at applications (for example, most of OpenOffice is written in Java).

Perl's good at quick and easy system administration, but (from what I understand) gets kind of hard to deal with for huge programs. ESR himself said that Perl was only good for <100 lines of code (although those hundred lines may be pretty packed).

If it's going to be a large project, it may make sense to do some parts in Perl and some in Java. The drawback is that you would need to know both these languages quite well. The plus side is that after such a project, you will know both languages quite well.

---

### Post by SunSpyda on 2009-11-03
> **fiddler616 said:**
> Java's good at applications (for example, most of OpenOffice is written in Java).

OOo is written in C++, with no Java dependencies. It's a *very* common myth due to the fact Sun is both behind Java & OOo.

Anyhow, I believe is getting the right tool for the job. Sure, you *could* write a massive GUI application in Perl, or a system maintaining tool in Java, but you wouldn't.

---

### Post by 0cton on 2009-11-03
OpenOffice is not mainly written in java, it's based on Star Office that was bought by sun, it has some java modules in it, but it's mainly written in C++.

---

