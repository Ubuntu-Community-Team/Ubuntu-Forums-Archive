---
title: "Using Remote Deskop Viewer to access multiple remote user accounts"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by dblack on 2008-10-19
I have one computer in one room (with Ubuntu 8.04) that I'd like to use to remote desktop into a second computer (with Ubuntu 8.04). The second computer has two user accounts. I'd like to get to the account that's not currently active.

I've tried this, and can log into and control the desktop that's active, but if I try to get to the non-active (logged out?) desktop, I just get a black screen.

Is it possible to use remote desktop viewer to access the logged out session on the remote computer?

---

### Post by jpkotta on 2008-10-21
I don't use the "Remote Desktop Viewer" or "Inactive accounts" (I assume you mean that the user is still logged in, but the screen is locked and you've started another session as another user).

I use VNC and ssh.  And I use this script to do it.  Maybe there is an easier way than this.  

You need ssh server and x11vnc on the remote host.
```
sudo aptitude install openssh-server x11vnc
```

vncviewer should already be installed on the local host.

```
#!/bin/bash

usage="$0 [user@]remote_host [<DISPLAY>]"

login="$1"
if [[ -z "$login" ]] ; then
    echo $usage
    exit 1
fi

disp="$2"
if [ -z "$disp" ] ; then
    disp=:0
fi

ssh "$login" "x11vnc -localhost -display '$disp' -scale 4/5 -bg" 
vncviewer -via "$login" localhost"$disp"
```

The graphical sessions are each running on top of an X server, and X servers are named with "display numbers".  The first one is display :0, the second is usually :1, etc.  So I would try to specify different display numbers.  You can learn what all the display numbers of all the X servers are with:
```
ssh user@remote ps -ef | grep /usr/bin/X | grep -v grep
```
```
root     24164  5459  2 Sep12 tty7     1-03:20:18 /usr/bin/X -br -nolisten tcp **:0** vt7 -auth /var/run/xauth/A:0-bVEvAM
```

And for fun, you can vnc into your local machine, and get an infinite desktop:
```
vnc_ssh localhost
```

---

