---
title: "Is someone logged into my system"
date: 2022-08-24
forum: New to Ubuntu
---

### Post by dmacpeak on 2022-08-24
I ran the whp command at 10:40 am today and got this output.  Does it mean someone logged in at 10:05 am?    What does "tty2' mean?


xxxx   tty2         2022-08-23 10:05 (tty2)

---

### Post by TheFu on 2022-08-24
whp?  Not familiar with that command.

ttys are directly connected, so if you don't see someone sitting there, then nobody except you is logged in via that method.
There are lots of other methods, but those require positive action and setup to enable. If you didn't allow RDP, VNC or ssh and aren't running a web server that can be accessed on the internet, then it is 99.9999% unlikely anyone is on your system remotely.

---

### Post by Doug S on 2022-08-24
I think "whp" was a typo for "who". i.e.:

```
doug@s19:~/kernel/linux$ who
doug     tty1         2022-08-24 08:26
doug     pts/0        2022-08-22 07:15 (192.168.111.122)
```

where I am logged in to s19 both local and via SSH.

But yes, otherwise +1.

---

### Post by dmacpeak on 2022-08-24
but I wasnt logged in at 10:05 am?

---

### Post by dmacpeak on 2022-08-24
but I wasnt logged in at 10:05 am? Can the system be doing something  internal on its own? I saw a window in the bottom of the screen for snapd  session agent....

---

### Post by TheFu on 2022-08-24
> **dmacpeak said:**
> but I wasnt logged in at 10:05 am?

check your door locks.

---

### Post by Doug S on 2022-08-24
Check /var/log/auth.log for corresponding entries.

Using my computer as an example again:

```
doug@s19:~/kernel/linux$ doug@s19:~/kernel/linux$ who
[COLOR="#FF0000"]doug     tty1         2022-08-24 08:26[/COLOR]
doug     pts/0        2022-08-22 07:15 (192.168.111.122)
```
And /var/log/auth.log:
```
Aug 24 08:17:01 s19 CRON[7797]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 24 08:17:01 s19 CRON[7797]: pam_unix(cron:session): session closed for user root
[COLOR="#FF0000"]Aug 24 08:26:04 s19 login[7816]: pam_unix(login:session): session opened for user doug by LOGIN(uid=0)
Aug 24 08:26:04 s19 systemd-logind[859]: New session 157 of user doug.[/COLOR]
Aug 24 08:39:01 s19 CRON[7959]: pam_unix(cron:session): session opened for user root by (uid=0)
```

I do not understand this:
> **dmacpeak said:**
> I ran the whp command at 10:40 am today and got this output.  Does it mean someone logged in at 10:05 am?    What does "tty2' mean?


xxxx   tty2         2022-08-23 10:05 [COLOR="#FF0000"](tty2)[/COLOR]

I don't see the (tty2), or (tty1) on any of my computers or desktop or server VMs. It might just be a version thing, but I don't know.

Were you logged in at 10:05 yesterday?

---

### Post by TheFu on 2022-08-24
The clock could be set to UTC, error reporting set to UTC or the TZ could be off.

Since DST last spring, Firefox javascript date() has been off by 1 hour, whereas the rest of the system has been correct, including other browsers.  No clue as to why, but it screws the grid showing TV recording programs and times. Can't wait for Nov, when DST ends here so the browser grid will be correct again.  Odd thing is that all the schedule data (I scrap a TV site) has the correct DST time as I massage it into xmltv format before having Jellyfin slurp it into the media center DB. Telling a program to record has always started and ended at the correct times.

The point is, don't get stuck thinking that only 1 possible answer is correct when there are many possible answers. Only when you figure it out, will you KNOW the truth.

---

### Post by dmacpeak on 2022-08-24
[h=2][/h] 		 				 				 		 			 				[INDENT]I   may have been on at 10:05  yesterday. My permision is being denied when I try to run the var/log/authprisation command.....? DO I need to do it from root?


d9780@ubuntu-Cyan:~$ /var/log/auth.log 
bash: /var/log/auth.log: Permission denied
d9780@ubuntu-Cyan:~$ sudo /var/log/auth.log 
sudo: /var/log/auth.log: command not found
d9780@ubuntu-Cyan:~$ /var/log/auth.log 
bash: /var/log/auth.log: Permission denied

[/INDENT]

---

### Post by TheFu on 2022-08-24
/var/log/auth.log  isn't a command. It is a log file - text.

---

### Post by ActionParsnip on 2022-08-25
You can just run:
```

w

```

Instead of:
```

who

```

---

### Post by dmacpeak on 2022-08-26
thanks  does anything look out of place here?21:40:12 up 1 day,  7:56,  2 users,  load average: 1.23, 1.48, 1.77USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHATd9780    tty2     tty2             Thu13   31:56m  0.14s  0.11s /usr/libexec/gnd9780    pts/1    -                16:55    4:42m  0.05s  0.27s sudo vi /etc/tod9780@ubuntu-Cyan:~$

---

### Post by Doug S on 2022-08-27
> **dmacpeak said:**
> thanks  does anything look out of place here?21:40:12 up 1 day,  7:56,  2 users,  load average: 1.23, 1.48, 1.77USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHATd9780    tty2     tty2             Thu13   31:56m  0.14s  0.11s /usr/libexec/gnd9780    pts/1    -                16:55    4:42m  0.05s  0.27s sudo vi /etc/tod9780@ubuntu-Cyan:~$

It is difficult to read your post. Please learn how to use the code tags, the "#" on the tool bar, so that you would have posted this:
```

21:40:12 up 1 day, 7:56, 2 users, load average: 1.23, 1.48, 1.77
USER TTY FROM LOGIN@ IDLE JCPU PCPU WHAT
d9780 tty2 tty2 Thu13 31:56m 0.14s 0.11s /usr/libexec/gn
d9780 pts/1 - 16:55 4:42m 0.05s 0.27s sudo vi /etc/to
d9780@ubuntu-Cyan:~$

```The formatting is messed up because I was trying to reconstruct and didn't do it well. And post the command you used, I assume "w" in this case. Example:

```

doug@s19:~$ w
 07:28:26 up 5 days, 12 min,  5 users,  load average: 0.00, 0.01, 0.00
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
doug     tty1     -                Wed08    2days  0.04s  0.02s -bash
doug     pts/0    192.168.111.122  Mon07    2.00s  0.16s  0.00s w
doug     tty2     -                Wed14    2days  0.04s  0.02s -bash
doug     pts/1    192.168.111.122  Thu08   47:16m 18.02s  0.04s sshd: doug [priv]
doug     pts/2    192.168.111.122  Thu08   46:32m  0.03s  0.00s sshd: doug [priv]
doug@s19:~$

```In your case I do not see the "w" command, so assume you ran it as root, although I don't know why.

EDIT: To answer your question, I do not know what "/usr/libexec/gn" is (something to do with gnome?), that you seem to have been running on tty2 at the time.

---

