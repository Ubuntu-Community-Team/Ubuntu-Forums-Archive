---
title: "How to &quot;Update to the Latest&quot; on TortuiseGit after Git Pushing?"
date: 2009-06-05
forum: Programming Talk
---

### Post by huangyingw on 2009-06-05
Hello,
    I am a beginner at git, I am using TortuiseGIt. And get many confusions about it.
    My first question is: After push action on a local cloned repository, how could the remote "parent" repository get the latest change?
    Currently, my only choise is to use "stash save", is this best and only way? Do git has the command like "update to latest" command? Or, by default, git will have to stash my work first, before updating to the latest version?
    To demo, let me take a simplest example.
    I clone from remote repP, to local repC. Both repP and repC only have the default master branch.
    I add some files on repC, and commit my work to local master. Then I use push command to push my change to the remote repP.
    After pushing operation on local repC, I go to repP. I could see my local repC's logs on repP, but I could not see the files I just added on repC. Until using "stash save" on repP, I could see the files I added on repC.
    Is there a simple command like "update to the latest" in Git to realize this?

---

