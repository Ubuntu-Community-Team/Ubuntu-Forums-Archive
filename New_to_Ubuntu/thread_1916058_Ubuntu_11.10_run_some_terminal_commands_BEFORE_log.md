---
title: "Ubuntu 11.10 run some terminal commands BEFORE login"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by ArcaneRain on 2012-01-27
Hello everyone. Subj. I've got a problem trying to resolve all day long. Googled a lot of articles, but nothing help. Tried to add a script like that "/etc/init.d/autostart.script", give him rights to execute and run "sudo update-rc.d autostart.script defaults 95", so it was added to queue for autorun. The content was something like
#!/bin/bash
mkdir ~/test
Tried with and without sudo. Nothing helps. Directory wasn't created. Seems that this method doesn't work in 11.10. :confused:
I'am actually need to run a "mount" command for shared dir from host OS(ubuntu 11.10 is guest os by vbox, but it doesn't matter) and some rails command so when ubuntu shows login screen the dir will be already mounted and rails project updated accordingly. Thanks for any suggestions!  :)

---

### Post by ajgreeny on 2012-01-27
You could try putting the command you need without the sudo prefix into the **/etc/rc.local** file just above the last line ```
exit     0
```As an example, here's mine with an extra line to stop openssh-server running after bootup, as I use it so seldom, then when I do need it, I start it with command ```
sudo service ssh start
```
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

service ssh stop

exit 0

```

---

### Post by ArcaneRain on 2012-01-27
Thanks for the answer! Tried to create a file as u say:
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mkdir ~/test
mount -t vboxsf trunk /var/www/myproject
exit 0

But no luck for some reason. The project wasn't mounted non before not after the login. And I check for the directory, but same:
cd ~/test
-bash: cd: /home/myproject/test: No such file or directory

Sorry if I get wrong something, but could u explain why this doesn't work?

---

### Post by ArcaneRain on 2012-01-27
Oh! Thanks! Make this example work changing:
mkdir ~/test
to
mkdir /home/myproject/test
:D

---

### Post by ajgreeny on 2012-01-27
> **ArcaneRain said:**
> Oh! Thanks! Make this example work changing:
mkdir ~/test
to
mkdir /home/myproject/test
:D
Sorry, I didn't notice that you were trying to make a folder in your home.  I presume you have now made that folder and that it will be permanently in your home, so my suggestion of /etc/rc.local was not needed.

---

### Post by ArcaneRain on 2012-01-27
Your suggestion help me so much!) mkdir was only for test purposes :) Thank you!

---

### Post by aeiah on 2012-01-27
by default, the entries in rc.local are run as root. i know the mkdir was only an example, but the directory it created will have root ownership.

you should run the command as a normal user if root isn't required. you can do this with sudo:

```

sudo -u username command
```


if you're actually wanting to just mount a directory at boot, you may be better off putting a [bind mount ]("http://backdrift.org/how-to-use-bind-mounts-in-linux")in your /etc/fstab file

---

### Post by luckyEddy on 2012-01-27
The mounted share from a "virtual box" is a setting in the virtual machine configuration.

---

