---
title: "what am i doing wrong with this shell script?"
date: 2008-06-30
forum: Programming Talk
---

### Post by Sonic Reducer on 2008-06-30
i've been trying out Kismet a little bit but when i close it wlan0 stays in monitor mode. i don't remember seeing a line in kismet.conf that lets me reset my interface back to the mode it was in before Kismet started, so i'm trying to write a shell script to run through the command line steps.

here is the original script (which didn't work)
```
#!/bin/bash
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
```

but upon further reading i saw that instead of sudo in each step i should run the script as super user and leave the commands without the sudo prefix

so the original script evolved into this:
```
#!/bin/bash
ifconfig wlan0 down;
iwconfig wlan0 mode Managed;
ifconfig wlan0 up
```

the script originally did not ave the semicolons, but i added them trying to get the commands to "seperate"

i was also trying to give the prompt for my sudo password a little style, so i'm also trying to change the terminal that comes up to a zenity text entry box:

```
#!/bin/bash

ifconfig wlan0 down
zenity --text="Enter Root Password" --entry-text --hide-text;
iwconfig wlan0 mode Managed;
ifconfig wlan0 up;
```

this is the output when i run the current script (the zenity one) from the terminal:

```
ryan@Ryan-Laptop:~$ /home/ryan/.Scripts/Reset_Wireless_Mode_With_Zenity.sh
SIOCSIFFLAGS: Permission denied
--entry-text is not supported for this dialog
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.
SIOCSIFFLAGS: Permission denied
```

i've noticed a little quirk, i am under the impression that *iwconfig* is just an *ifconfig* primarily for wireless. when i enter **sudo iwconfig wlan0 down** it gripes "_iwconfig: unknown command "down"_". is this normal?

---

### Post by justleen on 2008-06-30
you should run the command as root, just asking for a root passwd doenst enter the passwd .. what you have above is a passwd popup, which does nothing.
i'd suggest doing a "sudo su" before executing the script


iwconfig does not recognize up/down commands. it used for configuring wireless, not actually brining up the interface.

the correct zenity format is ```

zenity --entry --text "Enter root password" --hide-text

```
(its just --entry for a text-entry diag.)


edit: 
```

#!/bin/bash

PASSWD=`zenity --entry --text "Enter root password" --hide-text`    # ask for passwd
echo $PASSWD |sudo -S su                                            # go to "root" with sudo su

#execute commands, as su
ifconfig wlan0 down                                                 
iwconfig wlan0 mode Managed
ifconfig wlan0 up

#exit su
exit


```

---

### Post by Sonic Reducer on 2008-06-30
> **justleen said:**
> you should run the command as root, just asking for a root passwd doenst enter the passwd .. what you have above is a passwd popup, which does nothing.
i'd suggest doing a "sudo su" before executing the script


iwconfig does not recognize up/down commands. it used for configuring wireless, not actually brining up the interface.

how do i tell zenity to ask for a password then enter it as the sudo password?

---

### Post by justleen on 2008-06-30
check my edits...

---

### Post by justleen on 2008-06-30
it can be done even easier..

```
#!/bin/bash
gksudo ifconfig wlan0 down                                                 
gksudo iwconfig wlan0 mode Managed
gksudo ifconfig wlan0 up

```

---

### Post by Sonic Reducer on 2008-06-30
> **justleen said:**
> ```

#!/bin/bash

PASSWD=`zenity --entry --text "Enter root password" --hide-text`    # ask for passwd
echo $PASSWD | sudo -S su                                            # go to "root" with sudo su

#execute commands, as su
ifconfig wlan0 down                                                 
iwconfig wlan0 mode Managed
ifconfig wlan0 up

#exit su
exit


```

lets see if i've noticed all the important parts.

```
PASSWD=`zenity --entry --text "Enter root password" --hide-text`
```
**PASSWD** declares PASSWD as a variable in this script
**`zenity --entry --text "Enter root password" --hide-text`** defines the PASSWD variable, it's also encased in ticks (`) that i assume are there to tie that string together into one definition, instead of something like:
[CODE=Without Ticks]PASSWD=zenity --entry --text "Enter root password" --hide-text[/CODE] which would define PASSWD as "zenity" permanently, then apply the rest of the string as options on that definition

i'm assuming "|" (i think it's the absolute value symbol) seperates two commands so the first is run in response to the latter, or it would seem to me that it should be **sudo -S su | echo $PASSWD** would work better. is there a reason you put it in this order?

then, of course, **exit** leaves the super user session

.:EDIT:.
> **justleen said:**
> ```
#!/bin/bash
gksudo ifconfig wlan0 down                                                 
gksudo iwconfig wlan0 mode Managed
gksudo ifconfig wlan0 up

```

i actually have a script that gets the job done right now similar to this, but if i recall correctly "**gksudo**" is used for gui su, and sudo is command-line su. i copy this script in nautilus, then enter "sudo <paste>" in a terminal session

```
#!/bin/bash

ifconfig wlan0 down;
iwconfig wlan0 mode Managed;
ifconfig wlan0 up
```

do i need the semicolon's after each line? i remember that from dabbling with C++ last year

---

### Post by justleen on 2008-06-30
gksudo will give you the nice GUI in this case, instead of asking for a passwd with zenity, placing it in a variable, then use that variable in the script to sudo ...

the rest of your assumptin are correct.

the | is a pipe, which is very usfull in bash, it allows for input/output redirections. it passes the output of one command on to the next


that is what gksudo is for..

you dont need the ; after each line, bash will interpet any "next line" as a ;

if you place more then one command on each line seperate is with ;
```

for numbers in 1 2 3 4 5; do echo $numbers; done

``````

for numbers in 1 2 3 4 5
do
   echo $numbers
done

```

---

### Post by sisco311 on 2008-06-30
PASSWD=`zenity -- ...`
define PASSWD with the output of the command  zenity --text ...

`` command substitution
command1 `command2` = replace `command2` with the output of command2
ex: ls `echo / /home` lists the "/" (root) and /home directory

echo $PASSWD | sudo su

| (pipe) passes the output of echo $PASSWD to the input of sudo su

---

### Post by Sonic Reducer on 2008-06-30
> **sisco311 said:**
> PASSWD=`zenity -- ...`
define PASSWD with the output of the command  zenity --text ...

`` command substitution
command1 `command2` = replace `command2` with the output of command2
ex: ls `echo / /home` lists the "/" (root) and /home directory

echo $PASSWD | sudo su

| (pipe) passes the output of echo $PASSWD to the input of sudo su

so the pipe tells bash to **echo $PASSWD** for **sudo -S su** with the command ```
**echo $PASSWD |sudo -S su**
```

the ticks work like a pipe in a linear fashion right? i first saw then when you needed to install (i think) build-essential with
```
sudo apt-get install build-essential-`uname -r`
```

just to clarify, these two commands are equivalent right?

```
build-essential-`uname -r`
```
and
```
UNAME= "uname -r"
echo $UNAME | build-essential-
```

thats pretty nifty. i'm really starting to grasp the command-line lately (cracking my WEP network in 5 minutes was a breakthrough for me the other day.) I'm going to try to write an automation on my own for the aircrack suite, once i understand this enough.

---

### Post by justleen on 2008-06-30
no, those are not the same. almost right!

any thing between `` is replaced with the output of that command.
so build-essential-`uname-r`  will add the output on uname -r after the build essential

the pipe "|" is used to redirect standard output.
the example you use will not work. 
the standatd out of uname -r is " 2.6.22-14-generic", so you redirect that to "build-essential" which does nothing.

edit :
```

UNAME=`uname -r`
build-essential-`echo $UNAME`
```

---

### Post by Sonic Reducer on 2008-06-30
> **justleen said:**
> the standard out of uname -r is " 2.6.22-14-generic", so you redirect that to "build-essential" which does nothing.

i was hoping it would tack it on the end. even though that analogy was wrong, do you think i'm correctly understanding the correlation between double-ticks and pipes?

[COLOR="White"]speaking of pipes, mine is really helping me understand this programming stuff lol[/COLOR]

---

### Post by justleen on 2008-06-30
> **Sonic Reducer said:**
> i was hoping it would tack it on the end. even though that analogy was wrong, do you think i'm correctly understanding the correlation between double-ticks and pipes?


yea, you almost do..

as a rule of thumb, 

`` and $()  are used for command substution
```

DATE=`date`
DATETOO=$(date +%Y)

```

| are used for redirecting stdout
```

ps -ef |grep apache
```

the two can be combined
```

ls -la |grep `date '+%Y-%m-%d'`

```

---

### Post by x1a4 on 2008-06-30
Hi,

Do you absolutely have to run it from your own account?  I would imagine configuring your wireless card would be better served at boot.  Instead of creating a script, add your commands (without sudo) to /etc/rc.local and set the execute bit for the file
```
sudo chmod +x /etc/rc.local
```

/etc/rc.local is executed once all other start-up scripts have finished.

---

### Post by bapoumba on 2008-06-30
Moved to "Programming Talk".

---

### Post by Sonic Reducer on 2008-06-30
> **x1a4 said:**
> Hi,

Do you absolutely have to run it from your own account?  I would imagine configuring your wireless card would be better served at boot.  Instead of creating a script, add your commands (without sudo) to /etc/rc.local and set the execute bit for the file
```
sudo chmod +x /etc/rc.local
```

/etc/rc.local is executed once all other start-up scripts have finished.

instead of using a LiveUSB version of BackTrack 3 (which i both have and use to learn) i decided that installing the programs on my laptop would be the best way to learn, so i can configure them and see how they tick instead of getting them preconfigured.

> **bapoumba said:**
> Moved to "Programming Talk".

thank you, this seems to have grown from my original quick question into something that resembles a program more than a script :)

---

