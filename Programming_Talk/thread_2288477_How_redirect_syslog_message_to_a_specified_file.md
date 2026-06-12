---
title: "How redirect syslog message to a specified file?"
date: 2015-07-27
forum: Programming Talk
---

### Post by mfvpcrec on 2015-07-27
[COLOR=#000000][FONT=verdana]Hi [/FONT][/COLOR];)[COLOR=#000000][FONT=verdana]!  I have a question about syslog.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I want redirect the messages of log to a particular file[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]but i don't know how to do that or i don't get the results[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]that I expect.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]My program is something like this:
[/FONT][/COLOR]
```
#include <stdio.h>
#include <stdlib.h>
#include <syslog.h>


int main (void)
{
    openlog("Test",LOG_PID,LOG_USER);
    syslog(LOG_INFO,"LOG!!");
    closelog();
}

```[COLOR=#000000][FONT=verdana]

[/FONT][/COLOR][COLOR=#000000][FONT=verdana]And 50-default.conf is configured....

[/FONT][/COLOR]```

if $programname=='Test' then /home/me/var.log[COLOR=#000000][FONT=verdana]
[/FONT][/COLOR]
```

But after restart rsyslogd and  run the program var.log is empty:shock:

[FONT=verdana][COLOR=#000000]What is wrong with my code??
[/COLOR][/FONT]
[COLOR=#000000][FONT=verdana]Thank you for read my message![/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-07-27
I don't know how to do this from inside a program, but you need to use a FACILITY.  Choose one of LOCAL0 TO LOCAL7 as the destination for the messages, then direct the corresponding facility to a file.  Use /etc/rsyslog.d/50-default.conf as the template.

---

### Post by mfvpcrec on 2015-07-28
Ok SeijiSensei , i'm going to investigate about FACILITY

Thank you very much!

---

### Post by mfvpcrec on 2015-07-28
Ok it works , i just needed read more carefully the man pages ... but after try several times i realized that the files ONLY are saved in /var/log an that was a painfull learning because I always worked with  a log file in my home.
Also was very usefull this page [http://www.linuxjournal.com/article/5476?page=0,0](http://www.linuxjournal.com/article/5476?page=0,0)  that explains syslog . The first two pages were enough for me.
I could put in the tiltle [SOLVED] ?  Do you think?

Thank you for all!

---

### Post by SeijiSensei on 2015-07-28
I think if you wrote to a facility, LOCAL4 let's say, you could create an entry in /etc/rsyslog.d/50-default.conf that redirects output on LOCAL4 to a file in your home directory.
```
local4.*              /home/me/mylog
```

If you've answered your questions, then, yes, marked it as solved.

---

### Post by mfvpcrec on 2015-07-28
Ok for me it was solved.! :)
Thank you!

---

