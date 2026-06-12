---
title: "Coding submission/managment tools"
date: 2008-09-26
forum: Programming Talk
---

### Post by freshAndClean on 2008-09-26
So, I'm heading my first project, and I wanted to try to grab some suggestions people may have for programming related project tools.

I.E.I'm looking for a submission tool to control changes to project source code in a shared directory space where the project lives.  

I'm also looking for a scheduling tool to keep track of expected completion dates for project components, something like a gant chart.

Anyway, I've got a couple ideas on some of these, but I want to hear the input of some more experienced developers and there views on some of these tools.

---

### Post by skeeterbug on 2008-09-26
> **freshAndClean said:**
> So, I'm heading my first project, and I wanted to try to grab some suggestions people may have for programming related project tools.

I.E.I'm looking for a submission tool to control changes to project source code in a shared directory space where the project lives.  

I'm also looking for a scheduling tool to keep track of expected completion dates for project components, something like a gant chart.

Anyway, I've got a couple ideas on some of these, but I want to hear the input of some more experienced developers and there views on some of these tools.

Check out Trac. [http://trac.edgewall.org/](http://trac.edgewall.org/)

---

### Post by nvteighen on 2008-09-26
Bazaar: [http://bazaar-vcs.org](http://bazaar-vcs.org)

It supports Distributed Control Version and Centralized (SVN, CVS like), so it's pretty flexible. It's the tool that Ubuntu uses at Launchpad.

---

### Post by imdano on 2008-09-26
> **freshAndClean said:**
> I.E.I'm looking for a submission tool to control changes to project source code in a shared directory space where the project lives.You want version control software like bazaar, subversion, or git.

> **freshAndClean said:**
> I'm also looking for a scheduling tool to keep track of expected completion dates for project components, something like a gant chart.This is a little trickier.  Websites like [Launchpad](http://launchpad.net) and [Sourceforge](http://sourceforge.net) offer bug tracking tools that can also be used to track tasks.  Launchpad's Blue print system may actually be closer to what you want in terms of scheduling (See [an example here](https://blueprints.launchpad.net/ubuntu)).  Launchpad also integrates very well with bazaar, if you choose that as your version control software.

---

