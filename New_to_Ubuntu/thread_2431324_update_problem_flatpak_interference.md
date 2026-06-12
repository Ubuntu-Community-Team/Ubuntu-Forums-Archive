---
title: "update problem flatpak interference?"
date: 2019-11-14
forum: New to Ubuntu
---

### Post by grcoukell2 on 2019-11-14
Solved:     
When I used the terminal to update I got this message: The repository 'http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.

Is there something I can do to eliminate this problem?  I would like to use some flatpaks if it is permissible.

---

### Post by CatKiller on 2019-11-14
That PPA *doesn't* have releases for 19.10, as the message says. It also hasn't been updated in 2 months.

Flatpak is in the repositories anyway. If you're using 19.10, the version in the repositories is the same as the latest version in that PPA. Just get rid of that PPA.

As a general matter, leaping straight to downloading stuff from some website is the wrong approach. Had you used the package manager from the off, you wouldn't have got in that pickle. Linux isn't Windows.

---

### Post by grcoukell2 on 2019-11-15
Thanks for the advice. Solved.  How do I put solved in my entry to let others know? Or is this not done here on this forum? I will search adding solved.

---

### Post by grcoukell2 on 2019-11-15
I think I did it. Sorry to bother.

---

### Post by deadflowr on 2019-11-15
> **grcoukell2 said:**
> Thanks for the advice. Solved.  How do I put solved in my entry to let others know? Or is this not done here on this forum? I will search adding solved.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

