---
title: "[SOLVED] Need Makefile help"
date: 2007-09-05
forum: Programming Talk
---

### Post by dwhitney67 on 2007-09-05
Hi,

I am having trouble running shell-script in a Makefile.  This is what I am trying to do:

```
entry:
        cat > config.cache << "EOF"
        ac_cv_func_mmap_fixed_mapped=yes
        ac_cv_func_strcoll_works=yes
        ac_cv_func_working_mktime=yes
        bash_cv_func_sigsetjmp=present
        bash_cv_getcwd_malloc=yes
        bash_cv_job_control_missing=present
        bash_cv_printf_a_format=yes
        bash_cv_sys_named_pipes=present
        bash_cv_ulimit_maxfds=yes
        bash_cv_under_sys_siglist=yes
        bash_cv_unusable_rtsigs=no
        gt_cv_int_divbyzero_sigfpe=yes
        EOF
```

Does anybody have any suggestions as to how a shell-script similar to the above should be formatted?

---

### Post by fct on 2007-09-05
What problem exactly? Are you getting an error message? If so, which one?

---

### Post by dwhitney67 on 2007-09-05
$ make -f foo
cat > config.cache << "EOF"
ac_cv_func_mmap_fixed_mapped=yes
ac_cv_func_strcoll_works=yes
ac_cv_func_working_mktime=yes
bash_cv_func_sigsetjmp=present
bash_cv_getcwd_malloc=yes
bash_cv_job_control_missing=present
bash_cv_printf_a_format=yes
bash_cv_sys_named_pipes=present
bash_cv_ulimit_maxfds=yes
bash_cv_under_sys_siglist=yes
bash_cv_unusable_rtsigs=no
gt_cv_int_divbyzero_sigfpe=yes
EOF
make: EOF: Command not found
make: *** [entry] Error 127

I've tried placing \ characters after each line... that did not work.
I've tried placing all lines following the 'cat' statement at column 0... that did not work.

Any suggestions on how I can format a lengthy 'cat' statement in a Makefile?

---

### Post by geraldm on 2007-09-05
shell scripts can have "here" documents, but makefiles do not.
create an executable shell script with the document.
from the Makefile, execute the script with one comand line.

Gerald

---

### Post by dwhitney67 on 2007-09-05
> **geraldm said:**
> shell scripts can have "here" documents, but makefiles do not.
create an executable shell script with the document.
from the Makefile, execute the script with one comand line.

Gerald

Yes I've done this already, and yes it works.  But I was looking to contain everything within the Makefile.  It seems that you are confident that it can't be done.

Alternatively, I was thinking of executing one statement at a time; in other words, adding each line to config.cache similar to the following:
```
entry:
        echo "ac_cv_func_mmap_fixed_mapped=yes" > config.cache
        echo "ac_cv_func_strcoll_works=yes" >> config.cache
        .
        .
        .
```

If I do not receive any other suggestions, I will debate (alone) whether to retain your suggestion or to use the rote method above.

---

### Post by dwhitney67 on 2007-09-05
I've decided to insert the individual echo statements in the Makefile.  This reduces the number (by only 1!) of file that I need to maintain.

---

