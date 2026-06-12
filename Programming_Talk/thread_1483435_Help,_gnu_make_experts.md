---
title: "Help, gnu make experts"
date: 2010-05-14
forum: Programming Talk
---

### Post by paxxus on 2010-05-14
This is rather basic, but I just can't get it right.

I have a list of files in SRC_FILES coming from all sorts of directories. I want to copy these files to the TGT_DIR directory, but only if a source file is newer than the one already in the target directory. Actually it's not just a copy, but some time consuming operation, but that doesn't matter for the problem at hand, what matters is that I only want the operation done on the files which need it (obviously).

Now, I can create a list of target files like:

TGT_FILES := $(foreach F,${SRC_FILES},${TGT_DIR}/$(notdir ${F}))

But now what. I can't use a pattern rule since I can't deduce the source file directory from the target file name.

It seems like a very common thing, yet I just can't figure out what to do (other than super ugly things like generating a makefile and calling it recursively).

What am I missing here?

Example:

```
SRC_FILES = /tmp/fido.dat /home/goofy/work/test/foo.c

TGT_DIR = /tmp/xxx

TGT_FILES = /tmp/xxx/fido.dat /tmp/xxx/foo.c
```/tmp/fido.dat changes, I then want to copy /tmp/fido.dat to /tmp/xxx/fido.dat, and *only* that.

---

### Post by paxxus on 2010-05-16
You guys aren't much help, are you :P j/k

I went ahead with the ugly approach. I let all targets depend on an auto-generated Makefile, and I let this Makefile depend on all source files. If the rule for the auto-generated Makefile triggers, I generate the Makefile with bash code written directly in the rule-code and I then call make recursively on that Makefile, which ensures that only the needed files are processed.

Still, I'd like to know if someone has a more elegant way of doing this. As I said, it seems unbelievable to me that you can't express this stuff directly in make syntax.

My solution so far:

```
${TGT_FILES}: ${TGT_DIR}/Makefile

${TGT_DIR}/Makefile: ${SRC_FILES}
        @( \
          for SRC in ${SRC_FILES}; do \
            TGT=${TGT_DIR}/`basename $${SRC}`; \
            echo ""; \
            echo "$${TGT}: $${SRC}"; \
            echo "        cp \$$? \$$@"; \
          done; \
        ) > $@
        @${MAKE} -C ${TGT_DIR} ${TGT_FILES}
```Not exactly elegant :(

---

### Post by dwhitney67 on 2010-05-16
Why must you copy the latest versions of a file to a target directory before it can be compiled?  Why not just compile it where it resides?

If you are trying to resolve how to build only the files that have changed or those that depend upon a file that has changed, then what you really need to do is maintain a dependency list for each source file.  'make' already knows how to determine which files have changed (since the last build), thus there is no need for you to do the same.  The only thing 'make' is unaware of is the dependencies; thus the reason you need to provide the instructions for this.

Let me know if you require additional help.

---

### Post by paxxus on 2010-05-16
Thank you for your reply dwhitney67 :)

I used "cp" just to make the fundamental problem simple, in reality it is not a "cp" but a time consuming operation whose result must be stored in ${TGT_DIR}. I do not want to pollute my source tree with result and intermediate files (in fact, my source tree could be read-only), which is why I want the TGT_DIR stuff.

My file lists can be hundreds of files and is not known up front, but are actually determined by a previous step, so I cannot just tell make the dependency directly.

Actually, after having read a little more in the GNU make manual ("Generating Prerequisites Automatically"), it seems that the recommended method for doing what I want is pretty close to what I have done. The manual suggests generating a makefile for each target rule instead of one big makefile with all target rules but the idea is essentially the same.

Guess make is just ugly :P

> **dwhitney67 said:**
> Why must you copy the latest versions of a file to a target directory before it can be compiled?  Why not just compile it where it resides?

If you are trying to resolve how to build only the files that have changed or those that depend upon a file that has changed, then what you really need to do is maintain a dependency list for each source file.  'make' already knows how to determine which files have changed (since the last build), thus there is no need for you to do the same.  The only thing 'make' is unaware of is the dependencies; thus the reason you need to provide the instructions for this.

Let me know if you require additional help.

---

