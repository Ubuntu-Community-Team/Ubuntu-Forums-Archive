---
title: "problem : bazaar in launchpad"
date: 2008-07-15
forum: Programming Talk
---

### Post by lucky.developer on 2008-07-15
hi,
i am new to launchpad.net
i have been trying launchpad's features for some time now.
i created a branch(not associated with any project).
i tried to push some files from my system to that launchpad branch..but when i type that push commmand in my terminal(i gave the exact url of the branch given in lanuchpad site)..it says this


bzr: ERROR: Transport operation not possible: http does not support mkdir() 



what should i do?

---

### Post by bobbocanfly on 2008-07-15
Try running this command then trying to push

```
bzr launchpad-login
```

Otherwise, try this:

```
bzr push bzr+ssh://<USERNAME>@bazaar.launchpad.net/PATH/TO/BRANCH
```

If both of these fail please post the output of both of the commands.

---

