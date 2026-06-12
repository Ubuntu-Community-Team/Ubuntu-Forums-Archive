---
title: "[SOLVED] PHP vs php-cli"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by batfastad on 2008-11-27
Hi everyone

Just got a quick question.
I've just started messing around with administering apache2 and php5 on Linux, and I was looking to set up some cron jobs to perform various backup functions and update various MySQL databases.

I've been developing with PHP for a few years, but I've never used PHP from the command line.
I've installed PHP, and also the php-cli package.

Why is there a different package for command line operation?
Can you not just use the regular binary for running scripts through the command line?

Cheers, B

---

### Post by jgoguen on 2008-11-27
php5-cli provides the php binary that you can use for command-line tasks, running PHP scripts in cron jobs, etc.  The one I think you're thinking of as the regular binary is provided by php5-cgi, and is used by Apache and other servers.  I don't know if you could just use the CGI binary, but php5-cli (the binary is /usr/bin/php5) is probably what you want to be using for PHP scripts through cron jobs.

---

### Post by batfastad on 2008-11-28
Ok cool. That's what I figured so I went ahead and installed it.
On windows I had always just been using the php.exe which comes with the win binary package.

Thanks for the info
Cheers, B

---

### Post by jgoguen on 2008-11-28
Glad to hear it's all sorted out for you :)

Could you mark the thread as solved?  Just above your first post is a link that says "Thread Tools", when you click it a menu appears.  One of the entries there is to mark the thread as solved.  This will let other people know that your problem was solved and they may find an answer in this thread.

---

### Post by batfastad on 2008-11-29
Ah yes. Sorry, I normally do that but forgot this time. Thanks, B

---

### Post by batfastad on 2009-01-07
Hi everyone
Sorry to resurrect my previous thread, but I've finally got round to writing a command line script.

If I run a PHP script from the command line using: php scriptname.php
Will that automatically use the binary from the php-cli package?

Thanks, B

---

### Post by hyper_ch on 2009-01-07
normally apache uses the php5 mod and not the cgi.

---

### Post by jgoguen on 2009-01-07
> **batfastad said:**
> Hi everyone
Sorry to resurrect my previous thread, but I've finally got round to writing a command line script.

If I run a PHP script from the command line using: php scriptname.php
Will that automatically use the binary from the php-cli package?

Thanks, B
Yes, /usr/bin/php is from the php-cli package.  So if you write a script and use, from the command line, 'php script.php' you will use PHP from php-cli.  If you're using the script in Apache though, hyper_ch is right, Apache will use use mod_php instead.

---

### Post by batfastad on 2009-01-07
Ok that's what I wanted to know.
After installing the php-cli package, I wasn't sure if I would manually have to change which binary was used when I type php script.php in a shell command.

Thanks again!
Cheers, B

---

