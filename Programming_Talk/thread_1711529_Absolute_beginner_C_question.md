---
title: "Absolute beginner C question"
date: 2011-03-21
forum: Programming Talk
---

### Post by retrodans on 2011-03-21
We are trying to improve our varnish reverse-proxy with some inline C.  And as such, I have been starting to dabble.  I have put in what I think to be some rather simple code, but get an error which I believe is due to my ubuntu setup.

The below code works fine:

```
C{
  #include <syslog.h>
  #include <string.h>
}C
```

But this returns an error:
```
C{
  #include <syslog.h>
  #include <string.h>
  #include <libxml2/libxml/parser.h>
}C
```

[HTML]storage_file: filename: /var/lib/varnish/retrobadger-desktop/varnish_storage.bin size 1024 MB.
Message from C-compiler:
In file included from ./vcl.1P9zoqAU.c:418:
/usr/include/libxml2/libxml/parser.h:15: fatal error: libxml/xmlversion.h: No such file or directory
compilation terminated.
Running C-compiler failed, exit 1
VCL compilation failed
[/HTML]

Any ideas on whether my code is wrong, the parser.h file appears to be in the correct directory by default, so not sure where to start.

Thankyou for any advice you can give,
Dan

---

### Post by andrew1992 on 2011-03-21
It looks like there is some sort of dependency issue: parser.h relies on libxml/xmlversion.h, which is the header that's missing.  Take a peek into that directory and see if it's there.

---

### Post by trent.josephsen on 2011-03-21
Looks like the libxml2 headers expect to find the libxml directory somewhere in the search path, but in your case it's found in /usr/include/libxml2.  You fixed that with the first one by including <libxml2/libxml/whatever>, but the libxml headers themselves are still trying <libxml/whatever>, so running into problems.

With a command line I'd suggest telling the compiler -I/usr/include/libxml2.  Not sure what the best approach is in your situation.

---

### Post by retrodans on 2011-03-22
@andrew1992: xmlversion.h is in the directory:
```
/usr/include/libxml2/libxml/
```

@trent.josephsen: Sadly I do not compile these scripts when writing for varnish.  It is all inline c within the deffault.vcl file.  Is there another way of setting the include path inline?

---

