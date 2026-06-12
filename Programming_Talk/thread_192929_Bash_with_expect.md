---
title: "Bash with expect"
date: 2006-06-09
forum: Programming Talk
---

### Post by munwin on 2006-06-09
I am having some issues with the below script.
```
#!/bin/bash
HOST="192.168.10.28"
USR="mark"
PASS="password"

VAR=$(expect -c "
    spawn ssh $USER@$HOST
     expect {
     password: { send \"password\r\"; exp_continue }
     :~$ { send \"ls\r\"; }
     }
    exit
")

echo "==============="
echo "$VAR" 
```

I have installed 'expect'.
The script does connect and login to the remote box.
Box PCs are Ubuntu 6.06.

Issue #1 - I don't seem to be able to use $PASS instead of the actual password.
Issue #2 - the "ls" command doesn't seem to be executed, at all, on the remote host. I think it may be related to the :~$ prompt needing to be 'escaped'.

This is part of a larger project, the first step is getting commands executing on the remote host. Any help much appreciated.

---

### Post by rbalfour on 2006-06-09
```

#!/bin/bash
HOST="192.168.10.28"
USER="mark"
PASS="password"

VAR=$(expect -c "
    spawn ssh $USER@$HOST
     expect {
     password: { send \"$PASS\r\"; exp_continue }
     :~$ { send \"ls\r\"; }
     }
    exit
")

echo "==============="
echo "$VAR"

```

problem one fixed. USR variable was mis-spelled.
use $PASS instead of password.

---

### Post by nanotube on 2006-06-09
[QUOTE=rbalfour]```

#!/bin/bash
HOST="192.168.10.28"
USER="mark"
PASS="password"

VAR=$(expect -c "
    spawn ssh $USER@$HOST
     expect {
     password: { send \"$PASS\r\"; exp_continue }
     :~$ { send \"ls\r\"; }
     }
    exit
")

echo "==============="
echo "$VAR

```

problem one fixed. USR variable was mis-spelled.
use $PASS instead of password.[/QUOTE]
try putting quotes around the prompt. so, this part of your script looks like this:
```
VAR=$(expect -c "
    spawn ssh $USER@$HOST
     expect {
     password: { send \"$PASS\r\"; exp_continue }
     \":~$\" { send \"ls\r\"; }
     }
    exit
")
```

---

### Post by munwin on 2006-06-09
Yep, it now seems to log in - but still doesn't return the "ls" command ?

Have tried sending another command (a wget), but that also produces no result. Even if the returned output doesn't include the second commands results, the wget doesn't appear to have run (there is no downloaded file)...

I can do this manually (ssh into the box, then run ls or wget). I just need to get it scripted...

Thanks again.

---

### Post by nanotube on 2006-06-10
[QUOTE=munwin]Yep, it now seems to log in - but still doesn't return the "ls" command ?

Have tried sending another command (a wget), but that also produces no result. Even if the returned output doesn't include the second commands results, the wget doesn't appear to have run (there is no downloaded file)...

I can do this manually (ssh into the box, then run ls or wget). I just need to get it scripted...

Thanks again.[/QUOTE]
maybe you are expecting the wrong prompt? maybe ":~$" is missing something? try putting in a regexp for it that is pretty lenient (with a .* in it or something), and see what happens. so, this line:
```
:~$ { send \"ls\r\"; }
```
becomes this line:
```
-re \".*\$.*\" { send \"ls\r\"; }
```
(might have to double-backslash the $, because it could be interpreted by the shell first, before it is passed to the regexp filter.)

---

### Post by munwin on 2006-06-11
So here is my current code.
```
#!/bin/bash
HOST="192.168.10.28"
USER="mark"
PASS="password"
VAR=$(expect -c "
    spawn ssh $USER@$HOST
     expect {
     password: { send \"$PASS\r\"; exp_continue }
     -re \".*\$.*\" { send \"ls\r\"; }
     }
    exit
")
echo "==============="
echo "$VAR"
```

It logs in, but returns nothing more.
The prompt after login looks like this:
```
mark@machinename:~$
```
The regex appears to do nothing.
Apologies for being dumb at this - am just starting with Bash....

The complete return of $VAR is:
```
===============
spawn ssh mark@192.168.10.28
mark@192.168.10.28's password:
Linux machinename 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Sun Jun 11 19:17:58 2006 from 192.168.110.1
mark@machinename:~$
```

---

### Post by nanotube on 2006-06-11
well, i'm kinda out of ideas on this at this point. i haven't done much with expect myself, so maybe someone else who has more experience with it can pick it up from here? :)

---

### Post by nanotube on 2006-06-12
i've played around with this a bit more.. and found a few things. :) most notably, this version works:
```
#!/bin/bash
HOST="localhost"
USER="myuname"
PASS="mypassword"

VAR=$(expect -c "
spawn ssh $USER@$HOST
expect \"password:\"
send \"$PASS\r\"
expect \"\\\\$\"
send \"ls\r\"
expect -re \"$USER.*\"
send \"logout\"
")

echo "==============="
echo "$VAR"

```

your syntax, with one expect block, gave it a "choice of actions", but told it to only perform the choice once. for it to expect multiple things and to react multiple times, you need to give it multiple "expect"s. 

and another thing - for the output of 'ls' to be stored in the var variable, you need to give it one more expect, and tell it to do something else. otherwise, it exits immediately upon sending the "ls" command, without getting the output. (hence, i added the logout part).

note, for demonstration purposes, i showed both an expect with $ (it had to be quadruple-backslashed in order to be properly intepreted, since it is in quotes within quotes), and also the "simpler" expect simply on my username, since it is part of the prompt as well as $. you can choose either one and go with it. 

well, that should get you over the hump, i hope. :)

---

### Post by munwin on 2006-06-12
Thank you very much.
Yep - all working now.
I can now continue with auditing (remote) Ubuntu boxen, and add them into my SF project (see sig).

Thanks again.

---

### Post by nanotube on 2006-06-12
[QUOTE=munwin]Thank you very much.
Yep - all working now.
I can now continue with auditing (remote) Ubuntu boxen, and add them into my SF project (see sig).

Thanks again.[/QUOTE]
cool :) seems like a nice project, but runs only on windows?

---

### Post by sweetshubhi on 2010-01-14
[#!/bin/bash

RSYNC=/usr/bin/rsync
REMOTEUSER=rani
REMOTEHOST=192.168.1.99
REMOTEPATH=/home/rani/incrementalTestSrc
LOCALPATH=/home/rani/incrementalTestDest
PASS=rani
VAR=$(expect -c"
spawn rsync -av  $REMOTEUSER@$REMOTEHOST:$REMOTEPATH $LOCALPATH
expect \"password:\"
send \"$PASS\r\"
expect \"\\\\$\"
")

echo "==============="
echo "$VAR" 

hi i get lots of help from Ur code even my code also work really very well with some changes but im unable to understands expect \"\\\\$\" this line of code plz help me on that.again thanx a lot for ur help....

---

### Post by nanotube on 2010-01-15
> **sweetshubhi said:**
> 
hi i get lots of help from Ur code even my code also work really very well with some changes but im unable to understands expect \"\\\\$\" this line of code plz help me on that.again thanx a lot for ur help....

some extra escaping backslashes. i explained it in the post which contained the code - re-read carefully.

---

### Post by sweetshubhi on 2010-01-18
ya now i got it thanx a lot.

---

### Post by sweetshubhi on 2010-01-18
currently i m working on roaming profile where linux is the server & windows is the client ....i m implementing it using samba as pdc my linux version is 2.6.27.5-117.fc10.x86_64
and i m trying to install 
sudo dpkg-reconfigure debconf

sudo apt-get install slapd ldap-utils
when i tried to install these packages using yum it gives me the following reply

Loaded plugins: refresh-packagekit
fedora                                                                                                 | 2.8 kB     00:00     
updates                                                                                                | 3.4 kB     00:00     
Setting up Install Process
Parsing package install arguments
No package slapd available.
No package ldap-utils available.
Nothing to do


i dont understand what is the problem plz suggest me the soln or can u plz tell me the other way to have the roaming profile.thanx in advance..........

---

### Post by amorphinator on 2011-04-24
Thank you.

Worked great when adding ssh keys as well.
[HTML]
#!/bin/bash
keyfile='dedicated'
keypass='lalalala'

#do not edit below

countlines=`ssh-add -l |grep $HOME/.ssh/$keyfile |wc -l`
if [ "$countlines" != "1" ]; then
keyadd=$(expect -c "
spawn ssh-add $HOME/.ssh/$keyfile
expect \"$keyfile:\"
send \"$keypass\r\"
expect eof
")
echo "Added SSH Key"
fi

[/HTML]

---

