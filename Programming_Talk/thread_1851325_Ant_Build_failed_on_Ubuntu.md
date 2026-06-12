---
title: "Ant Build failed on Ubuntu"
date: 2011-09-28
forum: Programming Talk
---

### Post by itcodex on 2011-09-28
Hello,

We have a problem with Apache Ant.
We have 5 git repositories, every repository has the own build file and these build files are called from a central build.xml.
Now, when I try to execute "ant" command from the terminal or Eclipse J2EE IDE (Run as Ant Build) both of procedures fail with this error message:

```

BUILD FAILED
/home/superadmin/git-repos/...<path>.../Build/build.xml:13: The following error occurred while executing this line:
/home/superadmin/git-repos/...<path>.../DomainTier/Build/build.xml:13: The following error occurred while executing this line:
java.io.FileNotFoundException: /home/superadmin/git-repos/...<path>.../domain.tier.build.xml  (No such file or directory)

```
The file is EXIST on the location! 
Originally, these repos were in /usr/devenv folder, but I copied them to the user's home directory but it didn't solve the problem.

What can cause this problem? Access rights?
I chmod-ded all folders and files with 775!

Does anybody have an idea? :???:
Thanks in advance!

---

