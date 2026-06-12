---
title: "printing list of files in cvs module"
date: 2010-01-06
forum: Programming Talk
---

### Post by badperson on 2010-01-06
Hi,
How do you get a list of all the files in a module with cvs using the command line? Is that possible? 

bp

---

### Post by dwhitney67 on 2010-01-06
The most common commands with cvs are:
[LIST]
[*]init
[*]checkout (co)
[*]add
[*]commit (ci)
[*]update
[*]diff
[/LIST]
Each of these can be used via the command line with the command 'cvs'; some require additional command line arguments.

It is helpful to define environment variables that define your CVS configuration (ie. location of CVS repo, editor to use, protocol).  On my system, I have something similar to the following established:
```

CVSROOT=myhostname:/some/path/cvs-repo
CVS_RSH=/usr/bin/ssh
CVSEDITOR=/usr/bin/vim

```
Once these are included in my shell's environment, the first thing to do is initialize the CVS repo:
```

cvs init

```
This will setup the CVSROOT directory as defined by the environment variable.  If you already have a CVS repo setup, then ignore this step.

Next is to create a folder (directory) to import the CVS file(s) from the repo into your work area.
```

mkdir ~/workspace
cd ~/workspace
cvs co .

```
This previous step, I believe, answers your question.

Use the add/commit for adding new files to the CVS repo, and only add for adding new directories to the repo.  For example
```

mkdir dir1
touch one dir1/two
cvs add one dir1 dir1/two
cvs commit one dir1/two

```
Note that when using CVS, you may be prompted to enter your password (because CVS is using SSH), and also be thrown into the editor of your choice (in my case, vim) to insert a comment related to why you are committing a file.

You can reference the [CVS manual]("http://ximbiot.com/cvs/manual/stable") for details on the other commands.

---

