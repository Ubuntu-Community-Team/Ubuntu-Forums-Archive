---
title: "How to terminate the command in shell script"
date: 2011-11-07
forum: Programming Talk
---

### Post by kemparaju on 2011-11-07
Hi,
 
How to terminate the command in shell script, which is expecting Ctrl+c to get terminate. For example my shell script is
 
cat /dev/input/event1 > event1.txt
cat /dev/input/event2 > event2.txt
cat /dev/input/event3 > event3.txt
 
 
but it is not executing 2nd command, because first command will be waiting for the input of Ctrl+c to get terminate. But I dont want to press Ctrl+c manually.
Is there any way to execute these 3 commands without manuall input.
Please help me out.
 
Thanks
Kemparaju

---

### Post by ofnuts on 2011-11-07
> **kemparaju said:**
> Hi,
 
How to terminate the command in shell script, which is expecting Ctrl+c to get terminate. For example my shell script is
 
cat /dev/input/event1 > event1.txt
cat /dev/input/event2 > event2.txt
cat /dev/input/event3 > event3.txt
 
 
but it is not executing 2nd command, because first command will be waiting for the input of Ctrl+c to get terminate. But I dont want to press Ctrl+c manually.
Is there any way to execute these 3 commands without manuall input.
Please help me out.
 
Thanks
Kemparaju

Start in background, wait a bit, then send it a kill, ie:
```

cat /dev/input/event1 > event1.txt &
pid=$!
sleep 1
kill $pid

```

---

### Post by kemparaju on 2011-11-09
Thank you very much, great idea.

---

