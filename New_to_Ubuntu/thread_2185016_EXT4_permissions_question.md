---
title: "EXT4 permissions question"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by b1001421 on 2013-10-31
I recently put files on my external drive that is formatted as EXT4. I named the external drive Seagate

I ran the command "sudo chmod -R 777 /media/myaccount/Seagate" , entered my password and the terminal didn't display anything.

Did I use that command correctly? I  do not know much about EXT4 or permissions. I know what the command does but I don't know if I was supposed to enter that or the /dev/sdb1 line.

---

### Post by Dennis N on 2013-10-31
It probaby executed your command. There is no output in this case. Probe into the Seagate directory and check the permissions of the files and folders to see what happened.

---

### Post by merlyn2748 on 2013-10-31
run > ls -l in that directory and it will list the permissions since you wanted the files to be chmoded to 777 you should see something like: > -rwxrwxrwx

---

### Post by papibe on 2013-10-31
Hi b1001421.
> **b1001421 said:**
> ...entered my password and the terminal didn't display anything.
Linux uses this philosophy to whether report success or not:
> No news is good news.
(Inherited from Unix BTW).

Most commands has a 'verbose' (-v) option that would report more information, specifically success reports. In this case, you could use:
```
sudo chmod **[COLOR="#FF0000"]-v[/COLOR]** -R 777 /media/myaccount/Seagate
```
Hope it helps.
Regards.

---

### Post by b1001421 on 2013-10-31
> **merlyn2748 said:**
> run  in that directory and it will list the permissions since you wanted the files to be chmoded to 777 you should see something like:

Every file in the directory is showing drwxrwxrwx in the list. Thanks!

> **papibe said:**
> Hi b1001421.

Linux uses this philosophy to whether report success or not:

(Inherited from Unix BTW).

Most commands has a 'verbose' (-v) option that would report more information, specifically success reports. In this case, you could use:
```
sudo chmod **[COLOR=#FF0000]-v[/COLOR]** -R 777 /media/myaccount/Seagate
```
Hope it helps.
Regards.
Ah, I didn't even think of the verbose command. I did try it when I copied over a few more files and it showed everything! Thanks



I really appreciate the help.

---

