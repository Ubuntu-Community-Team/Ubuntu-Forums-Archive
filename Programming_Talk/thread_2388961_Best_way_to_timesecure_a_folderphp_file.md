---
title: "Best way to timesecure a folder/php file"
date: 2018-04-09
forum: Programming Talk
---

### Post by cazz on 2018-04-09
Hi
I have a webpage in PHP in a folder on apache2
if I want to just make it access between a time a specific date, what is the best way?

is it inside PHP or is to use some kind of htaccess?

---

### Post by TheFu on 2018-04-09
Do it in the router.

Or you can script it. Disable apache/enable apache at specific times.  Add/remove specific virtual-apache sites at specific times (don't forget to reload apache after any changes), or if you are willing to have errors happen to connected clients, just change the permissions on the top level directory.

When I need to perform maintenance on any of my websites, I redirect the main page to a "Down for Maintenance" page with an expected availability time ... usually from 6am-7am on Saturdays.  It usually takes about 15 minutes, but better to be predictable and slow than unpredictable and fast.   I also have daily periods of downtime for backups, but that is usually 1-3 minutes, so hardly worth telling anyone.  My bosses know that backups happen between 1a and 330a, so if any service isn't available then, to just wait a few minutes.

---

### Post by SeijiSensei on 2018-04-10
You don't tell us what visitors should see if they access the site outside of the permissible hours.  

If you're happy enough with the site being offline, then you can start and stop apache via entries in cron.  For simplicity, I'll use /etc/crontab for this task. Suppose the site is to be available between 6 am and 6 pm every day.  Then you could add these lines to /etc/crontab:

```

# start apache every day at 6 am
0 6  * * * root /sbin/service apache2 start
# stop apache every day at 6 pm
0 18 * * * root /sbin/service apache2 stop

```

That's a pretty clunky and unfriendly way to handle this task though. Instead I would use a "wrapper" script in PHP.  Suppose the ordinary content is contained in the file /var/www/normal_page.php.  In /var/www/html you could create an index.php script like this:

```

<?php

$H=intval(date("G"));  # returns a value between 0 and 23 for the current hour

$open=6;
$close=18;

if ($H >= $open && $H <= $close) {
     include("/var/www/normal_page.php");

} else {
    echo "<h3>This site is available between the hours of ".$open.":00 and ".$close.":00.  Please come back then.</h3>";

}
?>

```

I placed the included script outside of the DocumentRoot so it cannot be accessed directly.  I actually use a more  elaborate version of this method for the sites I design.  All the actual scripts are stored in a directory outside the web root and incorporated into index.php using include() or require() as needed.

---

