---
title: "g++ #pragma warning equivalent?"
date: 2007-10-04
forum: Programming Talk
---

### Post by aks44 on 2007-10-04
I've been looking for a g++ way to temporarily disable a warning, something like VC++ #pragma warning(...) and BCC #pragma warn. My warning options are too high for boost (thus many garbage is output by g++), and I don't want to lower them for my own code...

Any ideas? (ST*W didn't yield any relevant result :()

---

### Post by hod139 on 2007-10-04
There is [#pragma GCC diagnostic]("http://gcc.gnu.org/onlinedocs/gcc/Diagnostic-Pragmas.html")

But I've never used them, and I don't know if they have the same push/pop stack syntax as the windows pragma

---

### Post by aks44 on 2007-10-04
Thanks for the tip, but unfortunately it doesn't seem to work. **#pragma GCC diagnostic ignored "-Wwhatever-option"** just adds one more warning: "*ignoring #pragma GCC diagnostic*". Those GNU people have a strange sense of humour... :-|


Oh well, I guess it's a bit too late right now for me to sort it out tonight, I'll check that again tomorrow...

---

### Post by hod139 on 2007-10-04
That's kinda funny.  Seriously though, it looks like the diagnostic pragmas were just introduced, and are only availing in gcc 4.2.1.  Sorry.

---

### Post by aks44 on 2007-10-05
> **hod139 said:**
> the diagnostic pragmas were just introduced, and are only availing in gcc 4.2.1.

Indeed. I guess I'll have to live with it then, whether I like it or not.
I just hope that Gutsy will ship 4.2.1. :p

---

