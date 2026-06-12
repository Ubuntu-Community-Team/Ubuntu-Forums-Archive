---
title: "How do components interact?"
date: 2007-04-03
forum: Programming Talk
---

### Post by PopcornEaterMan on 2007-04-03
Hope this is an okay place to put the question; I figure the best way to get an informed answer is to ask the programmers themselves.

I am installing subversion on an apache server.  My question is not about apache and it isn't about subversion, rather, I'm wondering, how does subversion know how to configure itself with apache?  How do different packages know about one another?

In the windows world, this used to be done with the Windows registry.  If a component wanted to know if another component was installed on the system, it would ask the windows registry.  In linux, if I install subversion to the system, how does it know if apache is running, and how does it know if it is in the correct configuration?  What if I move apache's default directory.  Can I change the default directory?  Does one system know about another system because the locations are hardcoded?

What if team A sets their default location to /user/local/KillerApp and finds that someone has already claimed that directory?

I guess I am new to the linux world, limited on time, and I'm just trying to understand how things work here.

---

### Post by foxylad on 2007-04-04
> **PopcornEaterMan said:**
> Hope this is an okay place to put the question; I figure the best way to get an informed answer is to ask the programmers themselves.

I am installing subversion on an apache server.  My question is not about apache and it isn't about subversion, rather, I'm wondering, how does subversion know how to configure itself with apache?  How do different packages know about one another?

In the windows world, this used to be done with the Windows registry.  If a component wanted to know if another component was installed on the system, it would ask the windows registry.  In linux, if I install subversion to the system, how does it know if apache is running, and how does it know if it is in the correct configuration?  What if I move apache's default directory.  Can I change the default directory?  Does one system know about another system because the locations are hardcoded?

Just like Windows assumes all programs put their configuration data in the registry, Linux assumes all programs put their configuration data in /etc (or a subdirectory). Neither OS enforces this - there are lots of Windows programs that use ini files all over the place. So applications usually look for config data rather than the executables - both because the executables might be installed in several different places, but also because the application is usually much more interested in the config data than the executable.

> What if team A sets their default location to /user/local/KillerApp and finds that someone has already claimed that directory?

Usually a developer does a quick Google to make sure they have a unique name for their application, which solves the problem. The exact same thing could happen in the Windows registry, of course.

---

