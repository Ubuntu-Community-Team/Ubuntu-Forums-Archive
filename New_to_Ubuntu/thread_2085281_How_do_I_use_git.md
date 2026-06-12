---
title: "How do I use git?"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by whein on 2012-11-17
Ok, been using Ubuntu for a few years now, familiar with SVN and the concepts of revision control repositories, but... I have never used git before.  I am trying to get a patched version of OpenOCD installed on 12.04 and am having a hard time finding documentation meant for noobs.

I managed to clone the OpenOCD repository to my local machine using ```
git clone git://git.code.sf.net/p/openocd/code
```
and now I want to apply the patches from
[http://openocd.zylin.com/809](http://openocd.zylin.com/809)
[http://openocd.zylin.com/810](http://openocd.zylin.com/810)
[http://openocd.zylin.com/855](http://openocd.zylin.com/855)

This is all based on trying to follow the instructions at [http://pulkomandy.tk/_/_Electronique/_Discovering%20the%20STM32F3%20Discovery](http://pulkomandy.tk/_/_Electronique/_Discovering%20the%20STM32F3%20Discovery)

What I tried:
```

whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$ git clone git://git.code.sf.net/p/openocd/code
Cloning into 'code'...
remote: Counting objects: 42998, done.
remote: Compressing objects: 100% (9497/9497), done.
remote: Total 42998 (delta 35373), reused 40564 (delta 33375)
Receiving objects: 100% (42998/42998), 9.54 MiB | 114 KiB/s, done.
Resolving deltas: 100% (35373/35373), done.
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$ cd code
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/09/809/1 && git checkout FETCH_HEAD
remote: Counting objects: 11, done
remote: Finding sources: 100% (6/6)
remote: Total 6 (delta 2), reused 3 (delta 2)
Unpacking objects: 100% (6/6), done.
From [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd)
 * branch            refs/changes/09/809/1 -> FETCH_HEAD
Note: checking out 'FETCH_HEAD'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at 3b3e3ee... flash: add stm32f3 rev 2 flash support
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/09/809/2 && git format-patch -1 --stdout FETCH_HEAD
fatal: Couldn't find remote ref refs/changes/09/809/2
Unexpected end of command stream
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/10/810/1 && git checkout FETCH_HEAD
remote: Counting objects: 18, done
remote: Finding sources: 100% (11/11)
remote: Total 11 (delta 5), reused 6 (delta 5)
Unpacking objects: 100% (11/11), done.
From [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd)
 * branch            refs/changes/10/810/1 -> FETCH_HEAD
Warning: you are leaving 2 commits behind, not connected to
any of your branches:

  3b3e3ee flash: add stm32f3 rev 2 flash support
  a4830e7 Restore -dev suffix, archive NEWS file, add new blank NEWS file - start new cycle for version 0.7.0.

If you want to keep them by creating a new branch, this may be a good time
to do so with:

 git branch new_branch_name 3b3e3ee51d9f6a93fa6eda427de663e99b9409ee

HEAD is now at 6d248be... cfg: add STM32F3-DISCOVERY board support
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/10/810/2 && git checkout FETCH_HEAD
remote: Counting objects: 18, done
remote: Finding sources: 100% (11/11)
remote: Total 11 (delta 5), reused 7 (delta 5)
Unpacking objects: 100% (11/11), done.
From [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd)
 * branch            refs/changes/10/810/2 -> FETCH_HEAD
Warning: you are leaving 3 commits behind, not connected to
any of your branches:

  6d248be cfg: add STM32F3-DISCOVERY board support
  3b3e3ee flash: add stm32f3 rev 2 flash support
  a4830e7 Restore -dev suffix, archive NEWS file, add new blank NEWS file - start new cycle for version 0.7.0.

If you want to keep them by creating a new branch, this may be a good time
to do so with:

 git branch new_branch_name 6d248be7876e2c82838f05acfc3dae2cceb465d2

HEAD is now at 32c706a... cfg: add STM32F3-DISCOVERY board support
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/10/810/3 && git checkout FETCH_HEAD
fatal: Couldn't find remote ref refs/changes/10/810/3
Unexpected end of command stream
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocdgit](http://openocd.zylin.com/openocdgit) fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/55/855/1 && git checkout FETCH_HEAD
remote: Counting objects: 9, done
remote: Finding sources: 100% (5/5)
remote: Total 5 (delta 3), reused 4 (delta 3)
Unpacking objects: 100% (5/5), done.
From [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd)
 * branch            refs/changes/55/855/1 -> FETCH_HEAD
Warning: you are leaving 3 commits behind, not connected to
any of your branches:

  32c706a cfg: add STM32F3-DISCOVERY board support
  3b3e3ee flash: add stm32f3 rev 2 flash support
  a4830e7 Restore -dev suffix, archive NEWS file, add new blank NEWS file - start new cycle for version 0.7.0.

If you want to keep them by creating a new branch, this may be a good time
to do so with:

 git branch new_branch_name 32c706a850c187108daa34f47ee5feb39d2ffe18

HEAD is now at 19361ea... cfg: fix incorrect stm32f3 TAPID
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/55/855/2 && git checkout FETCH_HEAD
fatal: Couldn't find remote ref refs/changes/55/855/2
Unexpected end of command stream
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 

```
What am I doing wrong and what should I do instead?

---

### Post by dodle on 2012-11-19
It looks like you were able to download the source code, you just need to apply the patches, correct?

Here are direct links to the patches. Right-click and save them to your computer:

[809](http://openocd.zylin.com/gitweb?p=openocd.git;a=patch;h=0b98ca361090c9a407394da0b31938e46e1c4bf0)
[810](http://openocd.zylin.com/gitweb?p=openocd.git;a=patch;h=2076ba093d65f5d4a9069504aca09b9e1696bd02)
[855](http://openocd.zylin.com/gitweb?p=openocd.git;a=patch;h=abccd76ea45df7a3fad3fbb8e0def11e994fc20c)

When I was learning how to patch source code I followed this tutorial: [http://jungels.net/articles/diff-patch-ten-minutes.html](http://jungels.net/articles/diff-patch-ten-minutes.html)

You should be able to cd into the root of the source tree and apply the patches like this:

```
$ patch -p1 < /path/to/patch/file.patch
```

I hope that's the answer you are looking for.

**----- Edit -----**

It looks like the patches have already made it into the main source so it doesn't need to be patched. I just tried applying the patches and all of the changes were already deteced:

```
$ patch -p1 < ../809.patch
patching file src/flash/nor/stm32f1x.c
Reversed (or previously applied) patch detected!  Assume -R? [n] n
Apply anyway? [n] n
Skipping patch.
2 out of 2 hunks ignored -- saving rejects to file src/flash/nor/stm32f1x.c.rej

$ patch -p1 < ../810.patch
The next patch would create the file tcl/board/stm32f3discovery.cfg,
which already exists!  Assume -R? [n]
Apply anyway? [n] n
Skipping patch.
1 out of 1 hunk ignored

$ patch -p1 < ../855.patch
patching file tcl/target/stm32f3x_stlink.cfg
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n] n
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file tcl/target/stm32f3x_stlink.cfg.rej
```

---

### Post by bboyandru on 2012-11-28
Hi,
The simplest way is to use OpenOCD 0.6.1 which has these changes embedded.
I have a tutorial at:
[http://www.engineering-diy.blogspot.ro/2012/11/stm32f3-discovery-eclipse-openocd.html]("http://www.engineering-diy.blogspot.ro/2012/11/stm32f3-discovery-eclipse-openocd.html")
> **whein said:**
> Ok, been using Ubuntu for a few years now, familiar with SVN and the concepts of revision control repositories, but... I have never used git before.  I am trying to get a patched version of OpenOCD installed on 12.04 and am having a hard time finding documentation meant for noobs.

I managed to clone the OpenOCD repository to my local machine using ```
git clone git://git.code.sf.net/p/openocd/code
```
and now I want to apply the patches from
[http://openocd.zylin.com/809](http://openocd.zylin.com/809)
[http://openocd.zylin.com/810](http://openocd.zylin.com/810)
[http://openocd.zylin.com/855](http://openocd.zylin.com/855)

This is all based on trying to follow the instructions at [http://pulkomandy.tk/_/_Electronique/_Discovering%20the%20STM32F3%20Discovery](http://pulkomandy.tk/_/_Electronique/_Discovering%20the%20STM32F3%20Discovery)

What I tried:
```

whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$ git clone git://git.code.sf.net/p/openocd/code
Cloning into 'code'...
remote: Counting objects: 42998, done.
remote: Compressing objects: 100% (9497/9497), done.
remote: Total 42998 (delta 35373), reused 40564 (delta 33375)
Receiving objects: 100% (42998/42998), 9.54 MiB | 114 KiB/s, done.
Resolving deltas: 100% (35373/35373), done.
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$
whein@AwesomeLT:~/Desktop/stm32/tmp$ cd code
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/09/809/1 && git checkout FETCH_HEAD
remote: Counting objects: 11, done
remote: Finding sources: 100% (6/6)
remote: Total 6 (delta 2), reused 3 (delta 2)
Unpacking objects: 100% (6/6), done.
From [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd)
 * branch            refs/changes/09/809/1 -> FETCH_HEAD
Note: checking out 'FETCH_HEAD'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at 3b3e3ee... flash: add stm32f3 rev 2 flash support
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/09/809/2 && git format-patch -1 --stdout FETCH_HEAD
fatal: Couldn't find remote ref refs/changes/09/809/2
Unexpected end of command stream
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/10/810/1 && git checkout FETCH_HEAD
remote: Counting objects: 18, done
remote: Finding sources: 100% (11/11)
remote: Total 11 (delta 5), reused 6 (delta 5)
Unpacking objects: 100% (11/11), done.
From [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd)
 * branch            refs/changes/10/810/1 -> FETCH_HEAD
Warning: you are leaving 2 commits behind, not connected to
any of your branches:

  3b3e3ee flash: add stm32f3 rev 2 flash support
  a4830e7 Restore -dev suffix, archive NEWS file, add new blank NEWS file - start new cycle for version 0.7.0.

If you want to keep them by creating a new branch, this may be a good time
to do so with:

 git branch new_branch_name 3b3e3ee51d9f6a93fa6eda427de663e99b9409ee

HEAD is now at 6d248be... cfg: add STM32F3-DISCOVERY board support
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/10/810/2 && git checkout FETCH_HEAD
remote: Counting objects: 18, done
remote: Finding sources: 100% (11/11)
remote: Total 11 (delta 5), reused 7 (delta 5)
Unpacking objects: 100% (11/11), done.
From [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd)
 * branch            refs/changes/10/810/2 -> FETCH_HEAD
Warning: you are leaving 3 commits behind, not connected to
any of your branches:

  6d248be cfg: add STM32F3-DISCOVERY board support
  3b3e3ee flash: add stm32f3 rev 2 flash support
  a4830e7 Restore -dev suffix, archive NEWS file, add new blank NEWS file - start new cycle for version 0.7.0.

If you want to keep them by creating a new branch, this may be a good time
to do so with:

 git branch new_branch_name 6d248be7876e2c82838f05acfc3dae2cceb465d2

HEAD is now at 32c706a... cfg: add STM32F3-DISCOVERY board support
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/10/810/3 && git checkout FETCH_HEAD
fatal: Couldn't find remote ref refs/changes/10/810/3
Unexpected end of command stream
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocdgit](http://openocd.zylin.com/openocdgit) fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/55/855/1 && git checkout FETCH_HEAD
remote: Counting objects: 9, done
remote: Finding sources: 100% (5/5)
remote: Total 5 (delta 3), reused 4 (delta 3)
Unpacking objects: 100% (5/5), done.
From [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd)
 * branch            refs/changes/55/855/1 -> FETCH_HEAD
Warning: you are leaving 3 commits behind, not connected to
any of your branches:

  32c706a cfg: add STM32F3-DISCOVERY board support
  3b3e3ee flash: add stm32f3 rev 2 flash support
  a4830e7 Restore -dev suffix, archive NEWS file, add new blank NEWS file - start new cycle for version 0.7.0.

If you want to keep them by creating a new branch, this may be a good time
to do so with:

 git branch new_branch_name 32c706a850c187108daa34f47ee5feb39d2ffe18

HEAD is now at 19361ea... cfg: fix incorrect stm32f3 TAPID
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ git fetch [http://openocd.zylin.com/openocd](http://openocd.zylin.com/openocd) refs/changes/55/855/2 && git checkout FETCH_HEAD
fatal: Couldn't find remote ref refs/changes/55/855/2
Unexpected end of command stream
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 
whein@AwesomeLT:~/Desktop/stm32/tmp/code$ 

```
What am I doing wrong and what should I do instead?

---

