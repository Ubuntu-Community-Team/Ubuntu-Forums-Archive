---
title: "Ubuntu in a fictional IT project management senario"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by SteelCore on 2008-09-24
Greetings everybody,
I'm currently taking an IT project management course.  The assignments require that I create a fictional IT project and pass it thru the many phases or Proj Management such as; pa charter, a WBS, a budget, a quality plan, an organizational plan, a communications management plan....etc
Naturally I'll chose something related to Ubuntu which would serve as an introduction to Linux to both my professor and classmates. The project needs to be semi-realistic so I can benefit from it and not humongous coz I only have about a month to finish these assignments, amongst other things.
Based on [http://www.ubuntu.com/products/casestudies](http://www.ubuntu.com/products/casestudies) I could only think of a medium sized business company migrating its PCs and servers to Ubuntu. If anyone has suggestions, feedback or more links on this issue I'd be really grateful.  Thank you for your patience.

---

### Post by lian1238 on 2008-09-24
IMHO, I mean if I were to own a business, I would choose a system which works best for my business and at the same time, cutting costs. If my business were in a place where copyright is unheard of, then I'd probably go with Windows since most people are used to that already. But let's say you need to use legal software, I might go with open source software, such as Ubuntu. I think businesses go for open software solutions for cutting costs.
Just my opinion. I don't run a business so I could be wrong.

---

### Post by anewguy on 2008-09-24
I have a couple of comments, but don't know how useful they will be for you.  I come from a systems programming and systems administration background on large scale, medium scale, mini and micro computers.

As you layout this migration, be sure you have a fall-back plan.  Too many times I have seen others who failed to do so, tried to roll out a big change, and the result was chaos.  Remember to compartmentalize as much as possible so that any potential problems are easier to handle and don't affect the entire company at one time.  Remember test platforms and parallel operation.  Remember ISO requirements for disaster recovery, backups, etc..  Most of all, plan everything to the last detail and in such a way that it does not disrupt the company day to day business.  Plan to gather key users from each area affected, each department affected, and listen to their needs and concerns and plan with them to avoid friction, disapointment and resentment.  Having people on your side and cooperating can only happen with adequate planning and user participation.

Just some thoughts.

Dave :)

---

### Post by SteelCore on 2008-09-24
> **anewguy said:**
> I have a couple of comments, but don't know how useful they will be for you.  I come from a systems programming and systems administration background on large scale, medium scale, mini and micro computers.

As you layout this migration, be sure you have a fall-back plan.  Too many times I have seen others who failed to do so, tried to roll out a big change, and the result was chaos.  Remember to compartmentalize as much as possible so that any potential problems are easier to handle and don't affect the entire company at one time.  Remember test platforms and parallel operation.  Remember ISO requirements for disaster recovery, backups, etc..  Most of all, plan everything to the last detail and in such a way that it does not disrupt the company day to day business.  Plan to gather key users from each area affected, each department affected, and listen to their needs and concerns and plan with them to avoid friction, disapointment and resentment.  Having people on your side and cooperating can only happen with adequate planning and user participation.

Just some thoughts.

Dave :)

Very beneficial pointers. Can you please elaborate on what you mean by compartmentalizing the migration. Is it migrating company departments one at a time?

---

### Post by anewguy on 2008-09-24
It may mean a department or may mean even a smaller entity.  Sometimes email migration is done by groups, as is server migration - isolate things down to the smallest possible groups, especially until things are debugged and proven in more than just 1 rollout.  If you have say a small group that works on documentation, move their apps and mail over.  After things are known to be working okay, move on to the next group - starting with smaller groups and working up to the larger groups.  Start with the areas that would have the least impact on the day to day business if problems are encountered (using my previous example, I don't mean to imply a group doing documentation is insignificant!!).  Have a small group that uses a certain application?  Migrate that application over and debug before moving more.

Hope that helps explain more.

Dave :)

---

### Post by Hendrixski on 2008-09-24
Don't just think of existing companies, right?
Every new company that starts up in Silicon Valley and Cambridge are using Linux. It's a no-brainer because it makes them move faster than the corporate bohemoths who have to "migrate" and blah blah blah.

Perhaps an IT project could be "setting up a new company's IT setup from scratch". Because, having myself started a company which runs almost exclusively on Ubuntu, I have to say, that the startup is where Linux shines.

So, hopefully you don't have to do a project about just migrating, but on just starting from scratch.

---

### Post by billgoldberg on 2008-09-24
> **SteelCore said:**
> Greetings everybody,
I'm currently taking an IT project management course.  The assignments require that I create a fictional IT project and pass it thru the many phases or Proj Management such as; pa charter, a WBS, a budget, a quality plan, an organizational plan, a communications management plan....etc
Naturally I'll chose something related to Ubuntu which would serve as an introduction to Linux to both my professor and classmates. The project needs to be semi-realistic so I can benefit from it and not humongous coz I only have about a month to finish these assignments, amongst other things.
Based on [http://www.ubuntu.com/products/casestudies](http://www.ubuntu.com/products/casestudies) I could only think of a medium sized business company migrating its PCs and servers to Ubuntu. If anyone has suggestions, feedback or more links on this issue I'd be really grateful.  Thank you for your patience.

I don't agree with your medium size project statement.

There are big projects that use Ubuntu.

Google, archive.org, the French police and parliament, ...

---

### Post by anewguy on 2008-09-24
I guess what I would add is that it doesn't actually matter the scale of the project - small company all the way to large - the same guidelines apply for a successful project.

Given your 1 month time frame for this class, I would pick an imaginary company of say 200 users or so, divided up into perhaps 5 servers, and maybe 10 distinct "groups" for email - things that need to be isolated from each other.  Select perhaps 1 imaginary piece of software per server, and go from there.  Some details obviously cannot be explicitly stated - such a key user participation - and such should probably be mentioned as a key user for each group will participate in the planning, testing and implementation/migration without specific details.  State who would be first and why, and how it progresses up to more mission-critical things. Mentioning disaster recovery plans and backup types along with ISO certification can add a plus to the project.

As with any project, start with an outline, expand it, add to it, and add the relevant details with in section into a comprehensive document.  I am sure that given the time frame they don't expect tons of minute details, but are looking more at the overall concept and the grasp of the larger details that make up the big picture.

Also - remember that a migration IS a new implementation plus it has the added details of preserving functionality as the implementation takes place.  The extra there can not but help you with showing the scope of your planning, etc., to your professor.

Good luck with your school project!

Dave :)

---

### Post by SteelCore on 2008-09-24
> **billgoldberg said:**
> I don't agree with your medium size project statement.
There are big projects that use Ubuntu.


I only used that size due to the time limit on the assignment.

---

