---
title: "Gnome-shedule"
date: 2016-09-26
forum: New to Ubuntu
---

### Post by jwn-2 on 2016-09-26
Ubuntu 14.04 LTS

What exactly do one have to do to get scheduled tasks to run in Ubuntu??? On my previous computer I had problems with this and after much effort I eventually got gnome-schedule to run tasks at a scheduled time. Now I have a new computer and I have exactly the same problem again. I have now done everything I could find in write-ups all over, but my computer still refuses point blank to run any task I schedule with gnome-schedule. Please help!!!

---

### Post by ajgreeny on 2016-09-26
What tasks are you trying to run?  
If they are using GUI applications you will need to export the whole process in the job to a display with a prefix to the actual command```
export DISPLAY=:0 && command-to-run
```
If the commands demand root permissions it will be more difficult, and I am not totally sure how you would do that with gnome-schedule, though it is easy enough using cron as root.

See [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) for more details of cron.

---

### Post by jwn-2 on 2016-09-27
At the moment I am just trying to schedule a simple script which just pauses and do nothing else just to get the thing going. And I have already read the link you posted above and tried everything I can find there with no success.

---

### Post by ajgreeny on 2016-09-27
Two things to double check that are surprisingly easy to not even think about:-

1) Is the script you are running marked as executable; I have forgotten to do that in the past?
2) Have you used the full pathway to the script in your command and not used any shortcuts such as **~/** instead of **/home/username**?

Cron has a limited use of shells and commands when compared to using a terminal, so if you are able show us exactly the command you are running in gnome-schedule we might see a reason for your problem

---

### Post by jwn-2 on 2016-09-27
Yes the script is executable and yes I do use the full path (/home/jek/MyScripts/AllOther/jekk). I have also test-run it directly out of gnome-schedule and it do run. It just is not triggered to run on the scheduled time.

---

### Post by jwn-2 on 2016-09-28
Ajgreeny, I am pretty sure this is some permision problem of some kind. Is there any way I can check and/or correct my permision to use cron?

---

### Post by ajgreeny on 2016-09-28
Show us the content of the script that you are trying to run; that may give us some clues.

---

### Post by jwn-2 on 2016-09-28
The script just pauses for me to press Enter:

echo -n Press [Enter] to continue
read x

---

### Post by jwn-2 on 2016-09-28
Ajgreeny, I have just learned that if I redirect the output of my script to a file (/home/jek/MyScripts/AllOther/jekk > /home/jek/temp/temp) I do get the correct output in the temp-file (Press [Enter] to continue). So it does seem as if the script is running correctly in this case. Question now is, is it not running at all otherwise, or does the output go somewhere else, and if so, where? On my previous computer a terminal was opened with the output in it when the script runs, and that is what I want here too.

---

### Post by ajgreeny on 2016-09-28
Yes, I think I see what the problem is, though no promises.

Your script has an **echo** command which without somewhere to actually echo to, will probably be the cause of your script not running.

You will, I think, need to tick the "X application" box in gnome-schedule though I can't remember how you get the command to run in terminal and I do not use gnome-schedule to try it out.

I think your script will have to be something like ```
#!/bin/bash
gnome-terminal -exec echo -n Press [Enter] to continue
read x
```

---

### Post by jwn-2 on 2016-09-29
That didn't seem to make any difference Ajgreeny. I have now decided to re-install ubuntu and everything else from sratch again and see if I can determine at what point cron stops working correctly. But not today. I think I will attempt that on Sunday morning. Thanks so far for all your help though.

---

### Post by ajgreeny on 2016-09-29
That seems a bit sledgehammer to crack a walnut to me, as I'm sure there must be a simple answer to this which is simply escaping both of us.

---

### Post by jwn-2 on 2016-10-09
Ajgreeny, I was away for a while because I had to get everything else going again after the re-install. I wanted to re-install anyway because I wanted to encrypt my disk. Anyway I tried to schedule my test script right after the fresh install (before I installed anything else or coppied anything else to my disk, only basic Ubuntu 14.04 installed). I even used "crontab -e" then because gnome-schedule was not installed yet, and also tried "sudo crontab -e" (to schedule it as root). However the script simply does not run at the sceduled time. I have now installed gnome-schedule, but it also still does not help any. Gnome-schedule worked on my old (stolen) computer, but on the new one I simply can't get any jobs scheduled. The only difference between the two computers that I am aware of is that the old one was a 32 bit computer, and the new one is a 64 bit one. On both computers I had/have Ubuntu 14.04 installed. Is there not anything else that should be installed/set/enabled before I am able/allowed to schedule any jobs?

---

### Post by jwn-2 on 2016-10-10
Hi ajgreeny. Don't ask me what I did differently yesterday, but this morning when I started my comcupter the test task started running every minute correctly as was scheduled yesterday before I switched off. Maybe I am suppose to reboot after I have entered a schedule, however that does not sound right to me. Anyway, it seems to work now, thanks.

---

