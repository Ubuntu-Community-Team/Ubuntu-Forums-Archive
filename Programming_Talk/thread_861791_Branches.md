---
title: "Branches"
date: 2008-07-16
forum: Programming Talk
---

### Post by solarwind on 2008-07-16
Let's say I register a project on Launchpad and I'm using bzr. What branch should I push my project to initially? Should it be "trunk"? Also, if trunk is the main branch which is the focus of development (which will be the next major release) (let's say release version 2), then once version 2 is out, what will be the name of the next branch? How does this all work?
What are these branches anyway? I feel like my head's going to explode!

---

### Post by nanotube on 2008-07-17
> **solarwind said:**
> Let's say I register a project on Launchpad and I'm using bzr. What branch should I push my project to initially? Should it be "trunk"? Also, if trunk is the main branch which is the focus of development (which will be the next major release) (let's say release version 2), then once version 2 is out, what will be the name of the next branch? How does this all work?
What are these branches anyway? I feel like my head's going to explode!

i don't know how bzr's manual is, but cvs manual does a pretty decent job of explaining branching. so you would probably do well to look at the cvs manual for a general description of branching, merging, and all that good stuff. (of course ignore the actual command syntax, since it's different for bzr. :) ).

---

### Post by solarwind on 2008-07-17
> **nanotube said:**
> i don't know how bzr's manual is, but cvs manual does a pretty decent job of explaining branching. so you would probably do well to look at the cvs manual for a general description of branching, merging, and all that good stuff. (of course ignore the actual command syntax, since it's different for bzr. :) ).

My question is, what is the "general" way of managing a project?

Let's say I have project x. I develop x until v 1.0 where it becomes stable. Up till now it was only in one branch: the "trunk" branch. What do I do now? It's stable, do I branch it to a "1.0" branch and develop it separately?

Then let's say I do do that and now I have 2 branches: "trunk" and "1.0". I then develop the trunk until 2.0 while also maintaining 1.0. Now that 2.0 has become stable, do I branch that from the trunk to the "2.0" branch?

What are the common practices regarding this? What's the right way of doing it?

Ok, so now I have a 1.0, 2.0 and trunk branch. The trunk branch contains the entire history of the project. Is that ok? It will get pretty large, no? Wont it be a pain to branch the entire trunk for someone to branch my work? Also, wont the later versions (4, 5, 6, 7 for example) contain all the history of the project starting from revision 0?

This is what I'm thinking of but I don't know if it's the right way to manage a project:

```

trunk
^
|
|
| /---> 3.0
|/
|
| /---> 2.0
|/
|
| /---> 1.0
|/
|

```

I'm thinking of branching off the trunk as I go along, but something tells me this is not the right way of doing it...

Please help.

---

### Post by skeeterbug on 2008-07-17
Everyone does it differently. I have seen some that have a "development" branch, and trunk is the current stable release. 

At work we have it setup so trunk is the latest development code, and when we reach certain milestones, that code is tagged (release 2.4). If there are updates to 2.4 tag, it is branched, once that is fixed/done, it is re-tagged as 2.4.1, etc.

Currently we are working on our 3.0 release, but we still maintain bug fixes for 2.4. So there is currently trunk, a 2.4 tag, and a 2.4 branch (which will be tagged to 2.4.1 at some point). It works good for the most part, except the offshore developers don't understand SVN all that well. :(

---

### Post by solarwind on 2008-07-17
> **skeeterbug said:**
> Everyone does it differently. I have seen some that have a "development" branch, and trunk is the current stable release. 

At work we have it setup so trunk is the latest development code, and when we reach certain milestones, that code is tagged (release 2.4). If there are updates to 2.4 tag, it is branched, once that is fixed/done, it is re-tagged as 2.4.1, etc.

Currently we are working on our 3.0 release, but we still maintain bug fixes for 2.4. So there is currently trunk, a 2.4 tag, and a 2.4 branch (which will be tagged to 2.4.1 at some point). It works good for the most part, except the offshore developers don't understand SVN all that well. :(

Ahh! So your trunk contains the entire history of the project? So is it ok to do it the way I outlined above?

---

### Post by mssever on 2008-07-17
The way I do it in svn:

I have three dirs at root level: branches, trunk, and releases. Primary development takes place in trunk. When I do a release (e.g., 1.0), I copy trunk to a subdirectory of releases (e.g., releases/1.0). Since svn only stores the delta between revisions, the extra space to maintain the copy is negligible. I use branches for experiments or particularly invasive changes, especially if they involve breakage for a time. I try to make sure that trunk basically works, so development that would break trunk during that part of the work would go on a separate branch. I simply copy trunk to a subdirectory of branches. When I'm satisfied, I merge the branch back to trunk; alternatively, I just either abandon the branch or delete it.

I haven't used bzr, but I imagine something similar would work. I'm sure that there are also other ways to do it.

EDIT: By the way, in SVN, at least, it isn't too hard to modify your structure if needed, so don't worry too much about future-proofing. You can do that as the need arises.

---

### Post by solarwind on 2008-07-17
> **mssever said:**
> The way I do it in svn:

I have three dirs at root level: branches, trunk, and releases. Primary development takes place in trunk. When I do a release (e.g., 1.0), I copy trunk to a subdirectory of releases (e.g., releases/1.0). Since svn only stores the delta between revisions, the extra space to maintain the copy is negligible. I use branches for experiments or particularly invasive changes, especially if they involve breakage for a time. I try to make sure that trunk basically works, so development that would break trunk during that part of the work would go on a separate branch. I simply copy trunk to a subdirectory of branches. When I'm satisfied, I merge the branch back to trunk; alternatively, I just either abandon the branch or delete it.

I haven't used bzr, but I imagine something similar would work. I'm sure that there are also other ways to do it.

EDIT: By the way, in SVN, at least, it isn't too hard to modify your structure if needed, so don't worry too much about future-proofing. You can do that as the need arises.

Thanks! Now I understand what I'm doing and I have one last question.

Since you said SVN stores the delta between revisions (I'm pretty sure bzr does the same), copying the trunk to a release branch would copy the entire history (not just the last revision or something like that), wouldn't it?

---

### Post by skeeterbug on 2008-07-17
> **solarwind said:**
> Ahh! So your trunk contains the entire history of the project? So is it ok to do it the way I outlined above?

Yes trunk will contain the entire history of the project, and that is perfectly OK. In fact, source control facilities such as git track changes between branching/merging. With SVN, you lose that information.

---

### Post by tinny on 2008-07-17
This is what I do.

(Probably over generalizing here)

Say we have 4 developers on a team and 2 new features that a customer wants implemented (Feature A and Feature B).

What I will do is tag the current trunk head (Tag: “Pre feature A and B implementation”) and then create 2 new branches off the current trunk head (head is the current version). Then 2 developers will work on either branch to implement these features. It is good to work in separate branches because this means you wont stand on the other teams toes by making changes to over lapping code.

Then whichever team finishes first or has the least intrusive code changes will merge into the truck first and then tag the trunk (Tag: “Post feature A implementation”). Then the other team will repeat this process E.g. merge into trunk, tag trunk (Tag: “Post feature B implementation”). By creating tags you are giving yourself a sort of checkpoint that you can revert back too should everything turn to custard. 

But this is just how I do it.

---

### Post by nanotube on 2008-07-17
> **solarwind said:**
> My question is, what is the "general" way of managing a project?

Let's say I have project x. I develop x until v 1.0 where it becomes stable. Up till now it was only in one branch: the "trunk" branch. What do I do now? It's stable, do I branch it to a "1.0" branch and develop it separately?

...

Please help.

heh well while i was away, it looks like you've gotten plenty of help. just wanted to throw in my "vote" and say that i do it like skeeterbug and msserver - develop on trunk, tag releases, make branches for fixes to older releases, and make branches for particularly "invasive" bits of development. in short: don't branch, unless there's good reason to keep more than one separate "current" version; use tags.

---

### Post by solarwind on 2008-07-17
> **tinny said:**
> This is what I do.

(Probably over generalizing here)

Say we have 4 developers on a team and 2 new features that a customer wants implemented (Feature A and Feature B).

What I will do is tag the current trunk head (Tag: “Pre feature A and B implementation”) and then create 2 new branches off the current trunk head (head is the current version). Then 2 developers will work on either branch to implement these features. It is good to work in separate branches because this means you wont stand on the other teams toes by making changes to over lapping code.

Then whichever team finishes first or has the least intrusive code changes will merge into the truck first and then tag the trunk (Tag: “Post feature A implementation”). Then the other team will repeat this process E.g. merge into trunk, tag trunk (Tag: “Post feature B implementation”). By creating tags you are giving yourself a sort of checkpoint that you can revert back too should everything turn to custard. 

But this is just how I do it.

Thanks! I'm going to use tags and branches now, so that *things don't turn into custard*, haha.

---

### Post by solarwind on 2008-07-17
> **nanotube said:**
> heh well while i was away, it looks like you've gotten plenty of help. just wanted to throw in my "vote" and say that i do it like skeeterbug and msserver - develop on trunk, tag releases, make branches for fixes to older releases, and make branches for particularly "invasive" bits of development. in short: don't branch, unless there's good reason to keep more than one separate "current" version; use tags.

What if I want to support version 3 AND 4 at the same time? 4 is the latest but a lot of people use 3 and lets say it works on older hardware or something. I should make a branch for 3, shouldn't I?

---

### Post by mssever on 2008-07-17
> **solarwind said:**
> Since you said SVN stores the delta between revisions (I'm pretty sure bzr does the same), copying the trunk to a release branch would copy the entire history (not just the last revision or something like that), wouldn't it?
All that's necessary to store is a notation that the branch is equivalent to trunk at revision foo.
> **solarwind said:**
> What if I want to support version 3 AND 4 at the same time? 4 is the latest but a lot of people use 3 and lets say it works on older hardware or something. I should make a branch for 3, shouldn't I?
I imagine that I would maintain a separate development branch for version 3. I'd merge in changes from trunk when appropriate, and use that branch as the source for releases. That's just an idea, since I've never been in such a situation.

---

### Post by solarwind on 2008-07-17
> **mssever said:**
> All that's necessary to store is a notation that the branch is equivalent to trunk at revision foo.

I imagine that I would maintain a separate development branch for version 3. I'd merge in changes from trunk when appropriate, and use that branch as the source for releases. That's just an idea, since I've never been in such a situation.

Thanks, I got it all figured out now!

---

### Post by nanotube on 2008-07-17
> **solarwind said:**
> What if I want to support version 3 AND 4 at the same time? 4 is the latest but a lot of people use 3 and lets say it works on older hardware or something. I should make a branch for 3, shouldn't I?

yes, exactly! that's precisely what branching is for. :)

so then, you'd have two parallel development streams, looking somewhat like this:
```

       3.0.1 --------- 3.0.2 --- >
      /                    \
------3.0.0 ---- 4.0.0 ---- 4.0.1 ---- >

```

so, here's the "hypothetical timeline". you'd make a release from trunk at tag 3.0, then go on to do more development for version 4 and release it. then you realize that there are some bugs or minor enhancements that are needed in version 3, so you make a branch at tag 3.0.0, and do those fixes, and make a tag on that branch of 3.0.1 and make a release. then later you realize that you need to merge some fixes that you made for version 4.0.1, so you merge those in and make another release tag of 3.0.2. and so on. (same thing works if you want to merge some changes you made in v3 into v4).

and as long as you care to maintain the two (or more) separate branches of code, you can keep doing it.

edit: so yea, basically, what msserver said. i should remember to reload the page before posting... :)

i must note, though, that maintaining multiple branches is kind of a pain, so unless there is good reason to do it, try to avoid it. like, if you are doing a major rewrite of the code, which may lack the stability of prior versions or something. otherwise, don't go all branch-happy, and stay on the trunk. :)

---

