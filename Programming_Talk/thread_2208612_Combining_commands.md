---
title: "Combining commands"
date: 2014-03-01
forum: Programming Talk
---

### Post by ibjsb4 on 2014-03-01
I think first time ever I posted in programming;  I be running with the big dogs :D

Other than "&&" or ";;" is there a way to combine two move commands?  Example:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broke
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

You can cat two files by:

```
cat filename1 filename2
```

---

### Post by trent.josephsen on 2014-03-01
cat is a little different, since its actual job is to print as many files as you give it -- the name comes from "(con)catenate". mv's job is to move/rename one file, or to move a bunch of files into one directory.

However, for the given application, you may be in luck. (Not sure how portable the -b option is, it might only work with GNU mv.)

```
$ mv --backup --suffix=.broke /var/lib/dpkg/status-old /var/lib/dpkg/status
or to make that shorter
$ mv -bS.broke /var/lib/dpkg/status{-old,}
```

---

### Post by ibjsb4 on 2014-03-01
Thank you Trent, that&#8217;s what I was looking for.

---

