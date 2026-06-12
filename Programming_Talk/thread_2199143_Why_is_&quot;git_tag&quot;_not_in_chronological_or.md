---
title: "Why is &quot;git tag&quot; not in chronological order?"
date: 2014-01-12
forum: Programming Talk
---

### Post by terminator14 on 2014-01-12
I've been wondering this since I learned of git tags: what possible reason could the developers of git have for making "git tag" show tags in alphabetical order by default?
As far as I'm aware, tags are mainly used to label versions of a program. Why would anyone want to list version numbers alphabetically? This just sounds like an incredibly stupid idea to me. Am I missing something?

And even if there is a good reason for it, why is it so complicated to make it in chronological order? Surely this is something that would be used often enough to warrant a simple argument (ex: git tag -c), but instead, the solutions I've found do something like:

```
git log --tags --oneline --decorate --simplify-by-decoration
```

OR

```
git log --tags --simplify-by-decoration --pretty="format:%ci %d"
```

Why is this so complicated?

Note: If you suggest using git aliases, you're missing the point

EDIT: 

I asked this question on the git IRC channel on freenode, and this is what I was told:

1. "git tag" shows tags from all branches. While it may be helpful if you just cloned a project and only have the master branch, chronological order becomes significantly more useless when you have tags on multiple branches.
2. Lightweight tags don't store the date the tag was created. This means that if a tag is created today for a commit that was created a year ago, git has no way to know that the tag is newer than the commit.

---

### Post by 1clue on 2014-01-12
You made me realize that all my git tags are in both alphabetical and chronological order.  At least on the remote.

My local tags are the project I'm working on, and I've never had more than 2 at a time for one project yet. My remote tags are version numbers, which are in the format of v1_12_34 or similar.

In rare cases, we have several coworkers using a remote branch, but again there are only a few of those so far.  And they show up on top, since the versioned releases all have v1_...

---

### Post by terminator14 on 2014-01-12
Yes, sometimes using alphabetical order arranges the tags chronologically because tag names (version numbers) often follow a pattern, but that is basically a coincidence. When tags are displayed explicitly in chronological order, it doesn't matter what the tags are - they could have absolutely no pattern and they would still be arranged properly.

I see absolutely no advantage to having tags arranged alphabetically. Anyone know why they are?

---

### Post by 1clue on 2014-01-12
All I can think is that if you know what tag you want it would be easier to find.  But that assumes intimate knowledge of the project.  If you're just checking out a project to look at it you wouldn't know, and if you have a project that's been around for years you will probably have a LOT of tags.  I know our older projects have so many tags we put them in directories in Subversion.

Remember who wrote this.  Linus sort of assumes things about how people work.  I wonder if he would respond to this as a question?

---

### Post by terminator14 on 2014-01-12
> **1clue said:**
> All I can think is that if you know what tag you want it would be easier to find.  But that assumes intimate knowledge of the project.  If you're just checking out a project to look at it you wouldn't know, and if you have a project that's been around for years you will probably have a LOT of tags.  I know our older projects have so many tags we put them in directories in Subversion.

Remember who wrote this.  Linus sort of assumes things about how people work.  I wonder if he would respond to this as a question?

Linus has not made a commit to the git project since 2012, and in the entire 2012 year, he only made 5 commits. He has not been very active in the git project for quite some time. I would think that if this really was as stupid an idea as it appears to be, one of the active developers would have changed the default order of the 'git tag' command long ago. There must be a reason for it. I just can't figure out what it might be.

---

### Post by 1clue on 2014-01-12
I didn't realize he was off the project.

I don't see anywhere in the documentation how to make tag be chronological.  You would think they'd at least put a flag on it.

---

### Post by 1clue on 2014-01-12
The more I think about it, the more cases where chronological makes more sense than alphabetical.  I'd still want both though, but you could always sort by whatever column the tag name is in.

---

### Post by trent.josephsen on 2014-01-12
Maybe I'm thick, but I don't really see it. The point of a tag is to give a revision a nickname, not to keep your versions in order. When I use tags I always know what tag I'm looking for; I don't spend much time looking at the list. I'm not saying it's a bad idea -- I probably wouldn't notice if it changed -- but calling ASCII sort "stupid" is a little harsh in my opinion.

If chronological sort would work better for your workflow, patch it yourself. Obviously the Git dev team doesn't think it's a priority; that doesn't mean they're stupid, it just means they have a workflow that doesn't depend on it.

---

### Post by 1clue on 2014-01-12
Git is the most flexible revision control system I've ever seen.  Why would they not have a tagging system that can print chronologically?  I can see several reasons why it would be good to know chronology and even dates in the list.  For example, you have two tags with very similar names, which one is your recent one and which is from a few years back?

---

### Post by terminator14 on 2014-01-12
> **trent.josephsen said:**
> Maybe I'm thick, but I don't really see it. The point of a tag is to give a revision a nickname, not to keep your versions in order. When I use tags I always know what tag I'm looking for; I don't spend much time looking at the list. I'm not saying it's a bad idea -- I probably wouldn't notice if it changed -- but calling ASCII sort "stupid" is a little harsh in my opinion.

If chronological sort would work better for your workflow, patch it yourself. Obviously the Git dev team doesn't think it's a priority; that doesn't mean they're stupid, it just means they have a workflow that doesn't depend on it.

I didn't call anyone stupid. In fact, as I've stated, I'm not looking to change, or diss, but to understand why this is. I'm saying the idea sounds stupid, and comes from very intelligent developers, so there must be a reason for it.

> **1clue said:**
> Git is the most flexible revision control system I've ever seen.  Why would they not have a tagging system that can print chronologically?  I can see several reasons why it would be good to know chronology and even dates in the list.  For example, you have two tags with very similar names, which one is your recent one and which is from a few years back?

Indeed. But in addition to seeing several reasons why it would be a good idea, I see no reason NOT to do this by default. What advantages are there to having alphabetical order? Anyone looking for a specific commit can find it by having a rough idea when it was made, or doing a search (even grep will find it in seconds). Anyone looking for the latest tags, in order, has to type a long string. Why?

---

### Post by 1clue on 2014-01-12
@terminator14,

I agree with you.  It makes a LOT of sense to put the tags in chronological order, even more so because to sort it it's just **git tag | sort**.  Anyone using the command line for git knows about sort.

---

### Post by terminator14 on 2014-01-13
I asked this question on the git IRC channel on freenode, and this is what I was told:

1. "git tag" shows tags from all branches. While it may be helpful if you just cloned a project and only have the master branch, chronological order becomes significantly more useless when you have tags on multiple branches.
2. Lightweight tags don't store the date the tag was created. This means that if a tag is created today for a commit that was created a year ago, git has no way to know that the tag is newer than the commit. 

So I guess there's a reason for it after all.

---

### Post by 1clue on 2014-01-13
That's interesting.  And inconvenient.  That said, your commands in your first post are now aliases on my dev box.

That's one thing this thread accomplished, anyway.  :)

---

