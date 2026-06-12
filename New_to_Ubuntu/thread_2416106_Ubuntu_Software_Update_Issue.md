---
title: "Ubuntu Software Update Issue"
date: 2019-04-05
forum: New to Ubuntu
---

### Post by pradyumna108 on 2019-04-05
**[Error while updating software Ubuntu 18.04 LTS]("https://askubuntu.com/questions/1132333/error-while-updating-software-ubuntu-18-04-lts")**

I have posted this same issue in [https://askubuntu.com/questions/1132333/error-while-updating-software-ubuntu-18-04-lts](https://askubuntu.com/questions/1132333/error-while-updating-software-ubuntu-18-04-lts)


```
[  1201.873] _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
[  1201.873] _XSERVTransMakeAllCOTSServerListeners: server already running
[  1201.874] (EE) 
Fatal server error:
[  1201.874] (EE) Cannot establish any listening sockets - Make sure an X server isn't already running(EE) 
[  1201.874] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  1201.874] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  1201.874] (EE) 
[  1201.874] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by Rubi1200 on 2019-04-05
Hi and welcome to the forums :-)

Did you check the log?

> [COLOR=#000000]"/var/log/Xorg.0.log"[/COLOR]

Perhaps post the output of the log here for further analysis.

---

### Post by DuckHook on 2019-04-05
@ pradyumna108

&#8230;please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by pradyumna108 on 2019-04-09
Yes Sir. I have checked it. The log is also the same. 
-------------------Log---------------
[   197.261] _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
[   197.261] _XSERVTransMakeAllCOTSServerListeners: server already running
[   197.261] (EE) 
Fatal server error:
[   197.261] (EE) Cannot establish any listening sockets - Make sure an X server isn't already running(EE) 
[   197.261] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   197.261] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   197.261] (EE) 
[   197.261] (EE) Server terminated with error (1). Closing log file.

---

### Post by Rubi1200 on 2019-04-09
Let's check if XServer is running:

```
ps -C Xorg
```

I would also check here for answers [https://www.x.org/wiki/](https://www.x.org/wiki/)

---

### Post by pradyumna108 on 2019-04-11
Hi I have posted the same issue in below thread
[https://askubuntu.com/questions/1132333/error-while-updating-software-ubuntu-18-04-lts](https://askubuntu.com/questions/1132333/error-while-updating-software-ubuntu-18-04-lts)

---

### Post by pradyumna108 on 2019-04-11
ps -C Xorg

PID TTY          TIME CMD
1003 tty1     00:03:58 Xorg

---

### Post by pradyumna108 on 2019-04-16
I am stuck with this problem for too long. Can any one please help me

---

### Post by jdeca57 on 2019-04-16
Well, looking at the post in askubuntu there are two issues: there is a locale setting that gives a lot of warnings so please address that issue first like in [https://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue]("https://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue") and then there is the issue of X server already running. That may or not be a result of the first problem.

---

### Post by Rubi1200 on 2019-04-16
I would go with jdeca57 on this one. Try and sort out the locale issues. If that fixes the other issue, great. If not, post back here so we can try and help further.

---

### Post by pradyumna108 on 2019-04-19
**@**Jdeca57 : As you suggested I have checked the link *[https://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue](https://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue)*   and made those changes. 

But I am still getting this XORG issue. I am unable to install or update any thing on my system.   

I am using a dual monitor system, is it someway linked with XORG issue. 

$ locale 
******* Out Put **************************
LANG=en_IN
LANGUAGE=en_IN:en
LC_CTYPE="en_IN"
LC_NUMERIC="en_IN"
LC_TIME="en_IN"
LC_COLLATE="en_IN"
LC_MONETARY="en_IN"
LC_MESSAGES="en_IN"
LC_PAPER="en_IN"
LC_NAME="en_IN"
LC_ADDRESS="en_IN"
LC_TELEPHONE="en_IN"
LC_MEASUREMENT="en_IN"
LC_IDENTIFICATION="en_IN"
LC_ALL=en_IN

---

