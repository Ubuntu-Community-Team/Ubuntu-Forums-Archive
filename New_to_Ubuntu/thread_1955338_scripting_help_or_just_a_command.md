---
title: "scripting help or just a command"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-04-09
been working off and on for a few days on this and cant figure it out need a script or just a terminal command to kill
desktopnova-tray && desktopnova-daemon

have try using pkill killall but didnt work. tks

---

### Post by forrestcupp on 2012-04-09
You could try opening the System Monitor, find them in the Processes tab, and try ending those processes.

---

### Post by rburkartjo on 2012-04-09
for tks have tried that but must be any easier way and one compound command or script to kill both at once. just cant figure it out

---

### Post by kevdog on 2012-04-09
I assume these files run as root?

Can you just make a script that does runs with root permissions -- this could be done under the roots cron daemon file or you could just run the script with the sudo prefix -- that would ps -aux and then pass the result to egrep or grep to grep out the specific lines.  You could then extract the process ID number from the appropriate column and run the sudo kill PID on the resultant.

---

### Post by CharlesA on 2012-04-09
> **kevdog said:**
> I assume these files run as root?

Can you just make a script that does runs with root permissions -- this could be done under the roots cron daemon file or you could just run the script with the sudo prefix -- that would ps -aux and then pass the result to egrep or grep to grep out the specific lines.  You could then extract the process ID number from the appropriate column and run the sudo kill PID on the resultant.
Yep.

Could try something like this:

```
#!/bin/bash
tray=$(pidof desktopnova-tray)
daemon=$(pidof desktopnova-daemon)

kill -9 $tray && kill -9 $daemon
```

Run it with sudo and it *should *kill those processes, but only if they are only running once.

---

### Post by rburkartjo on 2012-04-09
charles tks worked great here is the final script i used

#!/bin/bash
echo xxxx | sudo -S
tray=$(pidof desktopnova-tray)
daemon=$(pidof desktopnova-daemon)

kill -9 $tray && kill -9 $daemon

---

### Post by dodo3773 on 2012-04-10
> **rburkartjo said:**
> charles tks worked great here is the final script i used

#!/bin/bash
echo xxxx | sudo -S
tray=$(pidof desktopnova-tray)
daemon=$(pidof desktopnova-daemon)

kill -9 $tray && kill -9 $daemon

Shouldn't it be like this?:

```

#!/bin/bash
tray=$(pidof desktopnova-tray)
daemon=$(pidof desktopnova-daemon)

echo xxxx | sudo -S kill -9 $tray $daemon


```

Edit: I am pretty sure you can specify more than one pid to kill at once.

---

