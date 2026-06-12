---
title: "how did i lose 300 gigs"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-28
okay so i look at my disk usage analyzer and i have 500 gigs available and then 2 min later i look again and theres 262 gigs available 
where did my 300 gigs go?

---

### Post by mr-Kirch on 2008-05-28
nvm i just restarted and it showed up as 525 again :guitar:

---

### Post by Joeb454 on 2008-05-28
Troubleshooting for Beginners:

#1 - Turn it off and on again

:D

On a separate note - can you please mark your thread as solved - it's under thread tools near the top of this page :)

---

### Post by ibutho on 2008-05-28
You are probably better of using "du -h" to check disk usage instead of the disk usage analyser. Many people say that sometimes it shows incorrect output.

---

### Post by Joeb454 on 2008-05-28
Actually I'd recommend ```
df -h
```

Though if you prefer more in depth analysis I'd use ```
du -h | less
```

---

### Post by robalcorn on 2008-05-28
How about it shows actual disk usage and not reboot? Just a thought call me crazy

---

### Post by Captain panda on 2008-05-28
Ahhh... The wonders of restarting a computer (it actually solves most of the problems that I find on my computer.)

---

### Post by ibutho on 2008-05-29
> **Joeb454 said:**
> Actually I'd recommend ```
df -h
```

Though if you prefer more in depth analysis I'd use ```
du -h | less
```

My apologies, I actually meand "df -h". I always seem to do a good job of mixing up these two commands. ;)

---

