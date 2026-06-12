---
title: "Is LAMP still a good idea?"
date: 2012-10-21
forum: Programming Talk
---

### Post by linlux on 2012-10-21
Hello,

I am an IT manager and have my first real opportunity to get back into programming since I finished college a year ago. A property manager wants me to create a custom website for management of her condo building (owner database, resident mail notifications, employee management, etc). It appears that Linux, MySQL, Apache and PHP (LAMP collectively) are the best and most cost effective (free) combination for creating a reliable server. I am quite familiar with all of these. However, since there are a plethora of languages out there I'd be interested if this is still a good route to begin with. The only concern I can think of is someday porting or replicating the system on a Windows machine.

---

### Post by Dimarchi on 2012-10-21
I don't quite see the problem here, if it is a website. What kind of porting or replicating problems do you envision?

---

### Post by llanitedave on 2012-10-22
LAMP in the classic sense shouldn't be a problem for Windows, necessarily.  It'll just become WAMP.

Choices have diversified in the last few years.  There are plenty of Python options available, and integrated tools like Django, and MySQL also has competition.

If anything, the solutions will be easier to achieve than before, but maybe harder to choose between.

---

### Post by coldraven on 2012-10-22
All sorts of info here: [http://www.howtoforge.com/howtos/linux/ubuntu](http://www.howtoforge.com/howtos/linux/ubuntu)
You might want to investigate things like nginx

---

### Post by Lars Noodén on 2012-10-22
Depending on what you are doing, you might also look at nginx.  It is on the edge of [becoming the #2 web server](http://news.netcraft.com/archives/2012/10/02/october-2012-web-server-survey.html).  Apache of course is still #1 by a long ways.  

About WAMP, I would say avoid it like the plague.  The AMP part is fine, but when I had to use it a few years back the W part was awfully unreliable.  Best to stick with the best of breed across the board and keep the L in LAMP.  That said, the BSDs and even Solaris are also good options for platforms. 

As far as portability goes, Perl is pretty much cross-platform and you will find it everywhere.  Python is nearly everywhere, but easy to add.

---

### Post by linlux on 2012-10-22
Thanks for the replies! I looked at some of the benefits of nginx, and it seems like a good idea for large scale setups. In the end I should probably start with the languages I'm most familiar in, then I can upgrade the webserver as needed.

Another thought I had was with MySQL licensing, but the GPL is very liberal on what you can do (this page explains it [http://www.xaprb.com/blog/2009/02/17/when-are-you-required-to-have-a-commercial-mysql-license/](http://www.xaprb.com/blog/2009/02/17/when-are-you-required-to-have-a-commercial-mysql-license/)

The software will most likely be hosted on a dedicated machine, so hopefully I can avoid using IIS by sticking to Linux.

---

