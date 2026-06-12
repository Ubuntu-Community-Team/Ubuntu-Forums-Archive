---
title: "can you SCHEDULE updates"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by klein de usa on 2008-08-31
hi
i'm wondering if you can schedule ubuntu to update like in the middle of the night automatically, could i have it download all updates at 3:00am and install them?  maybe it already does this and i have missed it some how?

---

### Post by DBrocks on 2008-08-31
Try this. Remember, you computer has to be on. It wont wake itself for updates unless you set it in the BIOS
[URL="http://www.watchingthenet.com/how-to-configure-automatic-updates-schedule-in-ubuntu.html"]
http://www.watchingthenet.com/how-to-configure-automatic-updates-schedule-in-ubuntu.html[/URL]

---

### Post by freak42 on 2008-08-31
You could also use cron to create your own automatic update times.

---

### Post by klein de usa on 2008-09-02
hi 
DBrocks using ubuntu update scheduler doesn't let you set a time.just once a day or week or month  

freak42 using cron well i'm not at all that good to be able to do that yet 

but i did find gnome schedule and it looks simple but i can't figure out how to word the command if i put sudo apt-get update && sudo apt-get upgrade it is going to ask for a password and i'm hopping i'm in bed when it runs, so is there a way around this or should i make an executable file and have gnome scheduler run that?     hum how do you make an executable file?

---

### Post by freak42 on 2008-09-03
> **klein de usa said:**
> 
freak42 using cron well i'm not at all that good to be able to do that yet 


there are tutorials for that out there:
[http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm](http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm)

(I know I am asking a lot, if you are a newbie with Linux, however the more you do such things the easier they get. Linux was daunting for me in the beginning and I spent a lot of time messing around with it, and trying out things. I just try to show one common way to solve your problem, no matter how hard or easy it is.)

hth

---

### Post by klein de usa on 2008-09-17
hi 
   well i took your advice freak42, and now i have cron updating  my computer at 3am every morning, that the computer is on.
   i made it so when my bash file runs it creates a text file on the desktop of exactly what it did while i was sleeping, if it did nothing i can delete it or keep it for a couple of days and see what happens, then if everything is ok i can delete it. and the next time i leave the computer on it creates a hole new file on my desktop. if i don't delete the file my bash file just adds to the file already there. 
  i figured i would put the output of my bash file on my desktop so if something goes wrong, i can boot my live cd and find the file easily.

---

