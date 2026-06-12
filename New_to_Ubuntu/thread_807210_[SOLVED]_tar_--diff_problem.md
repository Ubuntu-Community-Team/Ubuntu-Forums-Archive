---
title: "[SOLVED] tar --diff problem?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by bluefrog on 2008-05-25
trying to compare/diff a tar file and the original folder

mkdir .test 
touch .test/{1,2}
tar cf test.tar .test/
touch .test/new

tar --diff -vf test.tar .test/ 
gives me the same result as 
tar -tf test.tar

I was expecting it to pinpoint the new file that is in .test/ and not in test.tar

An idea?

found it while reading the gnu tar manual
in fact the --diff option will check differences for the files which were put in the tar file.
to do what I wanted to do, it is more the --incremental option which will be useful

---

