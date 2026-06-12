---
title: "Patch-based backup for free"
date: 2009-11-14
forum: Programming Talk
---

### Post by Ulysses_ on 2009-11-14
I have just discovered this software that makes extremely compact backups based on byte-by-byte comparisons, rather than directory comparisons.

[http://www.sharewareconnection.com/patchbreeze.htm](http://www.sharewareconnection.com/patchbreeze.htm)

"Data backup, in the form of cumulative updates, making the backup copies tens or even hundreds times smaller size than before!"

Unfortunately it is not free.  What's the linux package that does the same job for free?

---

### Post by diesch on 2009-11-14
To created patches there's *diff*. For backups have  a look at *rdiff-backup*.

---

### Post by Ulysses_ on 2009-11-19
I have many backups made by simply copying the folders to an external drive, and would like to join them.   As it is, I can search for text within all folders in the external drive and find a backup that contains the text.    Can I do the same with rdiff-backup, or even with version control systems?    Or rdiff-backup would force me to fully restore one backup at a time, and keep repeating until a search in the restored backup finds the text?

---

### Post by wmcbrine on 2009-11-19
rsync

---

