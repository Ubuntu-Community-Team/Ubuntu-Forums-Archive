---
title: "Vendor, Product and Version of C libraries"
date: 2015-07-08
forum: Packaging and Compiling Programs
---

### Post by fflorent on 2015-07-08
Hello,

On my Linux (Debian/Ubuntu), I can get the **PRODUCT **of a **library **with "apt-file search" or "dpkg -S".

May be I can get the **VERSION **by parsing the name of the library.so.

But, How can I get the _**VENDOR**_???

Thank you very much,
Florent

---

### Post by TheFu on 2015-07-08
Not all files have a vendor, so there isn't anything to find.
The older C files might have an RCS id inside - which can be retrieved using the **ident** command. [https://www.gnu.org/software/rcs/manual/html_node/ident.html](https://www.gnu.org/software/rcs/manual/html_node/ident.html) - alas, RCS has been replaced by other version control systems and I don't think most coders do the "id" tagging anymore.

That leaves just the "strings" command for what is inside the actual library files.```

$ whatis  strings
strings (1)          - print the strings
```

I think the best hope is to check the package files. There is no standard of which I am aware.

---

### Post by fflorent on 2015-07-08
Yes. Actually get the **package **with "apt-file search" or "dpkg -S". But to get the _**vendor **_it's more difficult :-)

---

