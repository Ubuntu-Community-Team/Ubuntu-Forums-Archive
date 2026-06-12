---
title: "Migrating from Windows To Linux - Git Repo Update Problem"
date: 2016-08-27
forum: Programming Talk
---

### Post by calimer on 2016-08-27
I'm migrating from windows to linux and I have a ton of gits (over 100) that I have to check for updates frequently so I use the script below.  My problem is that often times on Linux I get this error message:
> " * branch            master     -> FETCH_HEAD
   959353c..7a63e51  master     -> origin/master
error: Your local changes to the following files would be overwritten by merge:"
List of files
Then > Please, commit your changes or stash them before you can merge.
Aborting

I never get that message on Windows using the same script.  Also I'm never personally making local changes so I'm not sure why it even says that.

When I do get that message I have tried "git reset --hard origin/master" on the specific repo but I've had that error on repos that I've already done the Git Reset on, and also doing it on every one is incredibly tedious.  Is there a way I can force it to do the pull?  If it overwrites stuff that's fine, I never have local commits in there.  As a note they are almost all github repos.

```
#!/bin/bash

# store the current dir
CUR_DIR=$(pwd)

# Let the person running the script know what's going on.
echo "\n\033[1mPulling in latest changes for all repositories...\033[0m\n"

# Find all git repositories and update it to the master latest revision
for i in $(find . -name ".git" | cut -c 3-); do
    echo "";
    echo "\033[33m"+$i+"\033[0m";

    # We have to go to the .git parent directory to call the pull command
    cd "$i";
    cd ..;

    # finally pull
    git pull origin master;

    # lets get back to the CUR_DIR
    cd $CUR_DIR
done

echo "\n\033[32mComplete!\033[0m\n"
read
```

Any help would be greatly appreciated, thank you for your time!
-Mike

---

### Post by &amp;KyT$0P# on 2016-08-27
Try this -
```
git checkout --force
```

The problem is likely that the permissions got muddled when moving the repository from NTFS to a Linux filesystem.  This should straighten that out provided you're not continuing to keep the repos on a NTFS filesystem while using with Linux.

---

### Post by calimer on 2016-08-27
I was hoping to sync between the two using megasync, at least until all the info is migrated over, but if that can't happen then it isn't a big deal.  I'll give that command a shot, thank you!

---

