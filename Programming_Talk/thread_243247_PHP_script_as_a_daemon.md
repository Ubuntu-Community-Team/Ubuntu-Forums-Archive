---
title: "PHP script as a daemon"
date: 2006-08-24
forum: Programming Talk
---

### Post by atrophic on 2006-08-24
Googling and searching the forums hasn't helped me here so I turn to the forum community.

I need to run an infinitely looping php script as a daemon.  The script is an engine for a web-based game and does a bunch of checks for each iteration.  Some checks need to be ran every 3 seconds, others much less frequently.  Cron doesn't suffice as most tasks are more frequent than a minute.

I need some way of running the script as a daemon so it can be started, stopped, restarted, etc.  I don't know enough about init.d to add it there, or even to know if that's possible.

On Windows I ran it as a service with srvany, and that worked wonderfully.  I've completely migrated to ubuntu though and need some way of keeping this functionality.

I'm not looking for an alternate solution unless it's a really good one, and any solution requiring a change of coding language won't work.  I'm really hoping I can get it to work similarly to the way it was on xp.

Any ideas?

---

### Post by LordHunter317 on 2006-08-25
It's fairly easy to daemonize PHP.  Just follow the instructions for the daemon() function (in C).  If you can't manage that, I'll post some PHP code that emulates it.  But then all you have to do is start your program.

---

### Post by Miademora on 2006-09-03
Easiest way would be to run it inside "screen". Or just start it from commandline ```
/usr/bin/php script.php &
```

You can use builtin shutdownfunctions to stop it smooth or just kill it the hard way.

---

### Post by atrophic on 2006-09-04
I've looked at the daemon() function a bit, but not enough to figure out how to get it to run the php code.  A C wrapper would be fine, but I don't want to have to recode the thing in php.

I'm aware of how to run it as a background process (as that's what I'm doing so far), but I still have to start that up manually (or add it to a session startup, etc) which is less than ideal.  I'd like it as a daemon so that it can be programatically stopped/started/restarted, and so that it starts with the system.

---

### Post by LordHunter317 on 2006-09-05
Dude, you're going to have to implement daemon() in PHP, or use an existing PHP library that has it (there are a few AFAIK).  The manpage should tell you how to do it and it's like 6 lines of calls.

---

### Post by swan on 2008-03-31
[http://dev.pedemont.com/sonic/](http://dev.pedemont.com/sonic/)

---

### Post by atrophic on 2008-04-14
Thank you for reviving a 1.5+ year old thread ;)

Sonic is an interesting solution, but needs to run in the background itself.  So if I were to use Sonic the question would be how to I get a shell script to behave as a daemon (e.g. through init.d or something).

That said, I no longer need the answer to this, but if anybody has one feel free to post it for the benefit of anybody googling...

---

### Post by swan on 2008-05-06
sorry, i took it as a developer asking a coding question, sonic was just an example

but sonic does have pfork ability for www/scripts, but yeh i see now what your asking

---

### Post by kevmaster on 2008-09-05
Still alpha, but if you want to create a daemon in PHP, consider using [System_Daemon]("http://pear.php.net/package/System_Daemon")

Install like this:
```

aptitude -y update
aptitude -y install php-pear
pear install -f system_daemon

```

Use like this:
[PHP]
require_once "System/Daemon.php";
// Bare minimum setup
System_Daemon::setOption("appName", "simple");
System_Daemon::setOption("authorEmail", "kevin@example.com");

// Spawn Deamon!
System_Daemon::start();

// Your PHP Here!
while (true) {
    doTask();
}

// Stop daemon!
System_Daemon::stop();
[/PHP]

---

### Post by KevBurnsJr on 2010-11-06
BUMP to say KevMaster's library has come a long way in 2 years
[http://kevin.vanzonneveld.net/techblog/article/create_daemons_in_php/](http://kevin.vanzonneveld.net/techblog/article/create_daemons_in_php/)

---

