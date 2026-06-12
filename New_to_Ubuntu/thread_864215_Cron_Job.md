---
title: "Cron Job"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Drezard on 2008-07-19
I'm trying to schedule a basic HTTP download thro a cron job. Except I totally lack skills using linux. I got told to download Wget, so I have that but, I still dont know how I would set up the cron job. 

What would be the command to download [www.example.com/example.exe](www.example.com/example.exe) thro HTTP at 3:00am the day after the command was set???

Thanks so so much.

Daniel

---

### Post by Oldsoldier2003 on 2008-07-19
> **Drezard said:**
> I'm trying to schedule a basic HTTP download thro a cron job. Except I totally lack skills using linux. I got told to download Wget, so I have that but, I still dont know how I would set up the cron job. 

What would be the command to download [www.example.com/example.exe](www.example.com/example.exe) thro HTTP at 3:00am the day after the command was set???

Thanks so so much.

Daniel

```
* 3 * * *  DISPLAY=:0. /path/to/command
``` Will run a graphical application at 3am daily on display 0 (normally thats your desktop)

---

### Post by hyper_ch on 2008-07-19
why do you give an example to a gui app if he just wants to wget something?

---

### Post by Oldsoldier2003 on 2008-07-19
> **hyper_ch said:**
> why do you give an example to a gui app if he just wants to wget something?

whoops. I misread and thought he said gwget.
```

* * 3 * * /path/to/command
```

should sort him. (though he may need to redirect errors to /dev/null or run wget in screen- Idk because its not something i've bothered to do in the past)

---

### Post by hyper_ch on 2008-07-19
ah, misread :) can happen (happens also to me)... I was just curious why you gave that other one ;)

so in the example given I would

(1) create a a bash script like wget.sh:
```

#!/bin/bash
cd /path/where/you/want/to/save/that/file/to/
wget http://http://www.example.com/example.exe

```

(2) make it executable
```

chmod 0755 wget.sh

```

(3) make a cron.txt file that contains all the cron jobs (I prefer working on text files like that
```

nano cron.txt

```

(4) add the cron jobs to it:
```

* * 3 * * sh /path/to/wget.sh

```

(5) add cron.txt to the actual cronjob
```

crontab cron.txt

```

(6) check the content of the cronjob
```

crontab -l

```

---

