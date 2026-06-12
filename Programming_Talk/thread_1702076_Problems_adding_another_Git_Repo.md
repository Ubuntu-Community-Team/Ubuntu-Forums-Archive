---
title: "Problems adding another Git Repo"
date: 2011-03-07
forum: Programming Talk
---

### Post by partyk1d24 on 2011-03-07
Having trouble adding a new git repo. So I have an existing server set up and I am trying to add my model to a new Repo. To do this I started off editing the gitosis.conf...

```
[group coinstoremodel]
members = jackie@jackie-Latitude-E6410
writable = coinstoremodel
```Then I try to setup the new repo...

```
jackie@jackie-Latitude-E6410:~/workspace/coinstoremodel$ rm -rf .git/
jackie@jackie-Latitude-E6410:~/workspace/coinstoremodel$ git init
Initialized empty Git repository in /home/jackie/workspace/coinstoremodel/.git/
jackie@jackie-Latitude-E6410:~/workspace/coinstoremodel$ git add .
jackie@jackie-Latitude-E6410:~/workspace/coinstoremodel$ git commit -m "Creating the Repo" ./
jackie@jackie-Latitude-E6410:~/workspace/coinstoremodel$ git remote add origin git@66.228.32.121:repositories/coinstoremodel.git
jackie@jackie-Latitude-E6410:~/workspace/coinstoremodel$ git push origin master:refs/heads/master
fatal: 'repositories/coinstoremodel.git' does not appear to be a git repository
fatal: The remote end hung up unexpectedly
jackie@jackie-Latitude-E6410:~/workspace/coinstoremodel$ 
```

Any ideas?

[B]UPDATE!!!
[/B]Got it working using a mixture of 
[http://stackoverflow.com/questions/3433198/gitosis-git-error-fatal-home-git-repositories-idea-generator-git-does-not](http://stackoverflow.com/questions/3433198/gitosis-git-error-fatal-home-git-repositories-idea-generator-git-does-not)

[http://mapopa.blogspot.com/2009/10/git-insufficient-permission-for-adding.html](http://mapopa.blogspot.com/2009/10/git-insufficient-permission-for-adding.html)

---

