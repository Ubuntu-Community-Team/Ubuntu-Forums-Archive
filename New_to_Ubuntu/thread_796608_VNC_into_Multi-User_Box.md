---
title: "VNC into Multi-User Box"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by MasterSushi on 2008-05-16
Let me first explain what I am trying to do and then I will share what I have done.

I want to remote into my Ubuntu PC and either a.) log into a specific session or b.) simply see what is on the screen no matter who is logged in.

**Here is what I have done:**

I have configured Remote Desktop logged in under my account. As long as I am logged in and can see my desktop I can remote into this PC and it works perfectly.

I then added some users and then used the switch user to go to the login screen. Now my monitor is at the login screen. So I attempted to VNC into my PC. The password prompt comes up and successfully connects, however I get a black screen. Now when I go back to my monitor I see a black screen with a cursor flashing at the top left.
[B]
Does anyone have any ideas for how can I use VNC on a multi-user system successfully?[/B]

---

### Post by bpowell2005 on 2008-05-17
Hi MasterSushi,

I'm pretty new to Ubuntu (and linux) but I have this working, and here's what I did. I installed Ubuntu, set up the remote desktop (just as you did) and verified it worked...I can RDP into the Ubuntu box (providing it's logged on) and view / control the desktop (much to the frustration of my wife!)...I then added a user, and logged in as that new user (locally, from the machine itself, not remote)...and changed my desktop background (just an easy way to verify which desktop I'm on).

I then installed ssh-server, and vnc4server. I set up vnc4server generally based on this post: [http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964) ... I didn't use Xine, I just installed the vnc4server software. I then ssh into the Ubuntu box as my new user, and I type "vncserver"...I get a reply saying, "VNC running on display :1" I can then VNC into the Ubuntu box using vncviewer 123.333.333.333:1 (rather than :0 for the active desktop) and after a password, I'm  on my new desktop. I can play on this desktop at the same time my wife is working on the local desktop...works like a champ...although now I can't see all the guys my wife is chatting with! ;)

I hope this helps.

Brendan

---

### Post by bodhi.zazen on 2008-05-17
Even better, tunnel vnc over ssh

[uwiki]VNCOverSSH[/uwiki]

---

### Post by MasterSushi on 2008-05-23
bpowell2005 - I will give this a try soemtime this coming week and see if it works out for me. Did you disable the default remote desktop setup in Ubuntu first?

---

### Post by MasterSushi on 2008-06-10
I was unsuccessful at getting this to work using vncserver. I kept getting black screens when connecting to a session that was not up on the monitor.

However, I found an application called **No Machine** at [http://www.nomachine.com]("http://www.nomachine.com") and installed the server into Ubuntu and then the client in windows and I am able to connect just as I had wanted to. This is truly a very elegant solution.

'No Machine' also seems to cache fonts and graphics locally to speed up the display over a remote connection.

The 'No Machine' install was as simple as installing three .deb files (and there are 64bit .debs available which I used). I then opened up port 22 for SSH on my router so I could connect remotely and I was ready to go. No complicated configuration.

---

