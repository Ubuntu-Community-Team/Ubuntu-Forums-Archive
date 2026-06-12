---
title: "HOWTO: recover a subversion repository"
date: 2006-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by patsissons on 2006-05-29
Apparently, in most cases, the recovery process is as simple as using the svnadmin recover <repo_path> command.  However, in the event of a catastrophic failure (such as a power surge, power loss, etc...) you will most likely find that the previous command results in an unrecoverable database error message.

When this happened to me, I was rather worried since I had not made a backup in quite some time. However, after a lot of trial and error and a little searching through the net, I was pleasantly supprised to find that recovery is possible, however, not very documented.  So in lieu of the lack of recovery documentation, I am going to solidify some recovery tacticts for subversion repositories.  skip to the end of this post for a quick and dirty, commands only view of this procedure.

First things first, you must go get the Berkley DB utils package, a simple apt-get install db4.2-util should suffice (that is if it is not already installed).

Secondly, although not completely necessary, copy your subversion repository to a new location (just a safeguard since your data is already been corrupted once).

From this new location we need to dump the database into a the Berkley DB dump file.  This will not work properly with svnadmin dump until we have recovered the database with the db_recover tool, which is actually db4.2_recover in ubuntu.  run the command db4.2_recover -c -h <repo_path>.  Remember that this can also be run using the original repo path (if you have a really large repo, or low disk space).  This will generally run very quickly and have no output.

Now that the repo has been recovered (sort of), we can dump its contents to a file.  now we can use the svnadmin dump <repo_path> > dump.bdb.  If you want to be extra safe, you can also include a revision span, such as from 0 to the end minus 1.  if you had 955 transactions, you could do the following, svnadmin dump -r 0:954 <repo_path> > dump.bdb.  This is just incase you suspect your last transaction to have been corrupted.

Now that we have our dump file, we can then load it back into a new repository.  So first create a new repository, svnadmin create svn.backup.  Then load the dump file into the new repo, cat dump.bdb | svnadmin load svn.backup.  This will take a little while, spewing out a lot of output (unless you pass the -q option), however, this is the restoration of your svn repository.

Last but not least, you should follow up by verifying the contents of the new repo, svnadmin verify svn.backup should do the trick.  If all is smooth, start the replacement of your corrupted repo.  I suggest renaming your original repo, then sym-linking the newly created repo.  Then finally, if all is well, remove the sym-link and perform the move then remove the old corrupted repo.

I hope this helps anyone who has run into this problem.  Now for a quick review of what was done (and for those who don't feel like reading the whole post), here is a quick run down of the commands.

```

apt-get install db4.2-util
db4.2_recover -c -h /srv/svnrepo
svnadmin dump /srv/svnrepo > dump.bdb
svnadmin create svnrepo.backup
cat dump.bdb | svnadmin load -q svnrepo.backup
svnadmin verify svnrepo.backup

```

---

### Post by jhelfman on 2010-08-05
> 
```

apt-get install db4.2-util
db4.2_recover -c -h /srv/svnrepo
svnadmin dump /srv/svnrepo > dump.bdb
svnadmin create svnrepo.backup
cat dump.bdb | svnadmin load -q svnrepo.backup
svnadmin verify svnrepo.backup

```

I initially found this helpful, however this seems incomplete to me. In order to find out if you have a corrupt database, a db_verify should be run. If there is a problem, you should then run a recovery. After the recover, another db_verify should be run.

Beyond this, doing a svnadmin verify only verifies the data in the repository, however this doesn't verify the database.

I tried to run db_verify on a repository I have and it simply would not work.

---

