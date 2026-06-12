---
title: "Running scripts as an &quot;application&quot;"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by devxdev on 2012-06-01
I was wondering if it is possible to convert some of my bash scripts to pseudo applications, I have quite a few on my development machine that run with crontab and incrontab so for the sake of making things that much easier I would like to be able to call things like:

```
$ srsync MY_PARAM
#instead of
$ ./srsync.sh MY_PARAM
```

I've searched around a little and found: [[COLOR="DarkOrange"]How to add a script to command list[/COLOR]]("http://askubuntu.com/questions/53210/how-to-add-a-script-to-command-list")

I checked to see if ~/bin existed but it did not, so created it; Then made sure ~/.profile existed and had the $HOME/bin loop in it.

Now according to that post after I moved all my scripts to ~/bin should be able to just run `$ srsync MY_PARAM`; but this is not the case. When I try to run the script I just get:
`srsync: command not found`.

Any other ideas on how to get this working?

---

### Post by Cheesemill on 2012-06-01
Have you logged out and in again yet?

Also if you are running the scripts from crontab you will still need to supply the entire path as anything run from crontab only has /usr/bin and /sbin in the $PATH environmental variable.

---

### Post by devxdev on 2012-06-01
> **Cheesemill said:**
> Have you logged out and in again yet?

Now I feel like a moron.. that was the only thing I had not done yet (really bad about ever logging out or restarting..)

---

