---
title: "I made a cron job file, how I can make it executed?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-30
Hi
thank you for reading my post
I have some commands in a text file as follow:

```


00 03 * * * deluge
00 07 * * * /sbin/shutdown -P now

```

I know that these are cron job commands, but I can not find out how I can ask cron job daemon or service to pick up this file and tasks and add them to the the system scheduler.

Can you let me know what is next step to schedule this tasks? or add them to the list of tasks that cron job is usually doing?

Thanks

---

### Post by Sukarn on 2008-06-30
Type this command in terminal, it will open your cron file in which you can put your lines
```

crontab -e

```

---

### Post by hyper_ch on 2008-06-30
I don't like to edit crontabs directly, I rather like to work with crontab text files ;)

save those commands in a textfile and then run
```

crontab textfile.txt

```

I normally call it "cron.txt"

and then check if they were added:
```

crontab -l

```

---

### Post by legolas_w on 2008-06-30
Thank you , I used the second way.
I think it gives me more control.

after executing crontab cronjobs.txt can I delete the cronjobs.txt ?

thanks

---

### Post by hyper_ch on 2008-06-30
you can... but I leave it in case I want to add other crons later or modify it... if you delete it and the then just add 1 new cron and run the command again, then it will delete the other two crons also and only add the crons that are in the text file anew.

Hence I would not necessarily delete it.

---

