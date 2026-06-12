---
title: "Keep a program running after logging out of ssh session"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by jbrown96 on 2008-11-26
I went home for Thanksgiving, so I don't have access to my box. I restarted it via ssh and need to start Transmission again. How can I launch it via ssh and have it remain open after I log out??

thanks

---

### Post by opscure on 2008-11-26
didn't test it, but I think this will work for you:

```
ssh server 'program </dev/null >/dev/null 2>&1 &' 
```

---

### Post by Peter09 on 2008-11-26
Well there is supposed to be a command
detach
which will do this, however some seem to be saying that it does not work.

The best way to do this would be to install FreeNX, which will allow a session to run detached. Its relatively easy to do.


Here is the site

[http://freenx.berlios.de/download.php](http://freenx.berlios.de/download.php)

---

### Post by Titan8990 on 2008-11-26
I havn't tested this but wouldn't he be able to just disown the command like he was on the local machine?


sudo myscript.sh && disown

---

### Post by unutbu on 2008-11-26
```
ssh user@server
nohup transmission &           # nohup does what you want
exit
ssh user@server
ps axuw | grep transmission    # check that transmission is still running
exit

```

---

### Post by Peter09 on 2008-11-26
The trouble is that when you disconnect from the server there is no X-session left running so the application terminates.

---

### Post by jbrown96 on 2008-11-26
> **opscure said:**
> didn't test it, but I think this will work for you:

```
ssh server 'program </dev/null >/dev/null 2>&1 &' 
```

I tried this and it doesn't work. 
I can run it in screen and detach it, but when I logout (even detaching a session) causes transmission to stop.

Remote Desktop would be fine, but I can't change my router's firewall settings unless I'm on the network. 

Any suggestions?

---

### Post by unutbu on 2008-11-26
Edit: I've tested this; it works:
```

ssh -x user@server
nohup sudo /usr/bin/X11/xinit transmission -- :1
```

The -x flag disables X11 forwarding.

---

### Post by opscure on 2008-11-26
:confused:

so screen detaches it but it still stops?   What program is it if you don't mind me asking?

---

### Post by binbash on 2008-11-26
i always do this at my servers : 

blablacommand &

then do whatever you want

---

### Post by Titan8990 on 2008-11-26
That will not disown the program from the terminal.

---

### Post by Wicca on 2008-11-26
I use screen.
```
sudo apt-get install screen
```
I you have started a ssh connection to your box start 'screen' first. Then do your thing. Detach from the session by pressing Ctrl-a and then Ctrl-d. Close the ssh connection. Your session will remain active forever (untill the powercut:lolflag:).
After reconnecting do a 'screen -r' to connect to your session again.
With screen it is even possible to have multiple sessions running at the same time.

Good luck.

---

### Post by david_lynch on 2008-11-26
If you want an app that continues to run after you're logged out, you may need to find a command line app. The problem with an X windows app is that it's associated with an X session. If you end the X session, the app has nowhere to live. 

There are plenty of command line bittorrent clients to choose from. Then you can start them with screen, detatch, and reattach at will, as others have mentioned.

---

### Post by nhasian on 2008-11-26
what about the bittorrent client deluge?  you can have the daemon startup automatically when the pc boots, then you can remotely control it from any pc either over the internet via its website or connecting to the remote deluge daemon from your local machine.

---

### Post by Peter09 on 2008-11-26
FreeNX uses ssh for communication so 'I think' it should work without changes to your firewall. (I think)...

---

