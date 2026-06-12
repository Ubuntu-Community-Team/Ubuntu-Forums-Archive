---
title: "Shutdown process stops in a step"
date: 2023-05-10
forum: New to Ubuntu
---

### Post by netw844f on 2023-05-10
When my system is turn down the process stopped on this step:

```

A stop job is running for Session 3 of User Mike (30s / 1min 30s)

```

I need wait 1 minute and thirty seconds until the process moves forward.

How should I solve this issue?

My system is:

```

[FONT=monospace][COLOR=#000000]No LSB modules are available. [/COLOR]
Distributor ID: Ubuntu 
Description:    Ubuntu 22.04.2 LTS 
Release:        22.04 
Codename:       jammy 
Linux user 5.19.0-41-generic #42~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Apr 18 17:40:00 UTC 2 x86_64 x86_64 x86_64 GNU/
Linux[/FONT]

```

Thank you in the advance for any clue

---

### Post by aljames2 on 2023-05-10
When a process is not stopping the system will wait 90 seconds before killing it.  To try to identify the process that keeps hanging on your system, you can try searching journalctl to find entries where processes are being killed by systemd.

---

### Post by MAFoElffen on 2023-05-10
I would be curious to see this posted within CODE Tags:
```

journalctl -b-1 -g 'session' | tail -n 100

```

---

### Post by MAFoElffen on 2023-05-11
What aljames referred to are these timeout values:
```

mafoelffen@Mikes-B460M:/data/KVM-VM$ grep 'DefaultTimeout' /etc/systemd/system.conf
#DefaultTimeoutStartSec=90s
#DefaultTimeoutStopSec=90s
#DefaultTimeoutAbortSec=

```
The default is usually assumed as 90 seconds. Where that (there) could be uncommented and changed to a value of, say, 10 seconds, and that process would be  faster. But what is happening when that stop job is started, is that there are still pid's running in the session that need to be terminated, before killing the user session... For example having applications running and instead of closing them, and just telling the computer to shutdown.

The query above (in my previous post) might be accompanied with "session <#>- Killing process <pid>"... That is what you are looking for...

---

### Post by netw844f on 2023-05-11
Hello,

Firstly thank you for your help.
I found this lines through your clue "session <#>- Killing process <pid>"

```

mai 11 10:02:07 user systemd[1]: session-3.scope: Stopping timed out. Killing.
mai 11 10:02:07 user systemd[1]: session-3.scope: Killing process 1699 (kwin_x11) with signal SIGKILL.
mai 11 10:02:07 user systemd[1]: session-3.scope: Killing process 1797 (CPMMListener) with signal SIGKILL.
mai 11 10:02:07 user systemd[1]: session-3.scope: Killing process 5720 (n/a) with signal SIGKILL.

```

I look around, over the internet, about "kwin_x11" and "CPMMListener" but I don't think I am able to understand what this programs do and what I should do about this issue. I think it is better stand still and ask for help before I burn all my system :)

---

### Post by aljames2 on 2023-05-11
I am not familiar with the KDE environment, possibly a process not responding during shutdown.  Some searching seems to show others have had the same issue.  Some other folks her may know more.

---

### Post by Dennis N on 2023-05-11
How often does this happen? I used to get the stop job message once in a while, but just left the computer to shut itself down. You don't have to sit and watch. But, I haven't seen it for a long time. I read somewhere that the default 90s timeout was being cut to something shorter.

---

### Post by MAFoElffen on 2023-05-11
> **Dennis N said:**
> How often does this happen? I used to get the stop job message once in a while, but just left the computer to shut itself down. You don't have to sit and watch. But, I haven't seen it for a long time. [COLOR=#ff0000]I read somewhere that the default 90s timeout was being cut to something shorter[/COLOR].
True. Like I said in my last post... If you edit file /etc/systemd/system.conf and change
```

#DefaultTimeoutStopSec=90s

```
To
```

DefaultTimeoutStopSec=10s

```
Then it will change the timeout value to 10 seconds before it starts killing off those extraneous processes. People use that as a work-around for that.

Though, like I also said, there are things still running that it senses or thinks it needs closing down. If it happens often, like you mentioned, and you did close everything down before shutting down, then I would be curious to see what those processes actually were. <<=== Right?

Those process have already been killed off, but if you noted the PID's of the processes, you could probably check the logs to see what opened those processes to get a clue at what they were.

Does that make sense?

If it only happens every once in a while, then yes, those things do happen every once in a while, and is normal (occasionally).

---

