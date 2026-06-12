---
title: "Error with for loop..."
date: 2006-05-10
forum: Programming Talk
---

### Post by NewbieLinux on 2006-05-10
Could anybody tell me where the error is and why its not being recognised:

ps aux | awk '{print $3}' | grep [0-9][0-9].[0-9] > pid.txt

for process in `cat pid.txt` do
renice +19 $process
done

The error being produced is:

syntax error near unexpected roken 'renice'


Thank you.

---

### Post by NewbieLinux on 2006-05-10
This above is pretty urgent so if anybody has any sort of incling or an idea of what the error could mean, the input would be greatly appreciated.

---

### Post by ow50 on 2006-05-10
[QUOTE=NewbieLinux]This above is pretty urgent so if anybody has any sort of incling or an idea of what the error could mean, the input would be greatly appreciated.[/QUOTE]
I'll assume this is bash. I think you're missing a semicolon.
```
ps aux | awk '{print $3}' | grep [0-9][0-9].[0-9] > pid.txt

for process in `cat pid.txt`[SIZE="6"]**[COLOR="Red"];[/COLOR]**[/SIZE] do
    renice +19 $process
done
```

---

