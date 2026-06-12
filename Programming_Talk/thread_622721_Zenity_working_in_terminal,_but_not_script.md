---
title: "Zenity working in terminal, but not script"
date: 2007-11-25
forum: Programming Talk
---

### Post by mdpalow on 2007-11-25
Have been working with zenity in a script and can't get it to actually pop-up anything when called from CRONTAB.

If I take zenity part out and put it in a separate file, click it, and run in terminal, it brings up a terminal in the background and then the zenity pop-up.


```
#!/bin/bash

zenity --info --title="test" --text "test" # this doesn't work when called by crontab
```

If I run this test from cron, no pop-up; nothing.

How do you get zenity to just pop-up the message you want and also without the terminal in the background?

Thank you in advance..

---

### Post by GeneralZod on 2007-11-25
You'll probably want an 

```

export DISPLAY=:0

```

at the top of the script - this will let the script use X (assuming it's run as a user who is allowed to use X).

---

### Post by mdpalow on 2007-11-25
Thanks for this GeneralZod.

Your reply tipped me off to putting the user name in the crontab file to make zenity work. However, doing that causes a separate problem. My script needs to perform some sudo actions. If I have 'root' as user of the script in crontab it's fine. If I change crontab to user name then zenity works, but it won't perform the script right because the script needs 'root' to perform some sudo commands.

If I put root in crontab and then put 'sudo' in the script, it doesn't run at all.

any suggestions on how to make cron with 'user,' so zenity works, but also run the script with sudo powers?

Thanks to anyone that might be able to help...

---

### Post by geirha on 2007-11-25
In root's cron you could do something like ```
su *username* -c 'DISPLAY=:0 zenity --info --text="test"'
```

I think ...

---

