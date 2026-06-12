---
title: "Git newb question on 'git checkout'"
date: 2012-04-26
forum: Programming Talk
---

### Post by GammaPoint on 2012-04-26
Hi, I am getting started with git and understand (I think) the basic way to work with it, but I did something last night that I had a question about. 

I had started a new branch outside of master and had modified a file some. Then, instead of typing 'git checkout master' to go back to my master branch I accidentally just typed 'git checkout'. I haven't been able to find what *should* happen with the git checkout command with no arguments, but what it appeared to do is take me back to my master branch AND merge my experimental branch ontop of master. For example, if I then tried to merge my experimental branch onto master it would tell me that it was "already up to date" and it was clear that the file had been modified. 

Is this the expected behavior? It's fine by me because I was going to merge anyway, but I just couldn't find this expected result in any documentation.

---

### Post by Barrucadu on 2012-04-26
If given no arguments, "git checkout" does nothing.

---

### Post by MadCow108 on 2012-04-26
which version are you using?
I don't see any of this behavior with 1.7.9.5, git checkout does nothing.

if you checkout with changes it will try to apply your uncommitted changes to the new branch without committing them, or fail (then use -f to drop your changes)
I recommend using git-completions available in the git source to easily keep track of o which branch you are and in what state your working copy is (+ it gives tab completion on everything)
[https://github.com/git/git/blob/master/contrib/completion/git-completion.bash](https://github.com/git/git/blob/master/contrib/completion/git-completion.bash)

---

### Post by GammaPoint on 2012-04-26
> **MadCow108 said:**
> which version are you using?
I don't see any of this behavior with 1.7.9.5, git checkout does nothing.

if you checkout with changes it will try to apply your uncommitted changes to the new branch without committing them, or fail (then use -f to drop your changes)
I recommend using git-completions available in the git source to easily keep track of o which branch you are and in what state your working copy is (+ it gives tab completion on everything)


I'm using 1.7.7.4. I just repeated the behavior again.

```

[ME@hopper:~/my_codes]$git branch test
[ME@hopper:~/my_codes]$git checkout
[ME@hopper:~/my_codes]$git branch
* master
  test
[ME@hopper:~/my_codes]$git checkout test
Switched to branch 'test'
[ME@hopper:~/my_codes]$ls
batch_job  dft_io.py  GW  pseudo_related  README
[ME@hopper:~/my_codes]$emacs dft_io.py  <-----------made a change
[ME@hopper:~/my_codes]$ls
batch_job  dft_io.py  GW  pseudo_related  README
[ME@hopper:~/my_codes]$git status
# On branch test
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   dft_io.py
#
no changes added to commit (use "git add" and/or "git commit -a")
[ME@hopper:~/my_codes]$git checkout
M	dft_io.py
[ME@hopper:~/my_codes]$git status
# On branch test
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   dft_io.py
#
no changes added to commit (use "git add" and/or "git commit -a")
[ME@hopper:~/my_codes]$git checkout master
M	dft_io.py
Switched to branch 'master'
[ME@hopper:~/my_codes]$git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   dft_io.py
#
no changes added to commit (use "git add" and/or "git commit -a")

```

So you can see that my file has changed on my master branch despite me only changing it in the test branch (visual inspection of this file also confirms this).

---

### Post by Barrucadu on 2012-04-26
It's not "applied your changes", git merely isn't handling them. If you were to commit those changes in your test branch, you would see nothing in your master branch.

---

### Post by GammaPoint on 2012-04-26
> **Barrucadu said:**
> It's not "applied your changes", git merely isn't handling them. If you were to commit those changes in your test branch, you would see nothing in your master branch.

Yes, this is the behavior I see. Even if I run 'git checkout' in the test branch after making a commit it does not have those same changes present in master. 

I guess I just naively thought that anything I did would be contained to the test branch and that I didn't have to necessarily commit it to keep the two branches distinct (again, of course, this whole thing is caused by me typing 'git checkout' on accident so it's not a major issue obviously).

---

### Post by GammaPoint on 2012-04-27
I went ahead and marked this as solved. Thanks for all of those who helped answer my question!

---

