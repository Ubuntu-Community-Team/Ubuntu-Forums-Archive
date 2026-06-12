---
title: "git help"
date: 2009-02-09
forum: Programming Talk
---

### Post by kevdog on 2009-02-09
Ive noticed a lot of repositories now switching to git from svn.  I noticed the cvs -> svn switch several years ago.  What advantages does git offer?

Also
Many times when cloning git trees, the download process for me stalls.  During the receiving objects phase, the progress meter stalls.  Is there a way to break the operation (Cntl-C) but pick up where it left off without starting over again?

What is the git equivalent of svn up?

Thanks.

---

### Post by stroyan on 2009-02-09
You can read a reasonable overview of advantages at [http://en.wikipedia.org/wiki/Git_(software](http://en.wikipedia.org/wiki/Git_(software))

Or you can watch git's creator's one hour presentation on it at [http://www.youtube.com/watch?v=4XpnKHJAok8](http://www.youtube.com/watch?v=4XpnKHJAok8)

There is no resume for git pull.  It has been discussed. But it is very difficult to implement.

"git pull" is roughly equivalent to "svn up".

---

### Post by imdano on 2009-02-09
For me, the main draw of distributed VCS solutions like git and bazaar over svn is improved branching support.  Subversion is pretty terrible at branching and merging, and when you're dealing with OSS projects with many distributed contributors, its really nice to be able to do it easily.  Bazaar (and presumably git, I don't have much experience with it) also has some nice features like shelving that make life easier.

See here for more info on git (and why it's better than svn): [http://whygitisbetterthanx.com/](http://whygitisbetterthanx.com/)

---

