---
title: "Eclipse PDT debugging problem."
date: 2010-06-09
forum: Programming Talk
---

### Post by minerbog on 2010-06-09
Hi All,

I have a problem with Eclipse PDT debugger. Now I'm not sure if it started before or after I upgraded to 10.04 (I think it was after!!??).

When debugging a php script as a web page, it no longer debugs line by line but just loads the page as normal?

Whilst search through my error log on apache2 I found the following:

<b>Warning</b>:  Directive 'register_long_arrays' is deprecated in PHP 5.3 and greater in <b>Unknown</b> on line <b>0</b><br />
[Wed Jun 09 11:49:49 2010] [notice] caught SIGTERM, shutting down
Zend Debugger requires Zend Engine API version 220060519.
The Zend Engine API version 220090626 which is installed, is newer.
Contact Zend Technologies at [http://www.zend.com/](http://www.zend.com/) for a later version of Zend Debugger.

Now surely, a new version of anything is better, right??

I'm really and truly stumped with this one and any help would be greatly received by me and my ability to sleep!!

Gav.

---

### Post by minerbog on 2010-06-15
Solved it!!

I missed an update to php 5.3. My debugger was for 5.2!! DOH!

---

