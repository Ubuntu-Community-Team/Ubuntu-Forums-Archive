---
title: "bash attack"
date: 2010-05-13
forum: Programming Talk
---

### Post by Directive 4 on 2010-05-13
hi, i'm trying to make a shell script to start me gps working on login, but

i need to be root to get the command to run 

[B]#!/bin/bash

sudo pkill gpsd&&

gpsd -N -n -D 2 /dev/ttyUSB0 &

exit[/B]

it just outputs 

soni@Directive4:~$ [sudo] password for soni: Sorry, try again.
[sudo] password for soni: Sorry, try again.
[sudo] password for soni: Sorry, try again.
sudo: 3 incorrect password attempts

how do it get it to have my password?

cheers for any help.

---

### Post by rnerwein on 2010-05-13
hi
you have to modify your /etc/sudoers.
e.g. your script name is: gpsd_run then append the sudoers file by:

your_username ALL=NOPASSWD: /home/your_username/bin/gpsd_run

remember it must be the last line in the /etc/sudoers file and be  careful when you edit that file ! 
don't change the permissions and the owner/group of that file.
ciao

---

### Post by Directive 4 on 2010-05-13
> **rnerwein said:**
> hi
you have to modify your /etc/sudoers.
e.g. your script name is: gpsd_run then append the sudoers file by:

your_username ALL=NOPASSWD: /home/your_username/bin/gpsd_run

remember it must be the last line in the /etc/sudoers file and be  careful when you edit that file ! 
don't change the permissions and the owner/group of that file.
ciao


hi cheers for the help, it worked one time, umm but now it stoped
this is my sudoers file edited

[B]
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL 
soni ALL=NOPASSWD: /home/soni/conky/gps[/B]



this is my script at home/


[B]#!/bin/bash

sudo pkill gpsd&&

gpsd -N -n -D 2 /dev/ttyUSB0 &

exit[/B]



should work, i';; keep trying

---

### Post by Directive 4 on 2010-05-13
ok, so it works if.... i open the sudoers file bu sudo visudo then just exit it. that's all, but will not 
run untill i perform this action, am i missing something??/


soni@Directive4:~$ /home/soni/conky/gps
soni@Directive4:~$ [sudo] password for soni: Sorry, try again.
[sudo] password for soni: Sorry, try again.
[sudo] password for soni: Sorry, try again.
sudo: 3 incorrect password attempts
**sudo visudo**
[sudo] password for soni: 
visudo: /etc/sudoers.tmp unchanged
soni@Directive4:~$ /home/soni/conky/gps
soni@Directive4:~$ gpsd: launching (Version 2.92)
gpsd: listening on port gpsd
gpsd: running with effective group ID 1000
gpsd: running with effective user ID 1000
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: device open failed: No such file or directory - retrying read-only
gpsd: read-only device open failed: No such file or directory
gpsd: GPS device /dev/ttyUSB0 nonexistent or can't be read

---

### Post by rnerwein on 2010-05-14
hi
first is - visudo: /etc/sudoers.tmp unchanged - did you save your sudoers file ?
and
**sudo pkill gpsd &&  **
[B]gpsd -N -n -D 2 /dev/ttyUSB0 &
should be one line ?[/B]
i don't know that gpsd programm but it is looking for a device /dev/ttyUSB0 - on my box there isn't such a device !
where does it come from ??
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: device open failed: No such file or directory - retrying read-only
gpsd: read-only device open failed: No such file or directory
gpsd: GPS device /dev/ttyUSB0 nonexistent or can't be read

ciao

---

### Post by ryan858 on 2010-05-14
> **Directive 4 said:**
> ok, so it works if.... i open the sudoers file bu sudo visudo then just exit it. that's all, but will not 
run untill i perform this action, am i missing something??/


It's just because you used *sudo* once to run visudo... You are allowed to run any subsequent sudo's after the first one for 15 minutes in the same shell instance. This grace period can be changed in sudoers, by appending:

**Defaults        timestamp_timeout=*<number of minutes>***


As for why it the *NOPASSWD:* bit didn't work... I think you need to have it as:

**%sudo ALL=NOPASSWD: /home/soni/conky/gps**

That ommits the sudo group from having to enter a password for that program... You enter the sudo group when you type sudo, or when a script does it. So that basically gives the script the right to not use a password. But you still have to use the *sudo* command, or you won't become a sudoer, and thus get no rights.

I'm 90% sure on this... but it's a sketchy subject, that isn't well documented... at least in Ubuntu. If somebody out there knows differently, then *please* say something!
I think it worked for me though, when I tried it.

---

### Post by Directive 4 on 2010-05-14
> **rnerwein said:**
> hi
first is - visudo: /etc/sudoers.tmp unchanged - did you save your sudoers file ?
and
**sudo pkill gpsd &&  **
[B]gpsd -N -n -D 2 /dev/ttyUSB0 &
should be one line ?[/B]
i don't know that gpsd programm but it is looking for a device /dev/ttyUSB0 - on my box there isn't such a device !
where does it come from ??
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: device open failed: No such file or directory - retrying read-only
gpsd: read-only device open failed: No such file or directory
gpsd: GPS device /dev/ttyUSB0 nonexistent or can't be read

ciao


hi, yea i saved the sudooers file but no joy, 

also ttyUSB0 is just the gps, but it isn't pluged in yet, but anyway if you see that your home free.


> **ryan858 said:**
> It's just because you used *sudo* once to  run visudo... You are allowed to run any subsequent sudo's after the  first one for 15 minutes in the same shell instance. This grace period  can be changed in sudoers, by appending:

**Defaults        timestamp_timeout=*<number of minutes>***


As for why it the *NOPASSWD:* bit didn't work... I think you need  to have it as:

**%sudo ALL=NOPASSWD: /home/soni/conky/gps**

That ommits the sudo group from having to enter a password for that  program... You enter the sudo group when you type sudo, or when a script  does it. So that basically gives the script the right to not use a  password. But you still have to use the *sudo* command, or you  won't become a sudoer, and thus get no rights.

I'm 90% sure on this... but it's a sketchy subject, that isn't well  documented... at least in Ubuntu. If somebody out there knows  differently, then *please* say something!
I think it worked for me though, when I tried it.

yea, try thus also, but same problem. 


i guess this 
[B]Defaults        timestamp_timeout=[I]<number of minutes>
[/I][/B][I]
would work but i want it to run on start up so[/I]*****the terminal won't allready be sudo*****
oh, well, i'm of to the beach, i'll try more tomorrow..

cheers!

---

### Post by rnerwein on 2010-05-14
hi
be sure this works for me without a timestamp ( it's the last entry in the sudoers - it must be the last line or  it's overwritten by following rules !
my_account ALL=NOPASSWD: /bin/bash,/bin/su

ciao

---

### Post by Directive 4 on 2010-05-17
**bash attack** 			
  			  			 		   		 		 		 hi, i'm trying  to make a shell script to start me gps working on login, but

i need to be root to get the command to run 

[B]#!/bin/bash

sudo pkill gpsd&&

gpsd -N -n -D 2 /dev/ttyUSB0 &

exit[/B]

it just outputs 

soni@Directive4:~$ [sudo] password for soni: Sorry, try again.
[sudo] password for soni: Sorry, try again.
[sudo] password for soni: Sorry, try again.
sudo: 3 incorrect password attempts

how do it get it to have my password?
  
  
i changed my 
 
  
/etc/sudoers

to

sudo ALL=NOPASSWD: /home/conky/gps

and some other things, i just can't get it to work. 

does anyone the the correct line to use,

cheers!

---

### Post by hannaman on 2010-05-17
Instead of that, why don't you change the owner of the script to root and set the execute sticky bit for the owner?
```
sudo chmod 4750 filename
```

---

### Post by lisati on 2010-05-18
Threads merged

---

### Post by furlabs on 2010-05-18
Put the script in /etc/init.d/ and create runlevel links with update-rc.d. No need to muck around with sudoers file.

[http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/](http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/)

---

