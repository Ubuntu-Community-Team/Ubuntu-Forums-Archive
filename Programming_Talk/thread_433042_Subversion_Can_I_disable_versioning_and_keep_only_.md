---
title: "Subversion: Can I disable versioning and keep only HEAD?"
date: 2007-05-04
forum: Programming Talk
---

### Post by Brazen on 2007-05-04
I can't find any way to do this.  For what I want to use it for, Subversion works great, but versioning takes up way to much space and is completely unnecessary for our situation.  Is there anyway I can have Subversion only keep the latest version (HEAD).  Or it may even be useful to keep the last 1 or 2 versions, but no more.

---

### Post by KaeseEs on 2007-05-04
The closest thing to this you'll likely find is at [http://svnbook.red-bean.com/nightly/en/svn-book.html#svn.reposadmin.maint.diskspace](http://svnbook.red-bean.com/nightly/en/svn-book.html#svn.reposadmin.maint.diskspace) .  Though I might ask, if you don't want versioning, why exactly are you using a version control system?

---

### Post by deuce868 on 2007-05-05
You can export a repository, but that removes all version control. Are you just looking for a way to share files or what?

---

### Post by Brazen on 2007-05-05
> **deuce868 said:**
> You can export a repository, but that removes all version control. Are you just looking for a way to share files or what?

How would I export a repository to get rid of version control?  I read that link KaeseES gave, but all I can see is how to filter our branches or folders, but it sounds like it still keeps all versions of what is not filtered out.

> **KaeseEs said:**
> The closest thing to this you'll likely find is at [http://svnbook.red-bean.com/nightly/en/svn-book.html#svn.reposadmin.maint.diskspace](http://svnbook.red-bean.com/nightly/en/svn-book.html#svn.reposadmin.maint.diskspace) .  Though I might ask, if you don't want versioning, why exactly are you using a version control system?

Yeah, I know it's called a version control system, but it also has other abilities not available on a standard file server.  Namely, we need to keep files in a central place (the server), but due to the size of the files and the way the software works, the files must be opened from local storage.  So everyone needs to have a local copy of this data, but only one person can work on it at a time (this is where Subversions "locking" would be useful).  So basically, the ability to Update local storage from a central repository, lock those files, and then commit local changes back to the central repository are the features I need.  I just don't need, or want, versioning.

---

### Post by yaaarrrgg on 2007-05-05
> **Brazen said:**
> Yeah, I know it's called a version control system, but it also has other abilities not available on a standard file server.  Namely, we need to keep files in a central place (the server), but due to the size of the files and the way the software works, the files must be opened from local storage.  So everyone needs to have a local copy of this data, but only one person can work on it at a time (this is where Subversions "locking" would be useful).  So basically, the ability to Update local storage from a central repository, lock those files, and then commit local changes back to the central repository are the features I need.  I just don't need, or want, versioning.

But subversion isn't a locking system like cvs.  

svn applies patches to the main copy, and multiple people can edit the same file at the same time.  As long as they are editing different portions of the file, there's no conflict usually.  Otherwise changes have to be resolved by hand.

However, what do you do when people make mistakes?  The versioning is the best aspect of subversion... otherwise things inevitably get screwed up and there's no way to see what the last changes were, who made them, and there's no way to undo.

---

