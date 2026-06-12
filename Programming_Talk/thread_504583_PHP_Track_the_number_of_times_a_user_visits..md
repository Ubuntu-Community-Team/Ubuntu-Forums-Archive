---
title: "PHP Track the number of times a user visits."
date: 2007-07-19
forum: Programming Talk
---

### Post by 7Priest7 on 2007-07-19
This is a script I created to track visitors...
I run a Christian site and I wanted to know where my user base is...
The code is pretty straight forward and simple...
You have to create a "users" directory once...

```

<?php
if (!file_exists("users/{$_SERVER['REMOTE_ADDR']}.txt")) {
  $userfile = fopen("users/{$_SERVER['REMOTE_ADDR']}.txt","w");
  fwrite($userfile,"1");
  fclose($userfile);
}
else {
  $UserVar = file_get_contents("users/{$_SERVER['REMOTE_ADDR']}.txt");
  $UserVar++;
  file_put_contents("users/{$_SERVER['REMOTE_ADDR']}.txt",$UserVar);
}
?>

```

Maybe this may do a number of things for these forums...
Get More Visitors
Increase PR
or Help Users

Alex

---

### Post by smartbei on 2007-07-19
Well, all you are doing is tracking the number of times a certain IP address visits your site. Given that most people have dynamic IP connections, this means little as to the actual number of people visiting your site, though it can help you know their general location.

Frankly, you may as well use a simple counter for your site coupled with a tool that tells you the country for a given ip (like this one - [http://www.phpclasses.org/browse/package/1477.html](http://www.phpclasses.org/browse/package/1477.html))

See [http://www.php.net/reserved.variables](http://www.php.net/reserved.variables) for the exact definition of $_SERVER['REMOTE_ADDR'].

---

### Post by 7Priest7 on 2007-07-20
Frankly I did not ask for info...
I already know that a users IP changes...
However... Their IP is the only current way to uniquely identify them...
I was just sharing my code to help other users...
Use my code or don't it doesent bug me...

Alex

---

### Post by 7Priest7 on 2007-07-20
Ohh I have a reason for not using a counter
The reason is simple enough...
A counter will take away from my sites look...


Alex

---

### Post by tturrisi on 2007-07-20
> **7Priest7 said:**
> Ohh I have a reason for not using a counter
The reason is simple enough...
A counter will take away from my sites look...

Alex
You can still use a counter on a page and just not display it!
cross browser:
<div style="display:none; visibility:hidden;"><some-counter-code></end></div>
You can then add a php link or javascript link that toggles the visibility on & off.

anyway, thanks for YOUR code.
tt

---

### Post by smartbei on 2007-07-20
You could also, since you are using php, just stick it in php code that reads a text file, adds 1 to the total there, and then saves it. Simple enough.

---

