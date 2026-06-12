---
title: "Shell script that emails, twice?"
date: 2010-10-27
forum: Programming Talk
---

### Post by CrusaderAD on 2010-10-27
I've got kind of a strange situation here. I created a shell script that pulls an ftp file and then e-mails me that it completes. When I run the script by itself from the command line, I get the e-mail just fine, exactly as I wrote it. When I run it via cron script, I get two e-mails, one like I wrote it, and one from the Cron Daemon telling me this:

> Local directory now /home/user/ftp

Any idea why I would get this extra email?

---

### Post by DaithiF on 2010-10-27
By default cron is set up to mail you the output of your cron jobs.  Presumably at some point in your script you echo out the directory, and so thats what you get in your mail from cron.  Put 
```
MAILTO=""

```at the top of your crontab if you want to suppress this behaviour.

---

### Post by CrusaderAD on 2010-10-27
Thanks for the tip. I have my crons put together using webmin. I'd rather not mess with them in nano or vi, is there a way to change this default setting?

---

### Post by DaithiF on 2010-10-27
> **CerealCypher said:**
> Thanks for the tip. I have my crons put together using webmin. I'd rather not mess with them in nano or vi, is there a way to change this default setting?
Only by setting the MAILTO in the crontab file.  Sorry I have no experience with webmin so I don't know how it deals with cron, but its really not hard to just do crontab -e and add the line.

---

### Post by CrusaderAD on 2010-10-28
I took your advice and added the line. Do you know if this will effect other mailing functions in the cron? Within a few cron commands I have a mail command with the address and everything in the command. Will the MAILTO="" alteration have an effect on this?

---

### Post by CrusaderAD on 2010-10-28
Just ran a test script, the MAILTO="" line doesn't seem to effect other mailing functions in the cron. Sweet.

---

### Post by CrusaderAD on 2010-11-01
Just a quick update. If you use Webmin on your server, you can go to Cron Jobs and do a "Create a new environment variable." and set the variable to MAILTO. This should resolve it. If you do as I did and just add it to the cron file manually, it will show up in the list within webmin, so either way works.

---

