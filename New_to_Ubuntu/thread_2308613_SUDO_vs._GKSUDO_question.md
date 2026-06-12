---
title: "SUDO vs. GKSUDO question"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by sonicwind on 2016-01-04
Hey guys. I'm not asking the difference between sudo and gksudo. I've read about that including how sudo can accidentally change the wrong file permissions in certain situations.

Is it fair to say, when in doubt, use gksudo? Are there situations where that can do harm? I don't think so but I thought I'd ask.

Thanks. I love this forum.

---

### Post by deadflowr on 2016-01-04
gksu(do) and it's kde counterpart kdesudo are meant for graphical sudo access.
Used when needing to open something like gedit and nautilus.

sudo is command line only.
For things that can be done entirely within the terminal.

So, it's not really fair to say use gksudo when in doubt.
You would use it only to open a graphical application that will run outside of the terminal.
If that makes sense.


Moot point, probably. Because gksudo is being deprecated, from what I remember...

New methods to run graphical apps with sudo rights are
```
sudo -H app-name-here
```
the -H flag set sudo to preserve the user's home directory. This will keep sudo from messing with the user's permissions.
I gather.

And another method is to create policykit rules and actions for your apps.
Quite a few apps already use policykit, to some degree.
Some other apps do not have these rules. Like gedit or nautilus.
I good reference for understanding all that jibber-gabber here:
[http://askubuntu.com/questions/287845/how-to-configure-pkexec](http://askubuntu.com/questions/287845/how-to-configure-pkexec)

---

### Post by mastablasta on 2016-01-05
it CAN lead to serious issues such as not being able to login to OS anymore: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

use what deadflowr said when running graphical applications from terminal and you should be fine.

---

### Post by bab1 on 2016-01-05
> **deadflowr said:**
> gksu(do) and it's kde counterpart kdesudo are meant for graphical sudo access.
Used when needing to open something like gedit and nautilus.

sudo is command line only.
For things that can be done entirely within the terminal.

So, it's not really fair to say use gksudo when in doubt.
You would use it only to open a graphical application that will run outside of the terminal.
If that makes sense.


Moot point, probably. Because gksudo is being deprecated, from what I remember...
It's not depreciated, but it's not part of the default install anymore.  The package name is **gksu**.  Both gksu and gksudo are installed with this command```
sudo apt-get install gksu
```> 

New methods to run graphical apps with sudo rights are
```
sudo -H app-name-here
```
the -H flag set sudo to preserve the user's home directory. This will keep sudo from messing with the user's permissions.
I gather.

This is incorrect.  Using the -H switch only uses the home directory of the logged in user.  The operation is still run as root.  Since gksudo is still available that should be used if you have to launch a GUI app from the command line.  Sudo will always cause problems with the users ownership of files in certain situations.  Be advised; *_do not use sudo to run any GUI applications_* unless you fully understand the ramifications and know how to correct whatever errors you create.
> 


And another method is to create policykit rules and actions for your apps.
Quite a few apps already use policykit, to some degree.
Some other apps do not have these rules. Like gedit or nautilus.
I good reference for understanding all that jibber-gabber here:
[http://askubuntu.com/questions/287845/how-to-configure-pkexec](http://askubuntu.com/questions/287845/how-to-configure-pkexec)
...and another location that describes what you would need to do is:
[http://unix.stackexchange.com/questions/203136/how-do-i-run-gui-applications-as-root-by-using-pkexec]("http://unix.stackexchange.com/questions/203136/how-do-i-run-gui-applications-as-root-by-using-pkexec")

---

