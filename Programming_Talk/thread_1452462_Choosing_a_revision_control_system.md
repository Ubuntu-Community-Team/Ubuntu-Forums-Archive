---
title: "Choosing a revision control system"
date: 2010-04-12
forum: Programming Talk
---

### Post by carandraug on 2010-04-12
Hi

I started this post asking for advise on the best revision system if my only requirement was to change a line of the code every time I commit the changes. However, I realized that maybe it was a good idea to ask for a advise on the best approach to control it.

I have no serious education in programming whatsoever. I'm just a biologist who finds much more amusing to spend a few hours cooking a "program" to do the maths and plots than spend the said hours pasting and copying rows of numbers in a spreadsheet.

The workflow is: I have a program that processes every file of raw data, and saves each in a text file. Then I get another one that goes through all the processed data and shows it to me.

```
raw data (image) --> extracted data (1 text file per image) --> nice plots

```

My problem is that I keep increasing the number of options and complexity of my programs, and I have a big fear of inserting a bug by accident and not knowing when that happened. That would mean have to analyze everything again which at the moment would take a few days (and I'm just starting with my project). What I've been doing is keeping a copy of the old code and every time I make a change, I also change a variable which corresponds to the version of my program. This variable is then stored in the text file, together with all processed data. But doing this manually is boring, not to mention error prone.

All that said, I would like a revision system that would do that for me. I've read about [this in mercurial]("http://mercurial.selenic.com/wiki/VersioningWithMake") but I don't think it will work for me, because I'm not compiling anything (compiles in run time I think). I also thought about having a script so that every time I make a commit, it would change the line with the version before actually making the commit but I can see how that could fail.

Or maybe I'm trying to solve this problem in the wrong way and there's a much better way to do it, obvious for real programmers, and that I am just not aware of.

Any advise will be most welcome. Thanks in advance.

---

### Post by Simon17 on 2010-04-12
I would recommend having a file (say version.txt) under source control and use subversion keyword substitution on it. Read about it here:
[http://svnbook.red-bean.com/en/1.4/svn.advanced.props.special.keywords.html](http://svnbook.red-bean.com/en/1.4/svn.advanced.props.special.keywords.html)
What you'll be able to do is have svn automatically write the revision number to the file each time you update or commit a new version.

---

### Post by saulgoode on 2010-04-12
I've found [Fossil]("http://www.fossil-scm.org/") to be very easy to use.

---

### Post by carandraug on 2010-04-12
> **Simon17 said:**
> I would recommend having a file (say version.txt) under source control and use subversion keyword substitution on it. Read about it here:
[http://svnbook.red-bean.com/en/1.4/svn.advanced.props.special.keywords.html](http://svnbook.red-bean.com/en/1.4/svn.advanced.props.special.keywords.html)
What you'll be able to do is have svn automatically write the revision number to the file each time you update or commit a new version.

If I got it right, I could set this keyword substitution on, and if I had $Rev$, it would be substituted by the revision number. But that would be the revision number of that file, not the global revision number. The link points to a page of the manual about svnversion but seems it's not written yet. I googled and couldn't found anyone using it for this.

---

### Post by dgandhi on 2010-04-13
If you have only one program file, use RCS with variable substitution, it can accomplish this easily.

If on the other hand you have a multi-file program (which you should if you keep adding features) I would recommend mercurial, as it seems to meet your revision needs very well.

The issue of the version number is probably best dealt with as a script.

example:

commitit.sh
```
#!/bin/bash

root = /home/mine/code

cd $root
hg addremove
hg commit
hg ident | awk '{ print "version=" $1 ";" }' > header.h
```


Just use the commitit script for commits, and load the header.h file, and use the variable as part of your output file data. This way you can track your data based on the version of the entire system when it was created, and have the whole version control and numbering system managed automatically.

---

### Post by carandraug on 2010-04-13
> **dgandhi said:**
> 

If on the other hand you have a multi-file program (which you should if you keep adding features) I would recommend mercurial, as it seems to meet your revision needs very well.

The issue of the version number is probably best dealt with as a script. 

I thought about using a script like that before but I feel it's a bit of a dirty solution (I'll probably be using it tough). It's always change two files (the one with the change and the one with the version number). It also means that if I get someone to give me a hand on it I'll have to make them doing commits like that. It's not a solution I'd be proud to use but it's definitely much better than doing the whole revision control by hand.

Anyway, since I'm going to use a script, I can use any revision control. I also decided today to set it on an online repository and I picked launchpad (I didn't like the terms of agreement of sourceforge, specially the part about limiting access to people from some countries. Where's the freedom on that?), so I think I'll be using bazaar.

I'll have to figure out how to work with it yet. Already filled blueprints and bug reports (it's like If I was buying presents for me on my anniversary).

[frapinator]("https://code.launchpad.net/frapinator")

---

### Post by dgandhi on 2010-04-13
> **carandraug said:**
> I thought about using a script like that before but I feel it's a bit of a dirty solution 

A non-dirty solution is to use revision control, and then simply time-stamp your data files. You can then cross reference time stamps to see what is effected by a particular bug. That of course only works if you have one copy/version at any given time.

---

### Post by carandraug on 2010-04-13
> **dgandhi said:**
> A non-dirty solution is to use revision control, and then simply time-stamp your data files. You can then cross reference time stamps to see what is effected by a particular bug. That of course only works if you have one copy/version at any given time.

That would work for me only. But once someone from my lab starts using it it wouldn't help them specially because they won't upgrade every time I add a new feature.

I was going to say that I'd use the script when I thought of a solution that is even better than getting the global revision number. I do use keyword substitution (bazaar also has it) but I use the revision if of each file. Then I do it in all files, and at the start of my program, instead of storing a variable with the revision number, I store a hash with the revision number of all functions. This would be better because they are all octave functions which still make sense outside the context of the main program and someone could use them alone.

---

### Post by pbrane on 2010-04-13
Sounds to me like you could use svn. Just make your changes and commit. svn only stores the differences anyway. you can always back up a revision if you make a mistake. svn is not only for source code, you can use it for anything, documents, scripts, etc. write your script, code, etc. let svn do the version control for you.

---

### Post by carandraug on 2010-04-13
> **pbrane said:**
> Sounds to me like you could use svn. Just make your changes and commit. svn only stores the differences anyway. you can always back up a revision if you make a mistake. svn is not only for source code, you can use it for anything, documents, scripts, etc. write your script, code, etc. let svn do the version control for you.

I never thought about it. This can indeed be very useful, specially since I write all my documents in latex, it won't be that much of a burden on the disk. I may actually convince my advisor to set a svn server in the lab. Nice! Thanks a lot.

---

### Post by dgandhi on 2010-04-13
> **carandraug said:**
>  instead of storing a variable with the revision number, I store a hash with the revision number of all functions.

That's actually what the script I posted does, it pulls the commit hash out of mercurial, and uses that as a version descriptor... but you don't have to do it by hand.

Since somebody already mentioned SVN I'm going to say that the distributed version systems (mercurial and git) both do all that and more, as well as being easier to use and setup. I don't want to get into a holy war about it, but I think it needed to be said.

PS on third thought, you could actually have your code pull the version number out of your revision system when it was run. That way you don't need a script cludge, just have it run a shell command to get the current version hash, and use that in your data file.

---

