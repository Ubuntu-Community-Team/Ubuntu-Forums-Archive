---
title: "Why doesn't &quot;killall SIGUSR1 conky&quot; work?"
date: 2010-05-30
forum: Programming Talk
---

### Post by SnickerSnack on 2010-05-30
I need to know why this happens:

```
zsharon@Weierstrass:~$ conky
Conky: forked to background, pid is 13786
zsharon@Weierstrass:~$ 
Conky: desktop window (22000a9) is subwindow of root window (109)
Conky: window type - normal
Conky: drawing to created window (0x2600001)
Conky: drawing to double buffer
killall SIGUSR1 conky
Conky: received SIGINT or SIGTERM to terminate. bye!
SIGUSR1: no process found
zsharon@Weierstrass:~$
```

Basically, I'm using killall to send SIGUSR1 to all conky processes, but it's just killing them.  I found this given as way to have conky reload its config file, but it doesn't work.  Is there another way to send SIGUSR1 to a process (preferably without needing the PID)?

All I really need to be able to do is make conky reload its config file and it's best if I don't need to have the PID at the time.  Killing and then starting conky doesn't work well enough (it fails between 10% and 50% of the time depending on how the kill/start is implemented in my script, and I'm also looking how I might get around the error that causes that).

Thanks.

---

### Post by BoneKracker on 2010-05-30
Try
```
killall -SIGUSR1 conky
```

Because you forgot the dash, it thinks you are trying to send killall -SIGTERM (which is the default) to two programs: conky and some program named "SIGUSR1".  That's why it said, "SIGUSR1: no process found".

---

### Post by SnickerSnack on 2010-05-30
Yeah, that was a mistake, but even the correct command has the same problems.

First, running the command several times in quick succession crashed X.  So, I restarted X and then tried again.

I ran the command twice, and it work great the first time and simply closed (or crashed) conky the second time.  So, I ran conky in a terminal and watched the output as I ran 'killall -SIGUSR1 conky'.  It worked a few times and then caused the same error I've been seeing:

```
Conky: X Error: type 0 Display 9169648 XID 75497473 serial 317 error_code 1 request_code 0 minor_code 0 other Display: 9169648
```

I've asked about this error in the Desktop Environment subforum.

Edit: Due to the error I'm getting, 'killall -SIGUSR1 conky' cannot be used more than once without crashing conky, and repeated use is needed for my application.

---

### Post by BoneKracker on 2010-05-30
Well, I wouldn't call that "the same problems".

I suggest you try SIGHUP and see what happens.

Since you've asked about this new problem in an otherwise duplicate thread, you should probably mark this one solved.

---

### Post by SnickerSnack on 2010-05-30
I was able to fix my original problem a different way.

Though, I'd still like to know why

```
killall -SIGUSR1 conky
```

causes this error

```
Conky: X Error: type 0 Display 88a7820 XID 58720257 serial 493 error_code 16 request_code 10 minor_code 0 other Display: 88a7820
```

---

### Post by BoneKracker on 2010-05-30
Sorry, but I don't know.

FYI, it's considered bad form to create duplicate threads, even if they are in different forums.  Also, this question really isn't germane to programming.

Glad you got your problem sorted out.

---

### Post by SnickerSnack on 2010-05-30
> **BoneKracker said:**
> Sorry, but I don't know.

Maybe someone else does.

> **BoneKracker said:**
> FYI, it's considered bad form to create duplicate threads, even if they are in different forums.

I don't think this thread is a duplicate of the other one, but that is just my opinion.

> **BoneKracker said:**
> Also, this question really isn't germane to programming.

That may be.  Feel free to 'report' the thread and invite a mod to move to a more appropriate forum if one exists.  The thread was partially about bash scripting, which is a language afaik, and "any programming language is allowed".

> **BoneKracker said:**
> Glad you got your problem sorted out.

Thanks.

---

