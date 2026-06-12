---
title: "help with shell script, please"
date: 2008-10-24
forum: Programming Talk
---

### Post by iason on 2008-10-24
Hey guys I am trying to write a simple shell script to ensure that my game server is up and running, and if not open the screen and run it, then exit the screen.  Right now it check fine, but looks like it hangs up at screen -r.  I figured this would be the best place to post this. any ideas?

```

#echo "hello"
#AC Check
AC="ac_server"
PGREP="/usr/bin/pgrep"

# find ac_server pid
$PGREP ${AC}

if [ $? -ne 1 ]
then
echo "nothing to be done"
fi

if [ $? -eq 0 ] # if ac not running
then
 # restart ac
echo "hello"
screen -r
/home/ASSAULTCUBE/assaultcube/run.sh
screen -d
echo "restarted server"
fi

```

---

### Post by alberto ferreira on 2008-10-24
Try screen -r &

---

### Post by geirha on 2008-10-24
You're not using the $? right. $? contains the return value of the **last** run command. The first time you use it, it is the return-value of pgrep, but the second time you use it, it's either the return value of [ or echo ... You only need to check it once though, so remove the second if and put its content in an else clause.

Anyway, screen -r expects to be connected to a terminal, not a script. It's not the right way to do it really. I suggest you rather kill the screen if the ac_server isn't running, and then create a new one. 

```
screen -S assaultcube /home/ASSAULTCUBE/assaultcube/run.sh
```

---

