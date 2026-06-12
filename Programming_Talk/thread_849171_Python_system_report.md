---
title: "Python system report"
date: 2008-07-04
forum: Programming Talk
---

### Post by drubin on 2008-07-04
Hi guys,

I have justed starting python because of it's versatility. 

I have been searching for some python scripts/modules that allow me to get information about my computer/server. load average,  disk usage... and what ever else I can get.Would like to do this in python if possible to increase my knowledge.

The problem is I can't seem to find any modules that do this I do not want to use system level commands ie executing  `df -h` and then parsing this result is there another way?

Reason for this is I would like it to be put on a cron job and mail me the result just to keep tabs on things. The cron job and the mailing seems to be pretty easy..

Any help/suggestions on where to look. the sys/os modules seem to  be lacking in this department.

Thanks.

---

### Post by Zugzwang on 2008-07-04
It seems like you can obtain the load average by using "os.getloadavg()". As far as the rest is concerned - Since Python is cross-platform and you are asking for platform-dependent information, support might be quite limited. 

Apart from running command line programs, you can also access the information stored under the "/proc" directory in Linux.

---

### Post by drubin on 2008-07-04
> It seems like you can obtain the load average by using "os.getloadavg()". As far as the rest is concerned - Since Python is cross-platform and you are asking for platform-dependent information, support might be quite limited.


Ye I knew about the loadavg(), I was kinda hoping there was more info you could get. Might just have to write it in bash then.

Thanks @Zugzwang. If any one else has any other suggestions it would be great.

---

### Post by ghostdog74 on 2008-07-04
Python is nowhere as versatile when it comes to getting system information than the shell. tools are already provided in your system that you can use. df, uptime, vmstat, iostat, lspci, hwinfo, etc. 
If you really want to do it in Python, you can checkout cheeseshop and see if you can find anything.

---

### Post by drubin on 2008-07-04
> Python is nowhere as versatile when it comes to getting system information than the shell. tools are already provided in your system that you can use. df, uptime, vmstat, iostat, lspci, hwinfo, etc.

Ye worked that out now... I was only using it as an excuse to beef up my python skills.. 

My python is > then my bash as well.

And wanted to do some computing on the results on the info. ie if the disk usage is over 85% email the report, if the avg load on the box is too high email... guess we can merge bash and python :)

---

### Post by days_of_ruin on 2008-07-04
You can still do it in python:
```
import commands
a = commands.getoutput("uptime")
print a

```

---

### Post by drubin on 2008-07-04
Ye that is what i mean't by mixing bash and python :)

or the other way round.... bash calling python.

Cool PF pic hey. python guru?

---

### Post by ghostdog74 on 2008-07-04
> **rubinboy said:**
> 
 guess we can merge bash and python :)
try not to do that, whether its bash or python or any others, unless absolutely necessary. anyway, a snippet of what you want to do.
```

df -k | awk '$5+0>85{ cmd="mail -s \047"$1" more than 85%\047 root"; system(cmd) }'

```
the same with load average
```

uptime | awk '$NF>2{ #send mail }'

```

---

### Post by drubin on 2008-07-04
> df -k | awk '$5+0>85{ cmd="mail -s \047"$1" more than 85%\047 root"; system(cmd) }'


```

df: `/home/drubin/.gvfs': Transport endpoint is not connected
/bin/sh: mail: not found
```

Thanks this is the first time I have seen the | into awk solves so many simple issues of why I wanted to use python in the first place!

Could you also point me to what \047 is?

ps Just to make sure that mail account is more then likely because I do not have a mail server running on my local machine right?

---

### Post by ghostdog74 on 2008-07-04
> **rubinboy said:**
> ```

df: `/home/drubin/.gvfs': Transport endpoint is not connected
/bin/sh: mail: not found
```

Thanks this is the first time I have seen the | into awk solves so many simple issues of why I wanted to use python in the first place!

awk is a programming language. Its not just for simple one liners which i always see people doing. It doesn't have modules like what other languages have, but it can call system commands ( which are also "modules" if you know and understand what i mean)
> 
Could you also point me to what \047 is?

\047 is the single quote. I don't like putting too much quotes so i use \047 to distinguish. A habit of mine only. you can look at the ascii table to see many more.

> 
ps Just to make sure that mail account is more then likely because I do not have a mail server running on my local machine right?


mail is a tool that i have in my system. on yours you might want to try mailx. Don't know the command's name ?? try man -k mail.

---

### Post by pmasiar on 2008-07-05
> **rubinboy said:**
> I have been searching for some python scripts/modules that allow me to get information about my computer/server. load average,  disk usage... and what ever else I can get.

Python tries to be platform-independent, so of course does not dig as deep into the platform as native tools.

Maybe better idea will be to use native tools (after os module did not gained needed depth), and parse output in Python for some kind of dashboard overview.

---

### Post by drubin on 2008-07-05
> **ghostdog74 said:**
> awk is a programming language. Its not just for simple one liners which i always see people doing. It doesn't have modules like what other languages have, but it can call system commands ( which are also "modules" if you know and understand what i mean)

Ye exactly.. Still not 100% sure why you said don't mix programming languages and then this is exactly what we are doing ?

> **ghostdog74 said:**
> 
\047 is the single quote. I don't like putting too much quotes so i use \047 to distinguish. A habit of mine only. you can look at the ascii table to see many more.
Ye I have a few of those types of things as well... 

> **ghostdog74 said:**
> 
mail is a tool that i have in my system. on yours you might want to try mailx. Don't know the command's name ?? try man -k mail.
[/QUOTE]
No worries I will sort something out for sending mails/reports. The hardest issues was parsing the result of the outputted command.

Thanks again.

---

