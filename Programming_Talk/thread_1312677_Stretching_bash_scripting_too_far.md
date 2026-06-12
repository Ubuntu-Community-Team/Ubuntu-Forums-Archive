---
title: "Stretching bash scripting too far?"
date: 2009-11-03
forum: Programming Talk
---

### Post by QwUo173Hy on 2009-11-03
I've made a script which performs an action based on a string's content. The string is assigned based on the returned value of a command line application.

But on comparison, the script exits if the string contains special characters. My question is, have I gone beyond the scope of bash scripting? Or do I just need to learn more about it. Here's the script:

```
 #! /bin/sh
dropbox start

status=$(dropbox status)

while test $status != 'Idle'
do
  echo "Working"
  status=$(dropbox status)
done

echo "\nIdle again.. exiting"
dropbox stop

```

The command 'dropbox status' can return either:
"Idle" or Uploading 1 file (102.8 KB/sec, 1 min left)" and I think it's the latter that is causing the crashing.

---

### Post by diesch on 2009-11-03
Use
 
```
while test "$status" != 'Idle'
```

instead of 

```
while test $status != 'Idle'
```

In general it's a good idea to always quote variables in shell code as long as you have a good reason to not quote them.

---

### Post by QwUo173Hy on 2009-11-03
Thanks diesch, that works perfectly now. I've downloaded the Advanced Bash Scripting (ABS) guide so hopefully I can learn more about these kind of things from there.

---

### Post by QwUo173Hy on 2009-12-05
Just to let you know, I've credited you for your help here: 
[http://ubuntuforums.org/showthread.php?t=1321847](http://ubuntuforums.org/showthread.php?t=1321847)

Thanks again.

---

### Post by phrostbyte on 2009-12-05
It looks like you are polling 'dropbox status' in an infinite loop. Are you sure this is the best way to do it? I would at least put a 'sleep 2' in the loop somewhere.

---

### Post by QwUo173Hy on 2009-12-05
Practically speaking, it seems to work fine. But I think you're correct - it's a bit excessive.

From what I remember, when I was testing, the status of Dropbox could change quickly and I needed to catch that 'Idle' before it changed to yet another state so it may have been necessary.

But I think it would be healthier to take your advice. I'll test it out. Thanks phrostbyte ;)

---

