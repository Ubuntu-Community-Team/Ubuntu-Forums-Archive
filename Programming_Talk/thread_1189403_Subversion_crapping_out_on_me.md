---
title: "Subversion crapping out on me"
date: 2009-06-16
forum: Programming Talk
---

### Post by chris4amd on 2009-06-16
Call me mystified.  Google hasn't helped much here.  After using SVN on a project for a few months I go to check in my latest changes and this is my result:

```

svn: Error at entry 36 in entries file for '.':
svn: Bogus date

```

On attempting to track down this date in the entries file, I don't see anything amiss.  The dates for the project's "." entry in the filesystem are standard.

Any ideas?

---

### Post by johnl on 2009-06-16
The following might help:

svnadmin verify <repo> 
svnadmin recover <repo>

(back up your repository before doing anything to it so you can restore it if svnadmin borks it up)

Other than that, no clue -- never seen that specific error before :)

---

### Post by chris4amd on 2009-06-17
> **johnl said:**
> 
svnadmin verify <repo> 
svnadmin recover <repo>

Tried it without any luck.  This is what I get:

```
XXXX@flip:~/Projects$ svnadmin verify SvnRepos
* Verified revision 0.
* Verified revision 1.
* Verified revision 2.
* Verified revision 3.
* Verified revision 4.
* Verified revision 5.
* Verified revision 6.
* Verified revision 7.
* Verified revision 8.
* Verified revision 9.
* Verified revision 10.
* Verified revision 11.
* Verified revision 12.
XXXX@flip:~/Projects$ svnadmin recover SvnRepos
Repository lock acquired.
Please wait; recovering the repository may take some time...

Recovery completed.
The latest repos revision is 12.

```

No errors, but no fixes either.  Any other thoughts?

---

### Post by chris4amd on 2009-06-17
Bump.

---

### Post by geirha on 2009-06-17
Sounds like .svn/entries has been corrupted somehow, either by the subversion client itself, or some other program. Easiest fix is to rename/remove the currently checked out tree, and do an "svn checkout" again. That should get things back to normal.

---

### Post by chris4amd on 2009-06-17
> **geirha said:**
> Sounds like .svn/entries has been corrupted somehow, either by the subversion client itself, or some other program. Easiest fix is to rename/remove the currently checked out tree, and do an "svn checkout" again. That should get things back to normal.

Back in business.  Thank you.

---

