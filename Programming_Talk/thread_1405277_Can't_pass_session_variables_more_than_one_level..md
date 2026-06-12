---
title: "Can't pass session variables more than one level."
date: 2010-02-12
forum: Programming Talk
---

### Post by DFHIII on 2010-02-12
If I open a file and read a value, then assign that value to a session variable ($_SESSION['MYVAR']) redirect to another page, that page can get the variable with $myvar = $_SESSION['MYVAR'].  If I redirect from the second to a third page, that third page cannot see the session variable.

I am using php 5 and mysql with ubuntu 8..04 desktop.  My browser is Firefox 3.0.17 and I am doing my development testing on localhost.

This is a big project and many of the variables do pass from page to page with no apparent limit.

Is there a limit to the number of session variables I can use?  I have read the php.ini file and can't find any stated limitation.

In the php.ini file, register_globals = off.  That is the default.  Should I change that?

Where might I start looking?

Thanks,

Dan H.

---

### Post by turnermm on 2010-05-30
I have found the same problem, though I can't be sure yet whether it's because I am running Ubuntu in virtualization software on a Mac, although the same problem does not occur when running Windows in the Mac viritualization environment.

What I have found, however, is that Cookie variables are not lost. The session data is saved to disk and remains available if you know the session id.  PHP sets a cookie with the session id (PHPSESSID), or you can set your own cookie with the session id.   Then when you want the session data, you can get your session data back by calling **session_id**     ([  string  $id   ] ).

---

### Post by ju2wheels on 2010-05-31
It sounds like one of your pages is either overwriting the value (maybe you have an if statement setup as if( $_SESSION['VAR'] = VALUE) instead of if( $_SESSION['VAR'] == VALUE)) or you may be garbage collecting your sessions too fast. Check the garbage collection times on your sessions in php.ini. Also setup the logging to E_STRICT, there maybe something going on you are missing.

---

