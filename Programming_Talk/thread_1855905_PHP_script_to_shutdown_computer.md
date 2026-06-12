---
title: "PHP script to shutdown computer?"
date: 2011-10-07
forum: Programming Talk
---

### Post by superdaveozzborn on 2011-10-07
is it possible to shutdown one of my servers on my home network by clicking a link in the browser?

i have a "lamp" server running on my network, i would like to shut it down by clicking a link in my browser, i searched this for several hours and found very little, what i did find was of no luck. i am thinking that it must be a security issue, or that it is not possible to do it. my server is behind a firewall and is not accessible by the web but i dont really want to make it to risky to do. i can use login method that uses mysql to help secure the page that contains the script however i need the actual code to preform the shutdown.

is this possible?

any links or info would be appreciated thanks.

---

### Post by SlugSlug on 2011-10-07
```
<?php
$output = shell_exec('shutdown -p now');
echo "<pre>$output</pre>";
?>
```

---

### Post by SeijiSensei on 2011-10-07
Since the Apache server runs as user www-data and not as root, I don't think that example will work.

I've used a semaphore in these cases.  You need two scripts, a PHP script that displays in the browser, and a shell script that runs as root using cron.  Something like this:

Browser code:
```

if ($_POST['action']=="Shutdown") {
    $test=shell_exec("touch /tmp/shutdown");
}

```

Shell script /usr/sbin/check_shutdown 
```

#!/bin/sh
if [ -f "/tmp/shutdown" ]
then
   rm -f /tmp/shutdown
   /sbin/shutdown now
fi

```

Edit root's crontab using "sudo crontab -e" and add the line

```
* * * * * sh /usr/sbin/check_shutdown
```

This runs the check_shutdown script once each minute.  If it finds the /tmp/shutdown file created by the PHP script, it executes the shutdown command.

---

