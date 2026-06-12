---
title: "Permission Denied when running PHP script from terminal"
date: 2009-10-26
forum: Programming Talk
---

### Post by ularlaut on 2009-10-26
Hi all, 

I need help here. I planning to use cron_jobs to execute php script automatically .
But when I try to execute the script from terminal (prompt) to test it, it gives an error messages that says : 

[html]
root@ubuntu-server:~# /var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php
bash: /var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: Permission denied
[/html]I already setup the users account and their permission to read and write, for root and in the cron_jobs folder, which is listed in .htpasswd.

Is there something I missed ?

Thank you very much for the kind assistance anda helps.  ;)

---

### Post by korvirlol on 2009-10-27
did you make the script executable?

post the output of ls -l  on the file

---

### Post by ularlaut on 2009-10-27
Hi korvirlol,

Here are the output from : ls -l

[HTML]
root@ubuntu-server:/var/www/leiloes/www/htdocs/cron_jobs# ls -l
total 264
-rwxrw-rw- 1 root leiloes  3952 2009-10-26 17:07 activation_mail_reminder_cron.php
-rwxrw-rw- 1 root leiloes 10934 2009-08-25 20:19 archiv_cron.php
-rwxrw-rw- 1 root leiloes  3095 2009-04-20 22:01 archive_keywords_cron.php
-rwxrw-rw- 1 root leiloes  3753 2009-01-27 02:35 auction_counter_update_cron.php
-rwxrw-rw- 1 root leiloes 14858 2009-08-17 16:45 coisas_xml_cron.php
-rwxrw-rw- 1 root leiloes   316 2009-08-04 16:32 _cron_bottom.inc.php
-rwxrw-rw- 1 root leiloes  1949 2009-08-04 16:32 _cron_top.inc.php
-rwxrw-rw- 1 root leiloes  6175 2009-03-19 22:56 csv_cron.php
-rwxrw-rw- 1 root leiloes  7241 2009-05-19 22:45 daily_stats_cron.php
-rwxrw-rw- 1 root leiloes  4122 2009-02-16 18:22 data_confirmation_mail_reminder_cron.php
-rwxrw-rw- 1 root leiloes   666 2008-03-26 21:15 gbase_cron.php
-rwxrw-rw- 1 root leiloes 22501 2009-10-26 17:00 generate_static_content.php
-rwxrw-rw- 1 root leiloes   255 2007-07-20 15:50 index.htm
-rwxrw-rw- 1 root leiloes   668 2008-03-26 21:15 invoice_cron.php
-rwxrw-rw- 1 root leiloes 19147 2009-04-28 01:07 _main_cron.php
-rwxrw-rw- 1 root leiloes 19120 2009-08-10 22:51 main_cron.php
-rwxrw-rw- 1 root leiloes   973 2009-02-19 00:26 make_categories_xml.php
-rwxrw-rw- 1 root leiloes  4747 2009-03-04 03:22 make_featured_categories_auctions_cron.php
-rwxrw-rw- 1 root leiloes  5918 2009-04-20 21:13 make_tag_clouds.php
-rwxrw-rw- 1 root leiloes  1457 2008-03-26 21:15 newsletter_cron.php
-rwxrw-rw- 1 root leiloes  8387 2009-06-25 20:07 newsletter_feed_cron.php
-rwxrw-rw- 1 root leiloes  3432 2008-10-13 13:52 optimize_tables_cron.php
-rwxrw-rw- 1 root leiloes 14785 2009-03-17 16:12 option_newsletter_cron.php
-rwxrw-rw- 1 root leiloes  4504 2009-04-20 16:45 ping_user_id_cron.php
-rwxrw-rw- 1 root leiloes  7819 2009-08-24 17:12 related_words_cron.php
-rwxrw-rw- 1 root leiloes 13028 2009-06-17 00:34 shared_ads.php
-rwxrw-rw- 1 root leiloes 10739 2009-03-21 01:48 sitemaps_cron.php
-rwxrw-rw- 1 root leiloes  3217 2009-02-12 03:06 stv_pecas_cron.php
-rwxrw-rw- 1 root leiloes  3694 2009-06-25 18:04 ulogin_archive_cron.php
-rwxrw-rw- 1 root leiloes  7376 2009-07-22 17:56 watch_items_closure_warning.php
root@ubuntu-server:/var/www/leiloes/www/htdocs/cron_jobs# 
 [/HTML]

It appear that that script can not be run independently from terminal, is there any possible way to run the script automatically using web browser ?

Thank you very much for the kind assistance and help.. :)

---

### Post by -grubby on 2009-10-27
Run this

```

chmod +x /var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php

```

---

### Post by korvirlol on 2009-10-27
yea, its not executeable, run the above command ^

---

### Post by ularlaut on 2009-10-29
below are the screen capture..

[html]
root@ubuntu-server:/var/www/leiloes/www/htdocs/cron_jobs# chmod +x /var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php
root@ubuntu-server:/var/www/leiloes/www/htdocs/cron_jobs# ls -l
total 264
-rwxrw-rw- 1 root leiloes  3952 2009-10-26 17:07 activation_mail_reminder_cron.php
-rwxrw-rw- 1 root leiloes 10934 2009-08-25 20:19 archiv_cron.php
-rwxrw-rw- 1 root leiloes  3095 2009-04-20 22:01 archive_keywords_cron.php
-rwxrw-rw- 1 root leiloes  3753 2009-01-27 02:35 auction_counter_update_cron.php
-rwxrw-rw- 1 root leiloes 14858 2009-08-17 16:45 coisas_xml_cron.php
-rwxrw-rw- 1 root leiloes   316 2009-08-04 16:32 _cron_bottom.inc.php
-rwxrw-rw- 1 root leiloes  1949 2009-08-04 16:32 _cron_top.inc.php
-rwxrw-rw- 1 root leiloes  6175 2009-03-19 22:56 csv_cron.php
-rwxrw-rw- 1 root leiloes  7241 2009-05-19 22:45 daily_stats_cron.php
-rwxrw-rw- 1 root leiloes  4122 2009-02-16 18:22 data_confirmation_mail_reminder_cron.php
-rwxrw-rw- 1 root leiloes   666 2008-03-26 21:15 gbase_cron.php
-rwxrwxrwx 1 root leiloes 22501 2009-10-28 17:13 generate_static_content.php
-rwxrw-rw- 1 root leiloes   255 2007-07-20 15:50 index.htm
-rwxrw-rw- 1 root leiloes   668 2008-03-26 21:15 invoice_cron.php
-rwxrw-rw- 1 root leiloes 19147 2009-04-28 01:07 _main_cron.php
-rwxrw-rw- 1 root leiloes 19120 2009-08-10 22:51 main_cron.php
-rwxrw-rw- 1 root leiloes   973 2009-02-19 00:26 make_categories_xml.php
-rwxrw-rw- 1 root leiloes  4747 2009-03-04 03:22 make_featured_categories_auctions_cron.php
-rwxrw-rw- 1 root leiloes  5918 2009-04-20 21:13 make_tag_clouds.php
-rwxrw-rw- 1 root leiloes  1457 2008-03-26 21:15 newsletter_cron.php
-rwxrw-rw- 1 root leiloes  8387 2009-06-25 20:07 newsletter_feed_cron.php
-rwxrw-rw- 1 root leiloes  3432 2008-10-13 13:52 optimize_tables_cron.php
-rwxrw-rw- 1 root leiloes 14785 2009-03-17 16:12 option_newsletter_cron.php
-rwxrw-rw- 1 root leiloes  4504 2009-04-20 16:45 ping_user_id_cron.php
-rwxrw-rw- 1 root leiloes  7819 2009-08-24 17:12 related_words_cron.php
-rwxrw-rw- 1 root leiloes 13028 2009-06-17 00:34 shared_ads.php
-rwxrw-rw- 1 root leiloes 10739 2009-03-21 01:48 sitemaps_cron.php
-rwxrw-rw- 1 root leiloes  3217 2009-02-12 03:06 stv_pecas_cron.php
-rwxrw-rw- 1 root leiloes  3694 2009-06-25 18:04 ulogin_archive_cron.php
-rwxrw-rw- 1 root leiloes  7376 2009-07-22 17:56 watch_items_closure_warning.php
root@ubuntu-server:/var/www/leiloes/www/htdocs/cron_jobs# 
[/html]next I run the /var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php script from terminal, it shows : 

[html]
root@ubuntu-server:~# /var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.ph: No such file or directory
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 2: /////////////////////////////////////////////////////: No such file or directory
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 3: //: is a directory
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 4: //: is a directory
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 5: //: is a directory
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 6: //: is a directory
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 7: /////////////////////////////////////////////////////: No such file or directory
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.ph: No such file or directory
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 9: 04.06.2009: command not found
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 10: 30.03.2009: command not found
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 11: 02.02.2009: command not found
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 12: 30.12.2008: command not found
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.ph: command not found
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.ph: command not found
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.ph: No such file or directory
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php: line 16: syntax error near unexpected token `'../includes/global.php''
/var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.ph': line 16: `require_once ('../includes/global.php');
root@ubuntu-server:~# 
[/html]I know the above result are correct in certain ways, because when I run it in web browser, i act the way I wanted, which is updating the website.

I already setup the cron_jobs for the script which have interval of "everytime and everyday" with asterisk (*)..

However, the result of this cron_jobs is not logged or I can not found the log file for this cron jobs, even under /var/log folder. So I can not know is the cron_jobs running correctly or not.

---

### Post by korvirlol on 2009-10-29
its not running because there are errors in your script, and it is failing. 

So you can put your current: generate_static_content.php in cron and run it on specified intervals, but it wont help you much if it contains errors. 

The php CLI is quite robust, but you cant always think about it with the mentality that "if it runs in the browser it will run on the command line". While this is quite often true, some exceptions exist.

if you need help debugging your script, post it here.

You will know it is working in cron if you get the expected result from running the script locally. If the results of running the script locally are not what you are expecting, then you need to change your script in some way. 

Also, you have to specifically redirect the output of your cron jobs to a file, im pretty sure (could be wrong here) that output from cron isnt recorded without you specifically defining a log file to contain the output.

---

### Post by tom66 on 2009-10-29
bash thinks your script is a shell file. It needs to know how to execute it.

You need to either put #!/usr/bin/php (or another php interpreter) as the top line of your script. It MUST be the top line, before any php or html tags, and there must be nothing else on the same line except whitespace.

Or you can use php to run your script (/usr/bin/php file-name) and then it is unnecessary to make changes.

---

### Post by OpenGuard on 2009-10-29
```
sudo apt-get install php5-cli

```

Further reading: [http://php.net/manual/en/features.commandline.php](http://php.net/manual/en/features.commandline.php)

---

### Post by Reiger on 2009-10-29
An important thing to keep in mind is that the HTTP Server and the Cron job execute the script in different virtual file system environments: you will need to make sure your script is portable enough to work in both environments.

Example of how things would differ: / (root) is typically actually in a chroot jail (i.e. /var/www/ or /srv/www/ or $HOME/public_html/) under the HTTP Server but / or another chroot (i.e. $HOME/) under cron.

This has direct consequences for include paths. Things become a lot murkier if you have a script like this:

./worker.php
```

/* ensures only $scriptName and $scriptArgs are visible to the included script */
function jail($scriptName, $scriptArgs)  {
  return include("jail/$scriptName");
}

function invokeTest() {
  $result = jail("test.php", array('message'=>'Hello $s'));
  echo "Test results: &#8220;{$result}.&#8221;,PHP_EOL;
}

```

./helper.php
```

global $HTTP_USER = "Anonymous";
function getUser() {
  global $HTTP_USER;
  return isset($_ENV['USER']) ? $_ENV['USER'] : $HTTP_USER;
}

```

./jail/test.php
```

$pathToHelper = ''; // what path? .. actually it is: 'helper.php' !  
require_once($pathToHelper);

return str_replace('$', getUser(), $scriptArgs['message']);

```

EDIT: And for portability's sake: you do **not** want to include a shebang at all. If you want to run portions of it both via mod_php (under the HTTP server) and other portions via cron this will in all probability conflict with header() calls. Worse, shebangs are actually fairly system specific, i.e. they represent a portability problem in their own right.

---

### Post by ularlaut on 2009-10-30
Hi all

Thank you very much for the great tips and informations; It helps a lot..  :)

Here are the script for the cron_jobs in /etc/crontab file :

[html]
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
1 * * * * leiloes /usr/bin/php /var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php
1 * * * * root /usr/bin/php /var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php
#
[/html]and below are the script for cron_jobs in the /var/spool/cron/crontabs

[html]
# DO NOT EDIT THIS FILE - edit the master and reinstall.
# (/tmp/crontab.WcY4SI/crontab installed on Tue Oct 27 15:56:46 2009)
# (Cron version -- $Id: crontab.c,v 2.13 1994/01/17 03:20:37 vixie Exp $)
# m h  dom mon dow   command
1 * * * * /usr/bin/php /var/www/leiloes/www/htdocs/cron_jobs/generate_static_content.php
#
[/html]Is possible to set the time and the date all with asterisk (*) ?
So (i think) the cron_jobs will be run everytime and everyday...

Thanks again for the kind assistance and help...  ;)

---

