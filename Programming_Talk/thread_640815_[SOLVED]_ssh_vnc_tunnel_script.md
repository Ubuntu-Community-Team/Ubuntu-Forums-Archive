---
title: "[SOLVED] ssh vnc tunnel script"
date: 2007-12-14
forum: Programming Talk
---

### Post by wormser on 2007-12-14
Does anybody here have a script for a ssh vnc tunnel?  I have not got into scripting yet and cannot find anything out there already.  Basically the script needs to run the following commands.

ssh -L 5900:localhost:5900 myserver
xvncviewer localhost:5900

The vnc command also needs to make sure the ssh command has connected.  The ssh password is taking care of with certified keys.

Thanks.

---

### Post by geirha on 2007-12-14
Here's a script very similar to what you want [http://ubuntuforums.org/showthread.php?t=614894](http://ubuntuforums.org/showthread.php?t=614894)

---

### Post by wormser on 2007-12-14
Thanks for the link,  I am having problems figuring out where to put my information into it.

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

I always get the following error:
> ./testsshvnc: line 6: syntax error near unexpected token `)'
./testsshvnc: line 6: `selected)'


---

### Post by geirha on 2007-12-14
Sounds like line 5 has been split into two lines. Make sure your editor doesn't automatically split (word wrap) long lines. 

When you run the script it will ask you what hostname you want to connect to. Alternatively you can specify it on the command-line ```
./testsshvnc example.com
```

---

### Post by jpkotta on 2007-12-14
Here is what I use:
```

#!/bin/bash

usage="$0 [user@]remote_host"

if [[ x$1 == x"" ]] ; then
    echo $usage
    exit 1
fi

#ssh -L 5900:localhost:5900 $1 'x11vnc -localhost -display :0 -scale 4/5 -bg' 
ssh $1 'x11vnc -localhost -display :0 -scale 4/5 -bg' 
vncviewer -via $1 -encodings 'copyrect tight zrle hextile' localhost:0

```

Unfortunately, you need to enter the password twice.

---

### Post by wormser on 2007-12-14
> **geirha said:**
> Sounds like line 5 has been split into two lines. Make sure your editor doesn't automatically split (word wrap) long lines. 

When you run the script it will ask you what hostname you want to connect to. Alternatively you can specify it on the command-line ```
./testsshvnc example.com
```

I was using nano and that was the problem.  I pasted it into gedit and it works.  Thank you!

---

### Post by wynneth on 2009-06-20
In case someone comes across this thread looking for how to do this, a script is unnecessary. Simply use the following command: [code]xvncviewer -via sshmachineaddress vncserveraddress[code] Where sshmachineaddress is the hostname/ip of the machine you will ssh tunnel to, and vncserveraddress is the host/ip of the vncserver (as known to the ssh machine). So you could for instance do:[code]xvncviewer -via windowsblows.linux.org 127.0.0.1[code] Which would tunnel ssh to windowsblows.linux.org, and connect to a vncserver on the SAME machine.
See man xvncviewer for details.

---

