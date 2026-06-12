---
title: "How to do Freenx'ing via VNC (with Nomachine)"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by Cursed Lemon on 2013-04-03
To make a long story short, I've been trying to get VNC to work over Nomachine/Freenx because of using Mint on one of my systems, and Mint doesn't seem to have a desktop environment that is compatible with the normal "Unix" option on Nomachine (correct me if I'm wrong). 

However, I can't even get a VNC connection to work in a Ubuntu > Ubuntu setup, and I fear I'm just flat out doing something wrong. 

On the target system, I set up a VNC server using: 

```
support@idaho ~ $ vncserver

You will require a password to access your desktops.

Password:
Verify:
Would you like to enter a view-only password (y/n)? n

New 'X' desktop is idaho:1

Creating default startup script /home/support/.vnc/xstartup
Starting applications specified in /home/support/.vnc/xstartup
Log file is /home/support/.vnc/idaho:1.log
```

Keep in mind that in this particular instance, this is occurring over LAN. 

After that, I boot up Nomachine on my other system. 

[IMG]http://i.imgur.com/nNt6nys.png[/IMG]

I attempt to connect, and it shows the following sessions:

[IMG]http://i.imgur.com/tU44VbG.png[/IMG]

I select X1. after which I get this error report from Nomachine:

```
NX> 203 NXSSH running with pid: 6387
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.2.68 on port: 6219
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
Welcome to Linux Mint 13 Maya (GNU/Linux 3.2.0-23-generic i686)

Welcome to Linux Mint
 * Documentation:  http://www.linuxmint.com

73 packages can be updated.
0 updates are security updates.

HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.5.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: support
NX> 102 Password: 
NX> 103 Welcome to: idaho user: support
NX> 105 listsession --user="support" --status="suspended,running" --geometry="3286x1080x24+render" --type="vnc"
NX> 127 Sessions list of user 'support' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            12A088CC4F05878AB5AFF4E3BE307E9D --------       3286x1080      Running     X0 (Local)
1       Local            1DCB620EBCE45516C1939398320E6DD3 --------       3286x1080      Running     X1 (Local)
0       Local            6B63F66BA4DC085E11300036D53508B4 --------       3286x1080      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: support
NX> 105 listsession --user="support" --status="suspended,running" --geometry="3286x1080x24+render" --type="vnc"
NX> 127 Sessions list of user 'support' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            12A088CC4F05878AB5AFF4E3BE307E9D --------       3286x1080      Running     X0 (Local)
1       Local            1DCB620EBCE45516C1939398320E6DD3 --------       3286x1080      Running     X1 (Local)
0       Local            6B63F66BA4DC085E11300036D53508B4 --------       3286x1080      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: support
NX> 105 listsession --user="support" --status="suspended,running" --geometry="3286x1080x24+render" --type="vnc"
NX> 127 Sessions list of user 'support' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            12A088CC4F05878AB5AFF4E3BE307E9D --------       3286x1080      Running     X0 (Local)
1       Local            1DCB620EBCE45516C1939398320E6DD3 --------       3286x1080      Running     X1 (Local)
0       Local            6B63F66BA4DC085E11300036D53508B4 --------       3286x1080      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: support
NX> 105 listsession --user="support" --status="suspended,running" --geometry="3286x1080x24+render" --type="vnc"
NX> 127 Sessions list of user 'support' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            12A088CC4F05878AB5AFF4E3BE307E9D --------       3286x1080      Running     X0 (Local)
1       Local            1DCB620EBCE45516C1939398320E6DD3 --------       3286x1080      Running     X1 (Local)
0       Local            6B63F66BA4DC085E11300036D53508B4 --------       3286x1080      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: support
NX> 105 listsession --user="support" --status="suspended,running" --geometry="3286x1080x24+render" --type="vnc"
NX> 127 Sessions list of user 'support' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            12A088CC4F05878AB5AFF4E3BE307E9D --------       3286x1080      Running     X0 (Local)
1       Local            1DCB620EBCE45516C1939398320E6DD3 --------       3286x1080      Running     X1 (Local)
0       Local            6B63F66BA4DC085E11300036D53508B4 --------       3286x1080      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: support
NX> 105 listsession --user="support" --status="suspended,running" --geometry="3286x1080x24+render" --type="vnc"
NX> 127 Sessions list of user 'support' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            12A088CC4F05878AB5AFF4E3BE307E9D --------       3286x1080      Running     X0 (Local)
1       Local            1DCB620EBCE45516C1939398320E6DD3 --------       3286x1080      Running     X1 (Local)
0       Local            6B63F66BA4DC085E11300036D53508B4 --------       3286x1080      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: support
NX> 105 listsession --user="support" --status="suspended,running" --geometry="3286x1080x24+render" --type="vnc"
NX> 127 Sessions list of user 'support' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------
0       Local            12A088CC4F05878AB5AFF4E3BE307E9D --------       3286x1080      Running     X0 (Local)
1       Local            1DCB620EBCE45516C1939398320E6DD3 --------       3286x1080      Running     X1 (Local)
0       Local            6B63F66BA4DC085E11300036D53508B4 --------       3286x1080      Running     X0 (Local)


NX> 148 Server capacity: not reached for user: support
NX> 105 restoresession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="X1%20(Local)" --type="vnc" --agent_server="idaho%3A1" agent_password="******" --geometry="3286x1028" --client="linux" --keyboard="pc105/us" --id="1DCB620EBCE45516C1939398320E6DD3" 

NX> 596 Could not find shadowed session 1DCB620EBCE45516C1939398320E6DD3. Session failed.
NX> 596 Sharing: 
NX> 105 NX> 280 Exiting on signal: 15


```

I'm not sure why it says "could not find shadowed session," as I'm not actually attempting to run a shadow session, but then again, that's why I'm asking you guys. 

Anyone have any advice?

---

