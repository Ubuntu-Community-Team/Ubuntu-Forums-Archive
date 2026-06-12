---
title: "How to speed up boot sequence."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Daveg4otu on 2008-06-03
Running HH here dual boot with an XP system.

THere are two HDDs with a total of 6 partitions...that is.....

Unbuntu  + Swap partition
4 Windows partitions including the Active (C)

On bootup - once I pass the OS selection  screen and  UB starts booting it gets to a point a few seconds in where the splash screen disappears and  the detail appears on the screen - it then seems to spend around 2 mins counting the clusters and files on the non- ubuntu partitions before proudly presenting me with a total  for each partition . after that things speed up again.

Is there any way of  preventing or short circuiting this process?

Dave

---

### Post by rraj.be on 2008-06-03
It shows that there is some file system conflict between your windows and ubuntu partition.

The best way is to run chkdsk in both windows and ubuntu separately.

This should help you to fix any errors in you partition also.

---

### Post by Daveg4otu on 2008-06-04
[COLOR="Blue"]The best way is to run chkdsk in both windows and ubuntu separately.[/COLOR]

OK -what is the command for CHKDSK in Ubuntu please- presumably this  is done from terminal using sudo?

---

### Post by Fedz on 2008-06-04
AFAIK: ```
chkdsk /f
```

---

### Post by Fedz on 2008-06-04
Sorry should've added in Ubuntu AFAIK it's command is:
```
sudo shutdown -r -F now
```

---

### Post by Daveg4otu on 2008-06-05
Thanks  for all replies.

---

### Post by hyper_ch on 2008-06-05
install bootchart and check where what process is being started.

---

### Post by ray bot on 2008-06-05
chkdsk is a DOS/Windows command.  The equivalent command in ubuntu is fsck.

---

