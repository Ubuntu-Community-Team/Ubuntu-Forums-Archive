---
title: "Questions about CRON"
date: 2011-12-16
forum: Programming Talk
---

### Post by hakermania on 2011-12-16
Ok, here's the plan:

I want to add now and then specific or not cronjobs **through a script*** (when I say 'specific' I mean to specify exactly when and when I say 'or not' I mean that the job may have * values in month or day for example)

***no crontab -e allowed**

What's the right way to do it?
These are the things that I don't feel comfortable with:
** a)** When a 'specific' job is done cron doesn't delete it afterwards, how can this be solved?

**b)** When I want to add a new cronjob I have to check if there are any cronjobs, if they are then write to a temp file the crontab -l output and then append there your new job. Reinstall using 'crontab temp_file', is this quite right?

**c)** What's the right way to remove an 'or not' action? crontab -r removes the last action, so I guess that in order to delete a specific action I have to write somewhere the crontab -l, to edit the file with sed or something and re-install it?


Answering these (first of all) will clean some things out :) Thanks :D
[LEFT]
[/LEFT]

---

### Post by Lars Noodén on 2011-12-16
> **hakermania said:**
> ** a)** When a 'specific' job is done cron doesn't delete it afterwards, how can this be solved?


Wouldn't [at](http://manpages.ubuntu.com/manpages/oneiric/en/man1/at.1.html) be more appropriate for one-offs?

---

### Post by karlson on 2011-12-16
> **hakermania said:**
> 

These are the things that I don't feel comfortable with:
** a)** When a 'specific' job is done cron doesn't delete it afterwards, how can this be solved?


That's what **at** is for.

> 
**b)** When I want to add a new cronjob I have to check if there are any cronjobs, if they are then write to a temp file the crontab -l output and then append there your new job. Reinstall using 'crontab temp_file', is this quite right?


Sounds right

> 
**c)** What's the right way to remove an 'or not' action? crontab -r removes the last action, so I guess that in order to delete a specific action I have to write somewhere the crontab -l, to edit the file with sed or something and re-install it?


I think you really need to take a look at **at**.
```

crontab -r

```
will delete the user's crontab not the last action they specified in it.  If you want ad-hoc scheduling of tasks that users can do **at** is the answer.

---

### Post by hakermania on 2011-12-17
Hello for the suggestions! Just test 'at' and seems to be what I need.
Any idea how to run with at GUI applications? They doesn't seem to run, scripts run perfectly though!

---

### Post by Lars Noodén on 2011-12-18
> **hakermania said:**
> Hello for the suggestions! Just test 'at' and seems to be what I need.
Any idea how to run with at GUI applications? They doesn't seem to run, scripts run perfectly though!

For that you need to have the $DISPLAY [environment variable](https://help.ubuntu.com/community/EnvironmentVariables) set to the appropriate display.  Assuming the default display, the following might work, using firefox as the example.

```

DISPLAY=:0.0 /usr/bin/firefox

```

---

### Post by hakermania on 2011-12-18
> **Lars Noodén said:**
> For that you need to have the $DISPLAY [environment variable]("https://help.ubuntu.com/community/EnvironmentVariables") set to the appropriate display.  Assuming the default display, the following might work, using firefox as the example.

```

DISPLAY=:0.0 /usr/bin/firefox

```

Thanks, I knew that, but when I try it with 'at' it says
```
Cannot open input file DISPLAY=:0.0 /usr/bin/script.sh: No such file or directory
```

---

### Post by Lars Noodén on 2011-12-18
Are you sure it's /usr/bin/script.sh and not /usr/local/bin/script.sh ?

---

### Post by hakermania on 2011-12-18
> **Lars Noodén said:**
> Are you sure it's /usr/bin/script.sh and not /usr/local/bin/script.sh ?

Yes I'm sure that the file DOES exist, it isn't a script either, it was just an example.

When I call a GUI application it doesn't launch (couldn't connect to X server) but when I call it with
```

at -f 'DISPLAY=:0.0 /usr/bin/gui_app' 2am'

```
I get the not found error.

---

### Post by Lars Noodén on 2011-12-18
That because -f file reads the job from a file rather than standard input and you're telling it to look for a file named 'DISPLAY=:0.0'  You can either create a file and use that or try an alternate way of doing the same thing:

```

 echo 'DISPLAY=:0.0 /usr/bin/gui_app' | at 2am 

```

---

### Post by hakermania on 2011-12-18
Thanks a lot :D

---

### Post by Lars Noodén on 2011-12-18
If you just type 'at' by itself it will let you enter the script line by line.  That's another way.

---

### Post by hakermania on 2011-12-18
> **Lars Noodén said:**
> If you just type 'at' by itself it will let you enter the script line by line.  That's another way.

Cron is good because with one entry lets you do the same thing repeatedly, but you cannot modify the entries easily.

At is good because it lets you modify the entries very easily, but it isn't for repetitive things.

Could 'at' do a thing repeatedly?

Also, I realized that if my PC is suspended while 'at' should run something, when I wake up my PC and the time 'at' should run the command has past, the specific job doesn't delete itself or something. I would expect 'at' not only to check if minutes are equal, but also to check if specified time has passed.

Hm.... Main problem was solved though.

---

### Post by Lars Noodén on 2011-12-18
You *could* have [font=Courier New]at[/font] call itself recursively, but that would be foolish IMHO.  For repeating events, [font=Courier New]cron[/font] is the way to go.

As far as what happens to an [font=Courier New]at[/font] job when the computer is powered down, when I tried it [font=Courier New]at[/font] seems to get run at the next possible opportunity.

---

