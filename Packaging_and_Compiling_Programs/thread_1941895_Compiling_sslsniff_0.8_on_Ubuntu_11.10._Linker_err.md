---
title: "Compiling sslsniff 0.8 on Ubuntu 11.10. Linker error."
date: 2012-03-16
forum: Packaging and Compiling Programs
---

### Post by Imperton on 2012-03-16
Hello there!

I am trying to build sslsniff 0.8 on Ubuntu 11.10, but I get the error message undefined reference to boost::system::system_category(). I have added -lboost_system to sslsniff_LDFLAGSin Makefile.am, but it doesn't help. What should I do to fix this?

---

### Post by SevenMachines on 2012-03-16
sslsniff_LDFLAGS are for linker flags in automake. sslsniff_LDADD is what you want to add libraries. This is important as ldflags are added in a different place in the compile line to libs, and now ubuntu uses --as-needed by default for linking this can lead to undefined symbols

PS. You can add sslsniff_LDADD to Makefile.am, then you need to run automake to regenerate the Makefile or add it directly to the Makefile if you just want to test it out

---

### Post by Imperton on 2012-03-16
Thanks, that solved it! I added "sslsniff_LDADD = -lboost_system -lssl -lboost_filesystem -lpthread -lboost_thread -llog4cpp" the the Makefile.am and was able to compile.

---

