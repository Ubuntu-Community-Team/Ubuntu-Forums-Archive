---
title: "Help with Linux command... typo '-t' instead of '-i' switch with 'mv' command"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by kpm on 2008-09-15
the manual pages for 'mv' state that the '-t' switch is -t, "--target-directory=DIRECTORY  move all SOURCE arguments into DIRECTORY"
I wanted to move a directory from the current directory to another and made a typo: 
"mv -tnodewords ../../../../drupal-5-7/sites/all"

the '-tnodewords' should have been '-i nodewords'

so... just what did I do here?? I can't find that directory anywhere...

---

### Post by RealPSL on 2008-09-15
According to what I read and tried "../../../../drupal-5-7/sites/all" should be in the nodewords directory that was in your current directory when you executed the move. To test this I did:
```
mkdir dir1 dir2
mv -tdir1 dir2
```

At the end of that sequence dir2 was in dir1.

---

### Post by kpm on 2008-09-15
> **RealPSL said:**
> According to what I read and tried "../../../../drupal-5-7/sites/all" should be in the nodewords directory that was in your current directory when you executed the move. To test this I did:
```
mkdir dir1 dir2
mv -tdir1 dir2
```

At the end of that sequence dir2 was in dir1.

Thanks!  That makes sense... it was there. Sent myself into a bit of a panic with that switch typo...

---

