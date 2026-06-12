---
title: "[SOLVED] make crontab load a internet page."
date: 2008-11-13
forum: New to Ubuntu
---

### Post by niiklas on 2008-11-13
Hello is there any way to make crontab load this page [http://www.example.com/file.php](http://www.example.com/file.php) every day 3 in the morning?

edit: is it even possible? :P, if not then how could i make it load this website 1 time each day.

---

### Post by redbob on 2008-11-13
Do you mean everyday at 3 o'clock? Type it:
> 00 03  *   *   *     export DISPLAY=:0 && /usr/lib/firefox-3.0.3/firefox [http://www.example.com/file.php](http://www.example.com/file.php)


---

### Post by niiklas on 2008-11-13
> **redbob said:**
> Do you mean everyday at 3 o'clock? Type it:

yes, exactly what i needed!, but is that starting a visual firefox window or is it just in the terminal?, if possible i would want it to not start a visual firefox window since it will be running on a server.

edit:
I tried to run the following command in the terminal but got an error:
```

 export DISPLAY=:0 && /usr/lib/firefox-3.0.3/firefox http://www.example.com/file.php
No protocol specified
Error: cannot open display: :0

```

---

### Post by redbob on 2008-11-13
mmm... the command got error because you are running as CLI session, so there's no X interface on it. 
Look at this:
[http://deepbluespaces.blogspot.com/2008/05/running-php-in-console.html](http://deepbluespaces.blogspot.com/2008/05/running-php-in-console.html)

---

### Post by niiklas on 2008-11-13
> **redbob said:**
> mmm... the command got error because you are running as CLI session, so there's no X interface on it. 
Look at this:
[http://deepbluespaces.blogspot.com/2008/05/running-php-in-console.html](http://deepbluespaces.blogspot.com/2008/05/running-php-in-console.html)

okey thanks, so then the crontab text would be 
00 03 * * * php -f /var/www/filename.php

??

---

