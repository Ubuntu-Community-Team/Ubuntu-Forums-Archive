---
title: "run script on sleep/resume not working"
date: 2016-05-09
forum: New to Ubuntu
---

### Post by Noah_Babineau on 2016-05-09
I am having problems with my xfce lockscreen not working when I suspend to ram. Instead I am just brought back to the logged-in session when I resume. I already checked all the boxes in the session and startup to lock the screen when sleep, and I think at this point I have exhausted all the GUI ways of fixing this. The only way I can lock the screen is by running ```
xflock4
``` in the terminal. I am attempting to make a bash script that will run on resume/suspend that will execute this simple command so that my screen will lock. The problem is that none of my scripts work. I made a file in /etc/pm/sleep.d/ called "10_lock-screen.sh" and typed
```
#!/bin/sh

case "$1" in
    resume)
        xflock4
        
esac
```

I saved it as all files and did this as SU, so I know the file is actually there. However this will not run when i suspend/resume. What should I do to fix this? is there another way to write a script that will execute the ```
xflock4
``` command?

---

### Post by leunam12 on 2016-05-10
Sorry for the silly question but, did you make it executable? Also try this syntax
```

case "$1" in
  resume|thaw)
    xflock4
;;
esac

```

---

