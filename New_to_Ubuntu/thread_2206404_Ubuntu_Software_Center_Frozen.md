---
title: "Ubuntu Software Center Frozen"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by GUZZLR on 2014-02-18
Hello all...
The Ubuntu Software Center is frozen on  my screen.  I have tried turning the computer off, and then back on, but it is still there.  I've also gone into system monitor, but do  not know what the system  monitor is called to end the process?
Thanks for the help

---

### Post by deadflowr on 2014-02-18
killall software-center should kill it.

But as you posted in you Wallpaper thread, you're on 13.04?
The repos for it are gone now, because that release is dead.
That might be the problem, or a cause of the problem, with the hanging software center.

---

### Post by Bucky Ball on 2014-02-19
> **deadflowr said:**
> 
That might be the problem, or a cause of the problem, with the hanging software center.

Absolutely. If you continue with 13.04 you will find you'll probably encounter more problems as time goes on and diminishing options for getting help (you'll be one of a handful using it). You system will also become more vulnerable to security breaches.

---

### Post by GUZZLR on 2014-02-19
Actually, I am on 13.10, not 13.04...my mistake, sorry.   The window is still there this morning when I booted the computer.  Is there a "stop" command I can use to end the process?
thanks for the help

---

### Post by Impavidus on 2014-02-19
Yes, the kill command. In this case **killall software-center** should do the trick. It could cause some issues though, as an unclean exit from the software centre may cause some locks to remain. You may get an error the next time you use the package manager. (The software centre is one of the shapes of the package manager.)

---

### Post by GUZZLR on 2014-02-19
```
guzzlr@LATITUDE:~$ kill software-center
bash: kill: software-center: arguments must be process or job IDs
guzzlr@LATITUDE:~$ sudo kill software-center
[sudo] password for guzzlr: 
kill: failed to parse argument: 'software-center'

```

Tried the kill command, this is what I got?
Thanks

Sorry I forgot the "all" I now get this:

```
guzzlr@LATITUDE:~$ killall software-center
software-center: no process found
guzzlr@LATITUDE:~$ 

```

---

### Post by deadflowr on 2014-02-19
> The Ubuntu Software Center is frozen on  my screen.  I have tried  turning the computer off, and then back on, but it is still there.

Don't laugh at my silly thought, but this wouldn't happen to be a wallpaper snafu of a screenshot you took?

If you change wallpapers, does it persist?

---

### Post by GUZZLR on 2014-02-19
Maybe, I did change wallpapers...I'm at work now, I'll try later when I get home.
Thanks

---

### Post by GUZZLR on 2014-02-19
```
Don't laugh at my silly thought, but this wouldn't happen to be a wallpaper snafu of a screenshot you took?
```

BINGO
I changed the wallpaper and it went away...You're Genius!
Thanks for the help

---

### Post by deadflowr on 2014-02-19
That makes sense.
You probably mistakenly right-clicked and hit set as wallpaper.
(I've done that)

It made no sense why the software center wasn't closing/killable and would open frozen each restart.

---

### Post by Bucky Ball on 2014-02-19
Please mark the thread as solved to help others. Cheers and good thinking, deadflowr.

---

