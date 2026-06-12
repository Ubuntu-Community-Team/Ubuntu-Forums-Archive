---
title: "Changlog Syntax...?"
date: 2010-10-27
forum: Programming Talk
---

### Post by hakermania on 2010-10-27
This is my changelog file:
```
     some-1.0 version 1.0; urgency=low

       * The program is programmed in C++ with QtCreator.

      -- Jhon Smith <test@test.com>  2010-10-27
```

But it outputs the error:
[I][B]parsechangelog/debian: warning:     debian/changelog(l1): found change data where expected first heading
LINE:      some-1.0 version 1.0; urgency=low
parsechangelog/debian: warning:     debian/changelog(l6): found eof where expected more change data or trailer
parsechangelog/debian: error: Can't call method "as_string" on an undefined value at /usr/share/perl5/Dpkg/Changelog.pm line 250, <STDIN> line 6.[/B]
[/I]
What do I do wrong? I followed these info:
[http://www.debian.org/doc/debian-policy/ch-source.html#s-dpkgchangelog](http://www.debian.org/doc/debian-policy/ch-source.html#s-dpkgchangelog)
Thx in advance for any help!

---

### Post by MadCow108 on 2010-10-27
your format is not correct, read the policy again carefully.
the first line should look like this:

some-1.0 (1.0) some_distro; urgency=low

and the date formating is also wrong

better use *dch --create* from the devscripts package to create changelogs in the correct format
and dch -i for adding an entry and increasing the package version

---

