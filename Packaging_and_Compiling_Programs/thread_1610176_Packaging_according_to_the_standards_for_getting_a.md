---
title: "Packaging according to the standards for getting a program in the repositories"
date: 2010-10-31
forum: Packaging and Compiling Programs
---

### Post by caswiddershoven on 2010-10-31
I am one of the maintainers of OpenTeacher, a program which helps you learn a foreign language. We are about to release our 2.0-version (we are planning to release that around new year), and we wanted to try and get the program in the repositories. The most urgent problem however is, that we have no *good* packagers, who can package according to the standards for getting a program in the repositories. If someone would be able to tell us how to do this, or even better, to package our program, please! I beg you! Help us! Thank you.

---

### Post by MadCow108 on 2010-10-31
you should post a request for packaging bug at the debian bugtracker:
see RFP at [http://www.debian.org/devel/wnpp/](http://www.debian.org/devel/wnpp/)

you should also mail to debian-edu and/or ubuntu-edu list:
[http://lists.debian.org/debian-edu/](http://lists.debian.org/debian-edu/)
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-education](https://lists.ubuntu.com/mailman/listinfo/ubuntu-education)

here some links which might help you doing it yourself:
debian package maintainer guide:
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)
ubuntu package maintainer guide:
[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)
deian packaging policy (ubuntu has basically the same):
[http://www.debian.org/doc/debian-policy/#contents](http://www.debian.org/doc/debian-policy/#contents)

site where you can upload your package and have them reviewed.
[http://mentors.debian.net/cgi-bin/welcome](http://mentors.debian.net/cgi-bin/welcome)

reference:
[http://www.debian.org/doc/developers-reference/index.html](http://www.debian.org/doc/developers-reference/index.html)

debian mentors mailing lists:
[http://lists.debian.org/debian-mentors/](http://lists.debian.org/debian-mentors/)

(note: debian packages get imported automatically to ubuntu)

---

