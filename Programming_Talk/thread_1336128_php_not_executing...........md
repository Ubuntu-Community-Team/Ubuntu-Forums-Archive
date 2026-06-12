---
title: "php not executing.........."
date: 2009-11-24
forum: Programming Talk
---

### Post by abhilashm86 on 2009-11-24
there is an error, whenever i invoke browser ```
http://localhost/
```

The requested URL / was not found on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80

also in error log there is error reported........```
[Tue Nov 24 17:14:30 2009] [error] Unterminated <> operator at /var/www/display.php line 1.\n
[Tue Nov 24 17:15:25 2009] [error] Unterminated <> operator at /var/www/index.php line 1.\n
[Tue Nov 24 17:15:27 2009] [error] Unterminated <> operator at /var/www/index.php line 1.\n
[Tue Nov 24 17:17:40 2009] [error] [client ::1] Attempt to serve directory: /var/www/
```

but there is no error in line 1 in /var/www/index.php,
its a default thing that pops up......help please

---

### Post by Arndt on 2009-11-24
> **abhilashm86 said:**
> there is an error, whenever i invoke browser ```
http://localhost/
```

The requested URL / was not found on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80

also in error log there is error reported........```
[Tue Nov 24 17:14:30 2009] [error] Unterminated <> operator at /var/www/display.php line 1.\n
[Tue Nov 24 17:15:25 2009] [error] Unterminated <> operator at /var/www/index.php line 1.\n
[Tue Nov 24 17:15:27 2009] [error] Unterminated <> operator at /var/www/index.php line 1.\n
[Tue Nov 24 17:17:40 2009] [error] [client ::1] Attempt to serve directory: /var/www/
```

but there is no error in line 1 in /var/www/index.php,
its a default thing that pops up......help please

What do your index.php and display.php look like?

---

### Post by abhilashm86 on 2009-11-24
> **Arndt said:**
> What do your index.php and display.php look like?

its a huge file, shows seetings and info about php........
```
<?php

error_reporting(E_ALL ^ E_NOTICE);

define('IN_SCRIPT',1);



/* Get settings from the settings.php file */ 

require 'settings.php';



/* Start user session or output an error */

session_name('CCOUNT');

if (!session_start()) {

    error('Cannot start a new PHP session. Please contact server administrator or webmaster!');

}



/* If no action parameter is set let's force visitor to login */

if (empty($_REQUEST['action'])) {

    if (isset($_SESSION['logged']) && $_SESSION['logged'] == "Y") {

        pj_session_regenerate_id();

        mainpage();

    } else {

        login();

    }

} else {

    $action=htmlspecialchars($_REQUEST['action']);

}



/* Do the action that is set in $action variable */

if ($action == 'login') {

    checkpassword();

    $_SESSION['logged']='Y';

    pj_session_regenerate_id();

    mainpage();

} elseif ($action == 'save') {

    checklogin();

    savelink();

} elseif ($action == 'edit') {

    checklogin();

    editlink();

} elseif ($action == 'backup') {

    checklogin();

    sendbackup();

}  elseif ($action == 'remove') {

    checklogin();

    removelink();

} elseif ($action == 'reset') {

    checklogin();

    resetlink();

} elseif ($action == 'add') {

    checklogin();

    add();

} elseif ($action == 'restore') {

    checklogin();

    restore();

} elseif ($action == 'logout') {

    logout();

} else {

    login();

}

exit();
//goes on

```

---

### Post by Arndt on 2009-11-24
I think the contents of the php file is not important. It looks like it is being run by Perl instead of php. It's an error message from Perl.

---

### Post by abhilashm86 on 2009-11-24
> **Arndt said:**
> I think the contents of the php file is not important. It looks like it is being run by Perl instead of php. It's an error message from Perl.

oh yes, i actually gave path for perl same in php path, so i started to save both in same directory,
now i've changed a lot, i'm re-installing it..........

---

