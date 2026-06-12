---
title: "HOWTO: Connect to another user's console terminal using 'screen'"
date: 2006-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by dbott67 on 2006-11-13
Recently, I was helping another forum member setup and troubleshoot an SSH server and we were looking for an easy way to "share the terminal", so that he could see what I was typing & vice-versa.  The problem was that he was on dial-up and using VNC was not a very feasible option.

In the end, I just created a local account on my computer so that he could SSH into my computer and we used the 'write' command to pass messages back and forth between us.  After we resolved the problem, I was still interested in finding out if there was an application that allowed users to "share" a terminal session (i.e. they could both interact with the same terminal session and see what the other was typing).

After doing some searching, I found 'screen', which is labeled as a "Remote terminal viewer".  Most of these steps are pulled verbatim from this [article]("http://www.linux.com/article.pl?sid=06/08/14/1945249"), however, I made some minor modifications for clarity and added a few steps for the new user.

**_Case Scenario:_**

Assume user **jsmith** wants to share his terminal session with remote user **bjones** for training or troubleshooting purposes, but does not want to use VNC or other full-blown GUI remote control access.  

**_Requirements:_**
- GNU Screen
- Local account on host computer for remote user (i.e. bjones requires local account)

1. Install screen
```
sudo apt-get install screen
```

2. Set the screen binary (**/usr/bin/screen**) setuid root. By default, screen is installed with the setuid bit turned off, as this is a potential security hole.
```
sudo chmod +s /usr/bin/screen
```
```
sudo chmod 755 /var/run/screen
```

3.  The host starts screen in a local xterm, using the command **screen -S SessionName**. The **-S** switch gives the session a name, which makes multiple screen sessions easier to manage.
```
screen -S screen-test
```

4.  The remote user (bjones) uses SSH to connect to the host computer (jsmith).
```
ssh bjones@jsmith.computer.ip.address
```

5.  The host (jsmith) then has to allow multiuser access in the screen session via the command **CTRL-A :multiuser on** (all 'screen' commands start with the screen escape sequence, **CTRL-A**).
```
CTRL-A
:multiuser on
```

6. Next, the host (jsmith) must grant permission to the remote user (bjones) to access the screen session using the commadn **CTRL-A :acladd user_name** where *user_name* is the remote user's login ID.
```
CTRL-A
:acladd bjones
```

7. The remote user can now connect to the hosts 'screen' session. The syntax to connect to another user's screen session is **screen -x host_username/sessionname**.
```
screen -x jsmith/screen-test
```

Attached is a screenshot of 2 computers "sharing" the same terminal session.

-Dave

---

### Post by 23meg on 2006-11-14
This has potential to be very useful, thank you. It seems there's no end to the conveniences of screen.

---

### Post by zach12 on 2007-07-05
wow cool i'm going to set up web/email server and if i can config it from my laptop that would cool!!!

---

### Post by adrianmak on 2007-11-27
however the remote computer should open a ssh port on the firewall.
Is it possible to do similar thing as reverse vnc ? or I called it reserve ssh such that remote side initiate a ssh call to the remote helpdesk.

---

### Post by dbott67 on 2007-11-27
> **adrianmak said:**
> however the remote computer should open a ssh port on the firewall.
Is it possible to do similar thing as reverse vnc ? or I called it reserve ssh such that remote side initiate a ssh call to the remote helpdesk.

Yes... see my signature below for "[HOWTO: Reverse VNC]("http://www.ubuntuforums.org/showthread.php?t=299489")".

Be advised that it does not work with the latest version of Ubuntu (Gutsy 7.10).

-Dave

---

### Post by dbott67 on 2007-11-27
Oops, sorry.  I misread your question.  I thought you wanted to "Reverse VNC" (rather than "Reverse SSH").

Please ignore my post.

-Dave

---

### Post by adrianmak on 2007-11-27
If I just want to share console terminal, is it possible to do a reverse ssh ?

---

### Post by trwww on 2008-04-02
how do you cleanly leave the user's screen? I did screen -d and that completely detached it.

Thanks for the tips!

---

### Post by Weazel on 2009-02-25
when inside Screen - enter " Ctrl + A + D "
that will leave the screen open until the screen is reentered and detached.


another useful way of using the screen if the people who wish to talk are on the same user and machine.

one needs to type " screen "
and once it is open
the other maye type " screen -x "

that will enter the previous screen session if no other are already open.

Weazel.

---

### Post by RealG187 on 2009-09-16
I too am having this issue:

[http://ubuntuforums.org/showthread.php?t=1267497](http://ubuntuforums.org/showthread.php?t=1267497)

---

### Post by papyromancer on 2009-10-03
I've followed your instructions, but I get an error on trying to connect the second user to the screen:

Must run suid root for multiuser support.

I'm running 8.04 without x.

---

### Post by sipickles on 2010-10-28
@papyromancer: Did you ever resolve this? I have exactly the same error on 9.04

---

