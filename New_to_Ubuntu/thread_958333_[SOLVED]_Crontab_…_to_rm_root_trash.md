---
title: "[SOLVED] Crontab … to rm root trash"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by expatCM on 2008-10-25
What I want to do is to delete my root trash every 14 days at 06:30 hrs as  a cron event.  I have had a look at man crontab to try and find out the details but it does not seem to give me all I need to know.

I have looked at /etc/crontab and find that the following headings / syntax exist

# m h dom mon dow user	command

m and h I guess are minutes and hours.  Dom, mon, dow are a total mystery.  Does anyone know what they mean?

So to clear the trash I am proposing to use 

30 06  dom mon dow  root  rm -fr /root/.local/share/Trash/*

but I need to edit this to support every 14 days.

Could anyone please tell me what is the missing bit ….........

---

### Post by sdennie on 2008-10-25
dom - Day of month
mon - Month
dow - Day of week

crontab actually has two man pages.  One in section 1 and one in section 5.  To get the information you want, you'll need the one in section 5:

```

man -s 5 crontab

```

The easiest way to setup your crontab would be to do it the 1st and 15th of every month.  Something like this to do it at 6:30am:

```

30 6 1,15 * * whatever_command_you_want_to_run

```

---

### Post by expatCM on 2008-10-26
Well that really is obvious when you state it out so clearly.  Thanks for your help.

I had not realized that there was a second man page.  I have now taken a look and of course it is exactly the information I need .....

---

