---
title: "Ajax Poll Problem"
date: 2006-12-06
forum: Programming Talk
---

### Post by robtotheb on 2006-12-06
Trying to get a ajax poll working locally before I upload it to my site 

[http://www.dhtmlgoodies.com/index.html?whichScript=ajax-poller](http://www.dhtmlgoodies.com/index.html?whichScript=ajax-poller)

Been having a major headache getting it to work! 

If I call the main file ajax-poller.html the php doesn't parse
example - [http://www.salonbrowse.com/robs/ajax-poller.html](http://www.salonbrowse.com/robs/ajax-poller.html)

with a php extension - [http://www.salonbrowse.com/robs/ajax-poller.php](http://www.salonbrowse.com/robs/ajax-poller.php) I get nothing

its meant to do this - 

[http://www.dhtmlgoodies.com/scripts/ajax-poller/ajax-poller.html](http://www.dhtmlgoodies.com/scripts/ajax-poller/ajax-poller.html)

I have mysql and php working so I'm lost as what to try next.

---

### Post by Paul41 on 2006-12-06
> with a php extension - [http://www.salonbrowse.com/robs/ajax-poller.php](http://www.salonbrowse.com/robs/ajax-poller.php) I get nothing

Do you have error reporting turned off in you php.ini file? It could be there is an error with your php script and with error reporting turned off you will get nothing. You could check your server log to see if there was an error.

---

### Post by tocleora on 2006-12-06
On the first one (.html), you used to be able to set up in httpd.conf what extensions you want to be what filetypes, an entry called:

AddType application/x-httpd-php .php

You could add

AddType application/x-httpd-php .php .html

However, I'm running Apache2 now and that line is remarked out, and yet still parses php, so I'm not sure how it does it in apache2.

On the second one, Like Paul41 said it looks like you have error reporting turned off.  You'll have an entry similar to this:

error_reporting  =  E_ALL & ~E_NOTICE

Except E_ALL & ~E_NOTICE is more than likely set to something else, you can set that like mine and you should see the errors.  It's suggested you turn that back off once you find the error.  If you're willing to post the code we can look at it if you don't want to change the php.ini file or can't (shared hosting).

---

### Post by robtotheb on 2006-12-06
added

AddType application/x-httpd-php .php .html

to apache apache2.conf (restarted) no difference.


error_reporting = E_ALL & ~E_NOTICE is active already in both php4 and 5.

:confused: 

Where would it log the errors?

---

### Post by Paul41 on 2006-12-06
I think the error log is at /var/log/apache2/error.log

I am at another computer right now so I can't verify that this is the correct location.

---

### Post by tocleora on 2006-12-06
This may seem like an obvious question but, did you add any polls?  It's possible the .php one is working, just doesn't have a poll to show?  Just a quick brainstorm. :)

---

### Post by tocleora on 2006-12-06
> **Paul41 said:**
> I think the error log is at /var/log/apache2/error.log

Verified true. :)

---

### Post by Paul41 on 2006-12-06
Another thought along the same lines as tocleora's. Have you verified that this sql statement returns some values?

select * from poller_option where pollerID='$pollerId' order by pollerOrder

---

### Post by tocleora on 2006-12-06
Did you set up createDbTables.php?  You have to put your mysql settings in the file:

$conn = mysql_connect("localhost","username","password");

mysql_select_db("yourDbName",$conn)

Then it appears it will create the first poll for you.

---

### Post by robtotheb on 2006-12-06
Yes I have done all the obvious steps, I followed the install guide. Thanks for telling me where the log was - no errors ](*,) 

The admin side works fine btw

---

### Post by tocleora on 2006-12-06
Ok, I think I might see what the problem is.  in ajax-poller.php you should see this line:

```
$pollerId = 3;	// Id of poller
```

But in createDbTables.php it's creating the record with a pollerId of 1.  So change this line in ajax-poller.php to read this:

```
$pollerId = 1;	// Id of poller
```

And it should work.  But every time you add a new poll you'll have to manually change that pollerId value in ajax-poller.php.  I can provide you with code that pulls the newest pollerID from the table each time but I'm sure someone with more MySQL experience than I have could tell you a better way.  If you want it let me know.

---

### Post by tocleora on 2006-12-06
To clarify, the pollerId entry in ajax-poller.php should be set to the pollerID of the poll you want displayed.  So if you add a new one and it saves to the database with a pollerID of 20 then $pollerId = 20 to display that one.  Hope that makes sense. :)

---

### Post by robtotheb on 2006-12-06
Woo  One step closer - I get the question now but when I vote it just says "Getting poll results. Please wait..." 

But my shared hosting one is working now.
[http://www.salonbrowse.com/robs/ajax-poller.php](http://www.salonbrowse.com/robs/ajax-poller.php)

---

### Post by tocleora on 2006-12-06
Yeah the one at that link worked, GREAT! Are you saying there's a second one you're getting that error with or is your problem fully resolved now?

---

### Post by robtotheb on 2006-12-06
local development (edgy)is still not working. The results are not showing.

Thanks for your help :)

---

### Post by robtotheb on 2006-12-06
Fixed it - I had fiddled with one of the .js files.  Works locally too now.

Thanks again

---

