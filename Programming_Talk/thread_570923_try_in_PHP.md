---
title: "try in PHP"
date: 2007-10-08
forum: Programming Talk
---

### Post by DouglasAWh on 2007-10-08
I;'m making a facebook app and I'm pretty new to PHP.  My code is below.

```

<?php
require_once 'facebook.php';

$appapikey = 'right...';
$appsecret = 'el nadda';
$facebook = new Facebook($appapikey, $appsecret);
$user = $facebook->require_login();

//[todo: change the following url to your callback url]
$appcallbackurl = 'nope';

//catch the exception that gets thrown if the cookie has an invalid session_key in it
try {
  if (!$facebook->api_client->users_isAppAdded()) {
    $facebook->redirect($facebook->get_add_url());
  }
} 
catch (Exception $ex) {
  //this will clear cookies for your application and redirect them to a login prompt
  $facebook->set_user(null, null);
  $facebook->redirect($appcallbackurl);
}
?>

```

I am getting Parse error: parse error, unexpected '{' on line 13, which is the bracket after "try."  According to [http://devzone.zend.com/manual/language.exceptions.html](http://devzone.zend.com/manual/language.exceptions.html), it looks like I've got the syntax correct.  What's the deal?

---

### Post by deuce868 on 2007-10-08
Exceptoins are new to PHP5. Is your server PHP5 or version 4?

---

### Post by maddog39 on 2007-10-08
Yeah, try writing that script without the try catch statement. Your local server probably doesn't have PHP 5 and that why its giving you problems.

---

