---
title: "Making text balloon?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-08-01
I've been messing around with Zenity and I found the notification option, but I don't like it because it doesn't go away until you click it, and the script doesn't continue until you click it. I was wondering if there was a way to make a text bubble in the corner through Zenity or another program, that continues the bash script even while it's up. Or some flash, or reminder that you can glance at and will go away after a few seconds or a specified time. I would use 'beep' for this, but my system beep for some odd reason doesn't work, even though I have the option in my Sound preferences checked. >_>

I hope someone can help!

---

### Post by unutbu on 2008-08-01
```
#!/bin/sh
zenity --info --text 'Hi linkmaster03!' &
PID=$!
sleep 5
kill "$PID"

```

If you don't want the rest of your script to have to wait 5 seconds before continuing on, you can save the above into a script of its own, call it something like znote.sh.

Then from your main script you can run
```

znote.sh &
```
And it will run in the background as the rest of your script carries on.

---

### Post by linkmaster03 on 2008-08-01
No, that works perfectly! Thanks so much. :)

---

