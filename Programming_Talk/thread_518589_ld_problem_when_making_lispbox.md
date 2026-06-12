---
title: "ld problem when making lispbox"
date: 2007-08-06
forum: Programming Talk
---

### Post by austinp on 2007-08-06
I´m trying to compile lispbox, but get an error when I invoke ´make´:
 ```

/usr/bin/ld: cannot find -lXaw
collect2: ld returned 1 exit status
make[2]: *** [temacs] Error 1
make[2]: Leaving directory `/home/ajp/lispbox/emacs-21.3/src'
make[1]: *** [src] Error 2
make[1]: Leaving directory `/home/ajp/lispbox/emacs-21.3'
make: *** [all] Error 2

```

Lispbox is looking for the Xaw library. The problem is that Xaw is called Xaw3d throughout my system, as that´s what the Ubuntu package is listed as. I bypassed this in the include directory by creating a symlink to the Xaw3d directory, but I´m not sure how to do this with a lib. 

Is there a way to create such a link to the lib so it appears as Xaw, or is there a more permanent solution that I´m missing? I´m running Xubuntu 7.04, i386 Desktop. Thanks in advance!

---

