---
title: "rsync + mailx notification acting weird"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by hookitup on 2013-08-20
Hey Folks,

So i have an rsync job running every hour and after the job is done it is supposed to send me an email to my gmail account.
the issue here is that when the rsync job actually has something to sync it sends the log file as an attachment but when it has nothing to sync then it send it as text in my email and not an attachment (which is what i want). a little confused why this is happening. this is my code below.
```
#!/bin/bash

#this line synces the docs folder to the NAS
rsync -a --no-perms -O --progress /home/cj/Downloads/Docs/ rsync://cj@192.168.1.100:/rdocs > /home/cj/Logs/rsync.txt


#this line is going to mail the progress file when its complete
mailx -s Rsync_Complete myemailaddress@gmail.com < /home/cj/Logs/rsync.txt
```

does anybody see anything wrong with this. like why when it fills the log file with just ```
[FONT=arial]sending incremental file list[/FONT]

[FONT=arial]sent 951 bytes  received 10 bytes  1922.00 bytes/sec[/FONT]
[FONT=arial]total size is 1361904935  speedup is 1417174.75[/FONT]
```

it sends it in text in email but when it fills the log with ```
sending incremental file list
mydoctest1.txt


         332 100%    0.00kB/s    0:00:00  
         332 100%    0.00kB/s    0:00:00 (xfer#1, to-check=16/18)
mydoctest2.txt




       32768  12%    7.81MB/s    0:00:00  
      267364 100%    8.50MB/s    0:00:00 (xfer#2, to-check=13/18)


sent 272284 bytes  received 203 bytes  544974.00 bytes/sec
total size is 1361904935  speedup is 4998.05



```

it sends it as an attachment 
so strange. you think it has something to do with the spaceing or something that the bigger log file has the it doesnt like?
any help is appreciated

---

