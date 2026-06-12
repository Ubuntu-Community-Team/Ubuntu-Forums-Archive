---
title: "Sessions program"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-06-24
I am trying to add a file to the Sessions so that it starts automatically. (the program is Junglediskmonitor by the way...but that is probably not important)...when I browse to the folder to add the file, it tells me that permission is denied....that does not seem to make sense to me...surely if you can access the Session file and add to it, you must have root permission by default.....what am I missing here?

---

### Post by drs305 on 2008-06-24
> **dunbrokin said:**
> I am trying to add a file to the Sessions so that it starts automatically. (the program is Junglediskmonitor by the way...but that is probably not important)...when I browse to the folder to add the file, it tells me that permission is denied....that does not seem to make sense to me...surely if you can access the Session file and add to it, you must have root permission by default.....what am I missing here?

When you say "browse to the folder", are you accessing Sessions via System, Preferences, Sessions, Startup Programs, Add?

As to the second half of your question - not necessarily. You can start programs that belong to you but you wouldn't be able to run a program that would take over the entire system or require administrative powers. These programs would have to be placed in the applicable root startup folders to begin during boot. You are accessing Sessions as a user, not as an administrator.

---

### Post by dunbrokin on 2008-06-24
> **drs305 said:**
> When you say "browse to the folder", are you accessing Sessions via System, Preferences, Sessions, Startup Programs, Add?

As to the second half of your question - not necessarily. You can start programs that belong to you but you wouldn't be able to run a program that would take over the entire system or require administrative powers. These programs would have to be placed in the applicable root startup folders to begin during boot. You are accessing Sessions as a user, not as an administrator.

Ah..OK...yes I am am accessing it via System, Preference, Sessions, Startup Programs, Add.....is there a way I can do it as root?

---

### Post by drs305 on 2008-06-24
> **dunbrokin said:**
> is there a way I can do it as root?

You have several options. This is one. I won't guarantee it's the simplest solution. 

You can make a script and put it in the one or more of the folders referenced during the boot process. These scripts are run as root and thus will run scripts and apps that Sessions may not be able to.

To run an app or script at startup:

Make a startup script for the process you want started. 
Here is a sample script:
```

#!/bin/bash
# This is a sample startup script. Note it must include the complete path to the command.
# If it doesn't appear to work, you may want to add a "sleep 30 " line before the startup comand to make the script delay running for XX seconds after the boot process starts to allow other processes to run prior to running your command.
# The last line should be "exit 0".

/pathname/command.for.app.you.want.started
exit 0

```

Make it executable (command if in same directory as script):
```
chmod +x scriptname
```

Place in /etc/init.d/ 
```
sudo cp scriptname /etc/init.d
```

Update the init.d folders to include this startup script. You can read about runlevels and formats to learn what the available options are. The link will appear in /etc/rc2.d. The script will run the startup command in runlevel 2 with a low priority. Don't forget the . (period):
```
sudo update-rc.d scriptname start 99 2 . 
```

To remove the startup script *links* in the future, you would run this command and then delete the actual script located in /etc/init.d:
```
sudo update-rc.d -f scriptname remove
```

---

### Post by dunbrokin on 2008-06-24
> **drs305 said:**
> You have several options. This is one. I won't guarantee it's the simplest solution. 

You can make a script and put it in the one or more of the folders referenced during the boot process. These scripts are run as root and thus will run scripts and apps that Sessions may not be able to.

To run an app or script at startup:

Make a startup script for the process you want started. 
Here is a sample script:
```

#!/bin/bash
# This is a sample startup script. Note it must include the complete path to the command.
# If it doesn't appear to work, you may want to add a "sleep = 30 " line before the startup comand to make the script delay running for XX seconds after the boot process starts to allow other processes to run prior to running your command.
# The last line should be "exit 0".

/pathname/command.for.app.you.want.started
exit 0

```

Make it executable (command if in same directory as script):
```
chmod +x scriptname
```

Place in /etc/init.d/ 
```
sudo cp scriptname /etc/init.d
```

Update the init.d folders to include this startup script. You can read about runlevels and formats to learn what the available options are. The link will appear in /etc/rc2.d. The script will run the startup command in runlevel 2 with a low priority. Don't forget the . (period):
```
sudo update-rc.d scriptname start 99 2 . 
```

To remove the startup script *links* in the future, you would run this command and then delete the actual script located in /etc/init.d:
```
sudo update-rc.d -f scriptname remove
```

:~/Documents/scripts$ sudo cp startvarious /init.d
:~/Documents/scripts$ sudo update-rc.d startvarious start 99 2 .
update-rc.d: /etc/init.d/startvarious: file does not exist

What have I done wrong here?

---

### Post by drs305 on 2008-06-25
> **dunbrokin said:**
> :~/Documents/scripts$ sudo cp startvarious /init.d
:~/Documents/scripts$ sudo update-rc.d startvarious start 99 2 .
update-rc.d: /etc/init.d/startvarious: file does not exist

What have I done wrong here?

This:```

sudo cp startvarious /init.d
```
Should be:
```
sudo cp startvarious **/etc/**init.d
```

---

### Post by dunbrokin on 2008-06-26
> **drs305 said:**
> This:```

sudo cp startvarious /init.d
```
Should be:
```
sudo cp startvarious **/etc/**init.d
```

Duh!....sorry!.....thanks...

---

### Post by dunbrokin on 2008-06-26
> **drs305 said:**
> This:```

sudo cp startvarious /init.d
```
Should be:
```
sudo cp startvarious **/etc/**init.d
```

This is my file...

#!/bin/bash
# This is a sample startup script. Note it must include the complete path to the command.
# If it doesn't appear to work, you may want to add a "sleep = 30 " line before the startup comand to make the script delay running for XX seconds after the boot process starts to allow other processes to run prior to running your command.
# The last line should be "exit 0".
sleep = 30
/usr/jungledisk/junglediskmonitor
sleep = 10
/home/pj/wdisplay/WeatherD
exit 0

but neither of them started....

---

### Post by drs305 on 2008-06-26
Here are a some of things to check:

1. Do the *commands* work if you just run "/usr/jungledisk/junglediskmonitor" and "/home/pj/wdisplay/WeatherD" in terminal? If they don't run, what error messages do you get?

2. Does the *script* run if you start the script in terminal? If not, what are the error messages?

3. Do you see a your script in /etc/init.d/ (startvarious) and a link in /etc/rc2.d (S99startvarious) ?

**Added:** I saw some threads about JDM running but not showing the correct icons. You can see if it is running by typing (note you will see at least one reference, which is the search process):
```

ps aux | grep jungle

```

---

### Post by dunbrokin on 2008-06-26
> **drs305 said:**
> 

**Added:** I saw some threads about JDM running but not showing the correct icons. You can see if it is running by typing (note you will see at least one reference, which is the search process):
```

ps aux | grep jungle

```

 6788  0.0  0.0   3004   764 pts/0    S+   08:10   0:00 grep jungle

I presume that means it is running?

---

### Post by drs305 on 2008-06-26
> **dunbrokin said:**
> 6788  0.0  0.0   3004   764 pts/0    S+   08:10   0:00 grep jungle

I presume that means it is running?

Nope, that just means that the *search* for it is running. That's what I was trying to explain about seeing at least one search reference. If it was running you wouldn't see the 'grep' part... :(

How about the other questions? Does it run outside the script, etc?

**Added:** you might want to extend the first sleep time to 120 to allow for the system to completely boot before it attempts to start JDM. If it's successful you can tweak it lower until it doesn't work.

---

### Post by dunbrokin on 2008-06-26
> **drs305 said:**
> Nope, that just means that the *search* for it is running. That's what I was trying to explain about seeing at least one search reference. If it was running you wouldn't see the 'grep' part... :(

How about the other questions? Does it run outside the script, etc?

**Added:** you might want to extend the first sleep time to 120 to allow for the system to completely boot before it attempts to start JDM. If it's successful you can tweak it lower until it doesn't work.

Yes it works if I

 sudo /usr/jungledisk/junglediskmonitor

---

### Post by drs305 on 2008-06-26
I just saw something I didn't notice in your script earlier. The sleep command is "sleep XXX" with no equal sign. I've gone back and edited my post to avoid any confusion.

I'm not having any luck getting this to work. If I do I'll post back. Sorry.

---

