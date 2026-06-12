---
title: "path_include problem (Zend installation)"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by goldenbough on 2008-04-23
I am trying to run the Zend Framework here with my application. I had this error on my index page:

Warning: require_once(Zend/Loader.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/phpweb20/htdocs/index.php on line 3

Fatal error: require_once() [function.require]: Failed opening required 'Zend/Loader.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/phpweb20/htdocs/index.php on line 3

Presumably this indicated a problem with Zend and PHP; that it was unable to find the include path through /usr/share/php. This directory didn't even exist so I created one, and put the Zend folder in there. After doing this I reloaded the index page, and now have this error:

Fatal error: Uncaught exception 'Zend_Log_Exception' with message '"/var/www/phpweb20/data/logs/debug.log" cannot be opened with mode "a"' in /usr/share/php/Zend/Log/Writer/Stream.php:66 Stack trace: #0 /var/www/phpweb20/htdocs/index.php(12): Zend_Log_Writer_Stream->__construct('/var/www/phpweb...') #1 {main} thrown in /usr/share/php/Zend/Log/Writer/Stream.php on line 66

What does this error message mean?  I am not really certain where to go with this problem.

---

### Post by ZabiGG on 2008-05-16
Hi there and thanks for your question...

Sorry it took so long. Posts pile up pretty fast in this section of the forum.

Are you still trying to solve this issue? If you have, we'd love to know the outcome.

If you still need help, I can help you find some, so just post back.

Thanks,

ZabiGG

---

