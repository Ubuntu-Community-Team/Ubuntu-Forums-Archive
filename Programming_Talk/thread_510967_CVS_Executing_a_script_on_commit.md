---
title: "CVS Executing a script on commit"
date: 2007-07-27
forum: Programming Talk
---

### Post by olliepetch on 2007-07-27
i have a perl script that I would like to execute everytime a some code is commited to a CVS repository. does anybody know how this can be done.

cheers

ollie

---

### Post by meatpan on 2007-07-27
I'm not sure how to do this using CVS alone.  One possible workaround is to make an alias for your commit:

If your script name was '/home/user/do_work.sh', you could chain together two commands in an alias:

alias comNrun="/home/user/do_work.sh && cvs commit"

You would then run the command:  'comNrun <cvs commit args>'  where <cvs commit args> are your usual commit flags and args, such as -m, and filenames, etc...  For example:  comNscript -m"adaptered support" readme.txt adaptered.c

A useful place for defining aliases is your ~/.bashrc file.

---

### Post by the_unforgiven on 2007-07-27
> **olliepetch said:**
> i have a perl script that I would like to execute everytime a some code is commited to a CVS repository. does anybody know how this can be done.

cheers

ollie
CVSROOT/commitinfo has the required hooks.
More info @:
[http://cvsbook.red-bean.com/cvsbook.html#commitinfo](http://cvsbook.red-bean.com/cvsbook.html#commitinfo)

---

### Post by olliepetch on 2007-07-30
cheers thats exactly what i'm looking for

---

