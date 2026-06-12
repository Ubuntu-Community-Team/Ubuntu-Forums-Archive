---
title: "Bash users: anyone interested in helping me test out a watcher script?"
date: 2007-09-18
forum: Programming Talk
---

### Post by the_it on 2007-09-18
Script:
[http://rapidshare.com/files/56477998/sauron-07091802.tar.gz.html](http://rapidshare.com/files/56477998/sauron-07091802.tar.gz.html)

I was writing something to help me test out the uptime of my servers while at the same time someone asked me to periodically test out the uptime of something else, and I saw a general case that could unite the two and wrote a dirty little bash script to implement it.

My script, sauron, simply repeatedly executes some user-provided test/s and performs an action upon the test succeeding or failing. The tests can be given a maximum time to live before it is autokilled and assumed to fail. They can also be told to give a "toggling" behavior, that is, they will perform the success script only upon the first change of return status.

My main use case is to have the script email me upon the first time a "ping -c 1 somesite.somewhere" fails so that I can be informed of server downs before some client even hears about it. A second use case would be to write a system log entry whenever a "top -bn1 |head -n 3|tail -n 1|cut -f 2 -d \ |sed 's/%.*//g'" (report the percent cpu usage, does anyone know a shorter line?) goes above a certain percentage so I can have a record of peak usage times without logging everything.

Ordinary users might find some other use for it but I can't think of any at the moment.

To run a simple "is my internet up?" test:
1) unpack the tarball (named sauron)
```
tar zxvf sauron-whatever.tar.gz
cd sauron
```

2) start the scheduler (on one terminal window)
```
./sauron start
```

3) add some test using the following format (on another terminal window)
```
./sauron add 'ping -c 1 [www.google.com](www.google.com)' 'echo its up' 'zenity --error --text "google is down"' 0 1 1
```
where
'ping -c 1 [www.google.com](www.google.com) ' = the test to run
'echo its up' = the command to run on success
'zenity --error --text "google is down"' = command to run on failure
0 = time before we automatically assume google is down and kill test, 0 means we never kill test
1 = turns on toggling
1 = assume that the first test is successful

Expected behavior:
Every 30 seconds, it will ping google.
1st ping works: does nothing
2nd ping works: does nothing
nth ping fails: popup appears saying google is down
(n+m)th ping fails: does nothing
(n+m+p)th ping succeeds: "it works" appears on the terminal window of the watcher

additional use cases appear in the -h option.

complain loudly when the tests dont work as expected
complain loudly to add features
complain loudly when there's an easier way to do this
complain loudly when you want an easier input format for tests
complain loudly when script looks too ugly

---

### Post by apetresc on 2007-09-19
Good job solving a problem :)

For your own use, you may be interested in [Nagios](http://www.nagios.org/), which is essentially a much more sophisticated version of what you have described: a network resource monitoring tool. It's used by a lot of very large companies (with respectively very large networks).

Not that you should be discouraged from writing your own scripts, just pointing this out in case it is useful to you for more heavy-duty stuff.

---

### Post by the_it on 2007-10-17
Well, not like anybody was interested, but I don't have any log of my progress so I might as well post it here.

Anyways, I did some edits here and there and... I actually deployed it somewhere!  If only I can remember what I did since I didnt even think of the script all this time.

This was a deployed version of the script used somewhere.  I needed to tell a client whether their isp was reliable or not, and the simplest way for me to check was to do a simple ping to google and log whenever it's up or down.  By having a written record of when internet is down, I can tell the client "hey, whatever your problem is, it's not my system."

So there.  I've used nagios before, but it's too clunky for my purposes.  I just need one or two tests to run, not some framework with all that stuff.  (apologies to the guys who made it, I really didn't look into it that deeply).

I think I'd better put stuff in /var/spool/sauron instead of /var/sauron, but it was kinda rushed and all.

[http://rapidshare.com/files/63206814/sauron-07100800.tar.gz.html](http://rapidshare.com/files/63206814/sauron-07100800.tar.gz.html)

---

