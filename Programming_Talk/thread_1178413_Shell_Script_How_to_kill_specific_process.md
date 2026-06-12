---
title: "Shell Script: How to kill specific process?"
date: 2009-06-04
forum: Programming Talk
---

### Post by grubby23 on 2009-06-04
Hi

I wanna do the following using a shell script: I wanna do some performance measurements when two programs are running at the same time; during each run I would like to change the nice value of the program named
app10000. This program is NEVER terminating, so I have to kill it each time after app1 has finished executing before I restart it again with a different nice value! My script works fine so far, however, I dont know how I can kill the app10000 process after app1 is finished. So what I have to find out is how I can get the pid of the app so that I can kill it. Has anyone an idea how this could be done? Here is the script as it looks so far:


clear
echo "Executing app10000 with nice value -15"
nice -n -15 ./app10000 &
echo "Executing app1"
./app1
echo "Execution of app1 finished!"
# KILL app10000 which is still running before starting it again with different nice value
echo "Executing app10000 with nice value -14"
nice -n -14 ./app10000 &
echo "Executing app1"
./app1
echo "Execution of app1 finished!"
# KILL app10000 which is still running before starting it again with different nice value

---

### Post by MadCow108 on 2009-06-04
```

clear
echo "Executing app10000 with nice value -15"
nice -n -15 ./app10000 &
**PID=$!**
echo "Executing app1"
./app1
echo "Execution of app1 finished!"
# KILL app10000 which is still running before starting it again with different nice value
echo "Executing app10000 with nice value -14"
nice -n -14 ./app10000 &
echo "Executing app1"
./app1
echo "Execution of app1 finished!"
**kill $PID**
# KILL app10000 which is still running before starting it again with different nice value
```
$! holds the pid of the last starte d background process

---

### Post by grubby23 on 2009-06-04
Works! Thanks so much for the quick answer!

---

### Post by soltanis on 2009-06-04
also works (my favorite shell command)

```

ps -e | grep app1000 | awk 'print $1' | xargs kill -9

```

---

### Post by ghostdog74 on 2009-06-04
> **soltanis said:**
> also works (my favorite shell command)

```

ps -e | grep app1000 | awk 'print $1' | xargs kill -9

```

when use awk,no need to use grep
```


ps -e | awk '/app1000/{print $1}'| xargs kill -9

```

---

### Post by KyleBrandt on 2009-06-05
> **ghostdog74 said:**
> when use awk,no need to use grep
```


ps -e | awk '/app1000/{print $1}'| xargs kill -9

```

The killall command makes this a little shorter :-)

---

### Post by ghostdog74 on 2009-06-05
> **KyleBrandt said:**
> The killall command makes this a little shorter :-)

sure, if you are using systems that support killall, by all means. other tools include pkill ..

---

