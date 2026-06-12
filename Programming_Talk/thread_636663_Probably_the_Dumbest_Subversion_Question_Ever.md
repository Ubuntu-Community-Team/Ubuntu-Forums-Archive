---
title: "Probably the Dumbest Subversion Question Ever"
date: 2007-12-10
forum: Programming Talk
---

### Post by TylerMcManus on 2007-12-10
Hello all.

I'm running a LAMP server on Ubuntu, and I've heard great things about Subversion so I would like to set it up for managing my web-based application source code (I've never used source control prior to now). I've read a lot of documentation on various sites, but can't find the answer I'm looking for. It must just be too obvious to put in an FAQ, but: How does Subversion post the "live" code to the web root? I understand how the working copies go, and the commits, and the merges, but how does Subversion handle the live code? Or does it? Does a user just commit all their changes into the repository, then go do something else that posts the most updated version of your source code to the web server, or does Subversion somehow manage that for you? Are you supposed to use Subversion as a second server and then somehow get the code from Subversion to the web server?

If anyone can help me connects the dots, I would greatly appreciate it. I'm totally lost here.

Thanks,
Tyler

---

### Post by acl123 on 2007-12-10
You don't usually deploy your code using Subversion. Something else does the deployment, for example your IDE or you may just manually FTP your files to the live server.

---

### Post by aquavitae on 2007-12-10
Not sure if I entirelyunderstand the question, but it seems you're trying to find out how to get the code from subversion to the server?  The answer is, you don't.  You place the repository on the server, then download working copies, etc. The entire repository is kept on the server and the 'live' code (not sure what exactly you mean by that) is all stored internally in the repository. For example, I have a project on google code. Google handes the repository so all I need to do is downloack a working copy from it.  I also have another private project on my pc.  I've set up a local repository on a flash drive that I can carry between work and home (a bit excessive maybe, but it makes sure I have a couple of backups the whole time) so all I do is download from it (just using a local address instead of an internet address)

Does this help?

---

### Post by geirha on 2007-12-10
You basically check out the repository in the web root as you would for the one you use to do your changes. You can do this automatically by creating a post-commit script in the hooks/ folder of your repository. The post-commit script will be run whenever a successful commit has happened. Make the post-commit script run svn update on the subversion tree in your web root. Read chapter five of the redbook for more information [http://svnbook.red-bean.com/nightly/en/svn.reposadmin.create.html#svn.reposadmin.create.hooks](http://svnbook.red-bean.com/nightly/en/svn.reposadmin.create.html#svn.reposadmin.create.hooks)

And no, it's not a dumb question.

---

### Post by daou on 2007-12-10
> **geirha said:**
> You basically check out the repository in the web root as you would for the one you use to do your changes. You can do this automatically by creating a post-commit script in the hooks/ folder of your repository. The post-commit script will be run whenever a successful commit has happened. Make the post-commit script run svn update on the subversion tree in your web root. Read chapter five of the redbook for more information [http://svnbook.red-bean.com/nightly/en/svn.reposadmin.create.html#svn.reposadmin.create.hooks](http://svnbook.red-bean.com/nightly/en/svn.reposadmin.create.html#svn.reposadmin.create.hooks)

And no, it's not a dumb question.

A little follow-up question to your answer: is it possible to make a post-commit type script that runs when a trunk is tagged? I usually make a tag when I release a new version of software and need to run some scripts (checkout tag, tar, copy tar to server, update version rss feed via python script).

---

### Post by Loevborg on 2007-12-10
> **daou said:**
> A little follow-up question to your answer: is it possible to make a post-commit type script that runs when a trunk is tagged? I usually make a tag when I release a new version of software and need to run some scripts (checkout tag, tar, copy tar to server, update version rss feed via python script).

This is what I do. When I tag trunk as "live", the current trunk "goes live" so to speak. I don't update, but rather do a clean export every time and change symlink so everything is changed in one fell swoop. I assume that the svn repo is on the same box as your apache. Works great AFAICT. Here's my post-commit script, HTH. Let us know if it works for you!

```

if [ "$#" != "2" ]; then
        echo Invalid number of arguments. >&2
        exit 1
fi

REPOS="$1"
REV="$2"

BASE="$HOME"
PATH="$PATH:$BASE/opt/bin"
cd "$BASE"

if [ \! -d "$BASE/revisions" ]; then
        echo Revision directory not found: "$BASE/revisions". >&2
        exit 1
fi

TARGET="revisions/r$REV"
SYMLINK="my"

# check if tagged live

if svnlook changed "-r$REV" "$REPOS" | grep -qE '^A[ \t]*live/$'; then
        # dont export twice
        if [ \! -e "$TARGET" ]; then
                svn export "-r$REV" "file://$REPOS/live" "$TARGET"
        fi

        # switch to checkout
        rm -f "$SYMLINK"
        ln -s "$TARGET" "$SYMLINK"
fi

```

---

### Post by geirha on 2007-12-10
Yes. I should have also mentioned that you should check out chapter 9 concerning hooks. The post-commit script gets two arguments when it is run. The path to the repository and the revision of the commit that just took place. With that info, you could run svnlook and check if a tag was created. I.e.
```

#!/bin/bash
REPOS="$1"
REV="$2"
CHANGES=`svnlook changed -r$REV $REPOS`  # For a tag creation, the output of svnlook should be something like "A    /tags/release-1.0/"
#if $CHANGES has tags in it or something; then
#  svn up -r$REV /webroot/site/
#fi

```

EDIT: But, Loevborg beat me to it, and with a better answer :)

---

### Post by daou on 2007-12-10
Ok thanks for the replies. I just released the latest version 5 minutes ago, so I'll have to test it with the next one. I'll let you know how it goes.

---

### Post by TylerMcManus on 2007-12-10
> **geirha said:**
> You basically check out the repository in the web root as you would for the one you use to do your changes.

ohhh ok. well that makes sense. so after i commit my working copy to the repos, then i just do another check out but this time check it out directly into the web root? is that right? and thats also where that hook comes in? i followed your link and saved it for when i get to that point. the whole version control thing is new to me and i don't know anyone who already does it, so i'll have to do some more research in this area when i get to that point.

regarding ide: i'm open if anyone has any tips on using eclipse with the subeclipse plug-in? thats what i'm leaning toward as eclipse is my normal ide.

thanks to everyone for helping me connect the dots.

---

### Post by daou on 2007-12-11
Ok I just tested the post-commit.

Looks like it worked (with a few bumps along the way at first). Now an export triggers a version release: new source code archive, places it on the server, updates the html pages (few well placed sed commands) to show the new version and a link to it, plus an update of the version RSS feed.

Loevborg: I used a grep command similar to yours to check if a version was tagged, then extracted the version number. This then calls a python script that does everything else.

Thanks for the tips everyone.

---

### Post by daou on 2007-12-12
> **TylerMcManus said:**
> 
regarding ide: i'm open if anyone has any tips on using eclipse with the subeclipse plug-in? thats what i'm leaning toward as eclipse is my normal ide.

thanks to everyone for helping me connect the dots.

Eclipse Europa+subclipse is my developing combo of choice. If you are familiar with SVN commands and concepts, using subclipse is quite straightforward. 
First set up a repository with svnadmin and svn commands. Then make a new project in Eclipse. There should be an option which allows you to create the project by checking out an SVN repo.

As you work, right click the project in the project window and choose the "Team" menu item. There you can execute SVN commands: commit, add files to revision control, update, tag/branch, export, compare revisions, etc. The "SVN repo exploring" window is useful if you need to modify parts of the repo other than trunk.

---

