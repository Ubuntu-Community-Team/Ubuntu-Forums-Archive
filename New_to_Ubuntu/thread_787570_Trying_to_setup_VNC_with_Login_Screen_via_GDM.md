---
title: "Trying to setup VNC with Login Screen via GDM"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Jrdgames on 2008-05-09
I was going to post this in general but my account can't post there for some reason.

Hello, I am trying to setup VNC on a Ubuntu Dapper Drake system according to this guide [https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c](https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c) first I noticed on step 2 that /etc/xinetd.d does not exist so I went to /etc/init.d and on step 4 when I try to run sudo /etc/init.d/xinetd restart it says "sudo: /etc/init.d/xinetd: command not found"

Can someone please help me? I can't really progress until I issue this command correctly can I?

Any help more than a link is greatly appreciated.

---

### Post by MaindotC on 2008-05-09
Anything that ends in a "d" is usually a daemon - a process that usually runs in the "background" where you don't see it.  If you could see it, it would be in a terminal and constantly spitting out lines of output showing how it reacts to any event.

For example, in order for all initial daemons to start, the initd daemon has to be running (which is just a list of daemons and services).  The daemon to run the MySQL service is mysqld, http service is httpd, name resolution service is named, and so on.

You're looking for the xinetd daemon which is the eXtended INTernet Daemon.  I don't have this on my system which I determined using:
```

sudo updatedb
sudo locate xinetd
[code]

so I think it's been replaced with the command:

[code]
sudo /etc/init.d/networking restart

```

Try that in place of calls for xinetd.  If you want, you can download xinetd by using:

```

sudo apt-get update
sudo apt-get install xinetd

```

---

### Post by Jrdgames on 2008-05-09
Thankyou, that looks like it worked for step 4.

Now the server seems to have some problems because when I try to connect I see the password prompt so I enter it and then this comes up in terminal:
```
jrdinc@jrdserver1:~$ vncviewer localhost:!

VNC Viewer Free Edition 4.1.1 for X - built Mar 11 2005 16:09:29
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Fri May  9 09:25:45 2008
 CConn:       connected to host localhost port 5900
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7
Aborted
```
Strange thats an exclamtion mark I didn't notice that until now, heres what happens when it's a 1:
```
jrdinc@jrdserver1:~$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Mar 11 2005 16:09:29
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Aborted
```

When I try to start a session as described in the problems area I get this:
```
jrdinc@jrdserver1:~$ Xvnc :1 -fp /usr/share/fonts/X11/misc/
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

Xvnc Free Edition 4.1.1 - built Mar 11 2005 16:09:48
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40201000, The XFree86 Project, Inc


Fri May  9 09:35:50 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/fonts/X11/misc/, removing from list!
Fatal server error:
could not open default font 'fixed'
```

Does anyone have any ideas? I really do appreciate your help.

EDIT
I just tried changing the font path and lauching the server with this command:Xvnc :1 -fp /usr/share/X11/fonts/misc/ and it passed the font problem it now shows up like this:
```
jrdinc@jrdserver1:~$ Xvnc :1 -fp /usr/share/X11/fonts/misc/
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'

Xvnc Free Edition 4.1.1 - built Mar 11 2005 16:09:48
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40201000, The XFree86 Project, Inc


Fri May  9 11:52:32 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
```
And then I tried connecting with another terminal and I was prompted for my password so I entered itand it failed to connect with the following being outputted in the server terminal:
```
Fri May  9 11:59:27 2008
 Connections: accepted: 127.0.0.1::37832
 SConnection: Client needs protocol version 3.8

Fri May  9 11:59:28 2008
 SConnection: Client requests security type VncAuth(2)

Fri May  9 11:59:44 2008
 SSecurityFactoryStandard: neither Password nor PasswordFile params set
Aborted
```
Any ideas? maybe I need to try to find this /usr/X11R6/lib/X11/xserver/SecurityPolicy?

---

### Post by MaindotC on 2008-05-09
I just got to the forums so I haven't read all of your post, but in the meantime, can you try using a :0 instead of a :1 ?

Also, I'm not sure what Dapper is like but in later versions you can set up VNC by going to System -> Preferences -> Network or Remote Desktop.  Do you have a menu like that in Dapper?  Sorry if that's an obvious question.  I'll disect the rest of your post in a bit.

---

### Post by maybeway36 on 2008-05-09
I just use x11vnc to share my physical session over the network. (See my sig.) You might want to try that.
To make it even easier, you can install x11vnc and type in a terminal:
```
x11vnc -many
```

---

### Post by Jrdgames on 2008-05-09
> **strAlan said:**
> I just got to the forums so I haven't read all of your post, but in the meantime, can you try using a :0 instead of a :1 ?
0 also crashes.
> Also, I'm not sure what Dapper is like but in later versions you can set up VNC by going to System -> Preferences -> Network or Remote Desktop.  Do you have a menu like that in Dapper?  Sorry if that's an obvious question.  I'll disect the rest of your post in a bit.
Yes the menu is the same as in latter and former versions and I have used that but I can't use that unless a user is currently logged in and even then that won't work when either another user is currently logged in or noone is logged in and I am away from home.

> **maybeway36 said:**
> I just use x11vnc to share my physical session over the network. (See my sig.) You might want to try that.
To make it even easier, you can install x11vnc and type in a terminal:
```
x11vnc -many
```

I will try this but I would still like to work on the other and find out why it doesn't work.

Thank you for your help, both of you.

---

### Post by MaindotC on 2008-05-09
Oh I see what you're saying about a user being logged in.  Actually, I can't help because I've been trying to figure out the same thing!  The only way I can VNC into my box is if I go to the lab, log in, and then lock the screen and shut off the monitor.  If I do a reboot I'm screwed even if I set the IP statically.  It sucks b/c sometimes people are in the lab and see me working on it so they start messing w/ the mouse or walling me messages like "You are being watched".

---

### Post by Jrdgames on 2008-05-09
> **strAlan said:**
> Oh I see what you're saying about a user being logged in.  Actually, I can't help because I've been trying to figure out the same thing!  The only way I can VNC into my box is if I go to the lab, log in, and then lock the screen and shut off the monitor.  If I do a reboot I'm screwed even if I set the IP statically.  It sucks b/c sometimes people are in the lab and see me working on it so they start messing w/ the mouse or walling me messages like "You are being watched".

Yup and this is going to be for a computer which I won't have phisical access to so logging in at the console is not an option and everything needs to be able to be setup from ssh.

Working on this x11vnc I got to step 2 of setup and ran the command isted *ps wwaux | grep auth* and it outputted this:
```
root@jrdserver1:~# ps wwaux | grep auth
root      4380  0.0  0.1   1732   392 ?        S    May08   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/authdaemon/pid -start /usr/lib/courier/authlib/authdaemond.plain
root      4381  0.0  0.1   1836   524 ?        S    May08   0:00 /usr/lib/courier/authlib/authdaemond.plain
root      4410  0.0  0.0   1836   260 ?        S    May08   0:00 /usr/lib/courier/authlib/authdaemond.plain
root      4411  0.0  0.0   1836   260 ?        S    May08   0:00 /usr/lib/courier/authlib/authdaemond.plain
root      4412  0.0  0.0   1836   260 ?        S    May08   0:00 /usr/lib/courier/authlib/authdaemond.plain
root      4413  0.0  0.0   1836   260 ?        S    May08   0:00 /usr/lib/courier/authlib/authdaemond.plain
root      4414  0.0  0.0   1836   260 ?        S    May08   0:00 /usr/lib/courier/authlib/authdaemond.plain
root      4461  0.0  0.1   1824   484 ?        S    May08   0:00 /usr/sbin/couriertcpd -address=0 -stderrlogger=/usr/sbin/courierlogger -maxprocs=40 -maxperip=20 -pid=/var/run/courier/imapd.pid -nodnslookup -noidentlookup 143 /usr/lib/courier/courier/imaplogin /usr/lib/courier/authlib/authdaemon /usr/bin/imapd Maildir
root      4517  0.0  0.1   1828   484 ?        S    May08   0:00 /usr/sbin/couriertcpd -address=0 -stderrlogger=/usr/sbin/courierlogger -stderrloggername=imapd-ssl -maxprocs=40 -maxperip=20 -pid=/var/run/courier/imapd-ssl.pid -nodnslookup -noidentlookup 993 /usr/bin/couriertls -server -tcpd /usr/lib/courier/courier/imaplogin /usr/lib/courier/authlib/authdaemon /usr/bin/imapd Maildir
root      4565  0.0  0.1   1824   480 ?        S    May08   0:00 /usr/sbin/couriertcpd -pid=/var/run/courier/pop3d.pid -stderrlogger=/usr/sbin/courierlogger -maxprocs=40 -maxperip=4 -nodnslookup -noidentlookup -address=0 110 /usr/lib/courier/courier/courierpop3login /usr/lib/courier/authlib/authdaemon /usr/lib/courier/courier/courierpop3d Maildir
root      4648  0.0  0.1   1824   480 ?        S    May08   0:00 /usr/sbin/couriertcpd -pid=/var/run/courier/pop3d-ssl.pid -stderrlogger=/usr/sbin/courierlogger -stderrloggername=pop3d-ssl -maxprocs=40 -maxperip=4 -nodnslookup -noidentlookup -address=0 995 /usr/bin/couriertls -server -tcpd /usr/lib/courier/courier/courierpop3login /usr/lib/courier/authlib/authdaemon /usr/lib/courier/courier/courierpop3d Maildir
root      5023  0.0  0.2   6016   988 ?        Ss   May08   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
root      5029  0.0  0.1   6016   588 ?        S    May08   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
root      5030  0.0  0.1   6016   536 ?        S    May08   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
root      5031  0.0  0.1   6016   536 ?        S    May08   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
root      5032  0.0  0.1   6016   536 ?        S    May08   0:00 /usr/sbin/saslauthd -m /var/spool/postfix/var/run/saslauthd -a pam
root     18529  0.0  0.2   2880   812 pts/0    S+   18:58   0:00 grep auth
```

and it say it should output something similar to this:
> root      3838 10.1  1.7  13308  8840 tty7     Ss+  15:35   2:14 /usr/bin/X -br -nolisten tcp :0 vt7 -auth **/var/run/xauth/A:0-LliKdB**
erik      5156  0.0  0.1   2800   752 pts/0    R+   15:57   0:00 grep auth
And I need to find something similar to the bold part but I don't see anyhing even remotely similar, Do you see what I should be looking for?

EDIT

I found the file ~/.Xauthority so I am going to try it, I can always change it if anyone comes up with something else or it doesn't work.

EDIT2

I finished all the steps in the guide but now x/gdm doesn't want to start :( I tried changing the gdm conf back and restarting gdm but it didn't help any, since this thread isn't about this mainly I probably won't get any help on it but any help is greatly appreciated.

---

