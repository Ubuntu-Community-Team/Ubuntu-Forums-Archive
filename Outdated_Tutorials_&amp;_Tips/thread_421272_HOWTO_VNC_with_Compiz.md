---
title: "HOWTO: VNC with Compiz"
date: 2007-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Virtual DarKness on 2007-04-24
Browsing the forum I've found this page:
[http://bugs.beryl-project.org/ticket/385](http://bugs.beryl-project.org/ticket/385)

That suggests to use x11vnc in order to have vnc working with compiz/beryl enabled..

So I've made a little script to make things a bit easier:

```
#!/bin/sh

IP=`zenity --entry --title 'Insert IP' --text 'Connect to server:' --entry-text '192.168.1.'`
login_user=''
#login_user=`zenity --entry --title 'Insert user name' --text 'ssh User Name:' --entry-text $USER`
x11vnc_cmd='x11vnc -once -noxdamage -bg'
if [ -n "$login_user" ]; then
	ssh -l $login_user $IP $x11vnc_cmd
else
	ssh $IP $x11vnc_cmd
fi
vncviewer $IP
```

You can change the zenity's "entry-text" parameter to fit better your network settings..

What this script does is:
- popup a input message window that asks the IP the user wants to connect to (with some pre-input text for fastest input)
- launch x11vnc to the remote machine via ssh (if you are not an authorized host you have to run/open the script in terminal and insert the ssh password)
- connect using vncviewer

after you close vncviewer x11vnc will also be closed as the "once" parameter (that anyway should be active by default) is used.

If you need to connect via ssh using a different user just uncomment the line "#login_user=..."

so.. it's a bit tricky but for me it works (on feisty with compiz 0.5.0)

feedback is welcome ;-)

ciao,
Giovanni.

---

### Post by ario on 2010-08-27
It doesn't work!:-(
It asked me for password, when I entered password opened a window with my remote desktop in it, and with always other solutions it shows just a constant frame of my desktop without any changes I make in it. I can not see my cursor just a black dot. Whenever I open a window can not see it remotely but can see it on main computer's monitor.
I can scroll remote window to right and down because remote computers resolution is more than my laptop's but can not scroll back to left and up.
It doesn't work man:(
Compiz still wont work with VNC.

---

