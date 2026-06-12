---
title: "Integrating php-java-bridge in dapper?"
date: 2008-07-22
forum: Packaging and Compiling Programs
---

### Post by raghaven.kumar on 2008-07-22
Hi,
I have a Ubuntu dapper 6.06.2 server
it has apache2 and ISPConfig running on it.
I installed php-java-bridge-5.2.2 using a .deb file
and made the relevant changes in
/etc/php5/apache2/php.ini
and in java.ini

Now, its not showing any symptoms of running.
I tried installing lower and higher versions of php-java-bridge.

But still it doesn't run and thus doesn't show Java in phpinfo.php.
So,umm..., whats wrong in here?

Heres my java.ini

> ;; zend_extension = "/path/to/java.so"
extension = java.so

java.home = /usr/bin
java.library = /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/server/libjvm.so
And how do i restart php-java-bridge ??

---

### Post by raghaven.kumar on 2008-07-22
i think i found the problem

the phpinfo() page doesnot show the "additional .ini files parsed" option.

it even doesnt show a "scan this dir for .ini files" option

Is this a issue??
And how to rectify it?

---

