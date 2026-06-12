---
title: "Version control -- good idea? How to learn?"
date: 2010-04-08
forum: Programming Talk
---

### Post by Murrquan on 2010-04-08
I manage a couple of small WordPress sites. I don't really program for them so much as I tweak PHP theme files. These tweaks are important, though, as the themes-as-written don't serve my needs 100%. I'm also hoping to learn how to write and tweak plugins.

I try to choose actively-maintained themes and plugins. The problem is, what happens when something gets updated? Then I lose whatever tweaks I made, unless I go through and reimplement them.

**Question One:** Will learning a version control system help me integrate my changes with theirs? I am a total newb and don't know exactly what these things do, or if they will help with this use case.

**Question Two:** If it will help, which system should I use? I'm leaning heavily towards Bazaar, because it looks newbie-friendly. I'm open to suggestions though.

Many thanks in advance.

---

### Post by thabelo on 2010-04-08
Yes you will identify the changes and differences as long as the directory structure is similar and the file names. But you will not identify their previous changes [i.e before you start integrating your apps in the VC] since their apps are not stored in your Database worst they might no even have their own VC. 

But after you make your own VC ii suggest you make branches for parallel dev.

Hope that helps

---

### Post by km0r3 on 2010-04-08
> **Question One:** Will learning a version control system help me integrate my changes with theirs? I am a total newb and don't know exactly what these things do, or if they will help with this use case.

Version control system (VCS) == Source Code Management (SCM) == Revision Control

In the end all call them differently, but mean the same, though there are quite some differences between the applications. So for example, Git ( [http://www.git-scm.com](http://www.git-scm.com) ) is a **Distributed** Source Control Management tool, whereas SVN is not.

I recommend you looking up the Wikipedia articles on those topics.
> 
**Question Two:** If it will help, which system should I use? I'm leaning heavily towards Bazaar, because it looks newbie-friendly. I'm open to suggestions though.
I also started off with Bazaar and then used Mercurial for a few months. You can learn the basics in 5 minutes, so with bazaar. Later I switched to Git, which is also easy to handle but supports also complex workflows, if you think you need them.
I would recommend you starting with one of the earlier mentioned tools. It's not an error to start with Bazaar or Git or Mercurial. All three are quite popular and there's a lot of useful documentation for each of one.

There are more out there and you'll may get in touch with one or another when working on Open Source projects.

---

### Post by Murrquan on 2010-04-08
Ah, okay. Thanks, all! I'll take a look at Bazaar, then. Hopefully it will help!

---

