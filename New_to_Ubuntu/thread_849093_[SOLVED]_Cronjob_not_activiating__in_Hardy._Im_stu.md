---
title: "[SOLVED] Cronjob not activiating  in Hardy. Im stuck :("
date: 2008-07-04
forum: New to Ubuntu
---

### Post by fatality_uk on 2008-07-04
Hi guys. I did a clean install of Hardy, on release day actually, however, I haven't setup any cron jobs since. I tried this morning to run the following cron job

> 45 8 * * * me /home/me/Desktop/test.sh

I did > sudo gedit /etc/crontab to edit the cron file for that job.

Nothing, nada, zip!!! Nothing fired!! I had some jobs setup in fiesty and hardy and I'm pretty sure I did the same thing to get those running!
I set the files permissions to execute.

Any suggestions as to why it's not working? I am positive I have missed something obvious, but not sure what.

Thanks

---

### Post by hyper_ch on 2008-07-04
what is
```

me /path/to/some/script

```
supposed to do? Especially the "me" part?

---

### Post by fatality_uk on 2008-07-04
> **hyper_ch said:**
> what is
```

me /path/to/some/script

```
supposed to do? Especially the "me" part?

me is the user i am setting the job for. I didn't want it to run as root there's no need.

This is a very simple test script which does, nothing really!!!
> /home/me/Desktop/test.sh

```
#!/bin/bash
echo "HELLO WORLD"
```

---

### Post by hyper_ch on 2008-07-04
then add it to your user cron.... if you add it to the root cron the "me" will be root ;)

(1) create a cron.txt with the cronjobs
```

45 8 * * * bash /home/me/Desktop/test.sh 

```

(2) add the cron.txt to your cron
```

crontab cron.txt

```

(3) verify it's added
```

crontab -l

```

---

### Post by fatality_uk on 2008-07-04
> **hyper_ch said:**
> then add it to your user cron.... if you add it to the root cron the "me" will be root ;)

(1) create a cron.txt with the cronjobs
```

45 8 * * * bash /home/me/Desktop/test.sh 

```

(2) add the cron.txt to your cron
```

crontab cron.txt

```

(3) verify it's added
```

crontab -l

```

Thanks for that:) But still didn't work!
```
crontab -l
```confirms it's there, but still not working. :confused::confused:

---

### Post by hyper_ch on 2008-07-04
well, that cronjob will be executed at 08:45 ;)

---

### Post by fatality_uk on 2008-07-04
I changed it to a 9 honest :lol:

---

### Post by hyper_ch on 2008-07-04
and how do you know it did not run?

---

### Post by fatality_uk on 2008-07-04
Thought of that, i.e. bash not opening a new window and so changed the script to:
> #!/bin/bash
mv /home/me/Desktop/test.txt /home/me/Desktop/one/test.txt

To move a dummy file from the desktop into a new directory. Still no joy :(

---

### Post by hyper_ch on 2008-07-04
does your bash script work?

Try something more like this:

```

#!/bin/bash
DATE=/bin/date;
NOW=`$DATE '+%Y-%m'-%d__%H-%M`
touch ~/Desktop/$NOW

```

---

### Post by fatality_uk on 2008-07-04
Yeah running the script from bash moves the file, so at least THAt works :lol:

---

### Post by hyper_ch on 2008-07-04
did you move the file back again? so that the script can run it... well, I have no clue but that should work ;)

what's the output of
```

crontab -l

```?

---

### Post by fatality_uk on 2008-07-04
hyper_ch thanks for all your help mate. I think I have solved the problem. /etc/cron.allow & /etc/cron.allow both exist for some reason with a file I don't know what it is. I have removed them and it works fine now.

The dummy file moves 1 seconds after the time set ;) Perfect. Although it's a second late :lol:

---

