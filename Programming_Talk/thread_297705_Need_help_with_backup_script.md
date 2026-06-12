---
title: "Need help with backup script"
date: 2006-11-11
forum: Programming Talk
---

### Post by KhaaL on 2006-11-11
Hey all, I'm making a simple backup script, but I help with a little thing. the code is basically:
[INDENT]tar cvpzf backup.tgz blahblahblah[/INDENT]

...and i want backup.tgz to be named backup[todays date].tgz. how do I do this? 

thanks!

---

### Post by llonesmiz on 2006-11-11
You could try:

tar cvpzf backup-`date +%D`.tgz blahblahblah

the backticks (`) mean: evaluate what's inside. date +%D gives you the date as "month/day/year". If you want another arrangement you should look "date --help" or man date.

---

### Post by KhaaL on 2006-11-11
excellent, many thanks! :)

---

### Post by slavik on 2006-11-13
I would think it would be $(date)

---

### Post by shining on 2006-11-13
> **slavik said:**
> I would think it would be $(date)

[http://tldp.org/LDP/abs/html/commandsub.html](http://tldp.org/LDP/abs/html/commandsub.html)

Apparently, both works, but it seems that $( ) is possibly better than ` `.
In this case, I don't think it matters.

---

