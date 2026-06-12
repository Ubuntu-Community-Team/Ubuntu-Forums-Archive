---
title: "SIMPLE bash script"
date: 2007-11-16
forum: Programming Talk
---

### Post by truse on 2007-11-16
Hi

Im trying to make a script that wil help me set up the connection to use vnc over ssh.

It looks like this:
----------------------------------
#!/bin/bash

clear
echo -n "Server ip:  "
read server

gnome-terminal -e "sleep 5 && vncviewer localhost:1"

ssh -l <myusername> -L 5901:127.0.0.1:5900 $server
----------------------------------

what happens is that the ssh connection works FINE, but when the other gnome-terminal window opens, it does _NOTHING_.. :/

I need the other gnome-terminal window to sleep before the "vncviewer localhost:1" command,  because i can`t connect to localhost before the ssh connection is established. I dont know if im doing the  "gnome-termina -e"  thing wrong or what.. 

I hope someone can laugh at me and tell me what im doing wrong here :p

---

### Post by Nekiruhs on 2007-11-16
> **truse said:**
> Hi

Im trying to make a script that wil help me set up the connection to use vnc over ssh.

It looks like this:
----------------------------------
#!/bin/bash

clear
echo -n "Server ip:  "
read server

gnome-terminal -e "sleep 5 && vncviewer localhost:1"

ssh -l <myusername> -L 5901:127.0.0.1:5900 $server
----------------------------------

what happens is that the ssh connection works FINE, but when the other gnome-terminal window opens, it does _NOTHING_.. :/

I need the other gnome-terminal window to sleep before the "vncviewer localhost:1" command,  because i can`t connect to localhost before the ssh connection is established. I dont know if im doing the  "gnome-termina -e"  thing wrong or what.. 

I hope someone can laugh at me and tell me what im doing wrong here :p
Commands don't run simultaneously. Right now, its waiting, then trying to connect to localhost, then doing SSH. Its not going on at the same time. If i understand your problem correctly, try this:

```
#!/bin/bash

clear
echo -n "Server ip:  "
read server

ssh -l <myusername> -L 5901:127.0.0.1:5900 $server

gnome-terminal -e "sleep 5 && vncviewer localhost:1"

```

---

### Post by truse on 2007-11-17
Thanks for the fast reply!

I tried the code, the ssh connection establishes and i am connected to the server. (which is right)  BUT, I dont get the new terminal window unless i disconnect the ssh connection. (which is wrong.. cause i need the ssh connection to be up/established to use the vncviewer localhost:1)

any other sugestions? :)

I remind that if i open a terminal window MANUALY, i can do the "vncviewer localhost:1" without any problems.. i just want it to go automatic! :s

---

### Post by geirha on 2007-11-17
the -e option to gnome-terminal only excepts one process, so you'll have to spawn a new bash process. Here's your script with some modifications. Instead of sleep 5, it waits until port 5901 is bound.
```
#!/bin/bash

if [ "$1" == "" ]; then
    server=`zenity --entry --text="Enter hostname:" --title="VNC"`
    if [ ! $? == 0 ] ; then     # If zenity failed (i.e. cancel was selected)
        exit 1
    fi
else
    server=$1
fi

gnome-terminal -e '/bin/bash -c "while ! netcat -z localhost 5901; do sleep 1; done; vncviewer localhost:1"'

ssh -L 5901:localhost:5900 $server

```

Not a perfect solution, but it should work :)

---

### Post by truse on 2007-11-17
wow..! Thanks =) Works like a dream! :popcorn:

---

