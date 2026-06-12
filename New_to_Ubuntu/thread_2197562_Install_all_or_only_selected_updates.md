---
title: "Install all or only selected updates?"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-01-04
I am about 3 years as an Ubuntu user (99% GUI although I am now beginning to learn the CLI) and when the Update Manager pops up, I just click, authorize, and let it do it's thing. 

My question is should I be looking at each of the updates and vetting them as to whether or not I want them for one reason or another? In the past, I have just assumed that it was the right thing to do, but it suddenly dawned on me that this might not be a good idea.

Any guidance, and if it should be vetted, what should I be looking for and where should I look?

---

### Post by ptn107 on 2014-01-04
You are automatically set to get two kinds of updates; security updates, and regular [bugfix/functionality] updates.  Security updates should be installed without question.  Bug-fix updates are less critical but they do sometimes fix something major.  Desktop users can install both kinds of updates freely (though I still review them personally).  If you notice that there is something bad an update introduced you can always downgrade to the previous version until things get sorted out.

If you really want to see what changed you can pop open your browser and go here (replace **packagename** with the software you want to look at):

https://launchpad.net/ubuntu/+source/**packagename**/+changelog

and review the changes yourself.

---

