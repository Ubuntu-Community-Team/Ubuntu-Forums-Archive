---
title: "Revert a launchpad push?"
date: 2008-05-28
forum: Programming Talk
---

### Post by khughitt on 2008-05-28
Hi all,

I was wondering if anyone might be able to help me with a launchpad-related question. If I have a branched hosted at LP, and push a recent revision to the repository, is there any way to roll-back the push or to delete a specific revision?

Any help would be greatly appreciated.

Thanks!

---

### Post by Bubba64 on 2008-05-28
> **pwnedd said:**
> Hi all,

I was wondering if anyone might be able to help me with a launchpad-related question. If I have a branched hosted at LP, and push a recent revision to the repository, is there any way to roll-back the push or to delete a specific revision?

Any help would be greatly appreciated.

Thanks!

If you have downloaded a proposed update it is probably in synaptic and you can go back to the original package and force it. I am not sure if I am understanding your question.

---

### Post by bobbocanfly on 2008-05-28
> **pwnedd said:**
> Hi all,

I was wondering if anyone might be able to help me with a launchpad-related question. If I have a branched hosted at LP, and push a recent revision to the repository, is there any way to roll-back the push or to delete a specific revision?

Any help would be greatly appreciated.

Thanks!

Im not sure this will work but in theory it shoud:

```
cd $wherever_your_branch_is
bzr uncommit
bzr push
```

In theory this should remove the latest commit, then push the branch onto LP, without the commit. Let me know how this works!

---

### Post by khughitt on 2008-05-29
> **Bubba64]If you have downloaded a proposed update it is probably in synaptic and you can go back to the original package and force it. I am not sure if I am understanding your question.
[/QUOTE]

Hi Bubba64,

I think we are thinking of different things. I wasn't proposing a package update, but was rather working on a separate (non-Ubuntu) project on Launchpad, and trying to undo a revision.

[QUOTE=bobbocanfly said:**
> Im not sure this will work but in theory it shoud:

```
cd $wherever_your_branch_is
bzr uncommit
bzr push
```

In theory this should remove the latest commit, then push the branch onto LP, without the commit. Let me know how this works!

Thanks. This was the first thought I had, but unfortunately when I tried to push again I got an error message along the lines of "*Cannot push, branches have diverged!*"

In the end I decided to delete the entire branch (since I had just created it and there was only one commit anyways), and create it anew. This solution wouldn't have worked too well though if the branch was more mature. If anyone else has an idea of how to fix this sort of problem, I'd still be interested to hear it!

Thank you both for the input :)

---

### Post by bobbocanfly on 2008-05-29
I think the simplest way would be to just revert the changes? Delete the new files or lines of code or whatever, commit and push. Not quite as quick as having a script doing it for you, but still better than branch deletion.

/me awaits someone to come along with some obscure bash command that does this

---

### Post by khughitt on 2008-05-29
> **bobbocanfly said:**
> I think the simplest way would be to just revert the changes? Delete the new files or lines of code or whatever, commit and push. Not quite as quick as having a script doing it for you, but still better than branch deletion.

/me awaits someone to come along with some obscure bash command that does this

The only problem with that is that the reason I was trying to do the revert in the first-place was to remove some sensitive data that was accidentally uploaded. Because the entire history is available, changing back without removing the revision itself would still leave the data exposed.

The ideal solution to the problem really is not to upload things you don't want people to see in the first place :P

---

### Post by kiko-canonical on 2008-12-10
You were on the right track with the uncommit and push suggestion. You just missed a flag:

  bzr push --overwrite 

to finish the job. The reason you need --overwrite is that you're basically asking to change the history in your push location, which is destructive and therefore somewhat special.

---

### Post by andrikos on 2013-01-05
> **kiko-canonical said:**
> You were on the right track with the uncommit and push suggestion. You just missed a flag:

  bzr push --overwrite 

to finish the job. The reason you need --overwrite is that you're basically asking to change the history in your push location, which is destructive and therefore somewhat special.

Thank you very much!!

---

