---
title: "DO NOT eliminate leading zero in Bash"
date: 2017-12-24
forum: Programming Talk
---

### Post by dskdimon on 2017-12-24
Hi,

I am using bash and DO NOT need to eliminate the leading zero in the current time: $(date \+\%F-\%k-\%M). I'm using it in crontab in cp (copy) command: 0 * * * * root cp /home/1.txt /home/$(date \+\%F-\%k-\%M).txt
It works fine but in midnight till 10AM the files does not coping (creating) and from 10AM till 23PM all works fine again.
For example, in 23PM it creates YYYY-MM-DD-23-00, and I need it to give me 'YYYY-MM-DD-00-00.txt' in the midnight, but there is no files till 10AM.

Can anyone please help?

Thanks!!!

---

### Post by SeijiSensei on 2017-12-24
Use %H rather than %k.  See "man date" for details.

```
$ date +%F-%H-%M
2017-12-24-00-54

```

Notice that I didn't need to escape the + or the % with a backslash.

---

### Post by dskdimon on 2017-12-24
> **SeijiSensei said:**
> Use %H rather than %k.  See "man date" for details.

```
$ date +%F-%H-%M
2017-12-24-00-54

```

Notice that I didn't need to escape the + or the % with a backslash.

In case with 'date' command in the command line in terminal you are right, but check 'date' in crontab!! You'll see what happens))
P.S. Sorry for my bad english ))

---

### Post by SeijiSensei on 2017-12-25
I suspect you can embed the string in single quotes and avoid the escapes.

```
date '+%F-%H-%M'
```

Did using %H fix your problem?

---

### Post by dskdimon on 2017-12-25
> **SeijiSensei said:**
> I suspect you can embed the string in single quotes and avoid the escapes.

```
date '+%F-%H-%M'
```

Did using %H fix your problem?

No, %H didn't fix my problem! 

$(date \+\%F-\%0k-\%0M) fix my problem !! ))  man date helped me))

SeijiSensei, thanck you very much for your help.

---

