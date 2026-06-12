---
title: "php extension"
date: 2010-03-07
forum: Programming Talk
---

### Post by Randes on 2010-03-07
i install php with zlib.
phpMyAdmin give error: **Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.**

In php.ini uncomment lines and copy in folder ext

```
extension_dir = "/usr/local/php/ext"

extension=php_curl.dll
extension=php_gd2.dll
extension=php_mbstring.dll
extension=php_mcrypt.dll
extension=php_xsl.dll
extension=php_zip.dll
```

error_log:
**PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/local/php/ext/php_curl.dll' - /usr/local/php/ext/php_curl.dll: invalid ELF header in Unknown on line 0**
for all libs


How to decide this problem?

---

### Post by Hellkeepa on 2010-03-07
HELLo!

You're trying to use the Windows DLL files in Linux, which will not work. What you need to do is to tell PHP to load the .so libraries instead.

Happy codin'!

---

### Post by Randes on 2010-03-07
Where can get this *.so library?

---

### Post by Hellkeepa on 2010-03-07
HELLo!

Usually by installing it from the package manager.

Happy codin'!

---

### Post by Sim &amp; Co. on 2010-03-07
Almost ( haven't checked ) every library is available from the official Ubuntu repository - search for [COLOR="Green"]php[/COLOR] and you'll see them.

---

