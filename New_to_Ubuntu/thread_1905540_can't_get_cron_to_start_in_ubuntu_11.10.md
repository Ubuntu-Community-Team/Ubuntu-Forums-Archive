---
title: "can't get cron to start in ubuntu 11.10"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by rickuk on 2012-01-07
I can't get cron to start in ubuntu 11.10. I'm completely new to Ubuntu and really need an idiots guide note to show me what i might be doing wrong.

In the terminal I type:

crontab -e

this gets the nano editor open

I then have entered the following code to start a job at 8.27am every day

27 08 * * * /home/me/AEB/Example_7.1.pl/

cron seems to be running but when i open the system log I get a series of error messages

Jan  7 07:25:59 me-NC10 crontab[2254]: (me) BEGIN EDIT (me)
Jan  7 07:26:28 me-NC10 crontab[2254]: (me) REPLACE (me)
Jan  7 07:26:28 me-NC10 crontab[2254]: (me) END EDIT (me)
Jan  7 07:27:01 me-NC10 cron[2225]: (me) RELOAD (crontabs/me)
Jan  7 07:27:01 me-NC10 CRON[2276]: (me) CMD (/home/me/AEB/Example_7.1.pl/)
Jan  7 07:27:01 me-NC10 CRON[2275]: (CRON) error (grandchild #2276 failed with exit status 127)
Jan  7 07:27:01 me-NC10 CRON[2275]: (CRON) info (No MTA installed, discarding output)

The job never runs and I'm at a loss about how to fix the issue. What steps do I need to do to get cron to start for me? An help would be much appreciated!

---

### Post by kimda on 2012-01-07
You have to remove the "/" after the .pl for it to run properly. And what happens if you run it manually /home/me/AEB/Example_7.1.pl ?

---

### Post by rickuk on 2012-01-07
thanks. i've removed the / and it still doesn't run but the file does run manually

---

### Post by kimda on 2012-01-07
Maybe you can output the errors to stdout. Like this 
27 08 * * * /home/me/AEB/Example_7.1.pl 2> errors 

then read the output and change the script.

---

### Post by Paqman on 2012-01-07
Does it have to run at exactly that time? 

The easiest way to run a cron job daily is to just drop the script into /etc/cron.daily and make sure it's executable. You only need to mess about with crontab if you want really fine-grained control of your cron jobs.

---

### Post by rickuk on 2012-01-07
Thanks. Really appreciated.

The output reads:

/bin/sh: /home/me/AEB/Example_7.1.pl: not found

What should I do? Presume I have direct cron to the right path?

---

### Post by kimda on 2012-01-07
It cannot find the script at that location. You have to enter the correct full path to the script ex. /home/me/scripts/myscript.pl

---

### Post by rickuk on 2012-01-07
thanks for this. the file is executable but i might need more control over the timings i.e. it would have to start at a set time

---

### Post by rickuk on 2012-01-07
Thanks. I did think that I had specified the full file path with /home/me/AEB/Example_7.1.pl so that cron should execute the file at that location?

what does the /bin/sh mean?

---

### Post by kimda on 2012-01-07
/bin/sh is the shell which runs the file. There are different shells available like /bin/bash, /bin/ksh, /bin/zsh.

---

### Post by rickuk on 2012-01-07
FANTASTIC ! You are brilliant. Your quick tip of outputting the errors made me realise that I didn't need the .pl at the end of the file as it was executable. I removed that and it ran perfectly.

---

### Post by kimda on 2012-01-07
Thanks! :D

---

