---
title: "crontab problems"
date: 2009-10-31
forum: Programming Talk
---

### Post by mvalviar on 2009-10-31
Hi! I'm trying to run a php script that accesses files that are relative to the location of the script. When I run it manually it runs fine. But when cron runs it the script yells with can't find file.

I've already read that its something about cron not setting up the environment

I tried ```

MAILTO=me
PWD=/home/me/path/to/script
* * * * * $HOME/path/to/script/myscript.php
```

but it doesn't work.

---

### Post by Sporkman on 2009-10-31
> **mvalviar said:**
> Hi! I'm trying to run a php script that accesses files that are relative to the location of the script. When I run it manually it runs fine. But when cron runs it the script yells with can't find file.

I've already read that its something about cron not setting up the environment

I tried ```

MAILTO=me
PWD=/home/me/path/to/script
* * * * * $HOME/path/to/script/myscript.php
```

but it doesn't work.

Not sure, but you might need to explicitly set the entire absolute path, instead of assuming that HOME is set.

---

### Post by mvalviar on 2009-11-01
I already tried that before. Even specifiying the absolute path to doesnt' seem to help.

---

### Post by Sporkman on 2009-11-01
> **mvalviar said:**
> I already tried that before. Even specifiying the absolute path to doesnt' seem to help.

A couple of other things: I'm not sure that defining those other variables is the right thing to do in terms of what should be in a crontab script - i.e. it's not a regular shell script.

Also: You have '*' for every interval parameter, so that says you want it to run every minute, is that correct?

Here's a crontab tutorial:

[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

---

