---
title: "how to get a ruby application to load at startup?"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by dtomcat on 2012-02-03
Hello,
Pretty new to Ubuntu... (had linux and pearl classes before... so can catch on quick).
 
Short story... trying to get SiriProxy to load at startup... I've made some progress... but now am stuck so asking for help from smarter peoples :)
 
I can get a script to load, but it says that the command does not exist. If I run it from terminal, it works fine... Here are the files loaded at startup:
 
siri_start:
--------------------------
#!/bin/bash
gnome-terminal --execute bash -c "/path/to/reopen ; bash" &
--------------------------
 
reopen:
--------------------------
#!/bin/bash
source ~/.bash_profile
while true;
do
echo "Starting Server"
if rvmsudo siriproxy server; then
echo "[Info - SiriProxy] Pausing for 30 seconds"
sleep 30
else
echo "[Warning - Crash - SiriProxy] Crashed! Restarting in 2 sec!"
sleep 2
fi
 
done
---------------------------
 
Any help will be greatly appreciated. again... it works from command line... but when loading on startup... says the command can not be found... I had it print $PATH and it had the correct path. I'm very puzzled as a beginner!
Thanks!
 
-Rob

---

### Post by wolfen69 on 2012-02-03
Just put that script into /home (or wherever) and then go into Startup Applications>Add then navigate to it. I run a script to disable my touchpad, and this method works for me.

---

### Post by dtomcat on 2012-02-03
Thanks for the response!  I have already added it to the startup...  but when it runs the script, i get the error.   If i run it by myself... it works fine.  Thanks again though!
 
-Rob

---

### Post by wolfen69 on 2012-02-03
See [this]("https://github.com/plamoni/SiriProxy/issues/137") page, as I think it may help. Someone has the same problem, and found some answers.

---

### Post by dtomcat on 2012-02-03
Wolf,
  Thanks again for the quick reply.  I did come across that thread and unfortunetly it was not helpful for me.  I did a lot of searching before making a thread here.  I looked all through the github issues to see if someone else had an answer.  after 3 weeks of searching, I'm resorting to asking :)  I've tried several of the other "solutions" with no avial!  this is the closest I've come to it working.  I have the script loading at start up... but for some reason.... it can't find the command with "startup applications" launches it... but it does find it when I launch it.   something like /env/..... can't find command....  not sure and not where I can reboot to get the actual error.
 
Thanks again though for your help!
 
-Rob

---

