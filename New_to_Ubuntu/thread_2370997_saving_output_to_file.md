---
title: "saving output to file"
date: 2017-09-09
forum: New to Ubuntu
---

### Post by rburkartjo on 2017-09-09
i have a cron job clamscan -r / and want to save the output to /home/ray/vsr. what would be the correct command./tks

---

### Post by Keith_Helms on 2017-09-09
If you want just the normal output and not errors to go to the file and you want to overwrite whatever was already in the file add this following the command:
```
> /home/ray/vsr
```

If you want both the normal output AND errors to go to the file and you want to overwrite whatever was already in the file add this following the command:
```
> /home/ray/vsr 2>&1
```

If you want both normal output and errors to go to the file and you want to append (add on) to whatever
was already in the file add this following the command:
```
>> /home/ray/vsr 2>&1
```

---

### Post by rburkartjo on 2017-09-09
ray@nightmare:~$ clamscan -r >/home/ray/vsr  /
bash: /home/ray/vsr: Is a directory

---

### Post by sudodus on 2017-09-09
Try ```
clamscan -r >/home/ray/vsr/filename /
```

---

### Post by SeijiSensei on 2017-09-09
> **rburkartjo said:**
> ray@nightmare:~$ clamscan -r >/home/ray/vsr  /
bash: /home/ray/vsr: Is a directory

```
clamscan -r > /home/ray/vsr/clamscan.log
```

The "-i" switch lets you limit the output to only suspicious files. 

```
clamscan -i -r > /home/ray/vsr/clamscan.log
```

---

### Post by rburkartjo on 2017-09-09
figured it out. needed to make text file in home folder. then run sudo clamscan -r --log /home/ray/rrr /

---

### Post by rburkartjo on 2017-09-09
tks all

---

