---
title: "Debian/Ubuntu Filesystem Hierarchy Standard"
date: 2010-01-10
forum: Programming Talk
---

### Post by botfish on 2010-01-10
I am creating a .deb package for application I am developing.

I will be installing the:

executable in /usr/bin/<package-name>/
documentation in /usr/share/doc/<package-name>/
man pages in /usr/share/man/<package-name>/

My package requires a XSD (XML Schema Document) for correct operation. This XSD is fixed and will not change.

Where, in the standard Debian/Ubuntu Filesystem Hierarchy Standard, is the most appropriate place to install the XSD file?

Regards

---

### Post by nvteighen on 2010-01-10
> **botfish said:**
> I am creating a .deb package for application I am developing.

I will be installing the:

executable in /usr/bin/<package-name>/
documentation in /usr/share/doc/<package-name>/
man pages in /usr/share/man/<package-name>/

My package requires a XSD (XML Schema Document) for correct operation. This XSD is fixed and will not change.

Where, in the standard Debian/Ubuntu Filesystem Hierarchy Standard, is the most appropriate place to install the XSD file?

Regards

I'd place it in /usr/share/<package-name>... another possible location is /etc/<package-name> if the XSD is meant to be like a configuration file.

---

### Post by diesch on 2010-01-10
> **botfish said:**
> I am creating a .deb package for application I am developing.

I will be installing the:

executable in /usr/bin/<package-name>/
documentation in /usr/share/doc/<package-name>/
man pages in /usr/share/man/<package-name>/


/usr/share/doc/<package-name>/ is fine, /usr/bin/<package-name>/ and /usr/share/man/<package-name>/ aren't compatible to any standard. Put the executables in /usr/bin/ and the man pages in /usr/share/man/<section>/ instead

> **botfish said:**
> I
My package requires a XSD (XML Schema Document) for correct operation. This XSD is fixed and will not change.

Where, in the standard Debian/Ubuntu Filesystem Hierarchy Standard, is the most appropriate place to install the XSD file?


/usr/share/<packagename>/

---

### Post by botfish on 2010-01-10
Thanks!

---

