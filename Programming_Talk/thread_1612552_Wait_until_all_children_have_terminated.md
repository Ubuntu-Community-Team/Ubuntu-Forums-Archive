---
title: "Wait until all children have terminated"
date: 2010-11-03
forum: Programming Talk
---

### Post by JasonFWard on 2010-11-03
I'm working on a shell script at the moment as proof of concept for something I want to develop, utterly new to shell scripts and I've got myself stuck.

```
for ((i = 2; i <= 254; i++))
do
	ping -n -c 1 192.168.255.$i > null &
done
pgrep -P $$

sleep 3
arp -n | awk '$2 =="ether" {print $1,$3}'
```

What I in effect want is for the script to sleep whilst so ever any of the child processes have no finished.  As you can see I can list all the child processes, but I've not figured a way to use that...

---

### Post by spjackson on 2010-11-03
> **JasonFWard said:**
> What I in effect want is for the script to sleep whilst so ever any of the child processes have no finished.  As you can see I can list all the child processes, but I've not figured a way to use that...
The bash command "wait" without any parameters waits for all child processes to finish.

---

### Post by JasonFWard on 2010-11-03
:guitar:


Thanks

---

