---
title: "Compiling Firefox from source on 10.10"
date: 2010-10-30
forum: Packaging and Compiling Programs
---

### Post by Crayk on 2010-10-30
Hi guys,

I've been following the instructions on [https://developer.mozilla.org/En/Simple_Firefox_build](https://developer.mozilla.org/En/Simple_Firefox_build) to build Firefox from source, and when I run "make -f client.mk build" I get the following error:

```

~/firefox/192src/configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for gawk... gawk
checking for perl5... no
checking for perl... /usr/bin/perl
~/firefox/192src/configure: line 5080: syntax error near unexpected token `}'
~/firefox/192src/configure: line 5080: `$as_echo "yes" >&6; }'
*** Fix above errors and then restart with               "make -f client.mk build"
make[1]: *** [configure] Error 1
make[1]: Leaving directory ~/firefox/192src'
```Any ideas?

---

### Post by gmargo on 2010-10-31
I followed those instructions and it compiled without problem, on 64-bit 10.10 Maverick. Did you clone the repository or is your source from elsewhere?

---

### Post by Queue29 on 2010-10-31
> **Crayk said:**
> Any ideas?

It looks like you don't have perl installed. I would install perl and/or perl5.

---

### Post by Crayk on 2010-10-31
I do have perl installed, but the executable's called 'perl' rather than 'perl5' (hence the line in the output). I pulled the soruces for Firefox 3.6.12 from Mercurial, but it looks like they're broken, as I've now downloaded a tar and it compiles okay. Thanks.

---

