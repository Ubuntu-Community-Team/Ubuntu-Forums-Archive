---
title: "Mimic svn:externals behavior with Git."
date: 2010-08-17
forum: Programming Talk
---

### Post by tyfius on 2010-08-17
I apologize if this is posted in the wrong category, but I didn't really know where else to put it.

Using Git on a couple of projects I'm becoming quite a fan. Coming from subversion the single Git folder with multiple local branches is just fantastic. Thus, I'd like to introduce it at work where I currently maintain the subversion repository. I have been reading up on Git and more detailed on Git submodules but I can't seem to find a nice real-world example that explains the whole thing.

I currently have one main subversion repository with several folders:

```
+ Software/
    - Module.A/ (branches/tags/trunk)
    - Module.B/ (branches/tags/trunk)
    - Module.C/ (branches/tags/trunk)
    - Module.D/ (branches/tags/trunk)
+ Views/
    - Application1/ (branches/tags/trunk)
    - Application2/ (branches/tags/trunk)
```The Software folder contains the actual software source code and related data files, the Views folder contains an empty folder where I use svn:externals to link to a specific Module folder. For example, the Application1/trunk folder has svn:externals set up to the trunk folder of Module.A and Module.B but not Module.C and Module.D. Similarly, Application2/trunk has svn:externals set up to Module.A, Module.C and Module.D but not Module.B.

Now I need a similar approach on Git. From what I understand so far it's advisable to create separate repositories per Module and per View. Unfortunately so far I've only found ways to link to a specific revision using a submodule which doesn't update automatically when doing git pull, it doesn't allow me to directly push modifications to it and I have to configure it locally, which I don't want to do on every PC for every developer in the company.
Using subversion this is something that's done very easy on the repository and people just have to check out a certain view to get everything they need and allows them to work on it from one single folder without the need to have separate checkouts of each and every folder that is set up as an svn:external or be bothered with over a hundred Modules or other folders they don't need for the project they are working on.

So basically, what's the best and easiest way to mimic my current svn:externals setup when migrating to Git?

---

### Post by sunside on 2012-01-26
bump

---

### Post by markbl on 2012-01-26
You are making it too complicated. Just use one git repo. I admit there is a lot of confused advice around the web about this issue but IMHO you are better off with only one repo unless you have completely independent projects with independent developer groups.

---

