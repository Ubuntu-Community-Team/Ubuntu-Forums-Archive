---
title: "git vocabulary: distinguishing origin, master, HEAD"
date: 2016-02-25
forum: Programming Talk
---

### Post by Drone4four on 2016-02-25
Origin is a reference to the remote upstream repository.

The current local branch currently being worked on is HEAD

And master is the &#8220;current development branch&#8221;

So if I **git checkout -b experimental-branch**, I will leave the current branch (master) and am now working on my newly created branch (experimental-branch*)

After making many local changes and commits, when I think my experiment is ready, I can push it to the remote repository (origin).  When I&#8217;m ready, I&#8217;m gonna **git fetch origin** to make sure I have the latest changes, and then push to origin.

Amiright?

I&#8217;m having difficulty distinguishing between HEAD and master.  What&#8217;s the difference?

Thanks for your attention.

---

### Post by papibe on 2016-02-25
> **Drone4four said:**
> The current local branch currently being worked on is HEAD
Yes, but more like 'HEAD points to what you are working on right now'.

> **Drone4four said:**
> And master is the &#8220;current development branch&#8221;
Sort of. 'current' when you have it checked out'. 'Yes' in the sense that is the main developing branch.

> **Drone4four said:**
> So if I **git checkout -b experimental-branch**, I will leave the current branch (master) and am now working on my newly created branch (experimental-branch*)

After making many local changes and commits, when I think my experiment is ready, I can push it to the remote repository (origin).  When I&#8217;m ready, I&#8217;m gonna **git fetch origin** to make sure I have the latest changes, and then push to origin.
Yes if:
[LIST]
[*]experimental-branch is being track on origin. If not, you just push it (you can decide to push and mark it for tracking too).
[*]you first merged experimental-branch with master, and you want to push master to origin.
[/LIST]
> **Drone4four said:**
> I&#8217;m having difficulty distinguishing between HEAD and master.  What&#8217;s the difference?
HEAD is a pointer to a commit, usually the tip of a branch. For instance (alpha and beta are branches):

[IMG]https://people.gnome.org/~federico/misc/git-repo-3.png[/IMG]
Does that help?
Regards.

---

### Post by trent.josephsen on 2016-02-27
To elaborate a little on what papibe said, HEAD and master both ultimately refer to commits, but they differ in their behavior.  HEAD always refers to the commit that is *checked out in the working tree*. master always refers to the commit that is the *latest one in the branch named "master"*.

If you check out a branch other than master (such as by `git checkout -b`), git will remember that HEAD is connected to that branch. If master and experimental-branch at first refer to the same commit, but you make a commit with experimental-branch checked out, then the new commit will be a child of experimental-branch, and experimental-branch will be updated to point to it. But master will be left alone because it's not the same branch that HEAD refers to.

(HEAD doesn't have to refer to a branch. It can refer to an arbitrary commit, in which case you get a somewhat disturbing message about it being detached. But just like it's normal for your head to be on your neck, it's normal for your HEAD to be on the branch you're working in.)

It helps me to realize that commits in git aren't actually named stuff like "master"; they all have "proper" names, like 20db45b34467f7624f2527c89a9b967506baa92f. The different "nicknames" we refer to them by are all different kinds of pointers that people use for our own convenience, with different behaviors. Here's three common types of pointers, by increasing volatility:
- **Tags** always point to the same commit unless you change them explicitly.
- **Branches** such as master update when you commit to the branch, so that the branch name always points to the latest commit.
- **HEAD** updates whenever the "currently checked-out commit" changes, which can happen because you made a new commit or just checked out a different branch.

[This SO question](https://stackoverflow.com/questions/2304087/what-is-head-in-git) has some good answers on the nature of HEAD, including a link to [this talk](https://youtu.be/ZDR433b0HJY?t=45m58s), which has some good illustrative diagrams.

I often give too much information so I'm stopping here. Hope this helps.

---

### Post by papibe on 2016-02-28
> **trent.josephsen said:**
> ... good answers on the nature of HEAD, including a link to [this talk](https://youtu.be/ZDR433b0HJY?t=45m58s), which has some good illustrative diagrams.
Great video! Thanks for sharing it, trent.josephsen :)

Regards.

---

### Post by Drone4four on 2016-03-02
Thanks **papibe** for your clarifications.

A really large codebase organized by git will have feature and fix branches (many large, many small).  Each of these branches could be named just about anything, with names being determined by the individual contributors.  The master branch is the default one.  I Googled git 'branch diagram' which turned up numerous helpful information, with one particular image from a random blog post dated April 2014 titled, “[A Successful Git Branching Model With Enterprise Support]("http://tleyden.github.io/blog/2014/04/09/a-successful-git-branching-model-with-enterprise-support/")”. The main diagram in that blog post depicts the ‘mainline’ master branch, in addition to feature, release candidate and stable branches.  Origin is whatever lives on the primary, official GitHub repository (I know Linus doesn’t use GitHub to host his project). This makes sense.  

> **trent.josephsen said:**
> HEAD doesn't have to refer to a branch. It can refer to an arbitrary commit, in which case you get a somewhat disturbing message about it being detached. But just like it's normal for your head to be on your neck, it's normal for your HEAD to be on the branch you're working in.

I found a doc on git-scm which explains the ‘detached HEAD’ concept, titled: "[git checkout]("http://git-scm.com/docs/git-checkout#_detached_head")” So does HEAD follow each developer everywhere on the git branching hierarchy, no matter what branch s/he’s on? In most circumstances, yes, HEAD follows each developer on along his/her commits and branches but it is possible to have contributors making changes without HEAD, it’s just that git will pester the developer with “detached” HEAD messages. How accurate is this explanation?

---

### Post by trent.josephsen on 2016-03-02
> **Drone4four said:**
> A really large codebase organized by git will have feature and fix branches (many large, many small).  Each of these branches could be named just about anything, with names being determined by the individual contributors.  The master branch is the default one.[...]
Well... not necessarily. That is, lots of projects that use git *also* have workflows that involve feature branches, fix branches, and mainline branches named "master". But that's a fact about a specific workflow, not about git. Git is version control; it gives you a set of tools: add, commit, branch, checkout, merge. What you do with those tools is up to you. You can build many different workflows using git as an engine; [here's](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) a page comparing some popular ones.

> I found a doc on git-scm which explains the ‘detached HEAD’ concept, titled: "[git checkout]("http://git-scm.com/docs/git-checkout#_detached_head")” So does HEAD follow each developer everywhere on the git branching hierarchy, no matter what branch s/he’s on? In most circumstances, yes, HEAD follows each developer on along his/her commits and branches but it is possible to have contributors making changes without HEAD, it’s just that git will pester the developer with “detached” HEAD messages. How accurate is this explanation?
HEAD is both (1) what's currently checked out and (2) the parent of any commit you make. HEAD may be "detached", meaning it points to something that isn't a branch, but you can't *not* have a HEAD (in a regular non-bare repository). The danger (well, annoyance) of working detached is that HEAD will change whenever you check out anything else, and so the next time you run `git checkout` anything that you committed is lost unless you made a branch that points to it.

If you're struggling to visualize this, I encourage you to try it out in your own repository with some way of viewing the repo graphically, like gitk or `git log --graph`. You can ask for the proper name of HEAD by running `git show-ref --head HEAD`.

Hope this helps.

---

