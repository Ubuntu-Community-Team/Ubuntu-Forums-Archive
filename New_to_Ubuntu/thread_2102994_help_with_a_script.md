---
title: "help with a script"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-01-08
cant figure it out. need a script- want to run gcalcli calm in the terminal. it gives a monthly out put of my google calendar to the terminal. note that gcalcli is normally run directly in the terminal . tks

---

### Post by Toz on 2013-01-08
If I'm understanding correctly, how about:
```
#!/bin/bash
xfce4-terminal -T "Google Calendar Command Line Interface" -x "gcalcli calm"
```

---

### Post by rburkartjo on 2013-01-08
tks toz always appreciate your help. my problem that since it takes a few seconds for the script to load i failed to account for. so this is how i fixed

#!/bin/bash
gcalcli calm
sleep 50

works like a charm

---

### Post by HeroOfCanton on 2013-01-08
FYI, if you want the script to exit on your own terms (instead of a timer) you can make it wait for a key press with something like the following at the end:

```
echo "Press any key to exit"
read -n1
```

---

### Post by rburkartjo on 2013-01-08
hero tks for the info

---

