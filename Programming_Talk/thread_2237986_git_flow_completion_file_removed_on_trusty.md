---
title: "git flow completion file removed on trusty?"
date: 2014-08-05
forum: Programming Talk
---

### Post by stalet on 2014-08-05
I noticed after upgrading my ubuntu laptop to trusty that the bash completion for git-flow doesnt work anymore. And it seems like the /etc/bash_completion.d/git-flow file is missing.
I tried to install some other git packages to no avail. I therefor checked the package content for git-flow for the various distributions:

[http://packages.ubuntu.com/precise/all/git-flow/filelist](http://packages.ubuntu.com/precise/all/git-flow/filelist)
[http://packages.ubuntu.com/trusty/all/git-flow/filelist](http://packages.ubuntu.com/trusty/all/git-flow/filelist)

It seems that this file has been removed at some point. I restored the file from backup of my previous installation - and this worked fine.
But im still wondering: is there another package now that contains this functionality ? Have I been missing out on som git goodies ??
How should this be done now ?

---

### Post by stalet on 2014-08-05
I just found out that its registered a bug for this [https://bugs.launchpad.net/ubuntu/+source/git-flow/+bug/1322816](https://bugs.launchpad.net/ubuntu/+source/git-flow/+bug/1322816)

---

