---
title: "Git fatal error: Remote end hung up"
date: 2010-04-04
forum: Repositories &amp; Backports
---

### Post by Friqenstein on 2010-04-04
Hello all,

I'm trying to use **Git** to clone repository, however it keeps returning the following:```
:$ git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git
Initialized empty Git repository in /home/devs/linux/linux-2.6/.git/
remote: Counting objects: 1532234, done.
remote: Compressing objects: 100% (245746/245746), done.
fatal: The remote end hung up unexpectedly0.00 KiB | 5 KiB/s    
fatal: early EOF
fatal: index-pack failed
:$
```Any ideas why it's hanging up with no warnings or indication?
I've tried the Google search, but that didn't turn up anything worth a darn.
The only 'solutions' that are listed via searches are solutions that were related to the actual repository server side having issues.
I find it hard to believe that the main kernel repository would be having issues too, but I could be wrong.

Any help is greatly appreciated.
Tnx

---

### Post by Friqenstein on 2010-04-04
Well, I think I may have found the problem.
It seems that there were 2 different issues at hand:
1) The remote server did seem to have some connection issue briefly
2) The connection I'm using has just recently filed reports of massive dropouts/packet losses which seems to be an intermittent problem.

Now I'm able to get the Git to start cloning the repository, however it eventually drops out after about 12-25MB of downloaded source. So I'm just re-running the CLI and it picks up where it previously dropped off. Hopefully this will not lead to any CRC issues with the cloned sources.

L8rz

---

