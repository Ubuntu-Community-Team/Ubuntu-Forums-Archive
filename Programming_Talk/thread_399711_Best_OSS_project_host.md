---
title: "Best OSS project host?"
date: 2007-04-02
forum: Programming Talk
---

### Post by reacocard on 2007-04-02
I'm creating a new open-source project, and I'd like to know what the best place to host it is. The three choices I've found so far are:

- Sourceforge
- Google Code
- Launchpad

What are the benefits/pitfalls of each? Which do you recommend?

---

### Post by ssam on 2007-04-02
when i looked at this question for my own project i chose sourceforge

launchpad does not offer svn/cvs hosting, only bzr hosting. and that put me off.

i dont like the sourceforge bug tracker much, bug as long as i write bug free code this does not matter :-)

there is nothing to stop you hosting code on google, bug tracking on lauchpad, and having mailing lists on sf.

---

### Post by reacocard on 2007-04-02
> **ssam said:**
> when i looked at this question for my own project i chose sourceforge

launchpad does not offer svn/cvs hosting, only bzr hosting. and that put me off.

i dont like the sourceforge bug tracker much, bug as long as i write bug free code this does not matter :-)

there is nothing to stop you hosting code on google, bug tracking on lauchpad, and having mailing lists on sf.

Thanks. I hadn't thought of just spreading it across several, I may do that. As for Bazaar, since I have no experience with revision control whatsoever that's not really an issue.

---

### Post by pmasiar on 2007-04-03
> **reacocard said:**
> since I have no experience with revision control whatsoever that's not really an issue.

before you start project and ask other developers to join, you should learn some VCS. Good one and very popular is Subversion. [TRAC](http://trac.edgewall.org/) is excellent project integrating subversion, bug tracker, code browser (shows changes in color in browser) and wiki for website and documentation. Trac is rather popular and [many hosts](http://www.google.com/search?q=free+trac+hosting) provide free trac hosting for open source projects.

---

### Post by reacocard on 2007-04-03
> **pmasiar said:**
> before you start project and ask other developers to join, you should learn some VCS. Good one and very popular is Subversion. [TRAC](http://trac.edgewall.org/) is excellent project integrating subversion, bug tracker, code browser (shows changes in color in browser) and wiki for website and documentation. Trac is rather popular and [many hosts](http://www.google.com/search?q=free+trac+hosting) provide free trac hosting for open source projects.

I've seen Trac, it looks really nice, but it relies on Python, which no free host provides, so I can't use it.  As for the VCS, that's part of why I'm asking this now: so that I can sign up for the hosting and get some practice with the VCS before I release anything.  

I just registered it in launchpad, bazaar doesn't seem that hard, took me less than half an hour to figure out how to do my first commit.  I think I'm going to go with Launchpad for VCS/bugtracking, and the free hosting from tuxfamily for the website/downloads.

Thanks!

---

### Post by pmasiar on 2007-04-03
> **reacocard said:**
> I've seen Trac, it looks really nice, but it relies on Python, which no free host provides, so I can't use it. 

You are strange: many hosts provide you free Trac with subversion and everything, I am at loss why you cannot use it.

There are also many web hosts who provide free hosting for python web-based projects.
[http://wiki.python.org/moin/FreeHosts](http://wiki.python.org/moin/FreeHosts) lists hosts like [http://www.frihost.com/](http://www.frihost.com/) [http://www.xennos.com/package_features.htm](http://www.xennos.com/package_features.htm) [http://www.oinko.net/freepython/](http://www.oinko.net/freepython/)

So not sure what you are talking about problems with Python hosting. :-(

---

### Post by reacocard on 2007-04-03
> **pmasiar said:**
> You are strange: many hosts provide you free Trac with subversion and everything, I am at loss why you cannot use it.

There are also many web hosts who provide free hosting for python web-based projects.
[http://wiki.python.org/moin/FreeHosts](http://wiki.python.org/moin/FreeHosts) lists hosts like [http://www.frihost.com/](http://www.frihost.com/) [http://www.xennos.com/package_features.htm](http://www.xennos.com/package_features.htm) [http://www.oinko.net/freepython/](http://www.oinko.net/freepython/)

So not sure what you are talking about problems with Python hosting. :-(

Let me clarify that: I didn't know of any free host with python/trac. Incidentally, why is tuxfamily on that page? They don't have python support, just PHP. If they had python, I would just put trac on there.

As for me being strange, well, normality is relative. :p

---

### Post by pmasiar on 2007-04-03
In my link in post #4 are hosts which will host your repository with TRAC and everything - so you don't need to administer it - they will do it for you. They already have it, hosting one more project is trivial.

And there are other hosting providers (as i linked) which will give you free space for Python CGI scripts and MySQL database. Thats why I am confused - what else you need?

---

### Post by reacocard on 2007-04-03
> **pmasiar said:**
> In my link in post #4 are hosts which will host your repository with TRAC and everything - so you don't need to administer it - they will do it for you. They already have it, hosting one more project is trivial.

And there are other hosting providers (as i linked) which will give you free space for Python CGI scripts and MySQL database. Thats why I am confused - what else you need?

I wouldn't need anything else, but I decided to go with launchpad (post #5), so getting trac set up is a moot point now. Thanks for the links anyway, I may need them in the future.

---

