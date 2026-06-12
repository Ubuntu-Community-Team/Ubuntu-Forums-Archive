---
title: "managing multiple rsa keys (git, web server)"
date: 2016-07-11
forum: Programming Talk
---

### Post by Drone4four on 2016-07-11
I’m learning how to use git and GitHub.  When I ‘git push origin master’, it prompts me to enter my GitHub user and pass combo.  So setting up an ssh key would make my life easier and more convenient.  The guide I’m using is actually a udemy course by a teacher named Jason Taylor.  The course is behind a pay wall so I can’t really share the specific video. The module I’m on recommends entering this command:

```
$ ssh-keygen -t rsa -C "user@gmail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/gnull/.ssh/id_rsa): 
/home/user/.ssh/id_rsa already exists.
Overwrite (y/n)? n
$
``` 
Most other students in Jason Taylor’s udemy course would press ‘y’.  It’s a no brainer. But for me, I’ve already have an id_rsa file with a key in it for my web server.  So If I enter, ‘y’, I’ll revoke rsa access to my web server.  Amiright?

How do I preserve ssh key access to my web server AND establish an ssh key connection to GitHub?

Here are the contents of my .ssh directory located in my home folder:

```
$ ls
id_rsa  id_rsa.pub  known_hosts 
$
```

---

### Post by spjackson on 2016-07-12
You don't need to generate a new key pair if you already have one. Just add your existing public key to your GitHub account. [https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

---

