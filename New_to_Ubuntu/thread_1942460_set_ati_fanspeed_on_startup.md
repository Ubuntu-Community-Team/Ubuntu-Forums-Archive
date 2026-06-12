---
title: "set ati fanspeed on startup"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by bilboubu on 2012-03-17
This is on xbmcbuntu, I can control the fanspeed manually by doing
DISPLAY=:0.0 aticonfig --pplib-cmd "set fanspeed 0 20"

I would like this to be saved or to happen automatically each time I start up.

I tried doing crontab -e

@reboot DISPLAY=:0.0 aticonfig --initial -f
@reboot DISPLAY=:0.0 aticonfig --pplib-cmd "set fanspeed 0 20"

doesn't work

tried putting n a 
@reboot DISPLAY=:0.0 aticonfig --pplib-cmd "set fanspeed 0 20" in a file called ati.sh making executable and putting in init.d but this doesn not work.

Can please someone tell me exactly how I do this?

---

### Post by chipbuster on 2012-03-17
DISPLAY=:0.0 aticonfig --pplib-cmd "set fanspeed 0 20"

Put that into /etc/rc.local, it'll be executed as one of the last procedures during boot.

---

### Post by bilboubu on 2012-03-17
thanks you I have edited as below but it is not kicking in, is there something else I need to do?



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
DISPLAY=:0.0 aticonfig --pplib-cmd "set fanspeed 0 20"
exit 0

Change the execution bits?

---

### Post by chipbuster on 2012-03-17
Possibly. 

chmod +x rc.local

---

### Post by bilboubu on 2012-03-17
no difference, is there a way to see if the command ran? like > err.txt or similar?

---

### Post by chipbuster on 2012-03-18
Place 

echo "rc.local is runnin" >> /home/localcheck

into another line in the rc.local

If rc.local runs, it'll create a file named localcheck in the /home folder.

Please also check the executable bits of the file: ls -l /etc/rc.local

If you get the file in /home, but nothing happens to the fan, something else is afoot.

---

### Post by bilboubu on 2012-03-19
"#!/bin/sh -e
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
echo "rc.local is running" .. /home/localcheck
DISPLAY=:0.0 aticonfig --pplib-cmd "set fanspeed 0 20"
echo "rc.local is running" >> /home/localcheck
exit 0"

Cant see any localcheck folder after rebooting.

ls -l /etc/rc.local

-rwxr-xr-x 1 root root 454 2012-03-19 18:52 /etc/rc.local

---

### Post by bilboubu on 2012-03-19
found this on xbmc

XBMCbuntu uses the /etc/xbmc/ dir for script execution at boot.

/etc/xbmc/setup.d/ -> these script are executed once (at installation boot time)

/etc/xbmc/live.d/ -> these scripts are executed every time xbmc starts

and the script does run here as I get the localcheck file now but still no fanspeed change. doh!

---

### Post by bilboubu on 2012-03-19
if  I just run it in a terminal it works

/etc/xbmc/live.d/ati.sh

frustrating, could it be something to do with the account it is running under? Can I get the script to run under my account?

---

### Post by chipbuster on 2012-03-19
That's strange. I don't know about the xbmc distro, but rc.local runs with root priviledges. There are several reasons why config files won't run. 

[http://ubuntuforums.org/showthread.php?t=1717978](http://ubuntuforums.org/showthread.php?t=1717978)

Try looking through the link on post#3 there. I'm honestly stumped right now.

---

### Post by dlast on 2012-03-20
[FONT=Verdana]I am actually solving the same issue (in Ubuntu 11.10). I think that the problem is that the the command needs to be run within X session.

Normally, when I am logged locally in X session, I can execute in the terminal following commands without problems:[/FONT]
$ sudo aticonfig --pplib-cmd "set fanspeed 0 31"
$ sudo aticonfig --od-gettemperature

[FONT=Verdana]When I am logged remotely with SSH, I get the following output:

[/FONT][FONT=Courier New]$ sudo aticonfig --pplib-cmd "set fanspeed 0 31"
ati_pplib_cmd: Unable to open display `'.
aticonfig: parsing the command-line failed.

$ sudo aticonfig --od-gettemperature
ERROR - X needs to be running to perform AMD Overdrive(TM) commands
[/FONT]
[FONT=Verdana]I believe that the same kind of erroneous output is produced when trying to call it from /etc/rc.local. So the question is:

How to execute the [FONT=Courier New]aticonfig --pplib-cmd "set fanspeed 0 31"[/FONT] at startup from the X session? Someone knows? [/FONT]

---

### Post by bilboubu on 2012-03-20
I have been running the command remotely via putty when is has worked.
 
**DISPLAY=:0.0** aticonfig --pplib-cmd "set fanspeed 0 20"  works for me remotely.

---

### Post by bilboubu on 2012-03-20
Is it possible to have the script ssh or even simple telnet to the localhost and run the commands that way, simulating me running putty?
 
eg I have used ftp scripts on windows before, something similar?
 
ssh 127.0.0.1
user
password
**DISPLAY=:0.0** aticonfig --pplib-cmd "set fanspeed 0 20" 
exit
 
??
 
thks for help so far

---

### Post by bilboubu on 2012-03-20
[http://www.startux.de/linux/55-fan-speed-for-atiamd-gpus](http://www.startux.de/linux/55-fan-speed-for-atiamd-gpus)

is this a possible solution, dunno how it translates to lubuntu.

---

### Post by chipbuster on 2012-03-20
> **dlast said:**
> [FONT=Verdana]I am actually solving the same issue (in Ubuntu 11.10). I think that the problem is that the the command needs to be run within X session.

Normally, when I am logged locally in X session, I can execute in the terminal following commands without problems:[/FONT]
$ sudo aticonfig --pplib-cmd "set fanspeed 0 31"
$ sudo aticonfig --od-gettemperature

[FONT=Verdana]When I am logged remotely with SSH, I get the following output:

[/FONT][FONT=Courier New]$ sudo aticonfig --pplib-cmd "set fanspeed 0 31"
ati_pplib_cmd: Unable to open display `'.
aticonfig: parsing the command-line failed.

$ sudo aticonfig --od-gettemperature
ERROR - X needs to be running to perform AMD Overdrive(TM) commands
[/FONT]
[FONT=Verdana]I believe that the same kind of erroneous output is produced when trying to call it from /etc/rc.local. So the question is:

How to execute the [FONT=Courier New]aticonfig --pplib-cmd "set fanspeed 0 31"[/FONT] at startup from the X session? Someone knows? [/FONT]

Could try /etc/lightdm.conf (look for post-boot stuffs)


Bilboubu: It just occured to me that rc.local and other pre-login scripts might not run with the path that you have in your shell. could you "echo $PATH" and then set PATH=*whatever came out of echo $PATH* into rc.local and try again?

---

### Post by dlast on 2012-03-20
I made it work by putting the command into a script (/usr/local/bin/setfanspeed ; don't forget to chmod +x setfanspeed) and setting this script in /etc/lightdm/lightdm.conf : adding a line
display-setup-script=/usr/local/bin/setfanspeed
 
for debugging the script startup you can also add some redirection of the output and log it into a file:
**DISPLAY=:0.0** aticonfig --pplib-cmd "set fanspeed 0 20" 2> /tmp/setfanspeed.err.log > /tmp/setfanspeed.log
 
Unfortunatelly it is useless for me already, because my graphics died.... The stability problem that I was trying to solve by increasing fanspeed was actually just an indiciation that the card is about to leave...

---

### Post by bilboubu on 2012-03-20
sorry to hear about your card :(

I've just gone to bed, will try this tomorrow after work and report back.

What was your thinking of putting it in /usr/local/bin/ , and why it executes from there?

---

### Post by bilboubu on 2012-03-21
Works! Thanks.

What card do you think you'll get next?

---

