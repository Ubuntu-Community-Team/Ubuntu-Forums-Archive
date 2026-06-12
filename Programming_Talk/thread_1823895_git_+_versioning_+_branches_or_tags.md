---
title: "git + versioning + branches or tags"
date: 2011-08-12
forum: Programming Talk
---

### Post by azzamite on 2011-08-12
Hello forum

I have a private git repository from where I can clone, push and pull as long as there is internet.

Now I'm wondering how can I save the current status of the project under a version number or something like that.

I tried with branches and tags, but it seems that I'm missing something
```
git branch 3.0
git checkout 3.0
# do something, add, commit and push
```
That branch exists only in that directory because push didn't upload it to the private repository (or so I think), so I can't checkout 3.0 from other machine and even if I clone the whole project and list the branches 3.0 is nowhere to be found.

I basically want "head" to point to what I'm doing and still be able to go with my advisor and checkout/clone in his machine something that works, ie: 3.0 in this case.

Any ideas?

cheers

---

### Post by tanderson on 2011-08-12
Assuming your advisors repository is cloned from yours, you need to have him set up a tracking branch on your 3.0 branch. then after you make changes to the 3.0 have him pull down the changes with something like "git pull origin 3.0". Make sure that the 3.0 branch is checked out when the pull command is issued.

---

### Post by azzamite on 2011-08-12
> **tanderson said:**
> Assuming your advisors repository is cloned from yours,

The problem is that we can't connect to each other directly, it has to be trough the repository (public ip: ), and I don't know jet how to upload the branch to it.

I need to do what everyone on sourceforge, github, google code, etc. does:

Does it compiles and works? give it a new version and announce.

But I don't know how to do that using git (ie: without making a tar ball of the folder).

Any ideas?

---

### Post by Lux Perpetua on 2011-08-13
On your machine: ```
git push origin 3.0
```
On the other machine: ```
git pull origin 3.0
```

---

### Post by azzamite on 2011-08-13
> **Lux Perpetua said:**
> On your machine: ```
git push origin 3.0
```

That worked, thanks : )

---

### Post by Lux Perpetua on 2011-08-13
> **azzamite said:**
> That worked, thanks : )Happy to help. Make sure you understand tanderson's post as well: the other computer will need to set up a tracking branch before pulling. You can do this with ```
git checkout -b 3.0 origin/3.0
```Then you can pull the remote 3.0 branch into the local 3.0 branch. Every time you update the local branch, you need to check it out first.

---

