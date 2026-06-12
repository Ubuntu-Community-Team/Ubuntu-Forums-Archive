---
title: "&quot;Clearcase&quot; or &quot;Apex&quot; for Ubuntu"
date: 2007-05-10
forum: Programming Talk
---

### Post by Gig103 on 2007-05-10
Hi everyone,
I just installed Ubuntu Feisty last week and so far haven't done much with it. However, I'm getting ready to redesign my website and this time around, I want to be a good programmer and actually keep version history. At work, we use Clearcase, and Rational Apex, but neither are free and open source. So what is the standard around here? What has it's own interface? What integrates with Eclipse, Jedit, or Bluefish?


Thanks for the suggestions in advance!



Edit: For those unfamiliar, they are configuration management tools, for version histories and other advanced features, but really I just need the version histories.

---

### Post by ilautar on 2007-05-10
You should try subversion (svn - [http://subversion.tigris.org/)](http://subversion.tigris.org/)), it will take some time to get around if you're used to ClearCase, but it does everything (mostly) you need. Most OSS project use cvs or svn.

However, one thing which is lacking is a nice tree view like ClearCase has which can be used to do merges between branches etc. You will have a hard time if you're a heavy user of it (but this is true for most OSS version control tools - somebody will fill me up here, I haven't tried all of them). I suppose there are some GUI frontends one can use (like RapidSVN, kdesvn), but I preffer command line. I have found svnmerge.py ([http://www.orcaware.com/svn/wiki/Svnmerge.py](http://www.orcaware.com/svn/wiki/Svnmerge.py)) very helpfull working with merges in large projects. It made my life a LOT easier.

There are some tutorials on links I've mentioned for you to start. Basic repository set-up is trivial.

---

### Post by xtacocorex on 2007-05-10
Another option would be bazaar (bzr), but I would recommend svn.

---

### Post by Gig103 on 2007-05-13
Thanks so far. I saw SVN and it looks like the right thing for what I need, but could be considered too complicated. I'm the only one working on the files, I just want revision history not a whole lot of merging, etc.

Is there a "simpler" version? Maybe like how a wiki works?

---

### Post by ilautar on 2007-05-13
> **Gig103 said:**
> Thanks so far. I saw SVN and it looks like the right thing for what I need, but could be considered too complicated. I'm the only one working on the files, I just want revision history not a whole lot of merging, etc.

Is there a "simpler" version? Maybe like how a wiki works?

Well, if you do not need extra features, don't use them. What you need (just versioning) is really very simple. It comes down to few commands like:

svn co
svn add
svn status
svn ci

You can even use one of GUI interfaces and make things even more straight-forward.

---

