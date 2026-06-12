---
title: "More Info on cron.d?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by klenwell on 2008-10-21
I like the idea of using cron.d to set up cron tasks.  And this is how we're required to do it with Debian at work.  But I haven't been able to find a real thorough guide on its usage.

I've succeeded in setting up cron tasks with cron.d on Ubuntu at home by doing the following:

1. Create cron file (~/cron/test.cron):

```
# cron.d file
# to activate, link to /etc/cron.d: sudo ln -s [path/]fname.cron /etc/cron.d/link_name

# +---------------- minute (0 - 59)
# |  +------------- hour (0 - 23)
# |  |  +---------- day of month (1 - 31)
# |  |  |  +------- month (1 - 12)
# |  |  |  |  +---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# M  H DM MO DW     USER        SCRIPT
* * * * *       klenwell      touch /tmp/klenwell_test_cron
```

2. Make root owner of file:
```
$ sudo chown root:root ~/cron/test.cron
```

3. Link file to /etc/cron.d:
```
$ sudo ln -s ~/cron/test.cron /etc/cron.d/test_cron
```

This, and only this, works for me.  Can anyone help with these questions:

1. Do files linked to /etc/cron.d have to be owned by root?  My tests indicate that this is so, but I haven't seen this stated explicitly anywhere like the cron man file.

2. Is there a command to check that files linked to /etc/cron.d are running correctly -- something like, say, apache's syntax check for config files?  The only way I have been able to test cron files is to set them to run every minute then check the system log output?

Thanks,
Tom

---

### Post by jpkotta on 2008-10-21
Have you tried crontab?  It is made for regular user accounts that need cron.  It works for root too.

```
EDITOR="nano -w" # 'cause vi is weird
crontab -e
```
```
crontab -l
```

If it is something that just needs to run periodically, with root privileges, but not at a definite time (e.g. I want to index my filesystem everyday, but I don't really care when), then I just put scripts into /etc/cron.{hourly,daily,weekly,monthly}.

I've always just debugged cronjobs by trial and error, set it them to execute very often as you describe, until I'm satisfied that they work.  The beauty of the /etc/cron.*period* directories is that they're just plain scripts, and can be tested like any other script.

---

### Post by greg@localhost on 2008-10-21
Add the following to your ~/.bash_profile, ~/.bash_login or  ~/.profile - whichever you have - they will be looked up in that order, to specify a editor to open crontab file - i'm beginning to prefer nano ;)

```
export EDITOR=vi ;
```


**Common crontab commands:**

Edit your crontab file, or create one if it doesn't already exist.
```
crontab -e   
```  


Display your crontab file.
```
crontab -l 
```

Remove your crontab file.
```
crontab -r
``` 

Display the last time you edited your crontab file. (This option is only available on a few systems.)
```
crontab -v 
```

---

### Post by klenwell on 2008-10-21
Yes, I've used crontab extensively and its usage is pretty well documented.  It's cron.d that's more of a mystery.  A couple things I like about crontab:

1. You can schedule tasks as a regular user.
2. It lets you know upon saving when you make a mistake editing the crontab file.

Still, I like the modularity of cron.d.  It's handy for developing applications.

---

