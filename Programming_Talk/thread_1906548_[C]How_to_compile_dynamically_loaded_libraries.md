---
title: "[C]How to compile dynamically loaded libraries"
date: 2012-01-09
forum: Programming Talk
---

### Post by Jordanwb on 2012-01-09
I'm writing a server which has plugin support which would discover and load plugins at runtime. I can't seem to find any tutorials on how to put the plugin API into /usr/include and how to compile plugins against the API (or my Google Fu is weak today).

Do you programmers have any good tutorials on how to do this? I know how to load the libraries using dlopen, dlsym and dlclose.

Thanks.

---

### Post by nvteighen on 2012-01-09
The best resource I know for this... [http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html](http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html)

(The GNU C Tutorial has also a good one, but it skips the soname thing... that might yield some trouble)

---

### Post by Jordanwb on 2012-01-09
> **nvteighen said:**
> The best resource I know for this... [http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html](http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html)

(The GNU C Tutorial has also a good one, but it skips the soname thing... that might yield some trouble)

Thanks I'll take a look at that.

---

