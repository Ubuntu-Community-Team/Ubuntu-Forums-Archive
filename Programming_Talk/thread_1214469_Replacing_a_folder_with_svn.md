---
title: "Replacing a folder with svn"
date: 2009-07-15
forum: Programming Talk
---

### Post by orlox on 2009-07-15
Hi. Im mantaining a website using SVN, and many times I have to update the version of some components. Without version control, the simplest way to do this, is to delete a folder completely and to replace it with the one that has the new version.

The way ive been doing this, is by running an svn delete on the folder, doing a commit, then copying the folder and running svn add.
The problem with this, is that I leave a non-working version of the site in the repository...

What is the reasonable way of doing this, without leaving a non working version in the repo??

---

