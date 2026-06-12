---
title: "Learning bash: a few questions"
date: 2008-04-13
forum: Programming Talk
---

### Post by Griff on 2008-04-13
1)
For debugging purposes I have a cron job that I run want to run every 10 minutes.  Is there a shorter way to do that than
```

0,10,20,30,40,50 * * * * *command*

```
2)
I have a directory with tons of junk and want to remove all of the files except my .jpg files.  Is there a way to do this?

3)
I've looked online on bash scripts accepting arguments but they're all the same and kind of confusing.  How do you do this?  Along the same lines, how do you print a message to the prompt if no argument is passed to the script?

4)
I want to list all of the currently running processes, but exclude root.  Can this be done?  It's not just one user I want but all the ones logged on right now otherwise I'd use something like ps -u bob -U bob u.

Sorry I know it's a lot, but I tried to gather my thoughts all at once so I wouldn't have to make more than this one thread.  Thanks for all the help.  It's really fun for me learning this right now.

---

### Post by ghostdog74 on 2008-04-13
> **Griff said:**
> 1)
For debugging purposes I have a cron job that I run want to run every 10 minutes.  Is there a shorter way to do that than
```

0,10,20,30,40,50 * * * * *command*

```

you can try this */10 . Not tested.
> 
2)
I have a directory with tons of junk and want to remove all of the files except my .jpg files.  Is there a way to do this?

```

find /currentpath -type f ! -name "*.jpg" -exec rm {} \;

```
> 
3)
I've looked online on bash scripts accepting arguments but they're all the same and kind of confusing.  How do you do this?  Along the same lines, how do you print a message to the prompt if no argument is passed to the script?

study the bash manual link in my sig. Also look [here]("http://tldp.org/LDP/abs/html/internalvariables.html#ARGLIST")

> 
4)
I want to list all of the currently running processes, but exclude root.  Can this be done?  It's not just one user I want but all the ones logged on right now otherwise I'd use something like ps -u bob -U bob u.

```

ps -eo user,args | awk '!/root|user1/'

```

---

### Post by LaRoza on 2008-04-13
> **Griff said:**
> 1)
For debugging purposes I have a cron job that I run want to run every 10 minutes.  Is there a shorter way to do that than
```

0,10,20,30,40,50 * * * * *command*

```
2)
I have a directory with tons of junk and want to remove all of the files except my .jpg files.  Is there a way to do this?

3)
I've looked online on bash scripts accepting arguments but they're all the same and kind of confusing.  How do you do this?  Along the same lines, how do you print a message to the prompt if no argument is passed to the script?


0. That isn't very long, so why shorten it?

1. Move all the .jpg's else where? And delete directory?

```

$mkdir images
$cd junkdir
$ mv *.jpg ../images/

```

2. $# is the number of arguments, $@ is all of them, $0 is the scripts name, $1 is argument one, $2 argument 2, etc

---

