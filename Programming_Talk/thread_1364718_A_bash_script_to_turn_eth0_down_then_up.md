---
title: "A bash script to turn eth0 down then up"
date: 2009-12-26
forum: Programming Talk
---

### Post by spiky001 on 2009-12-26
Hi I have a task i have to do to get internet connection on my laptop. I conect to another pc for internet but need to config eth0 connection each day, I do this in terminal with command sudo ifconfig eth0 down   then sudo ifconfig eth0 up,  then i,m good to go with internet, I have read that you can have a script automate it for you.  This would be my 1st tme at attempting soeting like this

---

### Post by Barriehie on 2009-12-26
Could put this file in /etc/init.d/ and update the symlinks to it via update-rc.d .  I've named it internetgo.  You'll need root privelages to put it there and you'll have to chmod +x the file to make it executable.  After putting it in /etc/init.d/ run, from the terminal,
```
update-rc.d internetgo defaults
```

```

#!/bin/bash
#
# Script to enable my internet
# Usage: internetgo
#
ifconfig eth0 down
ifconfig eth0 up
exit 0

```

Barrie

---

### Post by The Secret on 2009-12-26
```
[COLOR=Green]#!/bin/bash[/COLOR]
[COLOR=DimGray]sudo ifconfig eth0 down
sudo ifconfig eth0 up[/COLOR]

```

Save it in /usr/local/bin as auto-ifconfig ( you can change the name of the file ) and you should be ready to go.

---

### Post by Jacks0n on 2009-12-26
Hm, you might want to try restarting networking with the "/etc/init.d/networking restart" command instead. Anyway, I tend to use zenity quite a bit to have graphical dialogs with scripts without too much effort. Open up a file using a text editor (gedit will be fine), and give it a .sh extension. eg. "restart-eth0.sh" and save the following script.

```

#!/bin/bash
# The line above tells the shell to use the program /bin/bash to run this script

# Get password from user using Zenity
passwd=$(zenity --entry --hide-text --text "Please enter your password to restart eth0")

# Execute ifconfig. "echo $passwd" means that the password's being piped to sudo so you don't
# have to type it in again. sudo will then execute ifconfig.
echo $passwd | sudo -S ifconfig eth0 down
echo $passwd | sudo -S ifconfig eth0 up

# Check if it ran correctly. If it did, the last command should return 0
# You can check the status of the last command using the $? variable.
if [[ $? != 0 ]] ; then
	zenity --error --text "Hm, something went wrong..."
fi

```

That's just an example - it *should* work but I haven't tested it! I hope the comments make sense. All lines beginning with a hash are comments. When you saved the file, right click then click properties, go to the permissions tab and tick "allow executing file as a program". From then on just double click the file, and hit run to run the script. 


Jackson

---

### Post by Can+~ on 2009-12-26
> **Jacks0n said:**
> Hm, you might want to try restarting networking with the "/etc/init.d/networking restart" command instead.

+1 to that, although I prefer:

```
sudo service networking restart
```

(I discovered the service command the other day, it saves you some typing, and the autocompletion is better)

---

### Post by spiky001 on 2009-12-26
Hi I,m Glad u replied I have seen something similar to what You have put Secret, the only prblemi have it needs to wait inbetween down & up,  i tried from command line sudo ifconfig eth0 down && sudo ifconfig eth0 up dosen't seem to work so have to wait till connection accutally stops before using UP, as i said i,m using scripts for the 1st time so installing them & then executing them is all new to me, i appreciate your help

---

### Post by spiky001 on 2009-12-26
Can thks for reply i was just posting missed  your post, have you come across this problem? not tried the restart methord, I have tried eth0 down && eth0 up is that the same comand as restart?

---

### Post by spiky001 on 2009-12-26
Hi I have a bash script that The Secret done for me i need to add a delay between ifconfig eth0 down & eth0 up

```

#!/bin/bash
sudo ifconfig eth0 down
delay s5
sudo ifconfig eth0 up
```

will this give me a delay of 5sec?

---

### Post by The Secret on 2009-12-26
```
sleep <seconds>

```

---

### Post by CharlesA on 2009-12-26
```
sleep 5
```

Will make it wait 5 seconds before proceeding.

EDIT: Totally Ninja'd.

---

### Post by spiky001 on 2009-12-26
thks every1 for your help will give it a try will let you know

---

