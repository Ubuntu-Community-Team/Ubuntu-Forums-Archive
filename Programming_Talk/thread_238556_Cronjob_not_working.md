---
title: "Cronjob not working"
date: 2006-08-17
forum: Programming Talk
---

### Post by cosmo1983 on 2006-08-17
I have a file that is suppose to update every minute, placed it in cronjob but the file doesn't get updated every minute. It randomly updates itself right now.

Not sure if there is something wrong with the conrjob code or not.

```

01 * * * *  php /test/somefile.php

```

What exactly am I doing wrong?

---

### Post by scxtt on 2006-08-17
just looking at the example you've given, you're just (essentially) referencing a file (/test/somefile.php), not telling it what to do, as in:

01 * * * * php php /test/somefile.php

where **php /test/somefile.php** will run as the php user ...

as for it randomly updating, that's weird ...

---

### Post by cosmo1983 on 2006-08-17
So, I have to add two php commands before the script?
Like this?

```

01 * * * * php php /test/somefile.php

```

---

### Post by scxtt on 2006-08-17
it's not 2 php commands, anacron allows you to run cronjobs from /etc/crontab (at least) as any user you want (assuming you have root access to edit it) ...

```
1 *     * * *   scxtt   echo `date` >> /home/scxtt/test.txt
```so the 1st php in your case is designating the php user (if there is one) and the second one is saying "run php on /test/somefile.php" ...

but i've never really had luck getting crons to run per minute ...

---

### Post by scxtt on 2006-08-17
looks like the format you want to use is:
[indent]0-59 * * * * php php /test/somefile.php[/indent]
it's working for me in my **echo `date` . . .** example ... also, using vim and color syntax helps a LOT (not w/ the 0-59 thing, but in general crontab format) ...

---

### Post by cosmo1983 on 2006-08-17
Let me give that a shot and I am logged in as root.

---

### Post by cosmo1983 on 2006-08-17
Works like a charm dude. Thanks alot.

---

### Post by true_friend on 2006-08-21
i want to run a script chaning my wallpaper after every 15 minutes. 
what command for me???
currently trying to use
15 * * * * /usr/bin/home/ss/wallpaper/.wallpaper
plz correct mine also.

---

### Post by scxtt on 2006-08-21
you should be able to get away with:

0,15,30,45 * * * * <username> /usr/bin/home/ss/wallpaper/.wallpaper

but it depends on how the wallpaper is "refreshed" ...

---

