---
title: "svn commit failed / database locked"
date: 2011-12-19
forum: Programming Talk
---

### Post by ufuser01 on 2011-12-19
Hi,

I am using a network drive for my subversion repository (between multiple machines). I am the only one who uses this repository and I recently started using a different machines (accounts being the same, only machines changed)

Of late, I am seeing this error

[B]Transmitting file data ..... svn: Commit failed (details follow):
svn: database is locked
|
|[/B]

To over come this, I do a **"svn update"** and select (mf) and then I see that there is a "Conflict discovered" showing a compiled .o file, and the update is successful.

Why is this happening? I don't see this conflict for any of the source files. Only the compiled file has this issue.

Any thoughts?

Thanks.

---

### Post by Arndt on 2011-12-20
> **ufuser01 said:**
> Hi,

I am using a network drive for my subversion repository (between multiple machines). I am the only one who uses this repository and I recently started using a different machines (accounts being the same, only machines changed)

Of late, I am seeing this error

[B]Transmitting file data ..... svn: Commit failed (details follow):
svn: database is locked
|
|[/B]

To over come this, I do a **"svn update"** and select (mf) and then I see that there is a "Conflict discovered" showing a compiled .o file, and the update is successful.

Why is this happening? I don't see this conflict for any of the source files. Only the compiled file has this issue.

Any thoughts?

Thanks.

Is there a particular reason for checking in the compiled file?

---

### Post by mukteshpatel on 2013-03-05
> **ufuser01 said:**
> Hi,

I am using a network drive for my subversion repository (between multiple machines). I am the only one who uses this repository and I recently started using a different machines (accounts being the same, only machines changed)

Of late, I am seeing this error

[B]Transmitting file data ..... svn: Commit failed (details follow):
svn: database is locked
|
|[/B]

To over come this, I do a **"svn update"** and select (mf) and then I see that there is a "Conflict discovered" showing a compiled .o file, and the update is successful.

Why is this happening? I don't see this conflict for any of the source files. Only the compiled file has this issue.

Any thoughts?

Thanks.

This problem is because cifs mounting. 

See here detail solution : [http://techathon.mytechlabs.com/qa_forum/discussion/3/svn-commit-failed-database-is-locked](http://techathon.mytechlabs.com/qa_forum/discussion/3/svn-commit-failed-database-is-locked)

---

