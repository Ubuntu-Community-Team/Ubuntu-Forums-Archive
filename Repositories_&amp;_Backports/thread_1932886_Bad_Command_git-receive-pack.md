---
title: "Bad Command: git-receive-pack"
date: 2012-02-28
forum: Repositories &amp; Backports
---

### Post by carthmen on 2012-02-28
Hi all, got a problem.

Ubuntu 11.10 64-bit.

git up-to-date from repositories. 

 I am trying to push a new project to a network repository.

When I use "git push repo master" I connect tot the repo ok, but then get Bad Command: git-receive-pack.


From what i have been able to figure this is a PATH issue.  The system environment in the ssh connection to the codespaces repository does not include the path to my git-receive-pack file.

I tried to solve this by adding 
```

PATH=$PATH:/usr/bin
export PATH

```to the top of my "/etc/profile" file as this is file (I think) sets the global environment, but this has not fixed the issue.

At this point I'm pretty lost where to go next.   Anyone else have a possible solution.

Thanks as always,
Roger
Chicago

---

### Post by carthmen on 2012-03-02
I'm still working on this but have been spinning my tires so far.

I did read the man page and it seems that git-reveive-pack is only enabled if the client is authenticated, so maybe something there, however, i am authenticating with codespaces.com and have made rsa keys, the authentication is successful.

---

### Post by carthmen on 2012-03-03
Ok, i installed open-ssh-server and logged into my ubuntu 11.10 installation and logged into the shell and cheeked the $PATH var.  It does indeed include the path to my git-reveive-pack.

So, i'm guessing my initial idea that path was not pointing there in the ssh connection that git makes was wrong.

Anyone have any other thoughts that i might explore, i'm really at a wall here.

Is anyone having problems with "git push repo master" to a freshly made repository.

---

### Post by carthmen on 2012-03-03
ok, seems to be a problem on code-spaces side, i tried connecting to a different repository and pushed with no problem.

---

