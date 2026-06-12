---
title: "Generating intermediate files with kbuild"
date: 2010-08-30
forum: Programming Talk
---

### Post by sara88 on 2010-08-30
I'm doing some development and require the intermediate .i files. They are the files that used to be generated after the preprocessor ran, but now gcc typically uses an internal preprocessor so I'm having issues generating them.

I'm working with gcc 3.4 and the Ubuntu 8.04 makefile.

I tried added the --save-temps flag to MAKEFLAGS, and I also just added -save-temps to HOSTCC, so gcc --save-temps would run on every invocation. This actually worked (.i and .s files were generated) but only for files in the first level of the directory hierarchy. So for example none were generated for the c files in net/core.

Any ideas are appreciated. Thanks.

---

### Post by Bachstelze on 2010-08-30
The -E flag of gcc will generate .i files. You can add that to your CFLAGS.

---

### Post by sara88 on 2010-08-31
Thanks for the reply. The -E flag did not generate the i files for inner directories (like net/core/). I added it to MAKEFLAGS and HOSTCFLAGS variables.

Any other ideas?

---

