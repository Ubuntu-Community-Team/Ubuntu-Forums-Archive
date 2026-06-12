---
title: "What attributes differs a good Code Manager from a bad one?"
date: 2008-07-11
forum: Programming Talk
---

### Post by jingo811 on 2008-07-11
What attributes differs a good Code Manager from a bad one?  Is it a matter of who is the most technically competent individual?
How can you test if a person should or should not take the role as a Code Manager?

Does the use of revision control systems (SCM's) make Code Managers unnecessary in a project?

---

### Post by tinny on 2008-07-11
> **jingo811 said:**
> Code Managers unnecessary in a project?

Yes.

This can be addessed at recruitment time. Employ above average developers implement a [peer review]("http://javasoapbox.blogspot.com/2008/06/code-reviews-101.html") strategy and you essentially get a team of "Code Managers".

---

### Post by pmasiar on 2008-07-11
What is Code Manager supposed to do?

Use some XP process like a Scrum, agile, etc, where roles of participant are defined by output of production code - and you will have the role, function, and way to measure the output.

C2.com pattern repository (the original wiki) has all the links you need to get started - and double-check with wikipedia.

---

### Post by tinny on 2008-07-11
I wonder if the OP means "Build Master"?

---

### Post by kavon89 on 2008-07-12
> **jingo811 said:**
> What attributes differs a good Code Manager from a bad one?

I would assume one proficient with the Copy, Cut, and Paste commands of their preferred operating system would be able to manage all of the code in their respective text files quite well.

Seriously, what is a Code Manager? Wouldn't the team of developers just use an SVN or something to manage the project?

---

### Post by skeeterbug on 2008-07-12
> **jingo811 said:**
> What attributes differs a good Code Manager from a bad one?  Is it a matter of who is the most technically competent individual?
How can you test if a person should or should not take the role as a Code Manager?

Does the use of revision control systems (SCM's) make Code Managers unnecessary in a project?

Are you referring to the lead developer?

---

### Post by jingo811 on 2008-07-12
I had this teacher who said that he once worked as a "CM" (Code Manager) in the past in projects using C.  He didn't say much more than this so I got curious.  From what I understand a CM is the spider who directs to junior coders what they should code and are responsible for the bigger picture of the project.

He didn't work in the US as a CM so the meaning of the word might have gotten lost in translation, it usually does with European countries.
I really don't know the difference between a "Code Manager", a "Build Master" or a "Lead Developer" :confused: Is it a case of same thing but different titles?

Anyhow back then I asked the teacher if the use of a CVS would make a Code Manager unnecessary?  
He answered NO a CM is still necessary when you use CVS's but he didn't explain why.  That's why I'm curious.
(I don't know anything about CVS's but I'm curious of how it works practically)

---

### Post by drubin on 2008-07-12
Code Manager sounds exactly like a lead Developer...

---

### Post by jingo811 on 2008-07-12
So what attributes differs a good Lead Developer from a bad one? Is it a matter of who is the most technically competent individual?

Can there be several Lead Developers working on the same project or would that create too much conflicts?
(Too many chefs doesn't make a good soup as the saying goes?)

How can you test if a person should or should not take the role as a Lead Developer?

---

### Post by rbprogrammer on 2008-07-12
I thought the original poster saying the words "Code Manager" meant Integrated Development Environment ( IDE ).

If thats true, to me I think a bad IDE is one that tries to eliminate the programmer by automatically generating code itself.  At times it may be faster, more efficient, or even easier.  But if a problem arises, the programmer might not be "qualified" enough to know how to fix it in an efficient manner.

To me a good IDE is one that allows total control to the programmer.  Even the compilation process.  I mean how many people really know how to use a compiler? And not just push the button "Compile"...

---

### Post by pmasiar on 2008-07-12
As I said, C2.com has better answers about project management that you can get from here - most people around are students and have zero industry experience.

Try first read at least relevant wikipedia pages to establish vocabulary so you can ask meaningful questions.

---

### Post by imdano on 2008-07-13
Well, I just finished school and entered industry, so I'll throw in my two cents based on what I've observed in my short time there.

I started a few weeks ago with a very large information management/storage company in a software engineering position.  I work with a group that is creating a new storage product for the company, in some areas utilizing existing code and in others implementing it from scratch. The project is split into two main teams, one that's mostly responsible for interaction with networked clients making use of the product (data path), and another (control path) which is responsible for managing the product itself.  I work with the control path team, which is also split into quite a few smaller projects (GUI, CLI, UI-toolkit, management protocol, storage services, etc.).

At the top is the manager in charge of the product itself.  He's responsible for making sure the product is released on time and is up to standards, etc.  He writes no code, and is separated by those who do by another level of management.

Each of the two sub-teams teams has a manager.  Like the product manager, they don't write any code, though most of them used to be developers.  They're responsible for a team of developers, and it is up to them to assign work to each of them.

Each of the projects within the sub-teams has a project lead.  They are senior level developers, so they still write code.  They have the added responsibility of planning how the component their team is assigned is going to be implemented, and assigning work to the developers working under them.  It's not as formal a leadership position as an actual manager, though those who find themselves liking the management aspects more than the technical (and want to make more money) might eventually make the switch.

Then at the bottom are folks like me who work in these subteams, and are assigned features to implement.  We don't manage anyone. :)

This is a bit of a simplification; there are a lot of other people involved, like architects, QA, release engineers, etc. that aren't actually developers, but are still very much involved in the development process.  And although the two main sub-teams and the projects within them are technically separate, they are still all working closely together, since at some point all of their code needs to interact.  While someone in the GUI team may not know all the inner workings of the logging framework, they need to understand how to make use of its API.

The "Code Manager" position you describe is probably closest to the sub-team management positions.  They aren't writing code, but are working very closely with all the project teams under them, setting goals for each team and each developer with them.  They're the ones who decide who is working where, and all design decisions are going through them.  They make sure everyone under them has the tools they need, are communicating well, and are staying on schedule.  My boss mentioned to me that he gets an average of one email per minute, and around 500 total per day, to give you an idea of the amount of info they're dealing with.

A lead developer position, where you have someone making most of the project design decisions as well as writing a lot of the code, doesn't really exist in this setup.  It's something you see in a lot of OSS projects, and maybe smaller commercial products.

Kind of a long-winded reply, but it hopefully gives you an idea of what one possible hierarchy is like within the development industry.  I interned at another large company last summer that had a very similar setup, so its probably a fairly common way to do it.

---

### Post by jingo811 on 2008-07-13
Thanks that helped me put the dot on the map somehow.  Now I just have to try and get my hands dirty so I can understand it practically.

---

### Post by pmasiar on 2008-07-13
> **imdano said:**
> Each of the two sub-teams teams has a manager.  Like the product manager, they don't write any code, though most of them used to be developers. ...(and want to make more money) might eventually make the switch.


Company like Google would ROFLMAO in such hierarchy. Seems like [http://en.wikipedia.org/wiki/Peter_Principle](http://en.wikipedia.org/wiki/Peter_Principle) company . Good luck there!

---

### Post by CptPicard on 2008-07-13
Is that some sort of a [Führerprinzip]("http://en.wikipedia.org/wiki/F%C3%BChrerprinzip") of software development? :confused:

---

### Post by imdano on 2008-07-13
Well, you're dealing with 2 former developers out of the 50+ or whatever it is working on the project, and I know at least one of them went back to school to get his MBA before getting the management job.  The company is one of the industry leaders in storage and virtualization, so this set up seems to be working out pretty well for them.

Also, [some people](http://1-800-magic.blogspot.com/2008/06/back-to-microsoft.html) (not saying I do, can't say without experienceing both) actually prefer the more traditional heirarchy over the Google style.

---

### Post by tinny on 2008-07-13
> **imdano said:**
> Also, [some people](http://1-800-magic.blogspot.com/2008/06/back-to-microsoft.html) (not saying I do, can't say without experienceing both) actually prefer the more traditional heirarchy over the Google style.

Probably not the best idea to use the most archaic software company in the world as a reference.

Also I think the people that like it are also generally at the top of these sorts of hierarchy's and not truly representative of a development team. (Id imagine that most dictators in the world are quite happy)

---

### Post by imdano on 2008-07-13
Well, it doesn't really matter *where* he was going, I referenced that only to point out that the google way doesn't necessarily appeal to everyone.  About your second point, a lot of my co-workers have been with the company a pretty long time and seem to be pretty happy and excited about their work.  I don't think working at a big company, and dealing with the corporation structure that usually goes along with it guarantees that you're going to have a miserable experience.

---

### Post by tinny on 2008-07-13
> 
I don't think working at a big company, and dealing with the corporation structure that usually goes along with it guarantees that you're going to have a miserable experience.


Yeah true. Ive enjoyed working in a much flatter structured company.

Let us know how you feel after a year or two. :)

---

### Post by jingo811 on 2008-07-14
Which structure would the Ubuntu project and Linux kernel project lean towards?  A flat or hierarchical structure when compared to ordinary life companies?

---

### Post by imdano on 2008-07-14
Flat.  Featuring [one of these](http://en.wikipedia.org/wiki/BDFL).
Ubuntu = Mark Shuttleworth
Linux Kernel = Linus Torvalds

---

### Post by pmasiar on 2008-07-14
Free software projects are usually flat meritocracy: man on the top is considered one of the the best coders of all, and couple of trusted lieutenants take care of subsystems.

---

### Post by jingo811 on 2008-07-15
I think I spoke to such a lieutenant once when I was searching for answers regarding open source.

**1.)**
He told me that his project group had trouble keeping people on board because people lost interest too quickly and lacked the patience (it's a huge project).
[B]
2.)[/B]
Also he said that people got offended very easily/often when the lieutenants pointed out that their coding wasn't good enough.

What solution would you guys suggest/implement in such situations to make things work better in the future?

---

### Post by mssever on 2008-07-15
> **jingo811 said:**
> What solution would you guys suggest/implement in such situations to make things work better in the future?
Improved leadership skills. In a corporate work environment, people have to do what the boss says unless they're willing to risk getting fired. That means that a boss can be somewhat effective even if he/she is a terrible leader.

When you're working with volunteers, though, you have to use pure leadership; you can't make anyone follow you. Linus Torvalds doesn't pay anyone to work on Linux. Instead, he has, over the years, created an environment and provided the leadership so that the kind of people he wants help from will be motivated to participate and be cooperative.

Leadership is no more and no less than influence.

---

### Post by tinny on 2008-07-15
I may be wrong but I think that a lot of these sorts of projects dont have any formal status given to any developers but a hand fill. (E.g. Lead Dev, lieutenant 1. lieutenant 2). Then anyone and everyone is free to hack on the project. As a anonymous type developer if I feeling i have hacked something of merit I submit it to a lieutenant to be considered for inclusion in the main code base.

Maybe I have over simplified it?


FYI, this is quite interesting.

[http://apache.org/foundation/]("http://apache.org/foundation/")

---

### Post by mssever on 2008-07-15
> **tinny said:**
> I may be wrong but I think that a lot of these sorts of projects dont have any formal status given to any developers but a hand fill. (E.g. Lead Dev, lieutenant 1. lieutenant 2). Then anyone and everyone is free to hack on the project. As a anonymous type developer if I feeling i have hacked something of merit I submit it to a lieutenant to be considered for inclusion in the main code base.
Yes, most projects have a small core and a large number of occasional contributers. But those outside contributers can't really be considered part of the team; they're outsiders.

Also of note: Eric Raymond's famous essay, "[The Cathedral and the Bazaar]("http://www.catb.org/%7Eesr/writings/cathedral-bazaar/cathedral-bazaar/")."

---

