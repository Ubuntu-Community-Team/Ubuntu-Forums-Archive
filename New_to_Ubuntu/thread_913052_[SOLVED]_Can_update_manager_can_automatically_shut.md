---
title: "[SOLVED] Can update manager can automatically shut down my comp after updates complet"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Andy Moon on 2008-09-07
Hello,

First, this is my first post here. I'm new to Ubuntu (a few weeks) and i really like it so far :) . I'm planning to make it my main OS, so I'm trying to configure a working environement that suits me best.

My specs : 
Ubuntu Hardy 8.04
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3

=====================What I would like to achieve================================
The update manager notifies me daily, if updates are available. So each day, after I'm done with my computer, instead of turning it off, I would like to launch the update download. And that my computer automatically shut down after the updates are complete.

====================My question========================
So : is there a way , maybe an option in the update manager preferences, or by some other mean (script .. ?) , to trigger the shutting down of the computer after the updates are complete ?

Thanks for any answer, or pointers to "technical terms" to help me find the solution .

Cheers,

Manuel

---

### Post by tamoneya on 2008-09-07
you could just run this command```
sudo apt-get update -y && sudo apt-get upgrade -y && sudo shutdown -H
```

---

### Post by Andy Moon on 2008-09-11
Alright thanks for the help. :)

Here's the final script code I ended with. Same commands as you advised, just different options :

Code of script :
```

#!/bin/sh
sudo apt-get update                             #update our list of available packages
sudo apt-get upgrade -y --force-yes             #after update is complete, we automatically install all the packages which are different (more uptodate)
                                                #from those on our computer

echo "JOB DONE!"                                #display success message on the console
sleep 10s

sudo shutdown -P now                            #once the installations are complete, we want the script to automatically quit linux and power off our computer

```Seems to be working ok.

Cheers,
Manuel

---

### Post by ad_267 on 2008-09-11
Cool. Now you could remove the sudos and add a launcher to the menu that uses gksu to run your script. You could use notify-send (sudo apt-get install libnotify-bin) to pop up a notification on the desktop when it's done.

---

### Post by ad_267 on 2008-09-11
```
#!/bin/bash

LOGFILE=/var/log/auto_updates.log

apt-get update
if [ $? -ne 0 ]
then notify-send -t 5000 "Error" "Package information could not be updated"
exit
fi
date >> $LOGFILE
apt-get upgrade -y --force-yes >> $LOGFILE

if [ $? -ne 0 ]
then
notify-send -t 5000 "Error" "Packages could not be upgraded"
exit
else
notify-send -t 5000 "Success" "Packes upgraded successfully. Shutting down."
fi

sleep 10s

shutdown -P now

```

And add a launcher for "gksu /home/username/path/to/script.sh" to your menu.

---

### Post by kpkeerthi on 2008-09-11
You might also want to redirect the output to a log file so you can take a look at should something break during the update process.

---

### Post by ad_267 on 2008-09-11
That's a good idea. I'll modify my post above to do this. This script should be pretty useful for me too.

---

