---
title: "Using .htaccess to redirect to a php script"
date: 2009-09-13
forum: Programming Talk
---

### Post by Johnsie on 2009-09-13
Hello, I have a folder that I want redirected:

[http://example.com/SpecialFolder/index.php](http://example.com/SpecialFolder/index.php) ----> [http://example.com/process.php?pageName=index.php](http://example.com/process.php?pageName=index.php)

[http://example.com/SpecialFolder/test.php](http://example.com/SpecialFolder/test.php) ----> [http://example.com/process.php?pageName=test.php](http://example.com/process.php?pageName=test.php)

[http://example.com/SpecialFolder/page2.php](http://example.com/SpecialFolder/page2.php)  ----> [http://example.com/process.php?pageName=page2.php](http://example.com/process.php?pageName=page2.php)

The thing is that I wont alway know what the name of the php file will be. Is there a way I can use .htaccess to do this kind of redirect?

---

### Post by Reiger on 2009-09-13
You would probably want to use mod rewrite & set up appropriate URL rewrite rules. Google should lead straight to some tutorials on that.

---

### Post by Finalfantasykid on 2009-09-13
[http://www.besthostratings.com/articles/mod-rewrite-intro.html](http://www.besthostratings.com/articles/mod-rewrite-intro.html)

ModRewrite might do what you are asking.  Though this might simply change the way the URL looks, rather than actually redirecting.

---

