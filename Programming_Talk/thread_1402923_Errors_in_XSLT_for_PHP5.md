---
title: "Errors in XSLT for PHP5"
date: 2010-02-09
forum: Programming Talk
---

### Post by ewg118 on 2010-02-09
Hi, I installed php5-xslt properly (as far as I know), and when I executue phpinfo() I get the following piece of information:

```
xsl

XSL => enabled
libxslt Version => 1.1.24
libxslt compiled against libxml Version => 2.6.32
EXSLT => enabled
libexslt Version => 1.1.24
```

But when I execute: 
[PHP]
<?php $xh = xslt_create(); // we check for the ability to use XSLT ?>[/PHP]

I get: Fatal error: Call to undefined function xslt_create() on line 1

I'm running Ubuntu 9.10 and my php version is:

PHP 5.2.10-2ubuntu6.4 with Suhosin-Patch 0.9.7 (cli) (built: Jan  6 2010 22:41:56) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2009 Zend Technologies

I looked up this problem in Google, but no one seems to have addressed it.

Thanks.

---

### Post by Hellkeepa on 2010-02-09
HELLo!

The test you posted seems to have been executed from the PHP-CLI executable, which uses a different "php.ini" than the web server. You also need to restart the web server to get to reload the "php.ini", and the additional libraries. So that's what I'd do first.
If it still didn't work, check the "php.ini" and use "phpinfo ()" in a web page.

Happy codin'!

---

### Post by Reiger on 2010-02-09
Out-of-the-box configurations for the PHP5 CLI and CGI SAPIs (on Debian/Ubuntu at least) are indentical when it comes to extension modules, since the configuration data for extension modules is stored in their own little configuration files that are read in both scenario's.

The real problem here is that you are using the wrong PHP code: between PHP 4 and PHP5 the code interfacing with XSLT processors received a major overhaul. You will want to study the new style PHP 5 code (new XSLTProcessor()) in the PHP manual on php.net.

---

### Post by Hellkeepa on 2010-02-10
HELLo!

D'oh! I should have picked up on that one, sorry about that.
**Reiger** is, of course, entirely correct.

Happy codin'!

---

### Post by ewg118 on 2010-02-10
Excellent!  Thanks.  My colleague was apparently unaware of the change from PHP4 to PHP5 syntax, and I myself am more of an XSLT person than a PHP person.

---

