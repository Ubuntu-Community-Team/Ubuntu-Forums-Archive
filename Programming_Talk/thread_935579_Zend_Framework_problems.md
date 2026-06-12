---
title: "Zend Framework problems"
date: 2008-10-01
forum: Programming Talk
---

### Post by emoxter on 2008-10-01
Anyone using the Zend Framework for PHP Development?  For some reason nothing is being included correctly within the Zend directory structure.  Every other include works but when trying to do anything with the Zend Framework its not working.  I've looked and looked I think I need other eyes.

Here's the error I'm getting:

[FONT="Courier New"]
Warning: require_once(Zend/DB.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/employee/index.php on line 16

Fatal error: require_once() [function.require]: Failed opening required 'Zend/DB.php' (include_path='.:/usr/share/php:/usr/share/pear:/var/CORE:/usr/share/php/libzend-framework-php') in /var/www/employee/index.php on line 16[/FONT]

Any ideas?

---

### Post by emoxter on 2008-10-06
Well I finally figured out the problem I was having, which is stupid on my part.  On my Rewrite Rules I was NOT using the project directory but using the root directory of the web server.  So anyone that was having the same problem there's the fix.

---

### Post by drubin on 2008-10-06
Nice work on the fix. Just remember to mark it as solved so that others having the same issue  will know there is a solution.

---

### Post by Penteado on 2008-12-06
I have the same problem. what do you mean by Rewrite Rules ?

---

