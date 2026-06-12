---
title: "PHP error."
date: 2006-03-19
forum: Programming Talk
---

### Post by Darkness3477 on 2006-03-19
HI, I've just gotten down all my php stuff, for a website so someone can sign up, log in and then do whatever.... And if they arenot logged in, it should refer them to the sign up page... But whatever page I open that I have just loaded up, it gives this error

```

Warning: main(DB.php): failed to open stream: No such file or directory in /var/www/db_connect.php on line 5

Fatal error: main(): Failed opening required 'DB.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/db_connect.php on line 5
```

Now, I cannot for the life of me read error messages very well, but I assume that i need to have something called DB.php. Which, if I remember is something to do with pear. So, if I'm correct, where can I download pear from, and if it's in the repositories do I just got sudo apt-get pear?

---

### Post by Darkness3477 on 2006-03-19
I've installed pear, php4, php5 and it's all in the right file path (/usr/share/) but still I get the same error message. Why is this?

---

### Post by LordHunter317 on 2006-03-19
Posting source code is helpful.  Likely, you don't have the include path correct.

---

### Post by Darkness3477 on 2006-03-19
```
<?php

//require the PEAR::DB classes.

require_once 'DB.php';


$db_engine = 'mysql';
$db_user = 'myuser';
$db_pass = 'mypassword';
$db_host = 'localhost';
$db_name = 'mydatabase';

$datasource = $db_engine.'://'.
			  $db_user.':'.
			  $db_pass.'@'.
		 	  $db_host.'/'.
	  		  $db_name;


$db_object = DB::connect($datasource, TRUE);

/* assign database object in $db_object, 

if the connection fails $db_object will contain

the error message. */

// If $db_object contains an error:

// error and exit.

if(DB::isError($db_object)) {
	die($db_object->getMessage());
}

$db_object->setFetchMode(DB_FETCHMODE_ASSOC);

// we write this later on, ignore for now.

include('check_login.php');

?>

```

Thats the thing I try to open up from localhost, and the error message is the one in the first post.

---

### Post by LordHunter317 on 2006-03-20
Is the php-db package actually installed?  If so, with that search path, it ought to be included.

---

### Post by Darkness3477 on 2006-03-20
I installed the php-pear using apt-get install, so I'm assuming it is there. Is there anyway I can test this?

---

### Post by Darkness3477 on 2006-03-20
OPh god, I feel rather foolish now. I assumed the db classes were included in PEAR, so I didn't get them... But, in my defence, the tutorial didn't actually state that I need to download the DB Classes.

Thankyou so much for making me actually check, as I was going spare tryingn to figure it out.

---

### Post by proy80 on 2006-04-07
[QUOTE=Darkness3477]I've installed pear, php4, php5 and it's all in the right file path (/usr/share/) but still I get the same error message. Why is this?[/QUOTE]

Could you tell me how you installed pear. I looked in my /usr/share, but there is no directory called pear. I am trying to use fruity to configure Nagios. I d have the binary called pear though. And it gives me this error

Warning: main(/usr/local/groundwork/fruity/includes/adodb/adodb.inc.php) [function.main]: failed to open stream: No such file or directory in /var/www/fruity/includes/config.inc on line 62

Warning: main() [function.include]: Failed opening '/usr/local/groundwork/fruity/includes/adodb/adodb.inc.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/fruity/includes/config.inc on line 62

Warning: main(/usr/local/groundwork/fruity/output/output.php) [function.main]: failed to open stream: No such file or directory in /var/www/fruity/includes/config.inc on line 63

Warning: main() [function.include]: Failed opening '/usr/local/groundwork/fruity/output/output.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/fruity/includes/config.inc on line 63

---

### Post by Darkness3477 on 2006-04-07
From memory I think I just went sudo apt-get install pear, or something similar. Search around on google and you'll find a hole list of useful thing to download for php.

---

