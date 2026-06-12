---
title: "Using bzr to Manage My Text Files"
date: 2008-09-26
forum: Programming Talk
---

### Post by igb on 2008-09-26
I am using bzr to create versioned "backups" of my Emacs org mode files. I run a nightly cron job which does a "bzr commit -m "Autoupdate". What I would like to do is to also somehow push these changes to a repository on my Web server, so I can always get an update of my files on my notebook if I go out without first updating them from my working copy.

bzr is so flexible that there seem to be numerous ways to do this. I am seeking advise on how other people would accomplish this task.

In a nutshell what I want to accomplish is for my auto-commmit script to also be able to update another "repository" on my web server to keep it in sync with the copy on my local network.

I guess that I could simply use rsync to do it, but is there a more bzr like way?

Ian.

---

### Post by olejorgen on 2008-09-29
Bear in mind that I'm a bzr noob, but I'd guess **bzr push**

---

### Post by days_of_ruin on 2008-09-29
[http://doc.bazaar-vcs.org/bzr.dev/en/user-guide/index.html#publishing-a-branch]("http://doc.bazaar-vcs.org/bzr.dev/en/user-guide/index.html#publishing-a-branch")

That should answer your question.

---

### Post by snova on 2008-09-29
I'm pretty sure the command is "bzr push", but although I can use Bazaar relatively well, I've never used the branching commands before.

You could also switch things around a bit and put the master copy on the server. Then your local copy would just be a checkout, and the command is "bzr commit" for certain.

Oh, and remember to create a branch on the server.

---

### Post by igb on 2008-09-30
Thanks for the suggestions. After more research I created a repo on my remote server and am using bzr rspush, as it's bandwidth friendly and I am using  standalone branch.

Ian.

---

