---
title: "Problems with installing TYPO3 on Ubuntu Server"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by Trini101 on 2012-09-25
Hello,

I'm a beginner to Ubuntu and TYPO3.

I have installed TYPO3 on my Ubuntu server but all I get is this error message:


Fatal error: Uncaught exception 'RuntimeException' with message 'Could not create directory "/var/www/mywebsite/typo3temp/Cache/Code/cache_phpcode/"!' in /var/www/mywebsite/t3lib/class.t3lib_div.php:2979 Stack trace: #0 /var/www/mywebsite/t3lib/class.t3lib_div.php(2948): t3lib_div::createDirectoryPath('/var/www/mywebs...') #1 /var/www/mywebsite/t3lib/cache/backend/class.t3lib_cache_backend_filebackend.php(201): t3lib_div::mkdir_deep('/var/www/mywebs...') #2 /var/www/mywebsite/t3lib/cache/backend/class.t3lib_cache_backend_filebackend.php(99): t3lib_cache_backend_FileBackend->createFinalCacheDirectory('/var/www/mywebs...') #3 /var/www/mywebsite/t3lib/cache/frontend/class.t3lib_cache_frontend_abstractfrontend.php(63): t3lib_cache_backend_FileBackend->setCache(Object(t3lib_cache_frontend_PhpFrontend)) #4 /var/www/mywebsite/t3lib/cache/frontend/class.t3lib_cache_frontend_phpfrontend.php(45): t3lib_cache_frontend_AbstractFrontend->__construct('cache_phpcode', Object(t3lib_cache_backend_FileBackend)) #5 [internal function]: t3li in /var/www/mywebsite/t3lib/cache/backend/class.t3lib_cache_backend_filebackend.php on line 203

Can anyone help me?

---

