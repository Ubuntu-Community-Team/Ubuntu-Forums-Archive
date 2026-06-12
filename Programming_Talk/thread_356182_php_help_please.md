---
title: "php help please"
date: 2007-02-08
forum: Programming Talk
---

### Post by gorilly on 2007-02-08
i've uploaded a free youtube style script but i am getting two errors, i really dont understand mysql/php... please can someone help?



Warning: require_once(k:/pm/youtube_prof/smarty/libs/Smarty.class.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/web8/web/include/config.php on line 40

Fatal error: require_once() [function.require]: Failed opening required 'k:/pm/youtube_prof/smarty/libs/Smarty.class.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/web8/web/include/config.php on line 40

---

### Post by jd65pl on 2007-02-08
You could try posting your question in the phpBB.com forum they may be more able to help you [http://www.phpbb.com/phpBB/](http://www.phpbb.com/phpBB/)

---

### Post by runningwithscissors on 2007-02-08
> **gorilly said:**
> i've uploaded a free youtube style script but i am getting two errors, i really dont understand mysql/php... please can someone help?



Warning: require_once(k:/pm/youtube_prof/smarty/libs/Smarty.class.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/web8/web/include/config.php on line 40

Fatal error: require_once() [function.require]: Failed opening required 'k:/pm/youtube_prof/smarty/libs/Smarty.class.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/web8/web/include/config.php on line 40

You need the PHP templating engine "Smarty" installed on your web server.
And I am guessing that won't be the end of your problems. These youtube scripts may have other dependencies too.

---

### Post by gorilly on 2007-02-08
thanks im looking at the smarty page now.

how can i find a list of dependancys?

there is nothing better than jumping in at the deep end..

---

### Post by runningwithscissors on 2007-02-08
> **gorilly said:**
> how can i find a list of dependancys?
I've never used any such youtube scripts. Maybe the site/party you got it from have an FAQ/howto of sorts or someone who'd be better able to give you that information.

---

