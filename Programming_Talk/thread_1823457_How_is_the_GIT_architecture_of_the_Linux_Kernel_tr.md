---
title: "How is the GIT architecture of the Linux Kernel tree set up?"
date: 2011-08-12
forum: Programming Talk
---

### Post by konti on 2011-08-12
I'd like to know how the GIT architecture of the Linux kernel is set up? 

I'd like to start using GIT for projects on my work. 

I did some research in where i found out it's better to create multiple repo's then to maintain one big repo at the top.

If you look at how the development is done within the linux tree. You'l see that people have there own repo (named after there name). In where they develop with small portions of the total linux tree.

I'm assuming they push these changes for evaluation to a different repo, that contains the entire tree?

Well these are all vague assumptions, and  i'd like to know how it works. So maybe there is some GIT guru here that can clear some things up, or point me in the right direction?

---

### Post by CptPicard on 2011-08-12
Git is not centralized -- there is no one canonical Linux repository. I suspect that the Linux developers develop against their own repository and push and pull changes between each other as needed. 

In the end I suppose the canonical Linux repo from where releases come from is Linus' own...

---

### Post by konti on 2011-08-12
But do all developers use the same repo? Or is it possible to just clone a portion of all the code, work in you own repo and push/pull that?

---

### Post by CptPicard on 2011-08-12
The whole idea is that no, you do not have to work from the same repo. We can have developers all working on their own repository, and then you can choose with whom to push/pull and so on.

---

### Post by konti on 2011-08-12
I've asked the question about the linux kernel, to see how they work with it.

But i'll try to clarify my problem/question with an example.

e.a.

```
            root
         /          \
      App1                   App2
     /    \                /      \
  SomeCode1 SomeCode2   Somecode3 Somecode4
```


Often we develop systems that consist of multiple applications. On request we implement these within projects. e.a. a projectA starts in where we need to make changes to Somecode1, Somecode2 and Somecode3.
When the work is done we commit/push changes to the repo's App1 and App2. Both we tag with projectA_Final.

Now we'd like to be able to clone/get all files that were changed within the projectA_Final. Is this possible? Or do you see an other way of working to accomplish this?

It would be ideal if we could create a release package from this.

---

