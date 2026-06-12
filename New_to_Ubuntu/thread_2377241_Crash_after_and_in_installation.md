---
title: "Crash after and in installation"
date: 2017-11-10
forum: New to Ubuntu
---

### Post by shout2341242342 on 2017-11-10
Hi! Yesterday, I installed Ubuntu 17.10 2 times. 
First time:
I wanted to install google chrome. While installation system crashed.
Wanted to open steam - I couldn't 
Wanted to install team speak version 3 - system crashed
It all happened in may be 10 minutes after system installation

after 4 hours break (I had to make me calm after 3 crashes) I decided to download new ISO and reinstall 

second time:
I wanted to install google chrome - installation time went good. When first time I've opened system crashed.
So i've restarted my computer and opened google chrome again. It's opened. 
I've downloaded steam - it's downloaded. System crashed when I tried to open it, though.

1.HW
CPU: i5 7600k
mother : z270 toma hawk (standrard)
RAM: 2x8 GB corsair 3000MHz ddr4
GPU: GTX 650 Ti
SSD Adata 240GB
HDD Toshiba p300 1TB
2. After installation I've updated everything by system program (I don't know how in English version it's called)
3. I didn't install any drives by myself 
4. I didn't make any other customizations before trying to install those apps.
5. I didn't get any error messages. Just system crashed, stopped and nothing could do except restart.
6. I've installed google chrome and steam I installed from their web, team speak version 3 have downloaded from team speak version 3 page and followed the tutorial [https://www.youtube.com/watch?v=KPEHLEozePY](https://www.youtube.com/watch?v=KPEHLEozePY)

---

### Post by DuckHook on 2017-11-10
Perhaps it would be useful to read the link in my sig: How to Ask for Help

It is impossible to help if you don't provide appropriate info, like:

[LIST=1]
[*]What HW do you have? We need full system specs and as much detail as possible. If you can post the info from the queries and commands referenced in my link, even better.
[*]Did you do the usual update/full-upgrade routine immediately after you first installed the system?
[*]Are you using the default open-source video drivers?
[*]Any other customizations made after installing but before trying to install those apps?
[*]What error messages did you get during the crash? We need either the error messages themselves or as close as memory allows.
[*]Chrome, ts3 and steam are not in the repos. Well, steam is, but I strongly suspect you did not use the repo version. How did you install them? What instructions did you follow? Give us the step-by-step breakdown. Also, please don't assume that Linux-heads automatically understand acronyms for apps that are primarily from the Windows world like "ts3". Kindly take the time to say Teamspeak version 3.
[/LIST]
Like all requests for help, put yourself in the shoes of those you are asking for help from. If you can't read their minds, then they are unlikely to be able to read yours either.

---

### Post by shout2341242342 on 2017-11-11
Done!

---

### Post by DuckHook on 2017-11-12
You say that the system crashed. Could you get to a console with <Ctrl>+<Alt>+<F1>?

Please post back to thread results of:```
cat /var/log/syslog
```If output is too large to post, please attach as file. If posting raw data, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by mat14 on 2017-11-16
Had the same issue with 17.10 and Chrome 62 64bit. Ubuntu as a presumed side-issue also kept opening me a login windows for the Google account to sync gnome-calender with Google.
After having tried un- / installing Chrome several times and disabling all extensions in the few seconds I had before crash I found the solution:

I had to **log out** of the current user (me) **close Chrome**, reopen it and **log in again**. That solved the problem for me

---

