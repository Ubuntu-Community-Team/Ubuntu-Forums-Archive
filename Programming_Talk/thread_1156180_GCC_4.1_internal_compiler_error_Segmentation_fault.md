---
title: "GCC 4.1 internal compiler error: Segmentation fault"
date: 2009-05-11
forum: Programming Talk
---

### Post by cnkbrown on 2009-05-11
First, not sure how/where to report this;

```
internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
Preprocessed source stored into /tmp/ccEvulXd.out file, please attach this to your bugreport.
Traceback (most recent call last):
  File "/usr/share/apport/gcc_ice_hook", line 34, in <module>
    pr.write(open(apport.fileutils.make_report_path(pr), 'w'))
IOError: [Errno 13] Permission denied: '/var/crash/_usr_lib_gcc_i486-linux-gnu_4.1.3_cc1plus.1000.crash'
```

I am using 4.1 to remain compatible with current project, upgrading compiler is not an option.

Preprocessed source attached.  There are several very similar files in my build, and they build on Fedora 7 using GCC Red Hat 4.1.2-27.

---

### Post by Zugzwang on 2009-05-12
> **cnkbrown said:**
> First, not sure how/where to report this;


As stated in the message, visit [http://gcc.gnu.org/bugs.html](http://gcc.gnu.org/bugs.html) for details.

Note that later versions of GCC are normally only getting stricter, so if you adapt your "current project" for GCC 4.3 or so, it should still be compilable using GCC 4.1.

---

### Post by Sockerdrickan on 2009-05-12
I get the internal seg fault too with 4.4 like this

[php]std::string foo {"bar"};[/php]

---

### Post by cnkbrown on 2009-05-12
> **Zugzwang said:**
> As stated in the message, visit [http://gcc.gnu.org/bugs.html](http://gcc.gnu.org/bugs.html) for details.



I would have thought so, too, but when I looked at gnu.org, it said to file the bug with the debian folks, and when I went to the debian page, it said something like, "Don't post bugs here, because no one watches this page."

---

### Post by samjh on 2009-05-12
Did you go to the right page?

Debian bug tracker: [http://www.debian.org/Bugs/](http://www.debian.org/Bugs/)

---

