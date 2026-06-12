---
title: "Apache2"
date: 2006-01-14
forum: Repositories &amp; Backports
---

### Post by Stormx on 2006-01-14
having some real problems with the apache2 package. Look:

```

Preconfiguring packages ...
Selecting previously deselected package apache2-utils.
(Reading database ... 134190 files and directories currently installed.)
Unpacking apache2-utils (from .../apache2-utils_2.0.54-5ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-common.
Unpacking apache2-common (from .../apache2-common_2.0.54-5ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.0.54-5ubuntu4_i386.deb) ...
Selecting previously deselected package apache2.
Unpacking apache2 (from .../apache2_2.0.54-5ubuntu4_i386.deb) ...
Setting up apache2-utils (2.0.54-5ubuntu4) ...
Setting up apache2-common (2.0.54-5ubuntu4) ...
Setting Apache2 to Listen on port 80. If this is not desired, please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.

Setting up apache2-mpm-worker (2.0.54-5ubuntu4) ...
 * Starting web server (Apache2)... /usr/sbin/apache2ctl: line 78: 13604 Segmentation fault      $HTTPD -k start -DSSL
                                                                         [fail]
invoke-rc.d: initscript apache2, action "start" failed.

Setting up apache2 (2.0.54-5ubuntu4) ...

```

What should I do? I've spoken in #apache and #ubuntu but I havn't really been able to get much help =(

---

### Post by Stormx on 2006-01-16
Bump. Please... I'm all out of ideas.

---

### Post by Stormx on 2006-01-16
Well I got it working. i completely uninstalled all things with apache in their name, removed every config file I could find, reinstalled all of apache2's dependancies, completely removed libapr (or something along those lines)

then did apt-get install apache2 and held my breath ;-)

And it works, i think!

---

