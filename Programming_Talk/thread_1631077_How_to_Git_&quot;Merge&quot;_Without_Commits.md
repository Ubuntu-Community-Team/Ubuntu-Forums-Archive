---
title: "How to Git &quot;Merge&quot; Without Commits"
date: 2010-11-26
forum: Programming Talk
---

### Post by huangyingw on 2010-11-26
Hello all,
    My next job is to use git to co-work with other guys. And this raise me a trouble, as describe bellow:
    I am using git to maintain my codes in private branch, say "dev". And branch "master" is the branch I co-work with others guys.
    Suppose that I have done a lot of casual and frequent commits at my own branch "dev". Sooner or later, I would like to "merge" my work at "dev" into "master" for others to fetch.
    But I could not do normal merge action, for it would also bring a lots of my casual commits into master branch at the same time. That is why I need a special "merge".
    Someone may recommend "diff" and patch, but the problem is that I always got a lot of patch failed errors after patching, even in a quite small demo-purpose git directory. So, I do not dare to use this solution to co-work with others. 
    I need a balance between my casual and free work and co-work with others:)

---

### Post by StephenF on 2010-11-26
This will merge in whatever is currently in your index as well so you might want to clean that out first.
```

git checkout dev
git reset --soft `git merge-base dev master`
git commit -m "Sum of changes in dev made since last merge"
git checkout master
git merge dev

```
Your fine grained history is destroyed. I hope that nobody else is working from your dev branch and bases their code off of that since they will no longer be able to easily merge their code back in.

Once you share a branch it is no longer exclusively yours and should from that moment not be altered except to add more commits.

---

### Post by skillet-thief on 2010-11-26
I suppose it depends on what is in your casual commits. StephenF's solution would lump them all into a single commit, but that may not be what you want. It sounds like you want to keep your "casual commits" private while merging your "good" commits into the public repository. 

You might think about starting a new local branch based on the current, upstream master, and then using git cherrypick to apply your "good" commits to it. When you are satisfied with this new branch, you could commit it to the public repo. 

This is what I would try, but then I'm not a git guru either.

---

### Post by huangyingw on 2010-11-26
> **StephenF said:**
> This will merge in whatever is currently in your index as well so you might want to clean that out first.
```

git checkout dev
git reset --soft `git merge-base dev master`
git commit -m "Sum of changes in dev made since last merge"
git checkout master
git merge dev

```
Your fine grained history is destroyed. I hope that nobody else is working from your dev branch and bases their code off of that since they will no longer be able to easily merge their code back in.

Once you share a branch it is no longer exclusively yours and should from that moment not be altered except to add more commits.
Sorry, I don't like my fine grained history is lost. For they might be important for me to do bisect to debut in future. That is why I like to do fine grained commit:)

---

### Post by huangyingw on 2010-11-26
> **skillet-thief said:**
> I suppose it depends on what is in your casual commits. StephenF's solution would lump them all into a single commit, but that may not be what you want. It sounds like you want to keep your "casual commits" private while merging your "good" commits into the public repository. 

You might think about starting a new local branch based on the current, upstream master, and then using git cherrypick to apply your "good" commits to it. When you are satisfied with this new branch, you could commit it to the public repo. 

This is what I would try, but then I'm not a git guru either.
In my understanding, git cherrypick would only apply the changes introduced by that commit. That would cause some trouble. For example, if "dev" branch has diverged from "master", and has three new commits:c1,c2,c3. If only
```

git checkout master
git cherrypick c3

```
then, since the changes by c1,c2, were not introduced, the final result would be very strange and dangerous.
However, as I am not familiar with "git-shell", maybe my next experiment is to try to realize a "loop cherrypick" from 'git merge-base dev master' to 'HEAD of dev'. 
I have not tried this solution, for I am not expert of "git-shell"
Could someone help me with this?

---

### Post by huangyingw on 2010-11-26
I have a rather rough solution: copy the origin git directory to another place. Do my work there, and at a mature stage, use ```
rsync --exclude .git 
```to "sync back" my code to the origin place for public to fetch. While this is rather raw.

---

### Post by skillet-thief on 2010-11-26
I guess I don't understand the problem you are trying to solve. If you want to merge all of your commits with the upstream repo, then a simple merge should be fine. If you want to merge just some of your commits, then git cherrypick might work for you. We may need more explanations of what you mean by "casual commits".

---

### Post by huangyingw on 2010-11-26
> **skillet-thief said:**
> I guess I don't understand the problem you are trying to solve. If you want to merge all of your commits with the upstream repo, then a simple merge should be fine. If you want to merge just some of your commits, then git cherrypick might work for you. We may need more explanations of what you mean by "casual commits".
yes, what I need is to introduce all the changes from all the diverged commits of the upstream repo, then, make one and only one commit with commit log at public branch.
In my context, "casual commits" == "fine grained". For English is not my mother language, so difficult to express clearly, until I saw StephenF's "fine grained":)

---

### Post by CptPicard on 2010-11-26
Are you sure the fine-grained commits are a problem? Git discourages huge commits anyway, and if you did dump a humongous commit somehow onto master, I'm not sure your preserved fine-grained history, if you had one, would be very meaningful in terms of master anymore... you'd have issues merging from dev in the future.

---

### Post by StephenF on 2010-11-26
Why even have a branch called dev if it's just yours? You could create feature branches which have short lives and specific themes. 

Suggestion: huang-feat[-mature]/revised-file-dialog

This says who owns it, that its a feature branch, and more or less what it's meant to do. If others think it's a good thing they can merge it themselves.

Git allows many different kinds of work-flow. Your problem appears to revolve around project management. Does the way the project code-base is integrated take full advantage of the strengths of Git, or conversely would a different tool fit your team's work style better?

This book covers project management: [Version control with Git]("http://oreilly.com/catalog/9780596520137")

---

### Post by huangyingw on 2010-11-27
> **StephenF said:**
> Why even have a branch called dev if it's just yours? You could create feature branches which have short lives and specific themes. 

Suggestion: huang-feat[-mature]/revised-file-dialog

This says who owns it, that its a feature branch, and more or less what it's meant to do. If others think it's a good thing they can merge it themselves.

Git allows many different kinds of work-flow. Your problem appears to revolve around project management. Does the way the project code-base is integrated take full advantage of the strengths of Git, or conversely would a different tool fit your team's work style better?

This book covers project management: [Version control with Git]("http://oreilly.com/catalog/9780596520137")
Currently, I am only working with myself, so, both the "dev" and "master" branch are only owned by myself. I am only prepare in advance for my future co-work in new company with git version control:(
Ennn,,thanks for providing information about git work flow. I have that pdf called "version control with git", and I will read it again.

---

### Post by huangyingw on 2010-11-27
> **CptPicard said:**
> Are you sure the fine-grained commits are a problem? Git discourages huge commits anyway, and if you did dump a humongous commit somehow onto master, I'm not sure your preserved fine-grained history, if you had one, would be very meaningful in terms of master anymore... you'd have issues merging from dev in the future.
I am not sure. I am just afraid that, this might be a problem in my next employer. While I am not sure about their principle, so, I am trying to predict the near future circumstance.

---

### Post by MadCow108 on 2010-11-28
you can use:
git rebase -i some-starting-rev
to interactively merge some of your "casual" commits into larger ones (->squash), remove useless ones (->just delete the line), edit them (->edit) and reorder them
Then you merge your cleaned up branch with master.
see the interactive section of man git-rebase

Obviously you should not have published your dev branch when you attempt to do this intrusive rebasing or you'll screw up the tree of other users.

---

### Post by wmcbrine on 2010-11-28
Git doesn't really support what you want to do, and IMHO, that's a good thing. Huge commits are always a lose. Just write adequate descriptions for every commit, and expect them all to be shared with your colleagues.

---

