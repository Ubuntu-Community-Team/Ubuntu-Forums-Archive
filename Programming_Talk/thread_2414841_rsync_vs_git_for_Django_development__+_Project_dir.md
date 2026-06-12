---
title: "rsync vs git for Django development?  + Project directory location?"
date: 2019-03-15
forum: Programming Talk
---

### Post by Drone4four on 2019-03-15
I have two questions.

To manage development of a Django project, when interfacing local changes and mirroring them to my remote webserver, would you people recommend using rsync or git? I have a little experience with both. I've been using rsync to mirror basic HTML and CSS changes from my local host to my remote Apache public_html directory for a while now. But in one of the Django courses I am taking, the instructor uses git and GitHub. I&#8217;m not sure if using git is overkill or not best practices. What would you people recommend?

Whether I go with git or rsync, I also need to make a decision about where to place my Django project folder on my VPS. One of the guides I am using titled, &#8220;[How To Set Up Django with Postgres, Nginx, and Gunicorn on Ubuntu 18.04]("https://www.digitalocean.com/community/tutorials/how-to-set-up-django-with-postgres-nginx-and-gunicorn-on-ubuntu-18-04")&#8221; suggests putting it inside the user&#8217;s home folder. I gather this isn&#8217;t the most secure option. It&#8217;s also not a good idea to place the Django project folder inside the Apache public_html folder, right? I read both these things somewhere a while ago but I can&#8217;t recall exactly where. Anyways, to set the record straight, where would you people recommend I place my Django project folder on my VPS?

---

### Post by TheFu on 2019-03-16
You should use a version control system, period.  But how you choose to deploy that code can be via git or rsync or some other method.  That is completely up to you.  I don't have a strong feeling about deployment with either, but I have used both.

I do have a strong feeling against using github.  These days, gitlab would be preferred if you feel the requirement to use a cloudy solution at all.  We don't use cloudy services for our custom code, ever.  If we were doing F/LOSS development, that would be a different need and gitlab would definitely be preferred.

I wouldn't deploy something as complex as Django to a HOME.  Something like that, which is likely to be the primary software for the entire server belongs under /var/www/ somewhere.  If you use shared hosting, you won't get the choice, but since you have a VPS, best to follow the standards.   Google "File system hierarchy standards" - this document is followed by all the major Linux distros and lays out where files belong.  Follow it.

BTW, your "rig" is very distracting. Linux would never have run on it.

---

### Post by Drone4four on 2019-03-16
Thank you for your reply. I appreciate it, **@TheFu**.  :KS

> **TheFu said:**
>  I wouldn't deploy something as complex as Django to a HOME.  Something like that, which is likely to be the primary software for the entire server belongs under /var/www/ somewhere.  If you use shared hosting, you won't get the choice, but since you have a VPS, best to follow the standards.   Google "File system hierarchy standards" - this document is followed by all the major Linux distros and lays out where files belong.  Follow it.

As you suggested, I Googled &#8216;File system hierarchy standards&#8217;. I found [the detailed Wikipedia entry]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"). Yes, I&#8217;ll follow this hierarchy standard.  Although I&#8217;m not writing my own O/S. Ubuntu obviously already firmly adheres to this standard. This Wikipedia entry does not advise on where to place web frameworks / CMS implementations. But you recommended /var/www. For /var, the above Wikipedia entry says:

> Variable files&#8212;files whose content is expected to continually change during normal operation of the system&#8212;such as logs, spool files, and temporary email files.

Django might handle logs but my project does not handle temporary email files. The corollaries for /var as it appears in that Wikipedia entry does not specify anything about /var/**www** nor mentions anything else related to web servers (like Apache, nginx).

Does a Django project directory involve "files whose content is expected to continually change during normal operation"? If this is true, then I suppose my question is answered.

Apache&#8217;s public_html directory can be found inside /var/www but putting Django in there is not secure, correct?

---

### Post by Drone4four on 2019-03-16
> BTW, your "rig" is very distracting. Linux would never have run on it.

Not a single soul on our beloved internetz would have any interest in seeking support on Google for Linux on a 286. Torvald&#8217;s initial kernel was written for his 386. :D My signature is just a precious momento and throw back to the era of Wolf3D (which is reflected in my forum avatar). It&#8217;s a token of nostalgia. If it&#8217;s a problem, then I suppose I could remove it.

---

