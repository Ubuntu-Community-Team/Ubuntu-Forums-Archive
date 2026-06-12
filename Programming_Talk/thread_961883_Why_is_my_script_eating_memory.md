---
title: "Why is my script eating memory?"
date: 2008-10-28
forum: Programming Talk
---

### Post by starcannon on 2008-10-28
Hi all, I'm trying to teach myself some shell scripting, and in the same stroke build something useful for myself. I'm starting out with a process monitoring script; I know that wheel has been built a million times before, but like I said, this is as much educational as it is practical.

So, heres my script:
```

#!/bin/bash
# Currently this script continues to eat memory, working on fix.
while true
do
clear
if   ps aux | egrep "TheProcess" | grep -v -q grep
then
echo "The Process is running."
else
echo "The Process is not running."
fi
sleep 1
done

```It does not take this script very long to go from only occupying a few hundred KiB of memory to occupying a MiB of memory, I of course shut it down, but would like to know: Why?, and How to stop it from doing that?
[COLOR=Red]**Adendum**[/COLOR], if you comment out the sleep line, you can watch the bug happen much faster, though causing the script to use up to 4% of the cpu.
Thanks
Rob aka starcannon

---

### Post by ddrichardson on 2008-10-29
Is the previous iteration still executing when the next loop starts? In other words does it improve if you increase the sleep value? This would be reinforced by the you removing the sleep value and it increasing.

---

### Post by starcannon on 2008-10-31
I increased the sleep to 5, problem still exists, but slowed down the problem a lot. An added benefit is that it fixed the cpu over usage issue completely. Track this little bug down, and I'll have a cool little script.

---

### Post by ghostdog74 on 2008-10-31
its "eating" memory, because you are using a while loop that loops forever, and at the same time calling an external command "ps" through pipes to a few external tools as well. The CPU will spend time processing your loop. Put sleep to 10 secs or more and it should be fine.

---

