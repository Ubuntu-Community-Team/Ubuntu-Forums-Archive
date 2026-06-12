---
title: "Stopping a bash script re-running"
date: 2011-08-04
forum: Programming Talk
---

### Post by Jonny87 on 2011-08-04
I want to set a bash script to run on a regular interval however I want to stop it from running again if its still running as it may take awhile. Is there a simple way to do this?

---

### Post by hakermania on 2011-08-04
How do you set the script running in a set interval?
cron job?
or it starts on boot and has a loop itself?
Explain please :)

---

### Post by Jonny87 on 2011-08-04
> **hakermania said:**
> How do you set the script running in a set interval?
cron job?
or it starts on boot and has a loop itself?
Explain please :)

Sorry yea should have explained. its just a back up script that backs up my wifes laptop to my desktop. It mounts her share but has an "if then" to make sure its mounted and will exit if its not. I thought about running it once every cupple hours so that it will likely more likely catch it when its on as its on at different parts of the day. I use cron to run it.
Also if theres an easy way to stop it running again if it already run once that day would be something else I'd like to set.

---

### Post by hakermania on 2011-08-04
Well, mention these things than can be done from inside the script:
a) you CAN mount the partition if it's not mounted
b) backup it
c) unmount it if needed

Also, you could have a file that contains 1 or 0 if you want it to run or not (make a check from inside of the script (if [[ $(cat file) -eq 0 ]]; then exit; fi) )
Also you could use notify-send to send notifications to the desktop so as to inform you:
Backup Aborted (file contained 0)
Backup Started/Finished (file contained 1)
Well, you could change the script itself and set it to run if other statements are true ( i don't know when you want it NOT to run)

---

### Post by Jonny87 on 2011-08-04
> **hakermania said:**
> Well, mention these things than can be done from inside the script:
a) you CAN mount the partition if it's not mounted
b) backup it
c) unmount it if needed

Also, you could have a file that contains 1 or 0 if you want it to run or not (make a check from inside of the script (if [[ $(cat file) -eq 0 ]]; then exit; fi) )
Also you could use notify-send to send notifications to the desktop so as to inform you:
Backup Aborted (file contained 0)
Backup Started/Finished (file contained 1)
Well, you could change the script itself and set it to run if other statements are true ( i don't know when you want it NOT to run)

Thanks thats given me an idea, I might use that concept of reading from a file. but instead of 0 or 1, use the date so it will be some thing like the following;
> 
mount laptop share
check if laptop is mounted
   if mounted then;
      if $(cat file) -eq $DATE then
         exit
      else
         backup
   else
      exit
  fi

*(I realise*[I] thats not what the  commands look like, just wrote the above as a quick example.)

[/I]Any way thanks, I'll have a play with it an see if that works.

---

