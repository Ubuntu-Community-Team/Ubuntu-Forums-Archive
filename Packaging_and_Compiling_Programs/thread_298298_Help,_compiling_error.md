---
title: "Help, compiling error"
date: 2006-11-12
forum: Packaging and Compiling Programs
---

### Post by Peter76 on 2006-11-12
Hello, I'm trying to compile brasero in a chrooted environment. I've tried compiling different versions, and every time I get this error:

make[2]: Entering directory `/var/build/brasero-0.4.91/po'
file=`echo ca | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ca.po
/bin/sh: -o: not found
make[2]: *** [ca.gmo] Error 127

I have this feeling I might be missing something in my chroot environment.... Can somebody help me out.

Thanks, Peter

---

