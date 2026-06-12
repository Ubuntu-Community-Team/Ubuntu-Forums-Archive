---
title: "HOWTO: Set up VNC server with resumable sessions"
date: 2006-01-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Tichondrius on 2006-01-27
[COLOR="Red"][b]Warning!
This howto is old, unsupported, and relies on a broken package. This should be used as reference only.[/b][/COLOR]

CLOSED THREAD

So here's the complete list of steps that are required to set the VNC server that any user can login into and start a session. It is also persistent, meanning that even if you disconnect the VNC client your X session will not end (unless you explicitly log out) and you can reconnect to the same session again. The VNC server uses a separate display (:1) than your regular X server, which works with your physical display (:0). So two sessions can be active at the same time (one person sitting at the physical display and another remotely connecting using VNC).

  1. Enable XDMCP
**System->Administration->Login Screen Setup**
      Tab **Security->Enable XDMCP**
      Tab **XDMCP**--> You can disable "Honor Indirect Requests"
    
Note: Before doing the next step, you need to make sure the extra repositories (e.g. universe) are enabled:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

  2. Install required packages (vncserver and xinetd)

```
sudo apt-get install vnc4server xinetd
```

Note to AMD64 users: The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:

```

wget http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb
wget http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb
sudo dpkg -i vnc4server_4.0-7.3_amd64.deb
sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb

```


  3. Set the VNC passwd
```
sudo vncpasswd /root/.vncpasswd
```

  4. Add vnc service to xinetd:
```
sudo gedit /etc/xinetd.d/Xvnc
```

Enter this into the new file:

```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

```

  5. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start
```

  6. That's it! To test that this is working first try to connect from the same machine (the machine we just set up the VNC server on):

```
vncviewer localhost:1
```

You should be prompted for the VNC password, and then see the GDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above). Remember to use the VNC server machine's domain name or IP address, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails, then this means you have a problem with a firewall which is blocking some ports. See the notes below about how to deal with that.

Note about ports: The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

Note about security: This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started.  So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300"  to change it to 5 minutes.

---

### Post by arnieboy on 2006-01-27
u are all set.. the other howto on VNC to GDM stands defunct from now on.

---

### Post by mssm on 2006-01-28
Tichondrius, Thanks a lot for the update. As I understand, I should remove the old /etc/xinted.conf file which the old how-to told us to create, right? I also found that XDMCP uses port 177 with UDP protocol. So this port should be taken in the router's config.(i.e. firewall and port forwarding)?

Can it be used to let a specific user login via vnc?

[COLOR="Red"]Update[/COLOR] : This is the output I got after I borught back /etc/xinited.conf to its original form and then following Tichondrius how-to. I have an AMD chipset, so I installed vncserver(instead of vnc4server). Moreover, I have opened port 177 in my router's firewall with UDP protocol and forwarded this port to my machine's internal LAN IP address. Also port 5901 is open in my firewall and forwarded to my laptop's LAN IP.

From the old how-to I still have this line in /etc/services 

 vnc1024 5901/tcp # VNC & GDM

Should I remove it? I am confused. I got this response by issuing the following command :

$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)

---

### Post by Tichondrius on 2006-01-28
You only need to do the steps in this howto. All other steps mentioned in the old howto (like editing /etc/xinetd.conf or /etc/services) are not required and may in fact interfere with this setup.

You need to have the original file /etc/xinetd.conf (from the xinetd package) which looks like this:

```

# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{


}

includedir /etc/xinetd.d

```

Notice how it instructs xinetd to load all the file in directory /etc/xinetd.d which is were we put the new Xvnc service configuration file. So restore the original /etc/xientd.conf if you made a backup copy, or just edit it to look like shown above.

After you've restarted the xinetd as shown in the step 5, you can check that xinetd is listening on port 5901 by doing this:

```
sudo netstat -tap | grep xinetd
```

And you should see a line like this: (your process ID doesn't have to be the same as mine 10932)

tcp        0      0 *:5901                  *:*                     LISTEN     10932/xinetd

Now you can try to connect with the local VNC client

```
vncviewer localhost:1
```

Let me know if this works.

---

### Post by mssm on 2006-01-28
Hi,

I have followed your instruction in toto but this command yields nothing :
sudo netstat -tap | grep xinetd

It just stays there without giving any output. Also I think the last line of step 5 of your how-to should be sudo /etc/init.d/xinetd start instead of sudo /etc/init.d/xinetd/start. I have also commented the line I entered in /etc/services following the old how-to.

I am running kubuntu though the display manager for login is gdm. Should I reboot then? Also I installed vncserver and not vnc4server since I have AMD64 chipset. Should I install vnc4server instead of vncserver?

---

### Post by Tichondrius on 2006-01-28
[QUOTE=mssm]Hi,

I have followed your instruction in toto but this command yields nothing :
sudo netstat -tap | grep xinetd

It just stays there without giving any output. Also I think the last line of step 5 of your how-to should be sudo /etc/init.d/xinetd start instead of sudo /etc/init.d/xinetd/start. I have also commented the line I entered in /etc/services following the old how-to.

I am running kubuntu though the display manager for login is gdm. Should I reboot then? Also I installed vncserver and not vnc4server since I have AMD64 chipset. Should I install vnc4server instead of vncserver?[/QUOTE]

Yes, please reboot. And then check again if xinetd is listening on port 5901 using the command 

```
sudo netstat -tap | grep xinetd
``` 

as I explained previously. If it still doesn't show anything, you should check the system log to see why xinetd didn't read the Xvnc service file.

```
grep xinetd /var/log/syslog
```

And you should see a few lines showing xinetd activity. Look for a line mentioning xvnc, it should look similar to this:

> Jan 27 03:42:32 localhost xinetd[10932]: Reading included configuration file: /etc/xinetd.d/Xvnc [file=/etc/xinetd.conf] [line=11]

Look for any error messages, or if it loaded successfully you should see another line which looks like this:

> Jan 27 03:42:32 localhost xinetd[10932]: Started working: 1 available service

btw, you are right about the spelling mistake in step 5, I corrected it. Also I understand you are using kubuntu on amd64, and if vnc4server package is not available for amd64, then vncserver (which is version 3.x) should be OK.

Let me know if this works.

---

### Post by mssm on 2006-01-28
Thanks Tichondrius. I rebooted and this time I got an answer from both the commands :

$ sudo netstat -tap | grep xinetd
tcp        0      0 *:5901                  *:*                     LISTEN     8397/xinetd

$ grep xinetd /var/log/syslog
Jan 28 15:05:06 localhost xinetd[8397]: Reading included configuration file: /etc/xinetd.d/Xvnc [file=/etc/xinetd.conf] [line=11]
Jan 28 15:05:06 localhost xinetd[8397]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.d/chargen] [line=12]
Jan 28 15:05:06 localhost xinetd[8397]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Jan 28 15:05:06 localhost xinetd[8397]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=26]
Jan 28 15:05:06 localhost xinetd[8397]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Jan 28 15:05:06 localhost xinetd[8397]: removing chargen
Jan 28 15:05:06 localhost xinetd[8397]: removing chargen
Jan 28 15:05:06 localhost xinetd[8397]: removing daytime
Jan 28 15:05:06 localhost xinetd[8397]: removing daytime
Jan 28 15:05:06 localhost xinetd[8397]: removing echo
Jan 28 15:05:06 localhost xinetd[8397]: removing echo
Jan 28 15:05:06 localhost xinetd[8397]: removing time
Jan 28 15:05:06 localhost xinetd[8397]: removing time 
Jan 28 15:05:06 localhost xinetd[8397]: Started working: 1 available service

Then 
$ vncviwer localhost:1 
gives me the same msg. as before. After this again I issued :
$ grep xinetd /var/log/syslog
which yielded 
Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Jan 28 15:08:18 localhost xinetd[8397]: Activating service Xvnc

But there were many error msgs.

What exactly should I get after issuing vncviewer localhost:1?

---

### Post by kacheng on 2006-01-28
I also get the following when issuing:

# vncviewer localhost:1
VNC viewer version 3.3.7 - built Sep 27 2005 12:10:30
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)


I am also running AMD64, with vncserver (not vnc4server) installed.

---

### Post by kacheng on 2006-01-28
I also get as mssm does:

# grep xinetd /var/log/syslog
Jan 28 08:29:56 localhost xinetd[13968]: warning: can't get client address: Transport endpoint is not connected
:
:
:
Jan 28 08:29:57 localhost xinetd[14180]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14181]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14182]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14183]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14184]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14185]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14186]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14187]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[10673]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Jan 28 08:30:07 localhost xinetd[10673]: Activating service Xvnc


What does this mean?

---

### Post by kacheng on 2006-01-28
I was just going through the HOWTO again and noticed that the Xvnc service doesn't seem to start:


$ sudo /etc/init.d/xinetd stop
Stopping internet superserver: xinetd.
$ sudo killall Xvnc
Xvnc: no process killed
$ sudo /etc/init.d/xinetd start
Starting internet superserver: xinetd.
$ sudo /etc/init.d/xinetd stop
Stopping internet superserver: xinetd.
$ sudo killall Xvnc
Xvnc: no process killed
$ sudo /etc/init.d/xinetd start
Starting internet superserver: xinetd.


I'll reboot and try again.

---

### Post by mssm on 2006-01-28
Yes, I also noticed like kacheng that no process is killed after issuing the command killall Xvnc.

---

### Post by Tichondrius on 2006-01-28
From your description it seems that after the reboot xinetd is listening on port 5901 and the setup is correct.

xinetd is supposed to start Xvnc as soon as it gets an incoming connection from a VNC client.

I assume you copied /etc/xined.d/Xvnc exactly from this howto without changing anything, right ?  if so, then maybe the fact you are using the old vnc sever (version 3.x) is related because it might not support some of the arguments ?   

After you start the vncviewer, xinetd should spwan Xvnc with the arguments specified in the Xvnc file we created in step 3.  So immediately after starting vncviewer (and even before entering the vnc password), you can check the Xvnc started by issueing this command:

```
ps -ef | grep Xvnc
```

This should show something like this:

> root      9777  9527  0 15:28 ?        00:00:00 Xvnc -inetd :1 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

If it doesn't work it means that Xvnc wasn't started. So in that case I would suggest to try starting Xvnc manually (not from within xinetd)  just to make sure it can run at all (we will use screen :2 so it doesn't overlap with the original Xvnc):

```
sudo Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
```

Now, from another terminal try to connect:

```
vncviewer localhost:2
```

tell me if that works......

---

### Post by mssm on 2006-01-29
Yes, I copied the /etc/xinetd.d/Xvnc exactly as you mentioned.

I issued : 
$ vncviewr localhost:1
which yields
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)

As you can see I am running vncserver 3.3.7, since I have an AMD64 chipset and in this matter I followed the old how-to by not installing vnc4server.

After this command I issued 
$ps -ef | grep Xvnc
which yields
myname  19963  8823  0 11:12 pts/1 00:00:00 grep Xvnc

Now I issued the big command :
$sudo Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

It asked for root passwd :
Password:
After entering the password, it said 
Unrecognized option: -DisconnectClients=0
use: X [:<display>] [option]
-a #                   mouse acceleration (pixels)
-ac                    disable access control restrictions
-audit int             set audit trail level
-auth file             select authorization file
bc                     enable bug compatibility
-bs                    disable any backing store support
-c                     turns off key-click
c #                    key-click volume (0-100)
-cc int                default color visual class
-co file               color database file
-core                  generate core dump on fatal error
-dpi int               screen resolution in dots per inch
-deferglyphs [none|all|16] defer loading of [no|all|16-bit] glyphs
-f #                   bell base (0-100)
-fc string             cursor font
-fn string             default font name
-fp string             default font path
-help                  prints message with these options
-I                     ignore all remaining arguments
-ld int                limit data space to N Kb
-lf int                limit number of open files to N
-ls int                limit stack space to N Kb
-nolock                disable the locking mechanism
-logo                  enable logo in screen saver
nologo                 disable logo in screen saver
-nolisten string       don't listen on protocol
-p #                   screen-saver pattern duration (minutes)
-pn                    accept failure to listen on all ports
-nopn                  reject failure to listen on all ports
-r                     turns off auto-repeat
r                      turns on auto-repeat
-s #                   screen-saver timeout (minutes)
-su                    disable any save under support
-t #                   mouse threshold (pixels)
-terminate             terminate at server reset
-to #                  connection time out
-tst                   disable testing extensions
ttyxx                  server started from init on /dev/ttyxx
v                      video blanking for screen-saver
-v                     screen-saver without video blanking
-wm                    WhenMapped default backing-store
-x string              loads named extension at init time
-query host-name       contact named host for XDMCP
-broadcast             broadcast for XDMCP
-indirect host-name    contact named host for indirect XDMCP
-port port-num         UDP port number to send messages to
-once                  Terminate server after one session
-class display-class   specify display class to send in manage
-cookie xdm-auth-bits  specify the magic cookie for XDMCP
-displayID display-id  manufacturer display ID for request
Xvnc version 3.3.7 - built Sep 27 2005 11:14:24

-geometry WxH          set framebuffer width & height
-depth D               set framebuffer depth
-pixelformat format    set pixel format (BGRnnn or RGBnnn)
-rfbport port          TCP port for RFB protocol
-rfbwait time          max time in ms to wait for RFB client
-nocursor              don't put up a cursor
-rfbauth passwd-file   use authentication on RFB protocol
-httpd dir             serve files via HTTP from here
-httpport port         port for HTTP
-deferupdate time      time in ms to defer updates (default 40)
-economictranslate     less memory-hungry translation
-maxrects num          max number of rectangles in an update (default 50)
-desktop name          VNC desktop name (default x11)
-alwaysshared          always treat new clients as shared
-nevershared           never treat new clients as shared
-dontdisconnect        don't disconnect existing clients when a new non-shared
                       connection comes in (refuse new connection instead)
-localhost             only allow connections from localhost
-inetd                 Xvnc is launched by inetd

Although I understand that it didn't work, even then I tried to issue this command from another workspace

$vncviewer localhost:2

which gave the expected result :

VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

Is it possible that I am using vncserver 3.3.7, it doesn't understand the commnds given in /etc/xinetd.d/Xvnc file? This file also contains the option -DisconnectClients and the above output shows that it is not a valid option.

---

### Post by Tichondrius on 2006-01-29
Ok, just for you I installed vncserver package on my system instead of vnc4server. It looks like this old version of vncserver has slighlty different options. 

Here's how your /etc/xinetd.d/Xvnc config file should look like:

```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -dontdisconnect -nevershared -rfbauth /root/.vncpasswd
        port = 5901
}

```

Now repeat step 5, and then try to connect:

```
vncviewer localhost:1
```

If that doesn't work then reboot and try to connect again.

Now I'm pretty sure it should work......keep us posted !

---

### Post by mssm on 2006-01-29
Nope, it's not working.

I issued the commands of step 5 after I  modified /etc/xinetd.d/Xvnc to its latest form and rebooted the machine. Next I issued the command :

$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)

What does this output imply?

Finally I issued the command as a root, after going to superuser shell by issuing su. Alas, I have no success this time too.

Did it work for your machine? Is it an AMD64?

---

### Post by Tichondrius on 2006-01-29
Turn OFF your firewall software (e.g. firestarter) - or at least add a rule to allow inbound connections on all ports from the localhost. I just realized it might be causing a problem even when connecting from localhost.

Now Try this - open a terminal and enter this command:

```
sudo /usr/bin/Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -dontdisconnect -nevershared -rfbauth /root/.vncpasswd
```

The Xvnc program should start correctly which will be confirmed by its output which will include a line tlike this:

> 29/01/06 03:20:11 Listening for VNC connections on TCP port 5902

Now, open another terminal (do not kill the Xvnc you started above) and give this command:

```
vncviewer localhost:2
```

You SHOULD be able to connect and see a login screen. Otherwise something is messed up in your system. And yes, this works for me 100%.

---

### Post by mssm on 2006-01-30
[QUOTE=Tichondrius]Turn OFF your firewall software (e.g. firestarter) - or at least add a rule to allow inbound connections on all ports from the localhost. I just realized it might be causing a problem even when connecting from localhost.

Now Try this - open a terminal and enter this command:

```
sudo /usr/bin/Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -dontdisconnect -NeverShared -rfbauth /root/.vncpasswd
```

The Xvnc program should start correctly which will be confirmed by its output which will include a line tlike this:



Now, open another terminal (do not kill the Xvnc you started above) and give this command:

```
vncviewer localhost:2
```

You SHOULD be able to connect and see a login screen. Otherwise something is messed up in your system. And yes, this works for me 100%.[/QUOTE]

I do not have any firewall software installed in my computer. On my cable modem cum router I have the ports 5900 and 5901 both open in firewall config. for both incoming and outgoing requests. Also these ports are forwarded to my internal IP address. Should I try to open any other ports? I did one extra thing : I have opened a UDP port no. 177 in my firewall for XDMCP. I shall turn it off and try.

I am at my office right now. So I shall try all these after I get back home. Thanks a lot for your patience and help.

BTW, I have tried a completely different thing : I tried to install tightvnc java-client from this thread

[http://www.ubuntuforums.org/showthread.php?t=107503&highlight=tightvnc](http://www.ubuntuforums.org/showthread.php?t=107503&highlight=tightvnc)

and it is perfectly working for me. I think this is allowed only when remote desktop is turned on. From my office computer, I just issued te command 

$vncviewer myservername.org

It opened the login screen but the one due to tightvnc java based client. Issuing the command

$vncviewer myservername.org:1 

gives connection reset by peer. To avoid confusion, I should add that vncserver was not working even befoer installing tightvnc java client, since it may seem that they are kind of conflicting each other. I forget to ask one thing: should I turn off ubuntu's built-in remote desktop feature for vncserver to work properly?

---

### Post by mssm on 2006-01-30
Yes, Tichondrius, it works !!!

After issuing that big command I got this output

30/01/06 22:03:59 Xvnc version 3.3.7 - built Sep 27 2005 11:14:24
30/01/06 22:03:59 Copyright (C) 2002-2003 RealVNC Ltd.
30/01/06 22:03:59 Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
30/01/06 22:03:59 All Rights Reserved.
30/01/06 22:03:59 See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC
30/01/06 22:03:59 Desktop name 'x11' (strings:2)
30/01/06 22:03:59 Protocol version supported 3.3
30/01/06 22:03:59 Listening for VNC connections on TCP port 5902

From another terminal, when I I issued : 

$vncviewer localhost:2

I got my login screen along with this output inside that terminal :
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.3 (viewer 3.3)
Password:
VNC authentication succeeded
Desktop name "root's x11 desktop (strings:2)"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Throughput 20000 kbit/s - changing to Hextile
Throughput 20000 kbit/s - changing from 8bit
Using viewer's native pixel format:
8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Throughput 20000 kbit/s - changing to Hextile
Throughput 20000 kbit/s - changing from 8bit
Using viewer's native pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Throughput 20000 kbit/s - changing to Raw

So what should I do now? Should I change my /etc/xinetd.d/Xvnc? I should also add that after startind xinetd by issuing

$sudo /etc/init.d/xinetd start

and then issuing this command :

$ps -ef |grep xinetd

yields 

myname  26831 24082  0 22:59 pts/2    00:00:00 grep Xvnc

It seems Xvnc is not running.

Another wild guess: does it depend in anyway on the permission of this file?

---

### Post by Tichondrius on 2006-01-30
Great, Xvnc works for you when you start manually, so now the only issue is to get it started by xinetd. Let me just clarify that xinetd listens on the requested port but only starts Xvnc when a client is attempting to connect. So it's ok that you don't see Xvnc running before connecting with a client.

So yeah, now go ahead and change the /etc/xinetd.d/Xvnc file to have the same options (on the server_args line) as when you started it manually, except that you should use screen :1 and also the "-inetd" option. That's exactly what I listed in my message #14 above.

Then try to connect to localhost:1 and see that it works. If it doesn't then maybe it's something with your Kubuntu display manager that is different than  regular GDM on Ubuntu.

BTW, you can also try to connect from another PC to the Xvnc you started locally by using the VNC server machine address with :2 appended.

---

### Post by kacheng on 2006-01-31
mssm I'm very jealous that you got it to work!

I just upgraded to Dapper to try and solve my nvidia driver issue.  Now I can't install vncserver due to dependency issue.
[I]vncserver:
 Depends: xserver-common  but it is not installable[/I]

However, I can install tightvncserver, but when I run your command Tichondrius, I get:

[I]# sudo /usr/bin/Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -dontdisconnect -nevershared -rfbauth /root/.vncpasswd

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000
Segmentation fault[/I]


Is this something to do with Dapper and it's changes in the Xserver?
How would I fix it?

---

### Post by mssm on 2006-01-31
Tichondrius, I observed a strange thing. Afetr starting the xinetd service, If I issue the command

$ vncviewer localhost:0

I am getting the current desktop screen but not the login screen which I obtained last time by issuing that big command.

[COLOR="Red"]Update[/COLOR] : This occurred due to enabling ubuntu's built-in remote desktop feature. When I turn off this feature, the above command yields nothing. But still vncviewer localhost:1 gave the error msg. I thought if this remote desktop feature is interfering with the vncserver setup, but it's not the case. 

Moreover, I should add that right now I am working in gnome desktop and my /etc/xinetd.d/Xvnc file is exactly identical to the config. you alluded to in post #14. And still, the error msg. with vncviewer localhost:1. So using kDE desktop is not an issue. I shall follow method of elimination to pinpoint the trouble, if I can. If anybody else can help us, it will be really appreciated.

Kacheng, sorry, I could not help you since I am a novice in this regard but you can try to install the tightvnc java-client from the thread I linked to in my previous post. You need to enable ubuntu's built-in remote desktop so that it can work and of course if you are behind a router, you need to fwd those ports.

---

### Post by mdr on 2006-02-01
[QUOTE=Tichondrius]sudo /usr/bin/Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -dontdisconnect -nevershared -rfbauth /root/.vncpasswd[/QUOTE]


I too am trying this on AMD 64., Following this thread I get to this point and I all I get is

Segmentation Fault 

:confused:

---

### Post by kacheng on 2006-02-02
mssm - thanks, I have no problem with using vnc and the remote desktop - even can tunnel over ssh.  That works great.


However, at some point I'd really like to get the XDMCP working properly and have the ability to utilize several sessions. (e.g. two people logged in at the same time).

---

### Post by CTD on 2006-02-02
using a fresh install of 5.10.  running

```
 sudo apt-get install vncserver xinetd
```
yeilds me the following results:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vnc4server
```
what am I missing here?  Do I need to add an additional installation source?

EDIT: I found the package in a different installation source.  Open package manager, go to settings->repositories, clicked the 'community maintained' button.

vnc4server installed and works like a champ.  Thanks!

---

### Post by linuxfan on 2006-02-03
[QUOTE=kacheng]mssm - thanks, I have no problem with using vnc and the remote desktop - even can tunnel over ssh.  That works great.


However, at some point I'd really like to get the XDMCP working properly and have the ability to utilize several sessions. (e.g. two people logged in at the same time).[/QUOTE]

Hi Kacheng,

Is there a How-To for tunnelling VNC over SSH? Some pointers would help a lot ... thanks ;)

---

### Post by Tichondrius on 2006-02-03
Yes, you are suipposed to enable the extra repositories because vnc4server is from the universe repository which is not enabled by default.

[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

---

### Post by CosMix on 2006-02-03
Hey guys,

ive installed vnc and it works fine...on one machine, while on the other, always the same breezy badger 5.10 installation, all i get is grey screen when i log onto vnc....
i mean....the server is obviously running, and i can access it from outside...but when i connect all i see is grey screen instead of my ubuntu desktop....what could this be? :-k 


Gorazd

---

### Post by mssm on 2006-02-03
[QUOTE=CosMix]Hey guys,

ive installed vnc and it works fine...on one machine, while on the other, always the same breezy badger 5.10 installation, all i get is grey screen when i log onto vnc....
i mean....the server is obviously running, and i can access it from outside...but when i connect all i see is grey screen instead of my ubuntu desktop....what could this be? :-k 


Gorazd[/QUOTE]

Hi cosmix, good to learn that you are running vnc on one machine? Did you follow Tichondrius's how-to? Are you behind a router? I am still trying hard.

---

### Post by kacheng on 2006-02-03
[QUOTE=linuxfan]Hi Kacheng,

Is there a How-To for tunnelling VNC over SSH? Some pointers would help a lot ... thanks ;)[/QUOTE]


Yes here's one:

[http://pigtail.net/LRP/vnc/](http://pigtail.net/LRP/vnc/)

There are many others.

---

### Post by mssm on 2006-02-04
[QUOTE=kacheng]Yes here's one:

[http://pigtail.net/LRP/vnc/](http://pigtail.net/LRP/vnc/)

There are many others.[/QUOTE]

Hi Kacheng, thanks for the link and thanks for your appreciation before.

I found that freenx is much smoother less jerky and easy to install than vnc. Moreover, it supports vnc too. There is no headache for port opening and forwarding, since it uses standard ssh port and hence the whole session can be encrypted. So I switched to freenx. I followed this thread :

[http://www.ubuntuforums.org/showthread.php?t=97277](http://www.ubuntuforums.org/showthread.php?t=97277)

Good luck!

---

### Post by kacheng on 2006-02-04
Thanks mssm, unfortunately, I have an amd64 system, and I'm running Dapper, and the repositories don't exist yet for me.

---

### Post by kacheng on 2006-02-09
Tichondrius,

Any insight as to why:

*# sudo /usr/bin/Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -dontdisconnect -nevershared -rfbauth /root/.vncpasswd*

yields:

[I]Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000
Segmentation fault[/I]


Again, I'm on amd64 using tightvncserver and xinetd.

Thanks.

---

### Post by Jaygo333 on 2006-02-15
Where Would I be able to add the IdelTimeout.
Right after the end of /etc/xvnc?

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 24 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
==>   idletimeout -300
}

Or where?

:h34r: Jaygo333 :h34r:

---

### Post by Eternal Blade on 2006-02-15
nevermind, I got it figured out

---

### Post by chugru on 2006-02-15
Hi, All...

I'm a new kubuntu user, and I'm very interested in this thread. I'm a little baffled though by the fact that I have KDE rather than Gnome, and I don't know what to do with the initial part concerning settings for XDMCP??

Would someone please give me some suggestions??

Thanks...

---

### Post by Tichondrius on 2006-02-15
[QUOTE=Jaygo333]Where Would I be able to add the IdelTimeout.
Right after the end of /etc/xvnc?

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 24 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
==>   idletimeout -300
}

Or where?

:h34r: Jaygo333 :h34r:[/QUOTE]


look at the HOWTO again:

> An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option **in the server_args line** in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300" to change it to 5 minutes.

You have to add it on the "server_args = ...." line:

```

server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 24 -once **-IdleTimeout 300** -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

```

---

### Post by TherapyQuestionMark on 2006-02-16
How would I go about adding the ability to connect to my server through a web based java client?

---

### Post by kacheng on 2006-02-16
You might try something like SSL Explorer.

However, this thread related mainly to connecting securely to your computer using VNC.

---

### Post by TherapyQuestionMark on 2006-02-17
that's what I meant, Vnc's java applet embedded in a webpage.

---

### Post by mbeach on 2006-02-18
thanks Tichondrius for the great info.  All is working for me as you lay it out.  However, I'm trying to get vnc4config to work and have met with failure thus far.  

If I have the working INETD model on the go, and try:
```
~$ sudo vnc4config -display 0 -connect myhost:myport
```

I get the error:
```
vnc4config: unable to open display "0"
```

and if I use
```
~$ sudo vnc4config -display :0 -connect myhost:myport
```
I get:
```
No VNC extension on display :0
```


(the same error is observed if I try -display 1 or variations such as -display localhost:0  or -display localhost:1 etc...)

So I tried starting the Xvnc manually with the one liner starting with:
```
~$ sudo Xvnc :2 -query localhost -geometry .....
```
which starts the Xvnc server nicely with the following:

```
Xvnc version 4.0 - built Apr 19 2005 04:26:49
Underlying X server release 40200000, The XFree86 Project, Inc

Sat Feb 18 22:58:07 2006
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0
```

so I try from another terminal:
```
~$ sudo vnc4config -display :2 -connect myhost:myport
```
which yeilds:

```
Xlib: connection to ":2.0" refused by server
Xlib: No protocol specified
vnc4config: unable to open display ":2"
```

and in the terminal runing the Xvnc, this audit appears:
```
AUDIT: Sat Feb 18 23:00:38 2006: 22313 Xvnc: client 5 rejected from local host
```

The pc at MYHOST is running a listening VNC viewer which I can connect to with a WinVNC 'add new client' option.  From my reading I thought vncconfig would start Xvnc if the -connect option was given which does not seem to be the case, but if there is a manually started Xvnc running, there does seem to be some interactivity between vncconfig and the Xvnc server.  

As you obviously know your stuff, any chance you could tell me if you can get vnc4config to initiate a connection to a remote server running a listening vnc viewer?  

mb.
( Ubuntu 5.10 on a Dell Optiplex GX150 [I'm extending the life of some older pcs] )

---

### Post by Jeromy on 2006-02-19
Below is a fix for users having trouble on AMD64 such as the "Segmentation Fault" or SystemException.  I had all the same problems as mssm and kacheng with the vncserver on an amd64 system.

There is a bug in vncserver for AMD64 that has been discussed in detail over at the Debian forums.
[http://lists.debian.org/debian-amd64/2004/11/msg00064.html]("http://lists.debian.org/debian-amd64/2004/11/msg00064.html") (late 2004)
[http://lists.debian.org/debian-amd64/2005/12/msg00255.html]("http://lists.debian.org/debian-amd64/2005/12/msg00255.html") (late 2005)

The work-around is briefly discussed at Ubuntu 5.10 Support (GNOME) > AMD 64 Users :
[http://ubuntuforums.org/archive/index.php/t-82548.html]("http://ubuntuforums.org/archive/index.php/t-82548.html")

Repeating the work-around, until there's a trusted source for vnc4server for amd64, you can download the fixed vnc4server and vncviewer as .deb packages from:

[http://qt1.iq.usp.br/download/]("http://qt1.iq.usp.br/download/")
vnc4server_4.0-7.3_amd64.deb [2.0M]
xvnc4viewer_4.0-7.3_amd64.deb [140K]

You then simply need to manually install them using dpkg from the download directory:
```

sudo dpkg -i vnc4server_4.0-7.3_amd64.deb
sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb

```

Once installed, Tichondrius' HOWTO works perfectly following the original instructions.  
It would be useful if a reference to the fix for AMD64 was included as the start of this how-to until vnc4server is available for amd64 by normal means.

Thanks!

---

### Post by simon0t7 on 2006-02-19
excellent howto, got it to work and it doesn't have problems with refreshing the screen unlike the other vnc servers i've tried

---

### Post by SSH Tech on 2006-02-19
Okay, so this setup will allow me to start a new session on display 1.  But can I resume an existing session on my physical display 0?  Let's say I start a session at home normally on display 0.  I start up gaim and firefox then lock the screen and go over to a friend's place.  Can I resume this session using this method, or only start a new session?

---

### Post by Tichondrius on 2006-02-20
[QUOTE=SSH Tech]Okay, so this setup will allow me to start a new session on display 1.  But can I resume an existing session on my physical display 0?  Let's say I start a session at home normally on display 0.  I start up gaim and firefox then lock the screen and go over to a friend's place.  Can I resume this session using this method, or only start a new session?[/QUOTE]


No, this howto will not do that. I actually have VNC on display :0 working as well using x11vnc which is a VNC extension to the regular X server (e.g. xorg). I plan to publish a separate howto on that. Stay tuned.

---

### Post by Tichondrius on 2006-02-20
[QUOTE=Jeromy]Below is a fix for users having trouble on AMD64 such as the "Segmentation Fault" or SystemException.  I had all the same problems as mssm and kacheng with the vncserver on an amd64 system.

There is a bug in vncserver for AMD64 that has been discussed in detail over at the Debian forums.
[http://lists.debian.org/debian-amd64/2004/11/msg00064.html]("http://lists.debian.org/debian-amd64/2004/11/msg00064.html") (late 2004)
[http://lists.debian.org/debian-amd64/2005/12/msg00255.html]("http://lists.debian.org/debian-amd64/2005/12/msg00255.html") (late 2005)

The work-around is briefly discussed at Ubuntu 5.10 Support (GNOME) > AMD 64 Users :
[http://ubuntuforums.org/archive/index.php/t-82548.html]("http://ubuntuforums.org/archive/index.php/t-82548.html")

Repeating the work-around, until there's a trusted source for vnc4server for amd64, you can download the fixed vnc4server and vncviewer as .deb packages from:

[http://qt1.iq.usp.br/download/]("http://qt1.iq.usp.br/download/")
vnc4server_4.0-7.3_amd64.deb [2.0M]
xvnc4viewer_4.0-7.3_amd64.deb [140K]

You then simply need to manually install them using dpkg from the download directory:
```

sudo dpkg -i vnc4server_4.0-7.3_amd64.deb
sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb

```

Once installed, Tichondrius' HOWTO works perfectly following the original instructions.  
It would be useful if a reference to the fix for AMD64 was included as the start of this how-to until vnc4server is available for amd64 by normal means.

Thanks![/QUOTE]


Done. Thanks !

---

### Post by CosMix on 2006-02-20
Hey there,

Im just curious about one thing...can i set another port on which vnc server would accept connections in order to be able to have two or more simultaneous connections on one vnc server ?...like...can i add another port in this conf file ?


service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 55566
        [COLOR="Red"]port = can i add another port here?[/COLOR]
}

And btw, great howto! Wish there were more ppl like you...willing to help and above all, able to help.

Gorazd

---

### Post by Tichondrius on 2006-02-23
[QUOTE=CosMix]Hey there,

Im just curious about one thing...can i set another port on which vnc server would accept connections in order to be able to have two or more simultaneous connections on one vnc server ?...like...can i add another port in this conf file ?


service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 55566
        [COLOR="Red"]port = can i add another port here?[/COLOR]
}

And btw, great howto! Wish there were more ppl like you...willing to help and above all, able to help.

Gorazd[/QUOTE]

Let me clarify that every X-windows server manges one display.  Your actual monitor is display :0 and is controlled by Ubuntu's default X-windows server. The Xvnc program is also an X-windows server which controls display :1 (which is a virtual diplay that can be projected to a VNC client) according to how we set it up in this guide. It also serves as a VNC server which listens on port 5901.

If you want more than one VNC client to share the display you can remove the -NeverShared option from the server_args line in the script. But that means that all the clients still connect to the server on the same port 5901 and see the exact same display. In fact, if any client moves the mouse for example, then the other clients will see the mouse cursor move as well.

If you want to allow more than one concurrent sessions, than you need to run another instance of Xvnc on a different display.  To do that, make a copy of the Xvnc script in /etc/xinetd.d called Xvnc2 (in the same directory), and in the new file change the display to :2 and the port to 5902.  Now restart xinetd as shown in step 6 of the howto, and you will have two Xvnc servers running, each waiting for a connection on a different port and managing a different display. So you could have two users running independent sessions, each one on a different virtual display.

---

### Post by edsel6502 on 2006-02-23
Hi there I'm having a problem resuming an old session.

What I do is login via GDM then quit the vncviewer program and then try to reconnect. Instead of letting me resume, it gives me the GDM login again.

The following is the args I'm passing Xvnc. I had to remove the -fp option as it refused to connect saying that I did not have a fixed font.

service vnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = no
user = root
server = /usr/bin/Xvnc
server_args = -inetd :1 -query localhost -geometry 1280x1024 -depth 16 -DisconnectClients=0 -IdleTimeout=0 -NeverShared -SecurityTypes=none
port = 5901
}

Update:

Ok I'm stumped. It seems to behave as expect when run from the commandline. Multiple tests to localhost:2 confirms it.

Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -DisconnectClients=0 -IdleTimeout=0 -NeverShared -SecurityTypes=none

The only thing it seems to be choking on is launching from xinetd which makes it want to login via GDM each and every time...

---

### Post by Tichondrius on 2006-02-23
I think it might be the fact that you set Idle timeout to zero, so try changing that option. I understand that when you disconnect you don't mean that you explicitly log out from the gnmoe session, right ?

Also you should restart xinetd and kill all the Xvnc processes by doing step 5, because sometimes things get messed up and xinetd just keeps spawning more and more Xvnc process instead of waking up the old one.

---

### Post by edsel6502 on 2006-02-23
When I quit I just quit the vncviewer application. I am still logged in via my windowmanager session.

I also do a cold boot. To make sure everything is running properly.

I'll try it without the IdleTimeout=0 But I really really need that vnc session not to timeout.

Update:

Nope that didn't work.

I think I might have to force a script to launch on boot.

---

### Post by kharyett on 2006-02-24
This is a great Howto. It worked great after I ironed out a stupidity issue.

Word of advice:
If you have the root accound enabled *with a password*, ***DO NOT*** set the vnc server passwrod the same  as your root password, otherwise, the sessions will not work, and it will chown .ICEauthority to root ownership and lock you out of any gdm sessions except for the one you are currently logged into. After loging out, you will be locked out till you chown the .ICEauthority file back to your usernames ownership.

Like I said, stupidity issue. Time to change that password... ;)

---

### Post by Tichondrius on 2006-02-24
Having the root account enabled is not a good idea, and it's even worse to log in to GDM as root. To perform system maintenance, you should log in as a user with administrator privileges (not root) and use sudo. If typing in your password every time you use sudo is too much of a hassle, you can edit /etc/sudoers file and change the admin line to read:

```
%admin  ALL=(ALL) NOPASSWD: ALL
```

Or follow this howto in the guide:

[http://easylinux.info/wiki/Ubuntu#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29](http://easylinux.info/wiki/Ubuntu#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29)

---

### Post by _kk on 2006-02-24
Hey guys.

I really hope someone will help me out here. I've read this guide many many times by now and I'm getting alot of the same errors as others here. I'm at the point where I can start the Xvnc by hand and that works great but now I need to get 'xinetd' to start it for me as I understand.

When I **sudo netstat -tap | grep xinetd** I get:
tcp        0      0 *:5901                  *:*                     LISTEN     6885/xinetd

and when I try **vncviewer localhost:1** I get this:
ReadFromRFBServer: rdr::SystemException read: Connection reset by peer(104)

I've checked the log: **grep xinetd /var/log/syslog** and I get the same as others has described:
Jan 28 08:29:57 localhost xinetd[14186]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14187]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[10673]: Deactivating service Xvnc due to excessive incoming connections. Restarting in 10 seconds.

I've really double checked everything and have no idea where to go now. I've used vnc a great deal on windows but linux is all new to me :?

Where do I go from here? :-k  

kk,
installed ubuntu yesterday

---

### Post by Tichondrius on 2006-02-24
Repeat steps 5 and 6

---

### Post by _kk on 2006-02-25
[QUOTE=Tichondrius]Repeat steps 5 and 6[/QUOTE]

Ok, in step 5 it says:

[B]Stopping the internet superserver: xinetd.
Xvnc: no process killed
Starting internet superserver: xinetd.[/B]

In step 6 I get:

**ReadFromRFBServer: rdr::SystemException read: Connection reset by peer(104)**

[COLOR="Silver"]*Update: Something has changed since yesterday. Now when I start the server manually and connect to it all I see is a blank screen. It's like a giant chess board with black and white pixels. Also the cursor changes into a big X*[/COLOR] - nevermind, XDMCP was disabled.

---

### Post by kharyett on 2006-02-25
[quote=Tichondrius]Having the root account enabled is not a good idea, and it's even worse to log in to GDM as root. To perform system maintenance, you should log in as a user with administrator privileges (not root) and use sudo. If typing in your password every time you use sudo is too much of a hassle, you can edit /etc/sudoers file and change the admin line to read:
[/QUOTE]

I know that having root with a passwrod is not a good idea for most people, but I have it enabled for a few good reasons which are irrelleavent here.

I don't allow a GDM or remote login by root anywhere besides console. And my sudo user is not allowed a remote login, only console and gdm. The console is locked up and accessable by only me.

Now, back to the conversation about VNC.

I wonder what kind of load it would be on the system to have a server setup like a terminal server for many users. Hmmmm.... I see possibilities here. I wonder how many would be too many... Time to start something over in the Server Talk forum...
\\:D/

---

### Post by simon0t7 on 2006-02-25
hm... I can login remotely via VNC, but when I'm at the actual machine my login no longer works.... am I missing a step here?

---

### Post by kharyett on 2006-02-25
[quote=simon0t7]hm... I can login remotely via VNC, but when I'm at the actual machine my login no longer works.... am I missing a step here?[/quote]

Do you get an error in the GDM when you try to logon? If it does, login to the console and check the ownership of the .ICEauthority file in your home directory. 

If there is no error, can you still login to the console?

---

### Post by simon0t7 on 2006-02-25
it tells me my password or login is incorrect.  I can log in fine via console from putty.


-rw-------   1 simon simon    787 Feb 25 11:50 .ICEauthority


That's the output for .ICEauthority, is it correct?

---

### Post by kharyett on 2006-02-25
That looks good. 
Check to see if any files in your home directory have suddenly changed to root ownership. If any have, let us know which ones. If none have, try the following:
```

sudo /etc/init.d/xinetd stop

sudo killall Xvnc

sudo /etc/init.d/xinetd start

sudo /etc/init.d/gdm restart

```

That will kill the xinet daemon, kill all Xvnc processes, restart xinet daemon and restart the GDM. See if that lets you login again.

When I screwed up with the root password, after I reclaimed ownership of the file, I had to do the above steps before I could login on the console GDM.

I have had a few quirks since then, but luckily I have ssh access for remote logins setup. Even if the console goes kerblewey, I can still use the SSH login... And yes, it happened that the keyboard was not accessable due to a motherboard port failure. SSH allowed me to get in and shut it down cleanly so I could changed the motherboard.

See if that helps.

---

### Post by Tichondrius on 2006-02-25
[QUOTE=SSH Tech]Okay, so this setup will allow me to start a new session on display 1.  But can I resume an existing session on my physical display 0?  Let's say I start a session at home normally on display 0.  I start up gaim and firefox then lock the screen and go over to a friend's place.  Can I resume this session using this method, or only start a new session?[/QUOTE]


Ok, to resume a session you started on your physical display (display :0) all you really need is to turn on Ubuntu's remote desktop feature using the Remote Desktop Preferences dialog box accessible from System->Preferences->Remote Desktop menu item.  Just check the first two options there (allow other users to view your desktop and allow other users to control your desktop) and set the password in the bottom of the dialog box (check the REuqire password option), and you're done ! 
  The above uses the built in VNC capability that Ubuntu comes installed with, but the drawback is that it's a little slow, and you need to enable it for each user which wants to allow his desktop to be view or controlled remotely. Also this doesn't allow remote VNC clients to log in to GDM, only to view a GDM session that was started by someone actually using the physical display. So if currently no one is logged in, a remote user cannot connect to display :0 and start a new session.
  But don't worry - there is a better way which allows you to view the phyical display remotely and also log-in to a new session from GDM (using a remote VNC client) !  And it works faster (as fast as the regular VNC server), and works for all users. Here's how to do that :

1. Install x11vnc package

```
sudo apt-get install x11vnc
```

2. Add x11vnc service to xinetd:

```
sudo gedit /etc/xinetd.d/x11vnc
```

Enter this into the new file:

```

service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg
        disable         = no
}

```

3. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo killall x11vnc
sudo /etc/init.d/xinetd start
```

4. From a remote machine use your VNC client to connect to display :0

```
vncviewer  vnchost:0
```

Note that after loggging from GDM and also after logging out from the X-session back and going back to GDM, the VNC client gets disconnected for some reason. So you just need to re-connect and you will get back into the session you logged into. When logging out, the disconnect happens when gnome asks you to confirm your intention to log out, so it's best to turn off the log-out confirmation dialog box by going to System->Preferences->Sessions and un-checking the "ask on logout" option.

Please tell me how this works out for you....I plan to add this to the HOWTO

---

### Post by _kk on 2006-02-26
Tichondrius, the x11vnc guide worked flawlessly for me. Easy peasy \\:D/

It's a bit faster than the buildin vnc but still not as fast as FreeNX, that I've tried too.

BTW, how do I change my screen resolution? Right now I get a tiny 640x480 display. If I go to **System > Preferences > Screen Resolution** I can see my current settings but I can't change them.

It's the same when I use the bulidin vnc. It happend after I unplugged the monitor from the box. I run the box all remotely and thus have no monitor connected.

---

### Post by Tichondrius on 2006-02-26
Your resolution is low because xorg X-server chooses the resolution based on the monitor capabilities which are dynamically communicated to the machine when X starts up. There is a way to override that, in the xorg.conf file but I don't remember exactly how. Just thought I give you a direction to search.

---

### Post by simon0t7 on 2006-02-26
[QUOTE=kharyett]That looks good. 
Check to see if any files in your home directory have suddenly changed to root ownership. If any have, let us know which ones. If none have, try the following:
```

sudo /etc/init.d/xinetd stop

sudo killall Xvnc

sudo /etc/init.d/xinetd start

sudo /etc/init.d/gdm restart

```

That will kill the xinet daemon, kill all Xvnc processes, restart xinet daemon and restart the GDM. See if that lets you login again.

When I screwed up with the root password, after I reclaimed ownership of the file, I had to do the above steps before I could login on the console GDM.

I have had a few quirks since then, but luckily I have ssh access for remote logins setup. Even if the console goes kerblewey, I can still use the SSH login... And yes, it happened that the keyboard was not accessable due to a motherboard port failure. SSH allowed me to get in and shut it down cleanly so I could changed the motherboard.

See if that helps.[/QUOTE]


I'll have to try that.  I just moved my /home to a different hard dirve but it doesn't auto-mount in fstab so i gotta see what's up with that first.  No home = no X :)
I'll keep you posted

---

### Post by _kk on 2006-02-26
[QUOTE=Tichondrius]Your resolution is low because xorg X-server chooses the resolution based on the monitor capabilities which are dynamically communicated to the machine when X starts up. There is a way to override that, in the xorg.conf file but I don't remember exactly how. Just thought I give you a direction to search.[/QUOTE]

Thank you for letting me know. Actually I *have* already been looking in the xorg.conf but I wasn't sure if that was the way to go. Now i'll just have to dig deeper.

[COLOR="SeaGreen"]Update: I got it to work nicely after some xorg.conf editing. Disabling the loading of 'dcc' and making a modeline for my screen did the trick.[/COLOR]

---

### Post by dermotti on 2006-02-27
You guys really should give FreeNX a try, its wayyyyy better than vnc, Much faster and works out the box...

---

### Post by Tichondrius on 2006-02-27
[QUOTE=dermotti]You guys really should give FreeNX a try, its wayyyyy better than vnc, Much faster and works out the box...[/QUOTE]

well, I did set up FreeNX as well, but I couldn't get resuming sessions to work - that is, I had to start a new session every time. Also sometimes it would go nuts and spawn many processes on the server, occupying the CPU 100%. So in my experience it wasn't as reliable and flexible as VNC, but I agree it was faster.

---

### Post by _kk on 2006-02-28
[QUOTE=dermotti]You guys really should give FreeNX a try, its wayyyyy better than vnc, Much faster and works out the box...[/QUOTE]

It's installed and running but have the same problem as Tichondrius. I can't resume sessions properly from windows... :-? I googled the problem and found that apparently it's a know bug when connecting from a win client. Such a shame because as you say it's very nice and fast.

---

### Post by Tichondrius on 2006-02-28
Well not being able to resume sessions from windows pretty much ruins it for me as a possible alternative to VNC. And btw I wouldn't call this a "known bug", I'd call this a crippling problem which undermines the usefulness of the whole app.

---

### Post by _kk on 2006-02-28
There's no problem in a linux => linux setup but using a win client makes this flaw appear. And I totally agree, it renders the app useless. Sadly, that is the same conclusion many others are making on the freenx mailing list: [http://mail.kde.org/pipermail/freenx-knx/](http://mail.kde.org/pipermail/freenx-knx/)

---

### Post by t_ras on 2006-02-28
AMD 64
ubuntu 5.10
installed as stated in 1st post this thread.

(though is seems I had vnc server installed before)

diplay :0 (remote desktop) works fine.
diplay :1 get restted by peer
diplay :2-... connection refused.
no firewall running (at least not from ISPconfig and I had installed no other)

manual connection given at thread for diplay 2 works fine.

any Ideas?

---

### Post by Coogan on 2006-03-03
Thanks for the guide; mine's working perfectly.  With one exception: my VNC session is a completely grey screen.  No icons, no toolbars, just zilch.  Kinda makes it tough to do anything :)

I'd managed to get VNC working a while back by editing my xstartup to fix it, but the method described here apparently doesn't use any of the xstartup scripts.  Where's the remote desktop login scripts stored at?

Coogan

---

### Post by Brent Nesbitt on 2006-03-04
[QUOTE=edsel6502]Hi there I'm having a problem resuming an old session.

What I do is login via GDM then quit the vncviewer program and then try to reconnect. Instead of letting me resume, it gives me the GDM login again.

The following is the args I'm passing Xvnc. I had to remove the -fp option as it refused to connect saying that I did not have a fixed font.

service vnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = no
user = root
server = /usr/bin/Xvnc
server_args = -inetd :1 -query localhost -geometry 1280x1024 -depth 16 -DisconnectClients=0 -IdleTimeout=0 -NeverShared -SecurityTypes=none
port = 5901
}

Update:

Ok I'm stumped. It seems to behave as expect when run from the commandline. Multiple tests to localhost:2 confirms it.

Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -DisconnectClients=0 -IdleTimeout=0 -NeverShared -SecurityTypes=none

The only thing it seems to be choking on is launching from xinetd which makes it want to login via GDM each and every time...[/QUOTE]
I am having this same problem (sessions always restart with GDM login).  
I'm pretty sure it has to do with "wait = no" in the xinetd conf, but "wait = yes" doesn't seem to work, as my sessions just die.

---

### Post by x0inx on 2006-03-08
Tichondrius, thank you for this great tutorial on vnc. People like you are making my switch to linux much easier and enjoyable. My only problem with x11vnc is that when I connect to :0, it does not prompt for a password like :1 does; it just goes straight to what is on my monitor. I am running Breezy AMD64.

Thank you.

---

### Post by biloyp on 2006-03-09
[QUOTE=Tichondrius]Ok, to resume a session you started on your physical display (display :0) all you really need is to turn on Ubuntu's remote desktop feature using the Remote Desktop Preferences dialog box accessible from System->Preferences->Remote Desktop menu item.  Just check the first two options there (allow other users to view your desktop and allow other users to control your desktop) and set the password in the bottom of the dialog box (check the REuqire password option), and you're done ! 
  The above uses the built in VNC capability that Ubuntu comes installed with, but the drawback is that it's a little slow, and you need to enable it for each user which wants to allow his desktop to be view or controlled remotely. Also this doesn't allow remote VNC clients to log in to GDM, only to view a GDM session that was started by someone actually using the physical display. So if currently no one is logged in, a remote user cannot connect to display :0 and start a new session.
  But don't worry - there is a better way which allows you to view the phyical display remotely and also log-in to a new session from GDM (using a remote VNC client) !  And it works faster (as fast as the regular VNC server), and works for all users. Here's how to do that :

1. Install x11vnc package

```
sudo apt-get install x11vnc
```

2. Add x11vnc service to xinetd:

```
sudo gedit /etc/xinetd.d/x11vnc
```

Enter this into the new file:

```

service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg
        disable         = no
}

```

3. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo killall x11vnc
sudo /etc/init.d/xinetd start
```

4. From a remote machine use your VNC client to connect to display :0

```
vncviewer  vnchost:0
```

Note that after loggging from GDM and also after logging out from the X-session back and going back to GDM, the VNC client gets disconnected for some reason. So you just need to re-connect and you will get back into the session you logged into. When logging out, the disconnect happens when gnome asks you to confirm your intention to log out, so it's best to turn off the log-out confirmation dialog box by going to System->Preferences->Sessions and un-checking the "ask on logout" option.

Please tell me how this works out for you....I plan to add this to the HOWTO[/QUOTE]
Fantatstic How-To. VNC did not work for me at first but the logfile told me I had a } missing on line 11 of Xvnc, I fixed it and everything worked. 

I can't get display 0 to come up, I will try on the local machine tomorrow. 

I found this How-To so I will give it a try and see what happens. Thanks for your help.

---

### Post by biloyp on 2006-03-10
Worked the very first time I set this up. I can log into a remote desktop (physical) and then log into a virtual desktop on the same machine. 

Thanks for this excellent How-To!!

---

### Post by LivnLarge on 2006-03-14
hello, I did steps 1 thru 6 however when i complete step 6 i get a i guess you can say a pixel screen because the resolution seems low but no GDM login,  attached in the pastebin link below,  is the pixel screen that appears once i type in 'vncviewer localhost:1' 
[IMG]http://www.imagestation.com/picture/sraid202/pda165827443509368eb032a32c2b417f/efd7b145.jpg[/IMG]

In the terminal this is displayed while you see the screen - 

[IMG]http://www.imagestation.com/picture/sraid202/pdd7fb65b36cb55d0bd34e958f98c2e04/efd7b13f.jpg[/IMG]

can someone tell me if this is normal and i assume that it didnt work right. also when i enter vncviewer localhost:0 i get to see my own desktop. so i dont know if that helps you guys figure out what wrong or not just thought iwould tell you. also on page  7 Tichondrius gives a how to login remotely to an existing session using vncviewer vnchost:0
am i able to try this and log in using the physical computer the one im using that is... to see if itll work. and what is the difference between his how to on page 1 and his how to on page2 i noticed one you instal vnc4server and the other x11vnc. and that you edit different files with gedit like vnc and the other is x11vnc. i just like to now what im doing when im following these threads. one thing is copying and solving a problem the other is knowing what you are doing. :) 

Also Im only at this thread in the first place because someone in #ubuntu channel on irc pointed me here when i had a problem with my ext harddrive.. which i still have.. accessing it.. and then setting up samba to share it with a win box that is the host computer on my wireless network. so i then mentioned how i also wanted to share the ext hd on my wireless network for my bro to access but also for me to access if im somewhere else like a friends house. and to be able to use their computer to read and write to the shared ext hd on my network home.  so thats how i got here \\:D/ 

thanks in advance 

Linux 4 ever.

---

### Post by LivnLarge on 2006-03-14
whoops noticed the terminal pic was blurry. here is what it displayed-

christopher@ubuntu:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password:
VNC authentication succeeded
Desktop name "x11"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-16-*-*-*-*-*-*-*" to type FontStruct
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
christopher@ubuntu:~$

---

### Post by sopo_dan on 2006-03-15
when trying to install vnc4server package i get this:
```
vnc4server:
 Depends: xserver-common  but it is not installable
```
tried getting xserver-common from somewhere else, but i can't find one matching my X.org ver (7.0.0)

what else can i do?
or will this how-to also work with vncserver_3.3.7?

---

### Post by kmi on 2006-03-19
Hello !
Thanks a lot for this how-to and the follow-up !

In my case it worked flawlessly at the first try... but not the second : every time I logged out after a successful login I could not manage to get the display back again. I had to reboot to be able to do it again... :evil: 

I installed vnc4-common and xvnc4viewer (I guess xvnc4viewer has nothing to do with the trick but installing it seemed quite logical :) ) and removed vnc-common & xvncviewer. 
Now everything is ok... I can log in/out/in/out/etc... :D

Do you also need to have these packages installed ? Are they installed during a step in the how-to that I haven't seen or that got messed up for some reason ?

---

### Post by cowmix on 2006-03-20
I am running Breezy 64bit and I am having the same issue where I get the 'startup' X screen but no login prompt.

[QUOTE=LivnLarge]hello, I did steps 1 thru 6 however when i complete step 6 i get a i guess you can say a pixel screen because the resolution seems low but no GDM login,  attached in the pastebin link below,  is the pixel screen that appears once i type in 'vncviewer localhost:1' 
[IMG]http://www.imagestation.com/picture/sraid202/pda165827443509368eb032a32c2b417f/efd7b145.jpg[/IMG]

In the terminal this is displayed while you see the screen - 

[IMG]http://www.imagestation.com/picture/sraid202/pdd7fb65b36cb55d0bd34e958f98c2e04/efd7b13f.jpg[/IMG]

can someone tell me if this is normal and i assume that it didnt work right. also when i enter vncviewer localhost:0 i get to see my own desktop. so i dont know if that helps you guys figure out what wrong or not just thought iwould tell you. also on page  7 Tichondrius gives a how to login remotely to an existing session using vncviewer vnchost:0
am i able to try this and log in using the physical computer the one im using that is... to see if itll work. and what is the difference between his how to on page 1 and his how to on page2 i noticed one you instal vnc4server and the other x11vnc. and that you edit different files with gedit like vnc and the other is x11vnc. i just like to now what im doing when im following these threads. one thing is copying and solving a problem the other is knowing what you are doing. :) 

Also Im only at this thread in the first place because someone in #ubuntu channel on irc pointed me here when i had a problem with my ext harddrive.. which i still have.. accessing it.. and then setting up samba to share it with a win box that is the host computer on my wireless network. so i then mentioned how i also wanted to share the ext hd on my wireless network for my bro to access but also for me to access if im somewhere else like a friends house. and to be able to use their computer to read and write to the shared ext hd on my network home.  so thats how i got here \\:D/ 

thanks in advance 

Linux 4 ever.[/QUOTE]

---

### Post by cowmix on 2006-03-20
Ok.. I found the answer.. I have to run 'gdmsetup' to allow XDMCP...

BTW.. the solution was contained in  [this]("http://www.realvnc.com/pipermail/vnc-list/2005-June/051059.html") post.

[QUOTE=cowmix]I am running Breezy 64bit and I am having the same issue where I get the 'startup' X screen but no login prompt.[/QUOTE]

---

### Post by kmi on 2006-03-23
[QUOTE=kmi]Hello !
Thanks a lot for this how-to and the follow-up !

In my case it worked flawlessly at the first try... but not the second : every time I logged out after a successful login I could not manage to get the display back again. I had to reboot to be able to do it again... :evil: 

I installed vnc4-common and xvnc4viewer (I guess xvnc4viewer has nothing to do with the trick but installing it seemed quite logical :) ) and removed vnc-common & xvncviewer. 
Now everything is ok... I can log in/out/in/out/etc... :D

Do you also need to have these packages installed ? Are they installed during a step in the how-to that I haven't seen or that got messed up for some reason ?[/QUOTE]

Well... It appears it still does not work perfectly at all : if I log out, I can log in back... BUT the simple fact to log out drives Xvnc to get crazy : it takes 99% CPU usage (controlled after I log out via ssh then 'top') !

Please have you got an idea/tip/solution ? Or maybe a good joke that would make me forget it still does not work after so much PITA ?

MANY thanks in advance ! :)

---

### Post by m0ps on 2006-04-03
[QUOTE=sopo_dan]when trying to install vnc4server package i get this:
```
vnc4server:
 Depends: xserver-common  but it is not installable
```
tried getting xserver-common from somewhere else, but i can't find one matching my X.org ver (7.0.0)

what else can i do?
or will this how-to also work with vncserver_3.3.7?[/QUOTE]

Hello,

I have the same problem :( and I can`t find resolution :(

---

### Post by iMick on 2006-04-09
I am having an intermittant problem VNC'ing to my ubuntu box.  Sometimes I cannot connect, my VNC viewers just don't show anything without errors.

 I run top on the box locally, the xvnc process is running at 100% CPU which seems to be blocking the connections.

Running:
   sudo /etc/init.d/xinetd stop
   sudo killall Xvnc
   sudo /etc/init.d/xinetd start
is my work around at the moment as is a reboot.

Is there anyway to prevent this from happening?

---

### Post by galesteven on 2006-04-21
Here's a cool one. Tichondrius' HOWTO works if in /etc/xinetd.d/Xvnc I change the port to 5902 and the display to :2 .  If I use the instructions as-is (port 5901, display :1) then the following strange things happen:

1.```
$ sudo netstat -tap | grep xinetd
``` gives the expected LISTENing results. So all is ok, right?  Not so fast!

2.```
$ vncviewer localhost:1
``` gives the error message ```
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)
```

3. ```
grep xinetd /var/log/syslog
``` shows lots of errors like this:
```
Apr 21 11:40:33 localhost xinetd[11941]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[11942]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[11943]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[11944]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[11945]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[10218]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Apr 21 11:40:43 localhost xinetd[10218]: Activating service Xvnc

```

I can use VNC on display :2, but that is just a work-around. Why can't I use display :1?

Reboots do not help.

Thanks,
Steve

---

### Post by Nordoelum on 2006-04-21
Thank you for the guide :D

One prob though. After I had installed and configed it. I tryed to run the command ```
$ sudo vncviewer localhost:1
```
I got this:
```
nordoelum@ubuntu-server:~$ vncviewer localhost:1
bash: vncviewer: command not found
```
To fix this I needed to install xtightvncviewer. It might have something with that I am using XFCE on my testing server.

If so, please add it to the main post, that you need xtightviewer to get to work in XFCE.

But anything else worked well.

---

### Post by Nordoelum on 2006-04-22
Ed1t: It does :P

---

### Post by Morphius on 2006-04-24
```

vnc4server:
 Depends: xserver-common  but it is not installable

```

This is an error which results on dapper. This is because the name of the xserver-common package has changed. Furthermore, due to a problem in the program this cannot be easily remedied. This bug has been documented. You should be able to subsitute vnc4server with Xvnc or vncserver. I am working on this problem now but have run up against this error:

```

Apr 21 11:40:33 localhost xinetd[11941]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[11942]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[11943]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[11944]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[11945]: warning: can't get client address: Transport endpoint is not connected
Apr 21 11:40:33 localhost xinetd[10218]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Apr 21 11:40:43 localhost xinetd[10218]: Activating service Xvnc

```

I'll update everyone if there's more that you need to know on dapper.

---

### Post by zasf on 2006-04-29
Thanks for the howto, it works on my Ubuntu Dapper box as client and Xubuntu Dapper as server just a few notes:

[[IMG]http://ubuntuforums.org/gallery/files/5/7/5/0/6/Screenshot-vnc_thumb.png[/IMG]]("http://ubuntuforums.org/gallery/files/5/7/5/0/6/Screenshot-vnc_original.png")

1. Enable XDMCP
On Xubuntu, run 'sudo gdmsetup'

2. Install required packages (vncserver and xinetd)
On Xubuntu, run 'sudo apt-get install vncserver'

3. Set the VNC passwd
```
sudo vncpasswd /root/.vncpasswd
```

4. Start the VNC server
```
sudo /usr/bin/Xvnc :2 -query localhost -geometry 800x600 -depth 16 -once -fp /usr/share/X11/fonts/misc -dontdisconnect -nevershared -rfbauth /root/.vncpasswd
```

5. Connect the client
```
xvncviewer <ip.ad.re.ss>:2
```

don't ask me why xvncviewer instead of vncviewer, but the former one didn't work ending up with a grey screen.

It works beautifully under win as well

[[IMG]http://ubuntuforums.org/gallery/files/5/7/5/0/6/Screenshot-vnc-win_thumb.png[/IMG]]("http://ubuntuforums.org/gallery/files/5/7/5/0/6/Screenshot-vnc-win_original.png")

I used tightvnc as client

Now I only miss how to configure xinted.

---

### Post by fantagol on 2006-04-30
> [COLOR="SeaGreen"]Update: I got it to work nicely after some xorg.conf editing. Disabling the loading of 'dcc' and making a modeline for my screen did the trick.[/COLOR]

How u have edited xorg.conf ???
>>Disabling the loading of 'dcc'<<  where is ???

>>and making a modeline for my screen did the trick<< :-k please explain me !!!

tks a lot

---

### Post by eentonig on 2006-05-01
Zaraf, if you got it Xinet.d config working, can you give us an update.

You're post just got it working on my machine as well.

---

### Post by zenobia on 2006-05-04
[QUOTE=iMick]I am having an intermittant problem VNC'ing to my ubuntu box.  Sometimes I cannot connect, my VNC viewers just don't show anything without errors.

 I run top on the box locally, the xvnc process is running at 100% CPU which seems to be blocking the connections.

Is there anyway to prevent this from happening?[/QUOTE]

I think I might be having the same problem as you, and I am clueless as to why it is happening.  I have gone through the how-to several times, and posted the same problem in the other thread about using Hamachi together with resumable VNC sessions for remote controlling PC's.

Intermittently, I will simply be unable to connect with VNC to the PC that has been setup with it.  There are no errors being displayed in VNC, and this happens either by running vncviewer locally on the box, or remotely from another PC.  I can't seem to find any errors elsewhere that would give some clue as to what is going on.  I have tried reconfiguring Xvnc to listen on another port, and to use display :2 instead :1, all to no avail.

Notably, this problem seems to happen on both of my Ubuntu boxes.

Does anyone have any clue as to what might be happening in these situations, or what I can look for? The problem is completely intermittent, one day I can start up the PC and it would be fine, the next day I fire up the PC and it doesn't work.  Furthermore, I can even login one day to the PC, use the PC for a while, log out, and when attempting to login again, VNC will fail with no errors.

Help! ] (*,)

---

### Post by vik4 on 2006-05-07
I've been trying this on a dodgy old server, and I don't want to install GDM (or the rest of gnome). Instead, I'm trying to use xdm, so far with little success. the vnc session starts fine, but leaves me with a window with an empty X session (grey background, X mouse pointer). I've tried a few things to make sure xdm is allowing xdmcp connections, but nothing so far. Any ideas?

---

### Post by vik4 on 2006-05-07
So I've bit the bullet and installed gdm, and it worked. Once. I logged out, and now I get the same problem as before - a blank X session. Any ideas?

---

### Post by encompass on 2006-05-07
[QUOTE=vik4]So I've bit the bullet and installed gdm, and it worked. Once. I logged out, and now I get the same problem as before - a blank X session. Any ideas?[/QUOTE]
Have you checked your firewall?  I had that grey screen and when I shutdown my firwall it all worked again.

---

### Post by Indiana Red on 2006-05-08
[QUOTE=vik4]So I've bit the bullet and installed gdm, and it worked. Once. I logged out, and now I get the same problem as before - a blank X session. Any ideas?[/QUOTE]


I am a brand new user and this sounds exactly like what I get.  I followed the several step procedure spelled out at the beginning of this thread and my VNC client can connect from my XP box in the other room (on the same subnet) and prompts for the pwd and then I get the full grey screen with the "x" as the mouse pointer.
No firewalls are between the ubuntu box and this XP machine, just a switch and 2 WAPs.
Hmmm    what did I do wrong?

---

### Post by sguart on 2006-05-08
hmm... i seem to have a different issue... i can't lock the screen. if i lock the screen on display 1, i don't see the lock dialog box asking for password. i can use mouse to interact but i no longer sees drop down menu. keyboard events are not registering. if i ssh in and kill gnome-screensaver then i am back in business. on display 0, i can lock the screen and all. 

also sometimes when logging out, the Xvnc process is not terminated. so next time, the vnc won't connect until i restart the xinetd and kill the Xvnc.

otherwise, it's working...

thanks

sg

---

### Post by Jose Catre-Vandis on 2006-05-12
> I am a brand new user and this sounds exactly like what I get. I followed the several step procedure spelled out at the beginning of this thread and my VNC client can connect from my XP box in the other room (on the same subnet) and prompts for the pwd and then I get the full grey screen with the "x" as the mouse pointer.
No firewalls are between the ubuntu box and this XP machine, just a switch and 2 WAPs.
Hmmm what did I do wrong?

I have just got to the bottom of this one myself.

gdm needs to be running, and xdmcp also needs to be enabled.

To start gdm use the following command on the machine you are trying to remote to ( this assumes you can either physically access it, or you have already "ssh"ed in Terminal)

sudo /etc/init.d/gdm start        (you might then need to wait a minute, depending on the speed on your machine)

Next ensure that XDMCP is enabled

sudo gedit /etc/X11/gdm/gdm.conf
or
sudo nano /etc/X11/gdm/gdm.conf (if doing this through Terminal)

and find the [xdmcp] section at the end of the file
change

Enabled=False

to

Enabled=True

Then save and then best to reboot. of course if gdm is not loaded on boot, you will have to start it again

---

### Post by tigerdyr on 2006-05-14
I have a little problem with this

I have set up the Ubuntu box as posted here and try to log in using TightVNC from a Windows XP box.

If I try to connect immediately after starting the Ubunto box it all works fine - I can connect through TightVNC and all is well.

However if I start the Ubuntu box and do not log in immediately but wait 10-15 minutes before trying to connect from the Windows box, I get nothing - the TightVNC viewer just does not "find" anything and hangs around in the task manager without doing anything (not even an error, that it can't find a the server...)

I can log in through SSH to restart gdm, but this does not change anything - I stil can't get TightVNC to connect. Do any of you have any suggestions as to what might cause this and how to solve this problem?

---

### Post by encompass on 2006-05-14
[QUOTE=Indiana Red]I am a brand new user and this sounds exactly like what I get.  I followed the several step procedure spelled out at the beginning of this thread and my VNC client can connect from my XP box in the other room (on the same subnet) and prompts for the pwd and then I get the full grey screen with the "x" as the mouse pointer.
No firewalls are between the ubuntu box and this XP machine, just a switch and 2 WAPs.
Hmmm    what did I do wrong?[/QUOTE]
YUP, I think I have got it down to this:
Firewall is restricting us..
I allow 5901 and now it lets me log in to the system... with IP:1... if I wanted more I could add them
If you don't like firewall and are not used to them... try friestarter, thats what I did...
> sudo apt-get install firestarter

---

### Post by kacheng on 2006-05-16
Tichondrius,

Now that vnc4server is fixed, I've had no problem installing XDMCP for both display 1 using vnc4server (original post) and for display 0 using x11vnc.
[I'm on a Dapper amd64 kernel.]
Thanks for that - you were way ahead of your time.

Is there a way to add more displays? If I wanted to utilize display 2, display 3, etc, what must I do to the xinetd configuration?  I tried adding and duplicating things here and there, but it did not work.  Sometimes i would get display 2, but lose display 1, etc.  

What's the proper way to implement this?

Thanks.

---

### Post by Morphius on 2006-05-16
[QUOTE=kacheng]Tichondrius,

Now that vnc4server is fixed, I've had no problem installing XDMCP for both display 1 using vnc4server (original post) and for display 0 using x11vnc.
[I'm on a Dapper amd64 kernel.]
Thanks for that - you were way ahead of your time.

Is there a way to add more displays? If I wanted to utilize display 2, display 3, etc, what must I do to the xinetd configuration?  I tried adding and duplicating things here and there, but it did not work.  Sometimes i would get display 2, but lose display 1, etc.  

What's the proper way to implement this?

Thanks.[/QUOTE]

Adding additional displays should be as easy as creating a second Xvnc file (say xvnc2) and changing the port and display information for each desired display session. Cheers.

---

### Post by kacheng on 2006-05-17
That does not quite seem to be the case.

I copied /etc/xinetd.d/Xvnc to /etc/xinetd.d/Xvnc2 and change the display to :2 and port to 5902.

This gets me closer - I now have an independent display :1 as before, but display:2 gives me the display:0 connection.

So, if I open three sessions, :0 is the physical display, :1 is an XDMCP session, and :2 is the physical display again.

Do I have a missed configuration setting somewhere?  I set the XDMCP settings to allow 5 displays per host.

---

### Post by jorge.maravi on 2006-05-25
I am sorry to bottle you folks,but i have a problem like this, i have already followed every step pointed here, i am using ubuntu 5.10 and when i tried to test vncviewer in the same computer where i installed the vncserver package (required here) i got this error message:

jmaravi@j-maravi1:~$ vncviewer j-maravi1:0
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection timed out
Unable to connect to VNC server

I can ping the name j-maravi1, i have set up all the configuration on the vino-preferences.....

The xinitd service is running, i don't know what else to do....

Thanks

Jorge

---

### Post by jadba on 2006-05-30
This is an excellent HOW-TO.  Helped to relieve me of the restrictions imposed by the Gnome Remote Desktop i.e. limited screen resolution.  Thanks Tichondrius.

---

### Post by lvivier on 2006-06-01
I have followed the instructions in the tutorial without much success.

Initially, I was able to connect locally to the vnc server, but all I got was a window with the infamous grey background and "X" cursor. I then edited my gdm configuration to enable XDMCP, and also changed my router settings to forward port 5901 (which I thought would be unnecessary for local connection) and rebooted.

After that reboot. when attempting to connect on localhost using vncviewer, I am prompted for the password, and after entering it vncviewer exits with:

ReadFromRFBServer: rdr::EndOfStream

which is not very helpful. Subsequent reboots have not affected anything. I have tried changing the password with "sudo vncpasswd /root/.vncpasswd" but it has had no effect.

Has anyone experienced anything like this, or does anyone know what this message means? Please let me know if I should provide any more information, and thanks in advance.

---

### Post by lime4x4 on 2006-06-04
okay i got this up and running for the most part..I can log in but the screen is all grey and wavy...i have a 21 inch widescreen lcd panel that runs at 1680x1050 would i have to edit the geometry line to something else?

---

### Post by dmizer on 2006-06-04
[QUOTE=Tichondrius]1. Enable XDMCP
**System->Administration->Login Screen Setup**
      Tab **Security->Enable XDMCP**
      Tab **XDMCP**--> You can disable "Honor Indirect Requests"[/QUOTE]
is there any way to perform this step with no gui interface?  i'm trying to get this done via ssh.

---

### Post by L4mp on 2006-06-05
> Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

How do you do this in dapper? I can't find these settings in dapper, my vnc worked perfectly in breezy but since i updated i get those dot screens.
This normally is because of the XDMCP setting.

---

### Post by Cirrocco on 2006-06-05
this HOW-To needs to be rewritten for Dapper.

of all VNC options - THIS ONE was my preferred option. and now it no longer applies due to XDMCP.

Someone please write a new 'resumable session vnc4server how to' for dapper.
[-o<

---

### Post by ABeakyboy on 2006-06-06
[QUOTE=L4mp]How do you do this in dapper? I can't find these settings in dapper, my vnc worked perfectly in breezy but since i updated i get those dot screens.
This normally is because of the XDMCP setting.[/QUOTE]

Ok, this is what I did.  I'm rather new at this so I can't be sure if this will work for you....or anyone for that matter.  I'm running Ubuntu 6.06.  

Please note, these steps are only what you want to do if you had your VNC setup working under 5.10 and then you upgraded to 6.06 and it doesn't work anymore.

1.  Log in to GNOME.
2.  Click "System" -> "Administration" -> "Login Window"
3.  Enter your password if necessary.
4.  Click the "Remote" tab.
5.  Under the "Style:" drop down box, choose "Same as Local".
6.  Click the "Configure XDMCP" button and make sure "Honor Indirect Requests" is set to what you want it to be set to.
7.  Click "close" twice.

See if this does it for you.  Good luck!

Edit:  Forgot to add that my VNC session doesn't seem to be resumable.  I don't know if it's due to the Dapper upgrade or if I messed up somewhere else.

---

### Post by Cirrocco on 2006-06-06
well I got xdmcp setup
followed the tutorial
it asks for a vnc password
and won't take the one I defined.

/poop

---

### Post by L4mp on 2006-06-06
[QUOTE=ABeakyboy]Ok, this is what I did.  I'm rather new at this so I can't be sure if this will work for you....or anyone for that matter.  I'm running Ubuntu 6.06.  

Please note, these steps are only what you want to do if you had your VNC setup working under 5.10 and then you upgraded to 6.06 and it doesn't work anymore.

1.  Log in to GNOME.
2.  Click "System" -> "Administration" -> "Login Window"
3.  Enter your password if necessary.
4.  Click the "Remote" tab.
5.  Under the "Style:" drop down box, choose "Same as Local".
6.  Click the "Configure XDMCP" button and make sure "Honor Indirect Requests" is set to what you want it to be set to.
7.  Click "close" twice.

See if this does it for you.  Good luck!

Edit:  Forgot to add that my VNC session doesn't seem to be resumable.  I don't know if it's due to the Dapper upgrade or if I messed up somewhere else.[/QUOTE]


thanks alot for your reply!

but i'm sorry to say that it didn't worked :???: 

still get the "pixelscreen" when i make the connection

---

### Post by jer2eydevil88 on 2006-06-07
Okay I am totally lost from all the posts in this topic.

Can someone tell me how to enable resumeable sessions in 6.06 with the commands to get the software (if any) through apt-get?

I would like to be able to VNC into my new ubuntu server as its the last peice of the puzzle for me.

---

### Post by elemental666 on 2006-06-07
I haven't read all 12 pages of this thread, but...  I did the howto in post 1, and did the stuff listed here: [https://wiki.ubuntu.com/VNC?highlight=%28VNC%29](https://wiki.ubuntu.com/VNC?highlight=%28VNC%29)

if I do vncviewer <ip>:0 I can take control of my desktop...
if I do vncviewer <ip>:1 I get a dead x screen (grey backgroud with x cursor)...

maybe GDM is the problem?

EDIT: Bingo!  enabled xdmcp in gdm.conf, rebooted and I'm in, at least locally

---

### Post by L4mp on 2006-06-07
Set up VNC server with resumable sessions on dapper (6.06) 


1. Enable XDMCP

```
sudo gedit /etc/gdm/gdm.conf

```

then find this rule:
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
# RemoteGreeter=/usr/lib/gdm/gdmlogin

remove the '#' in the last line so there should be:

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
   RemoteGreeter=/usr/lib/gdm/gdmlogin


Note: Before doing the next step, you need to make sure the extra repositories (e.g. universe) are enabled:
[http://easylinux.info/wiki/Ubuntu#Ho...a_repositories](http://easylinux.info/wiki/Ubuntu#Ho...a_repositories)

2. Install required packages (vncserver and xinetd)

Code:
```

sudo apt-get install vnc4server xinetd
```


Note to AMD64 users: The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:

Code:

```
wget http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb wget http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb sudo dpkg -i vnc4server_4.0-7.3_amd64.deb sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb
```



3. Set the VNC passwd
Code:

```
sudo vncpasswd /root/.vncpasswd
```


4. Add vnc service to xinetd:
Code:
```

sudo gedit /etc/xinetd.d/Xvnc

```

Enter this into the new file:

Code:
```

service Xvnc { type = UNLISTED disable = no socket_type = stream protocol = tcp wait = yes user = root server = /usr/bin/Xvnc server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd port = 5901 }

```

5. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

Code:```


sudo /etc/init.d/xinetd stop sudo killall Xvnc sudo /etc/init.d/xinetd start
```


6. That's it! To test that this is working first try to connect from the same machine (the machine we just set up the VNC server on):

Code:
```

vncviewer localhost:1

```

You should be prompted for the VNC password, and then see the GDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above). Remember to use the VNC server machine's domain name or IP address, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails, then this means you have a problem with a firewall which is blocking some ports. See the notes below about how to deal with that.

Note about ports: The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

Note about security: This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started. So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300" to change it to 5 minutes.




ps. This was copy/pasted from a few posts made by other ppl, I simply putted them together and tested everything! It works here for me now.

If questions just post :)

---

### Post by p_alexander on 2006-06-07
Can you delete these? I took out the question I had because I resolved it. Sometimes talking to yourself works. See below.

---

### Post by p_alexander on 2006-06-07
I added a bunch of stuff that I had to do in order to make this work on my amd64 box. This box was originally installed under 5.10 and upgraded to 6.06. Everything pretty much out of the box. YMMV.

Oh yeah, this also made Vino work as well, not sure why. Perhaps the xdmcp stuff. So, vino is on display 0, vnc4 on display 1.

This is copied from L4mp's post above with my changes added to the amd64 section.

PS - Ignore the "HTML" comment in the "HTML Code" boxes. I couldn't get regular code boxes to include line breaks. Noob at work.

1. Enable XDMCP

```
sudo gedit /etc/gdm/gdm.conf

```
then find this rule:
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
# RemoteGreeter=/usr/lib/gdm/gdmlogin

remove the '#' in the last line so there should be:

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
   RemoteGreeter=/usr/lib/gdm/gdmlogin

[COLOR="Red"]Note: I had to also change another part of the gdm.conf file. Also, a restart was required so gdm could read the new configuration.[/COLOR]

Look for the following piece of text in /etc/gdm/gdm.conf
[html]
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=false
[/html]
Change the Enable=false to Enable=true

Note: Before doing the next step, you need to make sure the extra repositories (e.g. universe) are enabled:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

2. Install required packages (vncserver and xinetd)

Code:
```

sudo apt-get install vnc4server xinetd
```
i386 users can skip to step 3, AMD64 users continue to 2a.

2a. Note to AMD64 users: The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:

Code:
[HTML]
wget http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb
wget http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb
sudo dpkg -i vnc4server_4.0-7.3_amd64.deb
sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb
[/HTML]
Some people may have unmet depencies in these packages and will need to install additional packages.

Code:
[HTML]
sudo apt-get install gcc-3.3-base
sudo apt-get install libstdc++5
[/HTML]
There is one dependent package that cannot be installed as it has been deprecated in the new 6.06. Therefore, we have to force the vnc4server packages to install.

Code:
[HTML]
sudo dpkg -i --force-all vnc4server_4.0-7.3_amd64.deb 
sudo dpkg -i --force-all xvnc4server_4.0-7.3_amd64.deb
[/HTML]
I am loathe to force package installs BUT it seems to work in this case. An updated, working AMD64 vnc4server package would be preferable.

3. Set the VNC passwd

Code:
```
sudo vncpasswd /root/.vncpasswd
```

4. Add vnc service to xinetd:

Code:
```

sudo gedit /etc/xinetd.d/Xvnc

```
Enter this into the new file:

Code:
[HTML]
service Xvnc
{
     type = UNLISTED
     disable = no
     socket_type = stream
     protocol = tcp
     wait = yes
     user = root
     server = /usr/bin/Xvnc
     server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
     port = 5901
}
[/HTML]

5. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

Code:
[HTML]
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start
[/HTML]

6. That's it! To test that this is working first try to connect from the same machine (the machine we just set up the VNC server on):

Code:
```

vncviewer localhost:1

```

You should be prompted for the VNC password, and then see the GDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above). Remember to use the VNC server machine's domain name or IP address, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails, then this means you have a problem with a firewall which is blocking some ports. See the notes below about how to deal with that.

Note about ports: The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

Note about security: This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started. So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300" to change it to 5 minutes.

---

### Post by L4mp on 2006-06-08
ok perfect dude!
i'll make a new thread with the tag of dapper 6.06 so other ppl will find it easy!

---

### Post by JeyKey on 2006-06-10
It doesn't work here, this is what happens:
[IMG]http://80.203.31.175/ubuntuforums/english/vnc.png[/IMG]

I haven't read through the whole thread, so perhaps someone has posted this before. And if it matters, I'm running Ubuntu 6.06 with GNOME

---

### Post by rockmanac on 2006-06-11
This is where I'm at...  I've read through the whole document and still can't get VNC Working.

-A

---

### Post by mjfarina on 2006-06-11
OK, so is there a way to configure VNC entirely from remote?? I want to log in over SSH terminal and configure VNC to accept my connection. Anyone know how to do this??

---

### Post by p_alexander on 2006-06-11
[QUOTE=mjfarina]OK, so is there a way to configure VNC entirely from remote?? I want to log in over SSH terminal and configure VNC to accept my connection. Anyone know how to do this??[/QUOTE]

Check out the instructions on page 12 of this thread and replace the command gedit with nano or whatever text editor you like to use from the command line.

---

### Post by mjfarina on 2006-06-13
[QUOTE=p_alexander]Check out the instructions on page 12 of this thread and replace the command gedit with nano or whatever text editor you like to use from the command line.[/QUOTE]
ya, I did that...I keep getting this "markfarina@UBN600:~$ vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory" when trying to set a password??

Of course, it tells me it can't start the vnc server without a password.

---

### Post by p_alexander on 2006-06-13
[QUOTE=mjfarina]ya, I did that...I keep getting this "markfarina@UBN600:~$ vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory" when trying to set a password??[/QUOTE]

I did an apt-file search to see which package that file is associated with. You can try installing the one that it returned: libstdc++2.10-glibc2.2

Type:
```

sudo apt-get install libstdc++2.10-glibc2.2

```

But I don't have that package installed and I didn't need the file you mentioned. Anyway, it's worth a shot.

---

### Post by iMick on 2006-06-13
[QUOTE=zenobia]I think I might be having the same problem as you, and I am clueless as to why it is happening.  I have gone through the how-to several times, and posted the same problem in the other thread about using Hamachi together with resumable VNC sessions for remote controlling PC's. (*,)[/QUOTE]


Glad I'm not the only one.  My problem is also intermittant, killing the xvnc process and restarting xinetd will allways fix the problem for a while.

Anyone think of a solution yet?  I don't want to update to Dapper untill I get this problem sorted.

Cheers

Go Socceroos!  First world cup win ever!

---

### Post by davidfdr on 2006-06-19
[QUOTE=JeyKey]It doesn't work here, this is what happens:


I haven't read through the whole thread, so perhaps someone has posted this before. And if it matters, I'm running Ubuntu 6.06 with GNOME[/QUOTE]

I'm using the same version of ubuntu and I'm having the same problem...

Anybody could help us with this problem?

---

### Post by Daiver on 2006-07-01
Thank you very much for this.  It worked perfectly on the first try using Ubuntu 5.10! :D

---

### Post by unixping on 2006-07-01
When I connect to myself i just see a checkered screen? What did I do wrong?

---

### Post by Test33 on 2006-07-06
> When I connect to myself i just see a checkered screen? What did I do wrong?

Same thing here. Any ideas?

---

### Post by krazykirk on 2006-07-09
hmm... it's not quite working for me...

```
kirk@kirk-desktop:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)
```

thats what happens when i try to test it.

Anyone know a solution?

---

### Post by gurgle on 2006-07-12
i set my password like in the guide, but it wont authenticate for me. weird.....

---

### Post by Zoltok on 2006-07-13
I'm having a weird problem connecting.  I've followed the instructions exactly and it seems to be working, but occasionally I will lose the ability to connect from my viewer.  I can ping the machine, but I am never asked for a password and the process keeps running; it simply looks like nothing happens.  If I restart the server it begins to work again, and if I log in and check the processes VNC is always running, but that may just be starting when I log in.

The worst part is that this is a machine in a locked server room, which means I generally won't have physical access to it.  If I try telnetting in, I just get a blank unresponsive window and I am still never prompted for my VNC password.  What gives?

---

### Post by AsYouWish on 2006-07-13
Hi

I followed these instrucions and have VNC working great... with one exception. Many things which should not be black are showing up black when I am logged in through VNC. A list:
Big chunks of the taskbar in Gnome (top and bottom)
All drop down menus (gnome and xfce)
parts of the syaptic background (gnome)
the background of the message box in gaim

For stuff like the drop down menus, if i scroll over the entries  the text changes colors and I can read it, but its just annoying not to see all the options. The icons are visible though.

Im using vnc4server on the ubuntu machine and RealVNC client on my winXP laptop. Is this a fixable problem, or just an interent vnc issue? Will a different client help? Suggestions?

Thanks

---

### Post by omegasoul on 2006-07-30
Just wanted to say thank you for the how-to.

---

### Post by James_N on 2006-07-31
Ive set it all up in dapper and it works fine internally. Externally i get this: RFB 003.008 when i type in the external IP and port (5901)

Ive port forwarded 5901 and it works fine internally but not externally. Anyone know why? :)

Thanks

---

### Post by James_N on 2006-08-01
> **James_N said:**
> Ive set it all up in dapper and it works fine internally. Externally i get this: RFB 003.008 when i type in the external IP and port (5901)

Ive port forwarded 5901 and it works fine internally but not externally. Anyone know why? :)

Thanks

anyone? :)

Thanks

---

### Post by James_N on 2006-08-01
Im trying to use firefox to access this. Can i use a web browser or do i have to use a VNC viewer (on windows systems)?

---

### Post by trmentry on 2006-08-01
> **Test33 said:**
> Same thing here. Any ideas?

I just followed the instructions as well and when I connect to localhost or from another machine on the lan, I get challeneged for the vnc passwd.  I enter it.  It pops up the 1024x768 window with an X mouse cursor, but that's it.  No logon afterwards.  

Running fresh install of Dapper.

---

### Post by dodob on 2006-08-02
> **trmentry said:**
> I just followed the instructions as well and when I connect to localhost or from another machine on the lan, I get challeneged for the vnc passwd.  I enter it.  It pops up the 1024x768 window with an X mouse cursor, but that's it.  No logon afterwards.  

Running fresh install of Dapper.

I think this happens because twm is not installed by default.

~/.vnc/xstartup is run when a VNC client is connected. It opens vncconfig, an xterm, and then tries to run twm.

What I did was comment out the two lines in ~/.vnc/xstartup "for a normal desktop", AND 'sudo chmod +x /etc/X11/xinit/xinitrc'. If I didn't make xinitrc executable, the second line that exec's xinitrc fails and I only get a checkered screen.

xinitrc goes on to source /etc/X11/Xsession, which starts a normal desktop. The session is resumable.

(It is worth noting that the above applies only to Ubuntu package 'vnc4server'. Package 'vncserver' is version 3.3.x and doesn't look for ~/.vnc/xstartup. Instead, it fires up /etc/X11/Xsession directly. I guess one can also edit xstartup to exec Xsession instead of xinitrc, leaving xinitrc non-executable.)

I did not enable XDMCP in /etc/gdm/gdm.conf-custom or use xinetd. I start the vncserver manually through SSH, limited to localhost connections, and tunnel the VNC port.

My questions:
[LIST=1]
[*] What are the vulnerabilities to having to +x /etc/xinit/xinitrc?
[*] Why twm and not a normal desktop by default? Is it purely a bandwidth concern or is there something more serious (security issues), or just nicer/sensible from an implementation perspective (normal desktop startup scripts doing desktop-y things that are unnecessary for remote login--like startup sounds)?
[*] Are there shortcomings to not using xinetd for VNC? I'm running the server on a semi-dedicated machine, so saving resources is not much of a problem. But even on personal machines, is VNC traffic heavy enough to warrant skipping over xinetd altogether?
[*] Does XDMCP provide a remote greeter/login screen upon connect?
[*] What connects opening an Xvnc session to XDMCP? What I mean is this: I tried enabling xdmcp in /etc/gdm/gdm.conf-custom, then started my vncserver as usual. But I saw no difference logging in through a VNC client (i.e.: no login screen). How do I tell that XDMCP is working?
[/LIST]

---

### Post by Peatey on 2006-08-14
> **dodob said:**
> Why twm and not a normal desktop by default? Is it purely a bandwidth concern or is there something more serious (security issues), or just nicer/sensible from an implementation perspective (normal desktop startup scripts doing desktop-y things that are unnecessary for remote login--like startup sounds)?

From the [RealVNC FAQ]("http://www.realvnc.com/faq.html#grey") (my emphasis added):

> 
Why do I just get a grey desktop in my Unix VNC Server?
You should run the vncserver script to start a VNC server, rather than the Xvnc program directly. vncserver runs Xvnc with appropriate options and starts some X applications to be displayed in the VNC desktop. **The applications it tries to start are specified in $HOME/.vnc/xstartup**, which **can be tailored to your requirements**. The default setup is to run the 'twm' window manager and a single 'xterm' window. If these applications fail to run, then you will see a grey 'rootweave' desktop. The most likely reason applications fail to run is that they are not in your path. Any error messages from this startup should appear in $HOME/.vnc/host:display#.log. For further information see the vncserver manual page.

From the FAQ, it appears that it's none of your reasonable speculations.  Looks like the RealVNC folks just started a bare-bones window manager with xterm in case the server was running without any graphical desktop environment.  HTH.

---

### Post by turath on 2006-08-15
Well Guys

I ave been trying to follow some of the advice you have given

From my windows box and on the ubuntubox when I 

vncviewer localhost:1

The windows opens up I can see the X cursor

but the whole damm thing is grey???


so Umm what did I do wrong :)

-TY

---

### Post by detyabozhye on 2006-08-15
Awesome Howtos man! Page one and page 7.

---

### Post by detyabozhye on 2006-08-16
> **x0inx said:**
> Tichondrius, thank you for this great tutorial on vnc. People like you are making my switch to linux much easier and enjoyable. My only problem with x11vnc is that when I connect to :0, it does not prompt for a password like :1 does; it just goes straight to what is on my monitor. I am running Breezy AMD64.

Thank you.

Yeah, same problem here, anybody figured this out yet?

---

### Post by detyabozhye on 2006-08-16
Never mind I figured it out:

sudo gedit /etc/xinetd.d/x11vnc

add this:
 -rfbauth /root/.vncpasswd

at the end of this line:
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg

---

### Post by turath on 2006-08-16
> **detyabozhye said:**
> Awesome Howtos man! Page one and page 7.

Howdy

Ok so far ...I am not sure how it happened...

somewhere between doin work and playing around with this and 
this forums support It's working.

Wow you guys are Magical Even

Unfortunately 

I have /usr/bin/x11vnc that I need to start up.

How do I have that automatically started up with boot?

I tried it myself by making a 

/init.d/xvnc1start

did chmod 700 a+x

update-rc.d xvnc1start

and it did not work.

So Where do I go now?

---

### Post by kingmob on 2006-08-26
Ok, i've been using this for a while now, but i actually want back to the situation where i basicly control screen 0. This so that i can remote control my computer from a handheld device. How do i revert back to the old situation and then make it work in xfce?

---

### Post by kb5won on 2006-09-12
Thanks Tichondrius!

This worked for me using Xubuntu 6.06

> **Tichondrius said:**
> Ok, to resume a session you started on your physical display (display :0) all you really need is to turn on Ubuntu's remote desktop feature using the Remote Desktop Preferences dialog box accessible from System->Preferences->Remote Desktop menu item.  Just check the first two options there (allow other users to view your desktop and allow other users to control your desktop) and set the password in the bottom of the dialog box (check the REuqire password option), and you're done ! 
  The above uses the built in VNC capability that Ubuntu comes installed with, but the drawback is that it's a little slow, and you need to enable it for each user which wants to allow his desktop to be view or controlled remotely. Also this doesn't allow remote VNC clients to log in to GDM, only to view a GDM session that was started by someone actually using the physical display. So if currently no one is logged in, a remote user cannot connect to display :0 and start a new session.
  But don't worry - there is a better way which allows you to view the phyical display remotely and also log-in to a new session from GDM (using a remote VNC client) !  And it works faster (as fast as the regular VNC server), and works for all users. Here's how to do that :

1. Install x11vnc package

```
sudo apt-get install x11vnc
```

2. Add x11vnc service to xinetd:

```
sudo gedit /etc/xinetd.d/x11vnc
```

Enter this into the new file:

```

service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg
        disable         = no
}

```

3. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo killall x11vnc
sudo /etc/init.d/xinetd start
```

4. From a remote machine use your VNC client to connect to display :0

```
vncviewer  vnchost:0
```

Note that after loggging from GDM and also after logging out from the X-session back and going back to GDM, the VNC client gets disconnected for some reason. So you just need to re-connect and you will get back into the session you logged into. When logging out, the disconnect happens when gnome asks you to confirm your intention to log out, so it's best to turn off the log-out confirmation dialog box by going to System->Preferences->Sessions and un-checking the "ask on logout" option.

Please tell me how this works out for you....I plan to add this to the HOWTO

---

### Post by madubuntuer on 2006-09-14
How come I cant install the package
 vnc4server depends on xserver-common; however:
  Package xserver-common is not installed.
I am using Dapper

---

### Post by paperdiesel on 2006-09-16
Has anyone been able to get this working using kubuntu 6.06?  I followed the guide verbatim, but I get this message:

```

ti@ti-kubuntu:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)
ti@ti-kubuntu:~$
```

I even edited my /etc/kde3/kdm/kdmrc and /etc/kde3/kdm/Xaccess files to enable XDMCP, rebooted, and I still get the same error.

Also, if I just run vncserver from the command line, I can then run xvncviewer and connect with no problems.  Why can't I connect the normal way?  Has anyone got this to work on kubuntu?

---

### Post by rmurphy440m on 2006-09-16
I attempted the install of VNC following the instructions at the beginning of this thread. I try to connect locally but I dont get a login screen in X. I've installed VNC on a windows box and it just ran after opening the port on the firewall...no configuration tweaks and I didnt have to touch the command line..it just installed and ran. Look at how BIG this thread is just to get a simple remote desktop application to work...this is nuts.

---

### Post by paperdiesel on 2006-09-17
**FIXED!!!**

I found out why I was getting this error:

ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)

When I had initially installed the packages using apt-get, I did it like this:

**wrong way:**
```
sudo apt-get install vncserver xinetd
```

Apparently, vncserver is **NOT** the same as vnc4server.  So to fix it, I ran:

```
sudo apt-get remove vncserver
```

Then I started completely over, this time doing it the right way:

**right way:**
```
sudo apt-get install vnc4server
```

I followed the rest of the steps and it's working perfectly on kubuntu 6.06!

Thanks!

---

### Post by ianma99 on 2006-09-19
I'm using 6.06LTS on a non-AMD64 system.  After following the instructions at the beginning of this thread verbatim I was having the same problems with Connection reset (104) as many other people.  After much frustration I now have a working solution.  It seems the problem is that vnc4server will work (partially at least) with the vnccommon package.  Hence it works when started from the command line but not from xinetd.  

There are two possible options:
1) modify the Xvnc conf file to 'wait = no'.  This seems to fix the disconnect problem but then the vnc session is not resumable.

2) make sure that you have the vnc4common package installed - ('apt-get install vnc4server' didn't automatically also get the vnc4common package for me).  This now works perfectly for resumable session if you followed the original howto from page 1 of the thread.

Hope this helps somebody else.

---

### Post by shizow on 2006-09-20
i use Kubuntu, how do i have to change the line with gdm?

> **Tichondrius said:**
> Ok, to resume a session you started on your physical display (display :0) all you really need is to turn on Ubuntu's remote desktop feature using the Remote Desktop Preferences dialog box accessible from System->Preferences->Remote Desktop menu item.  Just check the first two options there (allow other users to view your desktop and allow other users to control your desktop) and set the password in the bottom of the dialog box (check the REuqire password option), and you're done ! 
  The above uses the built in VNC capability that Ubuntu comes installed with, but the drawback is that it's a little slow, and you need to enable it for each user which wants to allow his desktop to be view or controlled remotely. Also this doesn't allow remote VNC clients to log in to GDM, only to view a GDM session that was started by someone actually using the physical display. So if currently no one is logged in, a remote user cannot connect to display :0 and start a new session.
  But don't worry - there is a better way which allows you to view the phyical display remotely and also log-in to a new session from GDM (using a remote VNC client) !  And it works faster (as fast as the regular VNC server), and works for all users. Here's how to do that :

1. Install x11vnc package

```
sudo apt-get install x11vnc
```

2. Add x11vnc service to xinetd:

```
sudo gedit /etc/xinetd.d/x11vnc
```

Enter this into the new file:

```

service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg
        disable         = no
}

```

3. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo killall x11vnc
sudo /etc/init.d/xinetd start
```

4. From a remote machine use your VNC client to connect to display :0

```
vncviewer  vnchost:0
```

Note that after loggging from GDM and also after logging out from the X-session back and going back to GDM, the VNC client gets disconnected for some reason. So you just need to re-connect and you will get back into the session you logged into. When logging out, the disconnect happens when gnome asks you to confirm your intention to log out, so it's best to turn off the log-out confirmation dialog box by going to System->Preferences->Sessions and un-checking the "ask on logout" option.

Please tell me how this works out for you....I plan to add this to the HOWTO

---

### Post by GoBieN on 2006-09-20
I had the famous checkboard screen after following all these steps on Ubuntu 6.06 server. 
Solution for me:
Log in as normal user in gnome, go to "system menu -> preferences -> remote desktop: Enable the checkboxes at allow to view and allow to control. Furthermore i also changed the settings in System -> Management -> logon window -> tab remote: to "style=same as local" and click on "Configure XDCMP" remove the checkbox at honor indirect requests.

ps: I to have vnc4server with session and the normal vncserver running side by side, altough I only installed the normal vncserver like 5 minutes ago, the seem to work side by side perfectly and automatically use a higer desktop number (:2) beacuse :1 is taken by vnc4server trough xinetd

---

### Post by charles.g.moore on 2006-09-23
I followed the steps in the how-to perfectly but am still getting the grey pixillated screen when i type:  vncviewer localhost:1
My mouse works but the screen just stays grey ???
This is what the output is:

charles@charles-desktop:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password:
VNC authentication succeeded
Desktop name "x11"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6

Could the fact that I am running a dual mointor setup on my desktop be an issue?

Im totally at a loss, I know I probably have not given you guys the info you need to diagnose the prob. but I truthfully don't know what type of info you need.  Any help would be appreciated.

btw im running the vnc4server package, on dapper 6.06lts, if you know of a better VNC server please tell me, and maybe a hint at how I would uninstall the vnc4server before adding the other (or do i really even have to uninstall?)

Here is my /etc/xinetd.d/Xvnc:
charles@charles-desktop:~$ sudo cat /etc/xinetd.d/Xvnc
Password:
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

---

### Post by detyabozhye on 2006-09-23
I had the same thing until I restarted (I know ur not supposed to restart on Linux, but hey, it fixed it).

---

### Post by charles.g.moore on 2006-09-24
> **detyabozhye said:**
> I had the same thing until I restarted (I know ur not supposed to restart on Linux, but hey, it fixed it).
Restarted and it worked perfectly!!!
Thanks for the reply...

---

### Post by charles.g.moore on 2006-09-25
I logged into my ubuntu box for the first time today and the login was successful but...

I have a dual monitor setup using twinview normally my login prompt shows up on the left screen.

When I logged in for the first time using my wife's windows laptop there was no main panel on the remote view screen and my Gdesklets starterbar did not show up. 

I guess I can understand the starter bar not being there and i dont mind putting the icons on my desktop.  but the main panel did not show up on the  remote screen and when I went back to my original ubuntu box the main panel was now on the right side rather than the left.

even worse when I tried to move it back to the left side it kept going back to the right, the only way it would stay is if i restarted then moved it.

Now on top of that the login box shows up on the right screen instead of the left like before now...?

Any help would be appreciated.

i used the login_name.server_name.com:1 to get into my home box. should I have used two or something???

What does this mean too.  I quit the remote VNC connection by closing the box and restarted my ubuntu box but I get this:

charles@charles-desktop:~$ who
charles  :0           2006-09-24 22:50
charles  pts/0        2006-09-24 22:59 (:0.0)
charles@charles-desktop:~$

Is that connection still open?

---

### Post by dissdigg on 2006-10-02
> **detyabozhye said:**
> Never mind I figured it out:

sudo gedit /etc/xinetd.d/x11vnc

add this:
 -rfbauth /root/.vncpasswd

at the end of this line:
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg


Thank you for this.

Just did a fresh install of 6.06 and didn't have luck with Xvnc, but x11vnc is working.
 
Anyone happen to know the server_args to customize the resolution?

---

### Post by justincataldo on 2006-10-04
Woohoo it works!

I had to add: > gnome-session & ...to my ~/.vnc/xstartup file (instead of): > twm &

---

### Post by magquatre on 2006-10-06
> **GoBieN said:**
> I had the famous checkboard screen after following all these steps on Ubuntu 6.06 server. 
Solution for me:
Log in as normal user in gnome, go to "system menu -> preferences -> remote desktop: Enable the checkboxes at allow to view and allow to control. Furthermore i also changed the settings in System -> Management -> logon window -> tab remote: to "style=same as local" and click on "Configure XDCMP" remove the checkbox at honor indirect requests.

ps: I to have vnc4server with session and the normal vncserver running side by side, altough I only installed the normal vncserver like 5 minutes ago, the seem to work side by side perfectly and automatically use a higer desktop number (:2) beacuse :1 is taken by vnc4server trough xinetd


thanks a bunch, that fixed my grey screen problem too. of course *after* i rebooted.

---

### Post by magquatre on 2006-10-06
> **dissdigg said:**
> Thank you for this.

Just did a fresh install of 6.06 and didn't have luck with Xvnc, but x11vnc is working.
 
Anyone happen to know the server_args to customize the resolution?

```
service Xvnc 
{ 
        type = UNLISTED 
        disable = no 
        socket_type = stream 
        protocol = tcp 
        wait = yes 
        user = root 
        server = /usr/bin/Xvnc 
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -o$
        port = 5901 
} 
```

-geometry flag will do the trick. that is if you are using xvnc. not sure about the x11vnc

try the man page.
[http://manpages.debian.net/cgi-bin/display_man.cgi?id=6bc299cad023497ac2424006adba3792&format=html](http://manpages.debian.net/cgi-bin/display_man.cgi?id=6bc299cad023497ac2424006adba3792&format=html)

---

### Post by thanathos on 2006-10-14
Hi Guys

I'm a total noob when it comes to linux....but i want to try and learn....
So , I got Unbuntu on one of my machines...about 2 hours ago
I tried to setup a VNC server ... followed all the instructions in the  first post... 
Well...i ran out of luck about here :

sudo gedit /etc/xinetd.d/Xvnc

I got the wondow opened but after I paste the suggested text...i can't save it.:-| It just gives me an error : could not save the file /etc/xinetd.d/Xvnc

a small kick in the a$$ for a big step forward anyone?
thanks

---

### Post by MBaran on 2006-10-18
I just wanted to post and update to this thread for anyone experiencing problems with Edgy (and maybe Beryl? not sure if thats what hosed me) setting this up.


In the /etc/xinetd.d/Xvnc file

change -fp /usr/share/X11/fonts/misc

TO

-fp /usr/share/fonts/X11/misc

This was my findings after ~2 hours of working away between x11vnc and vnc4server.

Thx.!

---

### Post by lovepolo on 2006-10-26
Hi All,

I followed OP's instruction and am able to run flawless. But I recently found some hacker got into my machine with vnc viewer. My password is reasonably long.

Can anybody confirm with me this method will have security issue?

---

### Post by detyabozhye on 2006-10-26
> **dissdigg said:**
> Thank you for this.

Just did a fresh install of 6.06 and didn't have luck with Xvnc, but x11vnc is working.
 
Anyone happen to know the server_args to customize the resolution?

I don't think you can set the resolution there, because it's forwarding your physical display.

---

### Post by reVox on 2006-10-27
> **MBaran said:**
> I just wanted to post and update to this thread for anyone experiencing problems with Edgy (and maybe Beryl? not sure if thats what hosed me) setting this up.


In the /etc/xinetd.d/Xvnc file

change -fp /usr/share/X11/fonts/misc

TO

-fp /usr/share/fonts/X11/misc

This was my findings after ~2 hours of working away between x11vnc and vnc4server.

Thx.!

Hey a big thanks MBaran - I just upgraded to Edgy and my vncviewer wasn't authenticating (i was not being prompted for password). I had to reestablish my System/Administration/login window/remote/style to 'same as user' in addition to your fix above. finally, was getting the grey screen after manual stop and start, so restarted system, and it worked first go. many thanks again! you saved me a good deal of ](*,) time.

---

### Post by fm1234 on 2006-10-28
Hi

after updrading from 606 to 6.10 my vnc setup stopped working. After trying it out in the command line I found out there was a problem with the fixed font. The font path is different: /usr/share/fonts/X11/misc  (fonts and X11 are swapped).

I am now able to run Xvnc from the command line and connect to it. However, I'm not able to have it running from xinetd. It listens to the port but Xvnc is not running. The xinetd.log file is not useful: "... 1 service running". I've also tried to set a logfile for the Xvnc service but the file stays empty. If I try to connect to Xvnc I get the error "...too many connections...".

I'm stuck here. Suggestions?

TIA,
Fernando

---

### Post by Footer on 2006-10-30
Fernando,

Could you explain a little further exactly where you switched around fonts and X11?  My vncviewer quit working as well when I went from Dapper to Edgy and it's not clear to me how I fix this.  Even after reading all of these posts!  It worked just fine under Dapper!

Here's the error I get:

vncviewer media_machine:2
VNC viewer version 3.3.7 - built Jul 4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.3 (viewer 3.3)
Password:
VNC authentication succeeded
Desktop name "media_machine:2"
Connected to VNC server, using protocol version 3.3
VNC server default format:
32 bits per pixel.
Least significant byte first in each pixel.
True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-16-*-*-*-*-*-*-*" to type FontStruct
Warning: Unable to load any usable ISO8859 font
Warning: Unable to load any usable ISO8859 font
Error: Aborting: no font found

Thanks in advance!

---

### Post by iansyngin on 2006-11-05
Tried the following

```
sudo Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
```Now, from another terminal try to connect:

```
vncviewer localhost:2
```tell me if that works......[/quote]

I receive the following after

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Sun Nov  5 13:20:56 2006
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0

Fatal server error:
could not open default font 'fixed'

---

### Post by Footer on 2006-11-05
I answered my own question and fixed my vncviewer font problem.  See reply #8 in this thread:

[http://www.ubuntuforums.org/showthread.php?t=288963](http://www.ubuntuforums.org/showthread.php?t=288963)

Not sure about the HOWTO subject of this thread however.

---

### Post by pjman on 2006-11-07
> **reVox said:**
> [QUOTE=MBaran;1630733]I just wanted to post and update to this thread for anyone experiencing problems with Edgy (and maybe Beryl? not sure if thats what hosed me) setting this up.


In the /etc/xinetd.d/Xvnc file

change -fp /usr/share/X11/fonts/misc

TO

-fp /usr/share/fonts/X11/misc

This was my findings after ~2 hours of working away between x11vnc and vnc4server.

Thx.!



Hey a big thanks MBaran - I just upgraded to Edgy and my vncviewer wasn't authenticating (i was not being prompted for password). I had to reestablish my System/Administration/login window/remote/style to 'same as user' in addition to your fix above. finally, was getting the grey screen after manual stop and start, so restarted system, and it worked first go. many thanks again! you saved me a good deal of ](*,) time.[/QUOTE]

Thank you both!

---

### Post by grahams on 2006-11-09
I also have problems getting vncviewer to work on Edgy. 

I get "ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)" errors. 

I tried the solution of swapping fonts <-> X11 in /etc/xinitd.d/Xvnc and it allowed me to start vncviewer, however I found out later that it appears to screw up my networking after a reboot (I could not ping even my local router). Editing /etc/xinitd.d/Xvnc back to the edgy default and rebooting cures the networking, but of course stops vncviewer.

Has anyone got a fully working solutions? i.e. tried rebooting with this change and still have networking.

---

### Post by jehosephat on 2006-11-09
Am I missing something obvious here?  I'm running a fresh install of 6.06.1 on amd64 (Pentium D Smithfield, Dell 9150) ... as far as I can tell this is the latest and greatest on the VNC over SSH issue, and Tichondrius has addressed the known bug for vnc, tightvnc, and vnc4 on amd64 systems (can't find 'fixed' font, graphical applications crash while opening over VNC connection).  However, I can't seem to find resolutions here to the following two problems:

(1) Out of the box, under 6.06.1, the first step in the HOWTO is inaccurate: ther is no XDMCP option under the Security tab under Login Window Preferences.  While I believe I've verified that it's enabled (by looking in gdm.conf, I believe), this makes me nervous that something's not right.

(2) MOST IMPORTANT: when installing the "fixed" vnc4server and xvnc4viewer (fixed for amd64 systems) there's a missing dependency: xerver-common.  While someone posted and said he had success just forcing the install (dpkg -i --force-all or --force-depends), I still have the amd64 bug behavior, so I suspect this is a problem as well.  From what I've googled, it seems that xserver-common has become xorg-common, but that doesn't tell me what to do about that dependency.

Thanks for all the great help so far ...
Can anyone advise on these issues?

---

### Post by jehosephat on 2006-11-09
... I should have said - after forcing the install of the "fixed" .deb packages, I still have the amd64 bug ...

---

### Post by dmizer on 2006-11-09
> **jehosephat said:**
> Am I missing something obvious here?
like ... you're working with a howto that was written for breezy?

> (1) Out of the box, under 6.06.1, the first step in the HOWTO is inaccurate: ther is no XDMCP option under the Security tab under Login Window Preferences.
see above.  in breezy, this was indeed an option.

> (2) MOST IMPORTANT: when installing the "fixed" vnc4server and xvnc4viewer (fixed for amd64 systems) there's a missing dependency: xerver-common.  While someone posted and said he had success just forcing the install (dpkg -i --force-all or --force-depends), I still have the amd64 bug behavior, so I suspect this is a problem as well.  From what I've googled, it seems that xserver-common has become xorg-common, but that doesn't tell me what to do about that dependency.
welcome to the world of the 64bit kernel :p .  again, your issue here is that you're working with dated material.  when i used this howto back in breezy, it worked fantastic.  after my update to dapper, it stopped working, and i haven't been able to make it work since.  but i have since become comfortable using the terminal so i haven't tried to make it work again.

anyway ... point is, don't complain about the howto because it worked well when it was written.  you'll need to take the howto and adapt it to your situation now.  i'm not trying to be antagonistic, i'm just hoping that, by realizing this, you'll be able to find your solution more easily.

---

### Post by jehosephat on 2006-11-09
I figured it was written for pre-dapper ... (but, er ... where is that noted in the HOWTO?  again, I'm probably missing something obvious).

Well, at one point I tried patching the vncserver source with a patch from a bugzilla ... it didn't work, but since that was the first time I'd ever built software from source I may well have made a boo-boo!  I'll definitely post again if I can sort it out ... that is, if I don't get lazy with the partial solution of using x11vnc.

Thanks.

---

### Post by dmizer on 2006-11-10
> **jehosephat said:**
> I figured it was written for pre-dapper ... (but, er ... where is that noted in the HOWTO?  again, I'm probably missing something obvious).
the date of the post and most recent edit date are pre dapper ;)

i do highly suggest wading through the entire thread though ... maybe working your way backwards.  someone else may have found and fixed your problem already.

---

### Post by Yako on 2006-11-10
> **MBaran said:**
> I just wanted to post and update to this thread for anyone experiencing problems with Edgy (and maybe Beryl? not sure if thats what hosed me) setting this up.


In the /etc/xinetd.d/Xvnc file

change -fp /usr/share/X11/fonts/misc

TO

-fp /usr/share/fonts/X11/misc

This was my findings after ~2 hours of working away between x11vnc and vnc4server.

Thx.!

I had the same experience. I couldnt figure out why xinetd kept restarting and crashing Xvnc.
Thanks for the help!

---

### Post by grahams on 2006-11-10
> **grahams said:**
> I also have problems getting vncviewer to work on Edgy. 

I get "ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)" errors. 

I tried the solution of swapping fonts <-> X11 in /etc/xinitd.d/Xvnc and it allowed me to start vncviewer, however I found out later that it appears to screw up my networking after a reboot (I could not ping even my local router). Editing /etc/xinitd.d/Xvnc back to the edgy default and rebooting cures the networking, but of course stops vncviewer.

Has anyone got a fully working solutions? i.e. tried rebooting with this change and still have networking.

I set up vnc on a separate Edgy system and the Xvnc works fine and doesn't effect networking. So the problem I report above are local to my setup. 

If anyone has clues as to where I should look to fix this, I'd be very grateful

---

### Post by jay73 on 2006-11-16
My vnc ubuntu desktop session log's out and "kills" all running programs when i disconnect my vcn client (session)... Why does it do that? ](*,) ](*,) :evil: :-k

---

### Post by breuerp on 2006-12-01
> **grahams said:**
> I also have problems getting vncviewer to work on Edgy. 

I get "ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)" errors. 

I tried the solution of swapping fonts <-> X11 in /etc/xinitd.d/Xvnc and it allowed me to start vncviewer, however I found out later that it appears to screw up my networking after a reboot (I could not ping even my local router). Editing /etc/xinitd.d/Xvnc back to the edgy default and rebooting cures the networking, but of course stops vncviewer.

Has anyone got a fully working solutions? i.e. tried rebooting with this change and still have networking.

Can someone explain to me what broke?  The solution "works" but I'm not following how someone got from the error message to the solution.

](*,)

---

### Post by johnnymac on 2006-12-07
The answer may be here and I'm not seeing it but...


I do this tutorial and it's all working except I'm not getting a GDM, I'm getting this screen - almost like the login manager won't run.  Is this some sort of font or RGB setting issue? [See Screenshot]

Any help is appreciated....

---

### Post by hxx4 on 2006-12-10
I originally had the problem ```
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)
``` when I typed ```
xvncviewer localhost:1
``` and then I tried to manually create the server with ```
 sudo /usr/bin/Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc  -nevershared -rfbauth /root/.vncpasswd
``` but got an error ```
Fatal server error:
could not open default font 'fixed'
```I then found [this]("http://www.fifi.org/doc/vnc-common/faq.html") FAQ and looked at the question for the error "Could not open default font 'fixed'. ". I typed ```
xset q
```and copied the font path to the file /etc/xinetd.d/Xvnc. Then I restarted my computer and typed```
xvncviewer localhost:1
```again and it worked!

---

### Post by pkbarber on 2006-12-11
Ive got that same "grey" screen problem.  Im sure its something ridiculously simple somewhere but currently its beyond me.

---

### Post by pkbarber on 2006-12-11
Ok that grey screen thing is REAL easy fix... I was just careless!  You need to go System>Administration>Login Window>Remote and select Same as Local.  That works for me!

---

### Post by eku on 2006-12-28
Ok, I don't know what I'm doing wrong, but I just can't get it working. All I get is X and grey/black checkerboard.

I don't have any monitor or keyboard or nothing connected to the box right now.

I belive I've tried everything in this topic. It's just not fair. :(

---

### Post by Footer on 2006-12-28
[http://www.realvnc.com/faq.html#grey](http://www.realvnc.com/faq.html#grey)

Does that solve your problem?

:)

---

### Post by eku on 2006-12-28
> **Footer said:**
> [http://www.realvnc.com/faq.html#grey](http://www.realvnc.com/faq.html#grey)

Does that solve your problem?

:)

> You should run the vncserver script to start a VNC server, rather than the Xvnc program directly.

How do I do that?

---

### Post by Footer on 2006-12-28
> **eku said:**
> How do I do that?

From a term window:

```
vncserver
```

or if you want root to start the process:

```
sudo vncserver
```

---

### Post by eku on 2006-12-28
Footer, thanks, it helped, a bit, I think. But I still don't get any desktop with icons or stuff. Only a term running.

What do I need to put in to the xstartup file? tdw? gdw? Something else?

Why Allah hates me? :(

---

### Post by Footer on 2006-12-28
Here's a pretty good tutorial:

[http://www.skullbox.net/vncserver.php](http://www.skullbox.net/vncserver.php)

Near the end you'll see what needs to be in the xstartup file, basically:

```
startx &
```

or

```
startkde &
``` (for KDE desktop)

You may need to provide the specific path if startx or startkde aren't in your path.

Good luck!

:)

---

### Post by eku on 2006-12-28
Okay, seems like the problem is in X.org config. Tells me that there's no screens found. What to do next?

---

### Post by Footer on 2006-12-28
Could you post your exact error message?  Are you sure it's not "no fonts found"?

What version of U(K)ubuntu are you running?  I had problems with VNC when I upgraded to Edgy from Dapper.  See my posts #171 & #173 in this thread for how I solved that problem.

In either case, please post your exact error message so we can continue troubleshooting.

Thanks!

---

### Post by eku on 2006-12-28
> **Footer said:**
> Could you post your exact error message?  Are you sure it's not "no fonts found"?

What version of U(K)ubuntu are you running?  I had problems with VNC when I upgraded to Edgy from Dapper.  See my posts #171 & #173 in this thread for how I solved that problem.

In either case, please post your exact error message so we can continue troubleshooting.

Thanks!

Seems like I'm running 6.06. Should I upgrade and then try again?
This is what ~/.vnc/laeski:2.log contains:
```
Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Thu Dec 28 22:04:47 2006
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
Option --login is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new --wind$
xauth:  creating new authority file /home/lauri/.serverauth.14946


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux laeski 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 28 22:04:51 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found

Thu Dec 28 22:04:54 2006
 Connections: accepted: 87.94.xxx.xxx::51119
 SConnection: Client needs protocol version 3.4
 SConnection: Client uses unofficial protocol version 3.4
 SConnection: Assuming compatibility with version 3.3
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
Couldnt get a file descriptor referring to the console

Thu Dec 28 22:05:00 2006
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 16 (16bpp) little-endian rgb565

Thu Dec 28 22:22:56 2006
 Connections: closed: 87.94.xxx.xxx::51119 (Clean disconnection)
 SMsgWriter:  framebuffer updates 20
 SMsgWriter:    ZRLE rects 17, bytes 3441
 SMsgWriter:    raw bytes equivalent 1601676, compression ratio 465.468178
```

For some reason :1 shows the checkerboard (or whatever) screen, and to get just grey background with Gnome terminal to :2, I have to run 'vnc4server'. (Seems like I confused these two before.)

---

### Post by Footer on 2006-12-29
I'm sort of confused.  What system are you running vncserver on (or vnc4server as you indicated?) and what system are you running vncviewer on?  Are they both Ubuntu boxes?  And no, you shouldn't need to upgrade to Edgy, Dapper should work fine.

Maybe you should remove the programs from both boxes (vncserver/vncviewer) and start over following that tutorial I sent a link for earlier.  Then fire up vncserver on the box you want you want to vnc to, go back to the box you want to vnc from and fire up vncviewer:

```
vncviewer 192.168.1.xxx:1
```

and see if it works.  I know you're close but perhaps this might clear out some of the bugs?  I was hoping to see a log of your vncviewer session but it looks like there might be a problem on the vncserver end as well.

Tricky stuff.  Keep trying and remember, Google is your friend!

:)

---

### Post by eku on 2006-12-30
Horay for me!

I just needed to run 'x-session-manager' to get it up and running. But would someone tell me why it worked that way?

---

### Post by Footer on 2006-12-30
WHOOHOO!!!  Congrats for figuring it out!  I've never had to use that as installing the server and viewer have always worked for me ... Aside from the font problem when I went to Edgy.

Well, good job!  I'm glad you finally figured it out.  Hopefully others will benefit from your success if they run in to the same problems!

:)

---

### Post by Rob_H on 2006-12-30
Tichondrius, thanks for a great HOWTO!

**KDE users:** I've taken the liberty of adapting this to Kubuntu Edgy. The process is a bit different for KDM. If anyone's interested, I've [posted the revised HOWTO]("http://kubuntuforums.net/forums/index.php?topic=12376.0") in the Kubuntu forums.

---

### Post by bhamail on 2006-12-31
Maybe a note could be added to the first HowTo page:

On edgy the font path is wrong in "server_args =..." in /etc/xinetd.d/Xvnc:

howto shows:

```
-fp /usr/share/X11/fonts/misc
```

but I had to change it (as per another post in this thread) to: 

```
-fp /usr/share/fonts/X11/misc
```

The symptom was vnc errors like:
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)
when trying to connect.

Also, when manually executing the vncserver command with the bad font path, I saw errors like: "Fatal Error" ... couldn't find font 'fixed'

---

### Post by billycub on 2007-01-05
I finally got this working on Edgy AMD64 -- yay!  Here are the steps that worked for me, slightly different than the original howto above:

**1. Install xinetd, vnc4server, xvncviewer.**  The regular vncserver package does not work which is why you need to install vnc4 (from universe).

**2. Create the file /etc/xinetd.d/Xvnc** and paste the following in:

[INDENT]Note that the snippet below **has a few differences from the original howto:** (1) the fontpath entry is specific to Edgy; (2) the server directive needs to be /usr/bin/Xvnc4, not Xvnc; (3) I used no security but you can use the password file from the original howto if you like. For my use case I didn't need it. [/INDENT]

```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc4
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared SecurityTypes=None
        port = 5901
}

```

3. **System - Admin - Login Window:** On "Remote" tab, change Style: to something other than 'disabled'.

4. **Reboot.**

Now I can VNC in using hostname:1 and it works like a charm.  Good luck!

-Billy

---

### Post by Marzocchi on 2007-01-08
I've done everything in the guide, but for some reason I get the following when I try to connect

ReadFromRFBSServer: rdr::EndOfStream

Any ideas what this is about?

---

### Post by perlappuntu on 2007-01-08
I had the same problem yesterday then I reverted the vncserver package back to the previous version and the problem went away.  In may case the problem happened after updating the package to the latest version, that's why I tried to go back...

---

### Post by biggunks on 2007-01-08
Has anyone seen this problem before?

I've had X and VNC working before.  I don't know what's happening.  I'm sure it's something simple.

---

### Post by Marzocchi on 2007-01-09
Now I get 

ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)

instead. Even though I have changed the from /X11/fonts/ to fonts/X11/

---

### Post by coulier on 2007-01-10
Hi!

I had the "ReadFromRFBSServer: rdr::EndOfStream" error message. Removing "-query localhost" from the server_args line in /etc/xinetd.d/Xvnc file solved this problem.

Now, I can connect to the vnv4server, but I get that grey screen. 

I don't know how to get the login screen back! 
I have only ssh access to this machine now, so I cannot go to System>Administration>Login Window>Remote and select Same as Local as suggested by pkbarber in post #188
Is there a way to modify this setting from a config file?

Everything was working fine on my edgy box, untill I made some update from uate_manager. I did'nt write down which packages were being updated, though.

Any help will be appreciated....

François

---

### Post by gregwill on 2007-01-10
I have a reasonably fresh install of 6.10 on AMD64 and the Xvnc4 setup recommended by billycub isn't working for me either - if the latest vnc4server package is broken, is there any way for me to get the previous one?

It's clearly listening on the right port:

tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN     4814/xinetd

But if I try to connect using a VNC client locally or remotely, they all seem to connect (and initially start drawing a gray screen) and then quickly get dropped, e.g.:

---------------
$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Jan  6 2007 09:47:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed Jan 10 18:30:12 2007
 CConn:       connected to host localhost port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding

Wed Jan 10 18:30:16 2007
 main:        write: Broken pipe (32)
------------

Does Xvnc4 have any logs anywhere?

---

### Post by perlappuntu on 2007-01-10
To confirm the what reported in the previous message (from coulier) I restate what I reported before: my problems with vnc and resumable sessions (vncserver instanciated by xinetd) started Saturday when I updated vnc4server to the lastest version, once I reversed it back to the previous release the problem went away.  Overall I still have problems using vnc though, few days ago I wrote a [message]("http://www.ubuntuforums.org/showthread.php?t=333738&highlight=vnc") in the forum to explain the issues but I didn't get any feedback so far. :-(   Briefly when I start a vnc session from ssh I get a gray screen on the vncviewer window, in my case the cause seems to be the fact that gnome fails to start.  I do not know how to fix it, if someone has any suggestion...

---

### Post by perlappuntu on 2007-01-10
You can select the version of the package you want to use.  Unfortunately I do not have the desktop in front of me to give you all the precise steps to do it but you can use the graphical package manager to uninstall the version of vnc4server you use then install it again, there is an option to select the version, pick the previous one.  If I remember properly you can access the available version list clicking on the object (vnc4server) properties.  I can give you the exact procedure later today if you will still need it.

> **gregwill said:**
> I have a reasonably fresh install of 6.10 on AMD64 and the Xvnc4 setup recommended by billycub isn't working for me either - if the latest vnc4server package is broken, is there any way for me to get the previous one?

It's clearly listening on the right port:

tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN     4814/xinetd

But if I try to connect using a VNC client locally or remotely, they all seem to connect (and initially start drawing a gray screen) and then quickly get dropped, e.g.:

---------------
$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Jan  6 2007 09:47:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed Jan 10 18:30:12 2007
 CConn:       connected to host localhost port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding

Wed Jan 10 18:30:16 2007
 main:        write: Broken pipe (32)
------------

Does Xvnc4 have any logs anywhere?

---

### Post by gregwill on 2007-01-10
Yes, you are right - downgrading vnc4server package from 6.10.1 to the previous version fixes it for me - thanks!

---

### Post by chrigri on 2007-01-10
Yes, I can confirm that downgrading fixes the problem.

--
Christer

---

### Post by coulier on 2007-01-11
hI!

I don't have an easy physical access to the machine. Is there away to downgrade using an ssh connexion?

François

---

### Post by bhamail on 2007-01-11
coulier,

I was able to "downgrade" via an ssh connection and apt-get using:

```
$ sudo apt-get install vnc4server/edgy
```

This will get the vnc4server from the "edgy" repo (instead of the latest from the "edgy-security").

The stuff below is just for info: Here's what I found in the man pages for apt-get:

 A specific version of a package can be selected for installation by following the package name with  an  equals and  the version of the package to select. This will cause that version to be located and selected for install. Alternatively a specific distribution can be selected by following the package name with a slash and  the  version of the distribution or the Archive name (stable, testing, unstable).

I found the exact version of what I have installed by trying to install from "edgy-security":

```
$sudo apt-get install vnc4server/edgy-security
Reading package lists... Done
Building dependency tree
Reading state information... Done
Selected version 4.1.1+xorg1.0.2-0ubuntu1.6.10.1 (Ubuntu:6.10/edgy-security) for  vnc4server
vnc4server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I then did the "downgrade" from "edgy":

```
$ sudo apt-get install vnc4server/edgy
Reading package lists... Done
Building dependency tree
Reading state information... Done
Selected version 4.1.1+xorg1.0.2-0ubuntu1 (Ubuntu:6.10/edgy) for vnc4server
Suggested packages:
  vnc-java
The following packages will be DOWNGRADED:
  vnc4server
0 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 1011kB of archives.
After unpacking 81.9kB disk space will be freed.
Do you want to continue [Y/n]? y
```

Hope this helps.
Dan

PS: I'm just a little worried that the security patch broke things, and wondering if anyone knows how to make it all work with the latest "security" patched version???

---

### Post by coulier on 2007-01-12
Thanks so much for the tip!
I will test it ASAP (right now, and for unknown reason, I can't get through to fr.archive.ubuntu.com: 80 (194.2.0.36) .

François

---

### Post by SVWander on 2007-01-12
At one time I had vnc server on two computers both with Ubuntu 6.10. I had to reinstall Ubuntu on this machine and have set up the wireless connection without too much trouble. But now when I run: vncviewer localhost:0

a dialog comes up asking:

Question
Another user is trying to view your desktop
A user on computer '127.x.x.x' is trying to remotely view or control your desktop.
Do you want to allow them to do so?

When I click allow the screen switches to a view of my other desktop . . . then to hundreds of views cascading down. Actually the other screen has an open desktop . . . with nothing on it. 

The terminal reports these settings:

tim@tim-desktop:~$ vncviewer localhost:0
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.7 (viewer 3.3)
No authentication needed
Desktop name "LibVNCServer"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Using shared memory PutImage
ShmCleanup called

Before when I used the command I would be prompted for my password (I did use the howto this time to set up my password whereas before I didn't but it still worked). Does anyone know how I messed this up?

Tm

---

### Post by breuerp on 2007-01-13
I seem to keep fighting this thing.  I have VNC running by forcing install the amd64 packages:

```
sudo dpkg -i --force-all xvnc4server_4.0-7.3_amd64.deb
sudo dpkg -i --force-all vnc4server_4.0-7.3_amd64.deb
```

The problems are:
a)  This is not the latest version (by a long shot) so I'm concerned about vulnerabilities
b) *MORE* importantly, apt-get/synaptic report the application as broken (since it's not the latest version) and won't let me update/upgrade any other packages until I "fix" it.  Of course "fixing" it means that I upgrade to the latest version which appears to not have the AMD64 bug corrected on it.  

Does anyone know where I can get a newer version of a vnc server package that will run on AMD64?  FreeNX is not an option because resumable sessions are an absolute requirement.

Thanks.

---

### Post by Hubris2 on 2007-01-16
Thanks for both the original guide and the subsequent posts.  I'm still having a couple issues and I was hoping someone might catch something I'm missing.

I remote my Edgy 6.10 box via SSH; using Vino I can connect to session 0 with no problems, other than it being slow and a much larger screen than my remote terminal.

I've followed the original guide and installed vnc4server and configured it for session 1.  I too had to change the font path as has been mentioned by a couple folks.  I've set the VNC password, and confirmed that port 5901 is being listened.

From a local terminal, if I execute vncviewer localhost:1 I'm prompted for a password, and after entering it I get [PHP]ReadFromRFBServer: rdr::EndOfStream
[/PHP]

When I try connect from remote (I know...local should be working first....) with a tunnel connected to port 5901, VNC reports an immediate disconnect - before even asking for the password.

When I check the syslog, I find [PHP] xinetd[6043]: warning: can't get client address: Transport endpoint is not connected
[/PHP]  Does anyone have any ideas why I can connect to vino on session 0, but can't connect to the separate vnc server on session 1?

Thanks!

---

### Post by cdt24 on 2007-01-16
I successfully got a single vnc server up and running just like the original HOWTO described.  Howver, I would like to not be limited to just one server running like this.  Ideally, what I'd like to do is enable anybody to login remotely via ssh, fire up a vncserver session with their own geometry, color depth, etc. and let them then connect to that server through the ssh tunnel.  Seems like I need something more dynamic, but I have no idea how to go about doing that.  Help!

---

### Post by Hubris2 on 2007-01-16
Related to my error message (VNC server failing to connect) I've located the following notice of a bug.  This states that the Dapper install is fine, but the Edgy install has a problem.

Anyone?

[https://launchpad.net/ubuntu/+source/vnc4/+bug/78282](https://launchpad.net/ubuntu/+source/vnc4/+bug/78282)

I found a solution to my problem....downgrade to the older version of vnc4server.  One version back I am able to connect with no problems and no crashes.

---

### Post by grahams on 2007-01-17
Hi 

I've been using this setup for months on edgy, but recently it just stopped working and I need help.

This is the output I get from vncviewer, which has been working for months and now stopped on 2 systems and I can't think of any common thread. I think the error is coming from vncserver.

$ vncviewer :1
VNC viewer version 3.3.7 - built Jul 4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password:
ReadFromRFBServer: rdr::EndOfStream
Edit/Delete Message
Looks like Xvnc stopped running.

ps -ef |grep vnc
grahams1 7400 5040 0 09:18 pts/0 00:00:00 grep vnc

If I start Xvnc manually I get "error opening security policy file /etc/X11/xserver/SecurityPolicy"

---

### Post by coulier on 2007-01-17
Hi,

I moved a little bit up.
Now, ```
 sudo Xvnc4 :2 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared -PasswordFile=/root/.vncpasswd 
``` works (although the server complains: ```
error opening security policy file /etc/X11/xserver/SecurityPolicy
```, and hang when I disconnect from the display.

However, I still get that grey screen with X-like pointer when connecting to :1
Xvnc is as follows:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc  -DisconnectClients=0 -NeverShared -PasswordFile=/root/.vncpasswd
        port = 5901
}
```

Any help?

François

---

### Post by perlappuntu on 2007-01-17
I'm still struggling with the vncserver but I was able to fix the problem related to /etc/X11/xserver/SecurityPolicy creating a software link to the new location.  Once I fixed it my problem moved to start gnome within the VNC session, I wrote about it in the forum ([message #1]("http://www.ubuntuforums.org/showthread.php?t=333738&highlight=vnc")) but it looks nobody knows how to fix it... 

> **coulier said:**
> ...
error opening security policy file /etc/X11/xserver/SecurityPolicy
...

---

### Post by grahams on 2007-01-17
There is an issue with the latest vnc4server see bug [https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282)

Downgrading vnc4server cures the issue until the bug is fixed.

---

### Post by neoflight on 2007-01-18
all i get is
> vncviewer xxx.xxx.xxx.xxx:1
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server


i can start the xwindow by vncviewer localhost:0 no problem here....

i am using ubuntu with uni wireless & vpn to connect to a ubuntu pc in the uni lan..

any ideas? is the vpn causing the problem...? 
i dont know a thing about port forwarding and all....

what is a port](*,)  and how to tell it to use one? :-k 

thanks

---

### Post by Hubris2 on 2007-01-19
If you can connect to port 0 on the remote box, then there isn't an issue with any of the network connectivity between you.  On Ubuntu, session 0 is managed by vino (the 'remote desktop') while sessions 1 and above are typically an entirely separate VNC server, with different settings and config.

Is there a firewall on this box?  Session 0 connects on port 5900, but session 1 is on 5901.

---

### Post by borland-c on 2007-01-19
> **gregwill said:**
> Yes, you are right - downgrading vnc4server package from 6.10.1 to the previous version fixes it for me - thanks!please explain howto downgrade vnc4server package, yes I can remove vnc4server but how to install older verision? where I can find it?

---

### Post by Hubris2 on 2007-01-19
Go to system, administration, Synaptic package manager.

Scroll down to the package for the server you installed, click it.  Choose 'package' from the drop-down menu, and you have an option of 'force package'.  That will give a pull-down with (in my case 2) choices....

After you've selected the older version, you have to apply - and it will make the change.

---

### Post by Crass Spektakel on 2007-01-20
Two things about setting up your VNC like described here:

1. You have to run your Display Manager (most likely gdm) or otherwise you will end up with the default X11 checker board background and nothing else. Run your Display Manager even if you aren't interested in loging into X11 at the system locally. There are ways to disable the local VGA-Display-Output and safe some memory but this is not the time and place to go into details.

2. I had to "chmod 755 /etc/X11/xinit/xinitrc" or otherwise my Xvnc only came up when called from commandline but not from inetd/xinetd. But after chmoding vnc4 also runs with the most recent vnc4server-packet.

---

### Post by josesanders on 2007-01-23
Initially, it just didn't work, so I did this to fix the font problem:

$ cd /usr/share/X11
$ sudo ln -s /usr/share/fonts/X11 fonts

That seemed to solve one problem, but then I just got the checkerboard background.  I downgraded to the older version, but no change.  Has anyone solved this problem yet?

I found #199 in this thread, and I don't know what it means but I tried anyway:

$ x-session-manager

and I get the following:

(x-session-manager:4931): Gtk-WARNING **: cannot open display:

I should say that right now I'm trying to get in remotely using an ssh tunnel, but it seems to me that if I can log in and it accepts my password, it's not a networking problem.

Thanks

---

### Post by josesanders on 2007-01-23
I fixed my own problem.  Logged into the server locally and changed the settings:

Login Screen->Remote

Changed to same as local.  I know this was here before, and I really thought I already did it, but sorry to post for something so simple.

---

### Post by childs999 on 2007-01-31
Feb  1 00:41:40 FS xinetd[5357]: warning: can't get client address: Transport endpoint is not connected

Can someone help me with this error (this is fromv var/log/syslog).
My VNCviewer connections from my windows machine, but then says:
read: Connection reset by peer (10054).

Any suggestions??

---

### Post by Hubris2 on 2007-01-31
That sounds like the same message I was getting, that was addressed by downgrading the version of VNC4Server.  Have you searched this thread?  That is a fairly common error..and it doesn't seem that any single solution always works.

---

### Post by childs999 on 2007-02-01
> **Hubris2 said:**
> That sounds like the same message I was getting, that was addressed by downgrading the version of VNC4Server.  Have you searched this thread?  That is a fairly common error..and it doesn't seem that any single solution always works.

I have actually downgraded and still having this problem.

---

### Post by Hubris2 on 2007-02-05
My VNC server is generally working as I want...however I occasionally have the putty connection crash while I'm connected to :1 over VNC...which screws up the session.  When I try reconnect to :1 I'll get an error about the session being busy and asking if I want to reconnect.

I normally switch back to :0 and kill the session manually but it hasn't worked yet.  I just had it happen...I issued 'vnc4server -kill :1'.  It was successful, but told me to manually kill the Xvnc process.  I did, and I was then able to reconnect to :1 and log in.  The screen would not update however....I had a solid color and not my desktop.  At this point I reconnected to :0 again but the desktop was 'hung' - I could move the mouse around but couldn't click on anything.  Eventually I used the shell from SSH to restart the machine.

How can I properly kill a 'borked' VNC session so it will let me sign back on and start working anew?  The 2 times this has happened (over probably 30 days), I've had to resort to a full restart to fix things.

Thanks,

---

### Post by zymorph on 2007-02-07
> **Hubris2 said:**
> How can I properly kill a 'borked' VNC session so it will let me sign back on and start working anew?  The 2 times this has happened (over probably 30 days), I've had to resort to a full restart to fix things.

Thanks,

Are you running VNC using xinetd for resumable sessions or running it by itself? If you're running it from xinetd, restart that service ("/etc/init.d/xinetd restart") and then issue the command "sudo killall Xvnc" because simply killing off the Xvnc process itself apart from xinetd doesn't work because xinetd kicks up another instance of Xvnc (at least that's been my experience). But if you're running VNC on its own, issue the command "sudo killall Xvnc" and try to start up that process again. Not sure if that helps, but I tried :)

---

### Post by Hubris2 on 2007-02-07
I'm running via xinetd as per the guide from this post.

I'm just considering the process here....restarting xinetd will probably halt and restart my SSH via which I'll be attempting the repair.  As long as it restarts I'll be able to reconnect and continue.

I don't understand how restarting xinetd.....(so it's running when I kill Xvnc) will work.  If I stopped xinetd, killed Xvnc and then restarted xinetd- that would make sense to me.....but if xinetd has been restarted prior to killing Xvnc, would it not create another instance of Xvnc as you stated?

> **zymorph said:**
> Are you running VNC using xinetd for resumable sessions or running it by itself? If you're running it from xinetd, restart that service ("/etc/init.d/xinetd restart") and then issue the command "sudo killall Xvnc" because simply killing off the Xvnc process itself apart from xinetd doesn't work because xinetd kicks up another instance of Xvnc (at least that's been my experience). But if you're running VNC on its own, issue the command "sudo killall Xvnc" and try to start up that process again. Not sure if that helps, but I tried :)

---

### Post by zymorph on 2007-02-08
Yeah you're right :) , I meant to say "stop" xinetd (not restart), kill your Xvnc sessions, then start xinetd again (which should kick up a Xvnc instance). Whenever I've connected via SSH and restart xinetd, it doesn't drop my SSH connection.

> **Hubris2 said:**
> I'm running via xinetd as per the guide from this post.

I'm just considering the process here....restarting xinetd will probably halt and restart my SSH via which I'll be attempting the repair.  As long as it restarts I'll be able to reconnect and continue.

I don't understand how restarting xinetd.....(so it's running when I kill Xvnc) will work.  If I stopped xinetd, killed Xvnc and then restarted xinetd- that would make sense to me.....but if xinetd has been restarted prior to killing Xvnc, would it not create another instance of Xvnc as you stated?

---

### Post by walix on 2007-02-09
Hi all,

Does anyone have idea while I get this message when trying to connect to the VNC server? 

"ReadFromRFBServer: rdr::EndOfStream"

VNC used to work fine till one day when I installed some updates and I can't figure out why.

Thanx a lot

---

### Post by Hubris2 on 2007-02-09
Try reverting back to the previous version of the VNC4Server app.  I had that problem, and it fixed it for me - I still have a security update for VNC4Server waiting...that I won't install.

---

### Post by bozack on 2007-02-16
Has anyone gotten this working with IPv6?

I can't find any info on whether or not vnc4server supports IPv6 or not.

My attempt at getting it running through xinetd didn't work out, though everything's great on IPv4.

Log files aren't helping.

Thanks in advance!

---

### Post by scarpent on 2007-02-16
This is quite a thread.  Thanks to Tichondrius for the writeup and all of the other posters who helped with figuring stuff out.

I think there are some other updated howto's for Edgy out there, but I pretty much used this one to put it all together.  I wrote up my own experience in getting this working, which I'm posting here in the hope that it might help others:

[HOWTO: Remote Desktop with VNC in Ubuntu Edgy]("http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/")

---

### Post by SBFC on 2007-02-20
Hello everybody, I'm having an interesting problem. I followed the guide step 
by step and actually had everything working. I had connected to my Linbox at home via VNC and was greeted with a gdm login screen.

I logged in and Fluxbox fired up. Could disconnect and it would stay running. However, last time I reconnected I exited fluxbox, thinking it would go back to the login screen. Sadly, that isn't what happened. I was disconnected, and after that was never able to reconnect. 

Been messing around with it for quite a while and in /var/log/syslog I was getting the following message:

```
warning: can't get client address: Transport endpoint is not connected
```

No idea why it started complaining about that. Through some experimentation I discovered that if I remove the '-once' tag from the server_args line in /etc/xinetd.d/Xvnc file I can connect, but it doesn't load GDM. I just get an empty X server.

I don't know why exiting Fluxbox foobarred everything. Afterwards I even restarted my computer and it still wouldn't work.

I'd also like to point out that I can use vnc4server normally with no problems. I would rather use the process this howto describes though, as it allows people to log into their own sessions rather than using mine (running 'vnc4server' cmd).

Any suggestions would be greatly appreciated.

---

### Post by prescor on 2007-02-22
> **kacheng said:**
> I also get as mssm does:

# grep xinetd /var/log/syslog
Jan 28 08:29:56 localhost xinetd[13968]: warning: can't get client address: Transport endpoint is not connected
:
:
:
Jan 28 08:29:57 localhost xinetd[14180]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14181]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14182]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14183]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14184]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14185]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14186]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[14187]: warning: can't get client address: Transport endpoint is not connected
Jan 28 08:29:57 localhost xinetd[10673]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Jan 28 08:30:07 localhost xinetd[10673]: Activating service Xvnc


What does this mean?


Indeed!  What does this mean?  I've been struggling for two days to get this to work on Edgy.  I'm VERY VERY CLOSE, I can SMELL IT!  But syslog has all these "can't get client address" messages (above).

???

---

### Post by Pollywoggy on 2007-02-22
I am using kdm.  I would need to use gdm to get this to work?
I don't know if I can install gdm because when I installed it on another Edgy system recently, a bug kept me from logging in and I had to reinstall kdm.

---

### Post by scarpent on 2007-02-23
I was getting that "endpoint is not connected" message also.  I'm not sure what the exact cause of it was since it was one problem among many while getting this to work.

Might it be that xdmcp isn't enabled?

A few comments up I linked to a post where I recapped my own experience getting this running.  A lot of it is advice I got in this thread, but I pieced together comments from the whole past year and tried to make it a coherent howto for Edgy.  One of the biggest things missing in the original howto that seems necessary in Edgy is to edit gdm.conf.

---

### Post by Pollywoggy on 2007-02-23
> **scarpent said:**
> I was getting that "endpoint is not connected" message also.  I'm not sure what the exact cause of it was since it was one problem among many while getting this to work.

Might it be that xdmcp isn't enabled?

A few comments up I linked to a post where I recapped my own experience getting this running.  A lot of it is advice I got in this thread, but I pieced together comments from the whole past year and tried to make it a coherent howto for Edgy.  One of the biggest things missing in the original howto that seems necessary in Edgy is to edit gdm.conf.

I also tried to connect to a machine running Debian Sarge from two machines running kubuntu Edgy and the connection was denied but I am able to telnet to the Sarge machine on port 5901 from the same kubuntu hosts.  This means the problem is probably on the Ubuntu machines.  I have used VNC with the same machines when all were running Debian and Freespire and the configuration on the Sarge machine is unchanged from then.

---

### Post by walix on 2007-02-24
> **Hubris2 said:**
> Try reverting back to the previous version of the VNC4Server app.  I had that problem, and it fixed it for me - I still have a security update for VNC4Server waiting...that I won't install.

Thanks Hubris2, your suggestion helped me. VNC works again.
Sorry for the delay, I was not able to try it before.

---

### Post by Tadhg on 2007-02-24
im having a little trouble with this.

I'm trying to tunnel the VNC connection through another machine, so I set up a SSH session:

ssh -L 5901:192.168.0.5:5901 [email]username@host.co[/email] -p 993

but when i start vncviewer on 127.0.0.1:5901 i get the following

```

VNC Viewer Free Edition 4.1.1 for X - built Jan  6 2007 09:49:08
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Sat Feb 24 15:18:13 2007
 CConn:       connected to host 127.0.0.1 port 5901
 main:        End of stream

```

and this in the syslog:

```

.
.
.

Feb 24 15:42:36 timmypc xinetd[7528]: warning: can't get client address: Transport endpoint is not connected
Feb 24 15:42:36 timmypc xinetd[7528]: warning: can't get client address: Transport endpoint is not connected
Feb 24 15:42:36 timmypc xinetd[7528]: warning: can't get client address: Transport endpoint is not connected
Feb 24 15:42:36 timmypc xinetd[7421]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.

```

I've downgraded the server and still no luck.Any ideas?

[EDIT], Ok, I've gotten somewhere. While i was unable to even get to the password screen before, I now have an X server booting up. [This post i]("http://ubuntuforums.org/showpost.php?p=1951958&postcount=202") fixed it for me, the 
-fp /usr/share/X11/fonts/misc needs to be changed to -fp /usr/share/fonts/X11/misc in your /etc/xinetd.d/Xvnc. Thanks bhamail!

---

### Post by Pollywoggy on 2007-02-24
> **Tadhg said:**
> 

[EDIT], Ok, I've gotten somewhere. While i was unable to even get to the password screen before, I now have an X server booting up. [This post i]("http://ubuntuforums.org/showpost.php?p=1951958&postcount=202") fixed it for me, the 
-fp /usr/share/X11/fonts/misc needs to be changed to -fp /usr/share/fonts/X11/misc in your /etc/xinetd.d/Xvnc. Thanks bhamail!

Thanks, this helped me.  I am now getting a screen.  There is nothing on it but this is progress.  I should have thought to check the path to the fonts when I first tried this and got errors, but I didn't.

---

### Post by Tadhg on 2007-02-24
yea, unfortunately im getting the grey screen of death and i havent a clue how to fix it

---

### Post by Pollywoggy on 2007-02-24
> **Tadhg said:**
> im having a little trouble with this.



```

VNC Viewer Free Edition 4.1.1 for X - built Jan  6 2007 09:49:08
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Sat Feb 24 15:18:13 2007
 CConn:       connected to host 127.0.0.1 port 5901
 main:        End of stream

```



This happened to me when I did not have a password set.
I then used the vncpasswd command to set one.

---

### Post by Pollywoggy on 2007-02-24
> **Tadhg said:**
> im having a little trouble with this.

I'm trying to tunnel the VNC connection through another machine, so I set up a SSH session:

ssh -L 5901:192.168.0.5:5901 [email]username@host.co[/email] -p 993



I just tried this and it works for me, but I am still getting the plain grey screen on the remote host.  Some other setup must be required to get this working but the ssh part works.

I am using kdm, not gdm, so perhaps that is the reason I am getting the plain screen with nothing on it once I connect.

---

### Post by SBFC on 2007-02-25
Aye, the grey screen of nothingness it is. Still haven't figured out what is causing it. 

I'm especially perturbed since everything actually worked until I chose to 'Exit' Fluxbox.

Arg...

---

### Post by grumpymole on 2007-02-26
If I remember, the grey-screen means that you have set up the connection, but the X server serving the session was not able to start an X session.  Possible reasons are usually: (1) XDMCP is not enabled, or (2) problem with the script that starts the X session.  Something set in it not allowing the X server to start.

Cheers

---

### Post by Pollywoggy on 2007-02-26
I finally got this working in kubuntu using the following:

[http://ubuntuforums.org/showthread.php?t=259448](http://ubuntuforums.org/showthread.php?t=259448)

There is a problem, though.  When I do:

xvncviewer remotehost :1

xvncviewer connects not to "remotehost" but to localhost.  It does this even if I use remotehost's IP address in place of "remotehost" in the xvncviewer command.

---

### Post by Pollywoggy on 2007-02-26
> **Pollywoggy said:**
> I finally got this working in kubuntu using the following:

[http://ubuntuforums.org/showthread.php?t=259448](http://ubuntuforums.org/showthread.php?t=259448)

There is a problem, though.  When I do:

xvncviewer remotehost :1

xvncviewer connects not to "remotehost" but to localhost.  It does this even if I use remotehost's IP address in place of "remotehost" in the xvncviewer command.

I got it working in kubuntu but it does not work in Debian Sarge and I believe it's because XFree86 is installed there, not xorg.  Also the fonts must be in a different place in Debian Sarge.

---

### Post by zupidupi on 2007-02-27
Hiya,

I'm fighting with the vnc as well. I have a a standard Ubuntu (Edgy) installation on a server, to which I want to set up a vnc-connection from a client running a live-cd bootup.

I've followed the step-by-step-guide at

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

rather closely.

I have no problem connecting when both are running Gnome. I issue the command "vncviewer 192.168.1.102:1" from a terminal on the client, enter the vnc-password, and I get a login-window which works A-OK.

The problem arises when I try to open a connection ***with the server in console mode***. I remove the gdm-link in the rc2.d-directory, start up the server again. When I try to connect again I get to enter the vnc-password, but then I get nothing but a grey screen.

It seems to me that I'm missing something. I read in another thread that it wouldn't be necessary to run a x-session on the server in order to get a GUI with vnc ([http://www.linuxquestions.org/questions/showthread.php?t=523864](http://www.linuxquestions.org/questions/showthread.php?t=523864), post #7) but I obviously need to do something else - fiddle with some settings, run some other daemon/program - you tell me!

Any help for solving this would be much appreciated!

Thx in advance,

Mike

---

### Post by Pollywoggy on 2007-02-27
> **zupidupi said:**
> Hiya,

I'm fighting with the vnc as well. I have a a standard Ubuntu (Edgy) installation on a server, to which I want to set up a vnc-connection from a client running a live-cd bootup.

I've followed the step-by-step-guide at

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

rather closely.

I have no problem connecting when both are running Gnome. I issue the command "vncviewer 192.168.1.102:1" from a terminal on the client, enter the vnc-password, and I get a login-window which works A-OK.

The problem arises when I try to open a connection ***with the server in console mode***. I remove the gdm-link in the rc2.d-directory, start up the server again. When I try to connect again I get to enter the vnc-password, but then I get nothing but a grey screen.

It seems to me that I'm missing something. I read in another thread that it wouldn't be necessary to run a x-session on the server in order to get a GUI with vnc ([http://www.linuxquestions.org/questions/showthread.php?t=523864](http://www.linuxquestions.org/questions/showthread.php?t=523864), post #7) but I obviously need to do something else - fiddle with some settings, run some other daemon/program - you tell me!

Any help for solving this would be much appreciated!

Thx in advance,

Mike

There is a line in /etc/xinetd.d/Xvnc which points to where the fonts are located.  I had to change this line, the default one was incorrect.  Another thing is that on one of my systems, I am running Debian and that fonts line is incorrect but I can't find the correct path, so I can't use this method, I have to ssh to that host and start the vncserver as a user. 

It's working on my machine that runs kubuntu Edgy.  These are the vnc packages I have installed in kubuntu:

ii  vnc4-common                            4.1.1+xorg1.0.2-0ubuntu1.6.10.1          Virtual network computing server software
ii  vnc4server                             4.1.1+xorg1.0.2-0ubuntu1.6.10.1          Virtual network computing server software
ii  xvncviewer                             3.3.7-12ubuntu1                          Virtual network computing client software

If you have xvnc4viewer installed, you should probably remove that.  xvncviewer is the one you want.

I was even able to use VNC from a laptop running wifi, I just ran a command similar to
ssh -L 5901:192.168.1.100:5900 pollywog@remotehost

followed by 

vncviewer localhost:5901

It's working on kubuntu but not Debian Sarge.  On Sarge I use tightvncserver and it works but it's not as good as the setup on kubuntu.  For one thing, I have to manually start the server in Sarge.

---

### Post by Underpants on 2007-03-02
> **Tichondrius said:**
> Ok, to resume a session you started on your physical display (display :0) all you really need is to turn on Ubuntu's remote desktop feature using the Remote Desktop Preferences dialog box accessible from System->Preferences->Remote Desktop menu item.  Just check the first two options there (allow other users to view your desktop and allow other users to control your desktop) and set the password in the bottom of the dialog box (check the REuqire password option), and you're done ! 
  The above uses the built in VNC capability that Ubuntu comes installed with, but the drawback is that it's a little slow, and you need to enable it for each user which wants to allow his desktop to be view or controlled remotely. Also this doesn't allow remote VNC clients to log in to GDM, only to view a GDM session that was started by someone actually using the physical display. So if currently no one is logged in, a remote user cannot connect to display :0 and start a new session.
  But don't worry - there is a better way which allows you to view the phyical display remotely and also log-in to a new session from GDM (using a remote VNC client) !  And it works faster (as fast as the regular VNC server), and works for all users. Here's how to do that :

1. Install x11vnc package

```
sudo apt-get install x11vnc
```

2. Add x11vnc service to xinetd:

```
sudo gedit /etc/xinetd.d/x11vnc
```

Enter this into the new file:

```

service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg
        disable         = no
}

```

3. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo killall x11vnc
sudo /etc/init.d/xinetd start
```

4. From a remote machine use your VNC client to connect to display :0

```
vncviewer  vnchost:0
```

Note that after loggging from GDM and also after logging out from the X-session back and going back to GDM, the VNC client gets disconnected for some reason. So you just need to re-connect and you will get back into the session you logged into. When logging out, the disconnect happens when gnome asks you to confirm your intention to log out, so it's best to turn off the log-out confirmation dialog box by going to System->Preferences->Sessions and un-checking the "ask on logout" option.

Please tell me how this works out for you....I plan to add this to the HOWTO


Alright...

I followed this: 
[http://ubuntuforums.org/showthread.php?p=771174#post771174](http://ubuntuforums.org/showthread.php?p=771174#post771174)

And everything goes well. I can connect at any time, but it doesn't prompt me for a password or anything of that nature. 

I'd like to add the option to use a password file, or only enable localhost connections for SSH tunneling...

I need help securing this thing...

This works
```
server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg
```

This does not. When I try to connect I get an "EndOfStream" error with the linux viewer, or the windows viewer will give me fits about protocol negotiation. 
```
server_args     = -inetd -o /var/log/x11vnc.log -display :0 -rfbauth /home/aaron/.vncpasswd -many -bg
```

Help

---

### Post by Pollywoggy on 2007-03-02
I wonder if there is a way to force the VNC server to bind to localhost.  I can then use SSH tunneling through localhost.  I can do that now but it would be nice to be able to force the VNC server to only accept connections through localhost.

---

### Post by Underpants on 2007-03-02
> **Pollywoggy said:**
> I wonder if there is a way to force the VNC server to bind to localhost.  I can then use SSH tunneling through localhost.  I can do that now but it would be nice to be able to force the VNC server to only accept connections through localhost.

There sure is. check the man page.

---

### Post by slAoD on 2007-03-12
> **Pollywoggy said:**
> I wonder if there is a way to force the VNC server to bind to localhost.  I can then use SSH tunneling through localhost.  I can do that now but it would be nice to be able to force the VNC server to only accept connections through localhost.

you could just block ports 5900-5901 with iptables..

So i have a question too.... i can connect to both 0,1 displays but i can't connect to display 1 with vnc over ssh.though i can connect to display 0 with vnc over ssh and display 1 with plain vnc (in port 5901)...any proposals?

note that i have configured both displays as mentioned in this thread.

---

### Post by Pollywoggy on 2007-03-12
> **slAoD said:**
> you could just block ports 5900-5901 with iptables..

So i have a question too.... i can connect to both 0,1 displays but i can't connect to display 1 with vnc over ssh.though i can connect to display 0 with vnc over ssh and display 1 with plain vnc (in port 5901)...any proposals?

note that i have configured both displays as mentioned in this thread.

I recall I had a similar problem relating to displays.

---

### Post by fuzzyeric on 2007-03-26
I've been fighting with getting vnc4server working on AMD64 without any luck.  An interesting current symptom is that I seem to have a link cycle now.  (Both members of the cycle go away when vnc4server is removed.)

With:
vnc4-common_4.1.1+xorg1.0.2-0ubuntu1.6.10.1_amd64.deb 
and 
vnc4server_4.1.1+xorg1.0.2-0ubuntu1.6.10.1_amd64.deb

$ which Xvnc
/usr/bin/Xvnc

$ ls -laF /usr/bin/Xvnc
lrwxrwxrwx 1 root root 22 2007-03-26 21:16 /usr/bin/Xvnc -> /etc/alternatives/Xvnc*

$ ls -laF /etc/alternatives/Xvnc
lrwxrwxrwx 1 root root 14 2007-03-26 21:16 /etc/alternatives/Xvnc -> /usr/bin/Xvnc4*

Strangely, even with this, I get activity when I Xvnc manually.  However, the net result is the "typical" xsession-less gray screen.  Feh.

So, ..., two questions:  How can a link cycle work at all?  and  Has anyone got a solution for the gray screen of limbo?

---

### Post by fuzzyeric on 2007-03-30
Ignoring my brain damaged problem distinguishing (/usr/bin/)Xvnc and Xvnc4, is there any progress with getting a window manager to actually start under vnc4server on AMD64?

> **fuzzyeric said:**
> I've been fighting with getting vnc4server working on AMD64 without any luck.  An interesting current symptom is that I seem to have a link cycle now.  (Both members of the cycle go away when vnc4server is removed.)

With:
vnc4-common_4.1.1+xorg1.0.2-0ubuntu1.6.10.1_amd64.deb 
and 
vnc4server_4.1.1+xorg1.0.2-0ubuntu1.6.10.1_amd64.deb

$ which Xvnc
/usr/bin/Xvnc

$ ls -laF /usr/bin/Xvnc
lrwxrwxrwx 1 root root 22 2007-03-26 21:16 /usr/bin/Xvnc -> /etc/alternatives/Xvnc*

$ ls -laF /etc/alternatives/Xvnc
lrwxrwxrwx 1 root root 14 2007-03-26 21:16 /etc/alternatives/Xvnc -> /usr/bin/Xvnc4*

Strangely, even with this, I get activity when I Xvnc manually.  However, the net result is the "typical" xsession-less gray screen.  Feh.

So, ..., two questions:  How can a link cycle work at all?  and  Has anyone got a solution for the gray screen of limbo?

---

### Post by fuzzyeric on 2007-03-30
In case it was inobvious, I'm still pursuing an AMD64 solution because the "wget $1; wget $2; dpkg -i $1; dpkg -i $2" instructions for AMD64 users are completely unworkable.  Both wget()s for the *4.0-7.3_amd64.deb files succeed.  However, the dpkg() invocations fail with:
dpkg: dependency problems prevent configuration of vnc4server:
 vnc4server depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
 vnc4server depends on xserver-common; however:
  Package xserver-common is not installed.

I suspect the first is that my existing libstdc++6 (4.1.1-13) isn't a viable substitute for libstdc++5.
I suspect the second is that xserver-xorg-common doesn't exist, xserver-common having been replaced with x11-common about 15 months ago.

Of course, insisting that dpkg --ignore-depends the relevant packages will get both packages installed; and neither will work.
/usr/bin/Xvnc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

So, the AMD64-specific instructions appear not to work on AMD64.

---

### Post by fuzzyeric on 2007-03-31
I too have the "gray screen" on AMD64 problem.  I've traced this problem down a bit.  It's caused by
1) I don't start a GUI on display :0.  (It's a headless server in a closet.  No point in wasting a couple hundred MB in pointless footprint.)
2) Xvnc starts no window manager.

So, although KDE is an XDMCP server, it's not running and isn't started by the xinetd->Xvnc chain.

Resolution:  Use vnc4server, which not only can start Xvnc, but can *also* start your window manager et al.  Modify the /etc/xinetd.d/Xvnc file to read as:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/vnc4server
        server_args = :1 -geometry 1280x768 -depth 16 -query localhost -inetd -o
nce -fp /usr/share/fonts/X11/misc,/usr/share/fonts/X11/misc/,/usr/share/fonts/X1
1/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/ -DisconnectCli
ents=0 -AlwaysShared -IdleTimeout=0 passwordFile=/root/.vncpasswd
        port = 5901
}

What's changed is the name of the server.  The arguments have also been sorted to suit the syntax of vnc4server.  Note that your desired arguments might be a bit different from mine.

---

### Post by fuzzyeric on 2007-03-31
Note: this uses the vnc4server package from the universe repository, version 4.1.1+xorg1.0.2-0ubuntu1.6.10.1  .

---

### Post by tubelius on 2007-04-05
I have a problem. How can I get this working with fvwm2 window manager. I just get grey screen when I Login..

---

### Post by Pollywoggy on 2007-04-05
I think the reason you are just getting a plain gray screen is that on the remote (server) side, you need to:

cd -

vi .vnc/xstartup

in the file xstartup put something like

fvwm2 &


Because of the way VNC is set up in this HOWTO, I believe you have to do that in /root rather than in your normal user directory.

---

### Post by tubelius on 2007-04-05
Thanks for your reply, but it didn't solve the problem.

I tried creating that ~/.vnc/xstartup and /root/.vnc/xstartup with "xinit" line. xinit command works in terminal with my user and root user. I still get the same grey screen if I login with VNC. The xstartup file was not present, I had to create it. Could the config file be wrong / somewhere else?

Some details:
[INDENT]tubelius@radiant:/root$ locate xstartup
/home/tubelius/.vnc/xstartup
/root/.vnc/xstartup
tubelius@radiant:/root$ more /home/tubelius/.vnc/xstartup
xinit
tubelius@radiant:/root$ more /root/.vnc/xstartup
xinit
tubelius@radiant:/root$ more /home/tubelius/.xinitrc
/usr/bin/fvwm-themes-start
tubelius@radiant:/root$ more /root/.xinitrc
/usr/bin/fvwm-themes-start[/INDENT]

---

### Post by Pollywoggy on 2007-04-05
You followed the instructions for Ubuntu and you are using gdm as your session manager?
The instructions are slightly different for kdm.

---

### Post by tubelius on 2007-04-05
Session manager is the login screen, right? I logged in from terminal and started fvwm manually. I try installing/fixing that gdm. Thanks.

Update: I got the gdm working, I can now login and run fvwm fron gdm login screen.

---

### Post by tubelius on 2007-04-06
The GDM is working now, but I still get the grey screen when I login. How can I access GDM from VNC? I tried without xstartup file and with "gdm" command in it too. I still get no GDM running on Xvnc.

---

### Post by Pollywoggy on 2007-04-06
> **tubelius said:**
> The GDM is working now, but I still get the grey screen when I login. How can I access GDM from VNC? I tried without xstartup file and with "gdm" command in it too. I still get no GDM running on Xvnc.

Don't put gdm in the xstartup file.  GDM (Gnome Desktop Manager) is your session manager and it should start automatically when you boot into Ubuntu.  If it doesn't, do 'sudo dpkg-reconfigure gdm' and specify gdm as your session manager.

Did you enable XDMCP as shown in the first post of this thread?  Since it appears you did not have gdm installed then, I think perhaps you had not done that.  Also make sure you install only the packages shown and no other VNC packages.

You probably don't need the xstartup file if you follow the HOWTO exactly.  I only use it because sometimes I start vncserver from my user account on the remote host.

Oh one more thing.  You only need to run a session manager on the remote host and it can be gdm, kdm, or maybe xdm.
The session manager running on the remote host will give you a choice of window managers depending on what is installed.  It will work the same as it does on your local machine.

---

### Post by tubelius on 2007-04-06
Hey, I rebooted and it started working. Maybe the GDM wasn't working properly untill the reboot.

Thank you very much for your help.

---

### Post by Pollywoggy on 2007-04-06
> **tubelius said:**
> Hey, I rebooted and it started working. Maybe the GDM wasn't working properly untill the reboot.

Thank you very much for your help.

When you make changes to gdm, you need to restart it (you do not need to reboot) and when you make changes to xinetd.conf or inetd.conf, you need to restart xinetd or inetd.

About the only time you need to reboot in Linux is when you are booting to a new kernel.
to restart xinetd:
/etc/init.d/xinetd restart
for gdm:
/etc/init.d/gdm restart

---

### Post by Pollywoggy on 2007-04-07
I just tried something that seems really useful.

I downloaded the deb-src packages for gdm and in the debian/rules file, I added the option 
--enable-secureremote=yes

When the package was done compiling, I installed it and rebooted the machine.
Now when I use xvncviewer to connect, I get the gdm login with an option to login directly to another machine via xdmcp.  I am not sure of this but I think this will only work if the remote host is running sshd (ssh server).  The nice thing is that you do not need to login to the local machine first, you can login directly to the remote machine.

GDM is not compiled with --enable-secureremote=yes by default, so you will need to compile it after executing 'sudo apt-get build-dep gdm'

---

### Post by Hubris2 on 2007-04-07
VNC is not considered to be terribly secure....I wouldn't implement it on an important box without restricting logons to local...and using SSH to tunnel in.

---

### Post by Pollywoggy on 2007-04-07
I need to add that I recompiled gdm with the secure option (see my previous post) on the client machine.  When I get gdm's login window, there is a choice of sessions (KDE, Gnome, etc) but there is one more that reads "secure remote connection" or something like that.  I select it and then a window opens up without my having to login to the local machine at all.  The window asks for the hostname of the remote host.  This only works if the remote host is running SSH.
I then get a prompt for my login and SSH passphrase.  When I am logged in it looks as though I am sitting in front of the remote host.

I don't think it is necessary to compile the remote host (the vnc server) gdm with this option, only the client.

Since the passphrase works, I must have somehow been logged in at the local machine though it is not obvious.

---

### Post by simon0t7 on 2007-04-08
hm.. i just installed ubuntu 6.1 on my new amd machine, but I'm getting a problem when trying to install the resumable vnc software.  I dont think i can live without it after installing it on my other machine.

anyways, I'm stuck at the vnc4server installation step:
I'm using an AMD Sempron processor

> simon@albatron:~$ sudo dpkg -i vnc4server_4.0-7.3_amd64.deb
Selecting previously deselected package vnc4server.
(Reading database ... 87464 files and directories currently installed.)
Unpacking vnc4server (from vnc4server_4.0-7.3_amd64.deb) ...
dpkg: dependency problems prevent configuration of vnc4server:
 vnc4server depends on xserver-common; however:
  Package xserver-common is not installed.
dpkg: error processing vnc4server (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vnc4serve

if I remove vnc4server and attempt to install xserver-common I get broken packages.

> The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
E: Broken packages


what should i do?  I did follow the other steps of xdmcp & getting the extra repositories.
The other thing I've done so far was install ssh, nvidia driver and run synaptic upgrade

Thanks,
S

---

### Post by Pollywoggy on 2007-04-08
> **simon0t7 said:**
> hm.. i just installed ubuntu 6.1 on my new amd machine, but I'm getting a problem when trying to install the resumable vnc software.  I dont think i can live without it after installing it on my other machine.

anyways, I'm stuck at the vnc4server installation step:
I'm using an AMD Sempron processor



if I remove vnc4server and attempt to install xserver-common I get broken packages.



what should i do?  I did follow the other steps of xdmcp & getting the extra repositories.
The other thing I've done so far was install ssh, nvidia driver and run synaptic upgrade

Thanks,
S

This is what I have on my kubuntu Edgy system, in addition to having installed gdm in place of kdm:
ii  vnc4-common                            4.1.1+xorg1.0.2-0ubuntu1.6.10.1          Virtual network computing server software
ii  vnc4server                             4.1.1+xorg1.0.2-0ubuntu1.6.10.1          Virtual network computing server software
ii  xvncviewer                             3.3.7-12ubuntu1                          Virtual network computing client

You can use kdm but kdm will not give you the option of securely (ssh) connecting to the remote host.  gdm will give that option only if you compile it yourself with the option enabled.

I would try 'sudo apt-get remove vnc4server', then try to remove vnc-common and then install vnc4-common and vnc4-server.  The HOWTO says that xvnc4viewer will not work.  Install xvncviewer last.

---

### Post by simon0t7 on 2007-04-08
hm.. those two packages don't exist for me vnc4-server and vnc4-common

---

### Post by Pollywoggy on 2007-04-08
> **simon0t7 said:**
> hm.. those two packages don't exist for me vnc4-server and vnc4-common


pollywog@slider:~$ apt-cache policy vnc4-common
vnc4-common:
  Installed: 4.1.1+xorg1.0.2-0ubuntu1.6.10.1
  Candidate: 4.1.1+xorg1.0.2-0ubuntu1.6.10.1
  Version table:
 *** 4.1.1+xorg1.0.2-0ubuntu1.6.10.1 0
        500 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
        100 /var/lib/dpkg/status
     4.1.1+xorg1.0.2-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages

You will need to enable 'universe' in your /etc/apt/sources.list

---

### Post by simon0t7 on 2007-04-09
Ahh...I blindly copied the sources list from the 5.10 file, so the links were busted
Installed but not fully configured

> simon@albatron:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Jul  4 2006 10:09:06
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
X connection to localhost:10.0 broken (explicit kill or server shutdown).


almost there....
I did enable remote logobe, and for configure XDMCP, i had that unchecked (disabled)

---

### Post by gurgle on 2007-04-10
i am still getting the "grey x" screen. any fix out for this yet?

---

### Post by simon0t7 on 2007-04-11
sweet! got mine up and running

gurgle: I got that problem too, but after I installed the display drivers and downgraded vnc4server to vnc4server /edgy, the problem went away.
if you install the newest upgrades in gdm or through apt-get ugprade, it will upgrade to a newer vnc4server which prevented me from vncing back into the system

---

### Post by deserthowler on 2007-04-15
I tried this and it worked just as you said.  Great.  :KS :KS :KS :KS :KS 

I am running UBUNTU 6.06 on a PII as a server and a Sun U30 running Debian Etch.

Earl Violet

---

### Post by Hubris2 on 2007-04-20
I just did an upgrade to Feisty, and find myself back able to connect in via SSH, but VNC sessions to :1 are immediately disconnected.  Since I'm currently working from a shell, it's the hard way to configure things..especially if not positive what needs to be done.

GDM remote is enabled, the VNC password is set, I have connectivity through a SSH....did we ever figure out exactly what the step was to fix immediate disconnects the moment you try connect to a VNC4Server session?

Thanks!

It seems that Feisty doesn't change the version of Vnc4Server from the 'latest' on Edgy...that broke a number of our sessions.  Perhaps a downgrade would fix things like it did before.  As I'm currently stuck at a shell, I can't run update manager to verify what the last version was.  I know I can downgrade from a command prompt, but I need to know the exact name of the older vnc4server package.  Can anyone help me out?

Update - I removed the default VNC4Server package the installed with Feisty, and manually downloaded vnc4server_4.1.1+xorg1.0.2-0ubuntu1_i386.deb .  When installed, my errors about refusing connections went away.  One problem....it gives me the Gnome login prompt, but after I enter my ID and pass...it just puts me back to the login prompt.  If I put in an incorrect password it states it - when it's correct there's no error, it just won't let me past the login screen.

I'm already signed in on display 0, before it used to give a warning but allow a second login on display 1.  Has something changed to not allow multiple Gnome logins with the same ID?

---

### Post by Hubris2 on 2007-04-23
Does anybody know why I might be able to connect to a session on display 1, but when I enter a correct username and password combo, I'm just returned to a gnome login prompt?  If my password is incorrect it tells me....but when everything is correct, the login just doesn't happen.

During this time I see one entry in the syslog, about Transport Endpoint not being connected.

Alternatively, can someone recommend another VNC server that has similar functionality to VNC4Server, but that doesn't seem to have problems like many have expressed here...and have been documented in bug reports  since January?

Thanks,

---

### Post by sefs on 2007-04-23
How do you do the first part of this article on feisty. 

that is the enabling of the xdmcp 

Thanks.

---

### Post by gesquive on 2007-04-24
This goes for both Fiesty and Edgy:
Goto **System -> Administration -> Login Window** and click on the Remote tab.
In the Style dropdown select "Same as Local". This should make a "Configure XDMPC" button to appear in the bottom right corner. Just click on it and make sure that "Honor indirect requests" is checked. The default settings worked just fine for me.

---

### Post by shill88 on 2007-04-28
I tried installing using this guide but I get ReadFromRFBServer: rdr::EndOfStream after I enter the VNC password for VNCViewer.

I tried downgrading to the edgy version using the following command.

sudo apt-get install vnc4viewer/edgy

but it returns 

E: Couldn't find package vnc4viewer

How can I fix this error or install the edgy version?

Thanks
Shawn

---

### Post by scarpent on 2007-04-28
You need vnc4server/edgy, not vnc4viewer/edgy.

This thread was very helpful to me in getting this working -- I wrote up a howto at:

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

That has everything I learned consolidated.  I saw that same EndOfStream error also.

---

### Post by shill88 on 2007-04-28
shawn@shawn-desktop:~$ sudo apt-get install vnc4server/edgy xinetd
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'edgy' for 'vnc4server' was not found

Sorry I should have put that before.

This is on Feisty BTW

Shawn

---

### Post by bhamail on 2007-04-28
Hi Shawn,

I don't know how to make this work on Fiesty (in fact, I just upgraded a box to Fiesty, and I'm now back to square one...). If anyone knows how to make this work on Fiesty, please post!

Dan

---

### Post by Hubris2 on 2007-05-01
As near as I can tell..the most recent binary in the repository (a custom build for Ubuntu) for VNC4Server is broken...it has problems that lead to connection problems (which I am experiencing since my upgrade to Feisty) and others are also able to connect, but have issues running certain applications (related to the version of GCC used to compile the custom version).

A number of people have made suggestions that 'fix' things for them, but in my experience, nobody has actually found the 'solution' to these issues.  There is an official bug report on the issue and has been for months, but the binary is not being fixed, and nobody is assigned to the problem.

Today, if you follow this guide, I do not believe you will have a working VNC session - whether in Edgy or Feisty.

---

### Post by dantemustdie94 on 2007-05-03
Hey this was very helpful. When I connect on localhost the screen is black and when I connect remotely the screen is black here is a screen shot of what I get. [IMG]http://img68.imageshack.us/img68/1016/vncgaynesson1.jpg[/IMG] the mouse moves and on the vncviewer but not on the machine with the vncserver

---

### Post by scarpent on 2007-05-04
Here's something, perhaps some hope for the problem of the broken vnc4server.  Warren over at grumpymole mentions a -extension XFIXES option you can add to your command that appears to work with the latest vnc4server.  There is also an new option in Feisty Fawn you have to get right so you can have multiple logons.

Warren's post: [http://grumpymole.blogspot.com/2007/04/workaround-for-vnc4server-end-of-stream.html](http://grumpymole.blogspot.com/2007/04/workaround-for-vnc4server-end-of-stream.html)

Discussion at launchpad.net: [https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282)

I upgraded one of my Ubuntu Edgy (6.10) machines with the latest vnc4server (through the GUI software updater), and confirmed that it broke my VNC setup.  (Viewer is prompted for password, but got a "connection closed" immediately after typing in password.)  Then I tried the -extension XFIXES option in /etc/xinetd.d/Xvnc and after a reboot VNC worked again.  I'm going to update my guide at movingtofreedom.org with this info.

I don't have any Feisty machines so can't confirm about the multiple logon setting.

Hope this is helpful for somebody!

---

### Post by Aellus on 2007-05-04
Hey guys,

I too have been fighting with the rdr::EndOfStream error for a while, couldn't figure out how to do this at all with GDM. I had the same problem on Edgy, gave up and just left a user logged in and used the normal vnc util that comes with Ubuntu. I just recently upgraded to Feisty and had the same problem.

The link above solved my problem completely... adding the following line to the server_args in the Xvnc script worked!

```
-extension XFIXES
```

---

### Post by willsomebody on 2007-05-05
I am  a **complete** linux noob.  

When I try to set the password with this command: sudo vncpasswd /root/.vncpasswd, it tells me the password is too short.  What am I doing wrong?

---

### Post by penno on 2007-05-06
Great guide Tichondrius and everyone who contributed. ^_^ Thank you.

Does anyone know how to get copy and paste working? (From remote to host and vice versa?) I've played around with the -SendCutText and -AcceptCutText parameters in the server_args section of Xvnc, but to no avail.... Sad huh.

---

### Post by Hubris2 on 2007-05-08
I can also confirm that updating to the latest version available from the repositories and adding the -extension XFIXES yields exactly the same result as does going back to the old version....it does not immediately disconnect after you enter your VNC password.  Thanks!

However....as indicated, I am having exactly the same results...which in my case is not good.  I get a Gnome login prompt, and when I enter a correct ID and password, it just returns to the login prompt.  My syslog shows the following entry:

warning: can't get client address: Transport endpoint is not connected

I've had this problem ever since I upgraded to Feisty, and haven't been able to use VNC4Server once - although it worked perfectly under Edgy.

Does anyone have any suggestions?

Thanks,

---

### Post by schwieb on 2007-05-08
If you are having trouble using this with multiple users in Feisty, there is a simple fix.  

Go to System > Administration > Login Window

On the "General" tab uncheck the box marked "Disable multiple logins for a single user"

---

### Post by hotani on 2007-05-08
Trying to set this up on Dapper. I've done everything in this thread (several times), rebooted, reconfigured, re-edited, etc....

But I'm still getting this same frakking error:
```

VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

```

I even have it working on another identical machine. I can't see a difference between the two. What is happening here?

After making several of the gdm.conf file changes, I noticed in the WORKING config, that under [xdmcp], it was set to 'false'!

The XDMCP setting mentioned in the first post doesn't even exist. The config is called "Login Window" and has no such method of "enabling xdmcp". And according to my working config, it isn't even necessary. 

What is this "ConnectToTcpAddr" error? VNC is set up, the password is set up, the firewall has the port open.

EDIT: wow. in the Xvnc file, it will throw the above error if you change the formatting from:
service Xvnc
{

to:

service Xvnc {

So that was a stupid error on my part, I am extremely anal about my own code and just reformatted it to fit. I had no idea it would be so finicky. Oh well. Anyway, my above comments stand: the 'allow indirect login' box does NOT need to be unchecked, the edits to gdm.conf are completely unnecessary, and if you leave the formatting alone in the Xvnc file, you should be fine. *grumble, grumble*

---

### Post by Sharpeee on 2007-05-10
Okay, I followed the how-to exactly, but it doesn't work. When I try to connect to the server I get this after I entered the password:

```
vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Jan  7 2007 17:30:38
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Thu May 10 17:08:23 2007
 CConn:       connected to host localhost port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8

Thu May 10 17:08:27 2007
 main:        End of stream

```

Just to get this far I had to install xvnc4viewer, the "standard" vncviewer refused it totally.
I'm running a fresh install of Feisty if that helps.

---

### Post by SeanOB on 2007-05-10
I'm on an AMD64 with a fresh install of feisty.
VNC was the first app I wanted to install b/c I don't have a KVM yet...

I was originally planning on just manually running vncserver something like this:
vncserver -geometry 1920x1200 -desktop "My Desktop"

I couldn't get connected...  so I went through the TODO - figuring I'd just take the trodden path, even if it's not quite what I want.

Ultimately I'd like my users to be able to run vncserver from the command line and then connect as needed to their own sessions - each with resolutions appropriate for their PCs.

The trodden path didn't work for me either; and that's *with* the - -extension XFIXES addition to the Xvnc script.

Are there any other tricks that I need to be aware of?  Maybe something AMD64 specific?
I did NOT follow the TODO AMD64 manual download steps because apt got me a version that was more up-to-date than the manual download told me to get.

OH - here's what I get when I try to connect...  I get a connection failed do you want to reconnect message dialog box from RealVNC.  When I click yes the desktop pops up - filled PINK (not the X gray pattern) that goes away almost as soon as it pops up.

Any ideas of where I can look?  I don't even know where to look for logs for this.  I just blindly followed the TODO.

Thanks!

Sean

---

### Post by danzinho on 2007-05-11
Hi everyone

I've followed the HOWTO taking note of the XFIXES issue (which got round one problem).  All seems well until I issue

$ vncviewer localhost:1

I get this 

VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password: 
VNC authentication succeeded
Desktop name "x11"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-16-*-*-*-*-*-*-*" to type FontStruct
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Using shared memory PutImage

and then dappled black/white screen seen by an earlier poster.  It has a simple black diagonal cross cursor which moves but doesn't respond to mouse clicks.

Can anyone help me take the final step to getting VNC working?

Many thanks

Daniel

---

### Post by deserthowler on 2007-05-14
I haven't had a chance to look at this thread for a while so am kind of behind.  The b/w tweed you are seeing might be twm.  It looks like twm on my Debian Sarge server.  Check if you have TWM and menu loaded on your machine. 

If you don't have menu, that could account for no response to mouse clicks.

I think twm is the default window manager for some of the vnc servers.  You might need to reconfigure to get it to open to the gnome or kde login manager.

I'm not sure as twm was my default manager for my server.

Earl

---

### Post by danzinho on 2007-05-14
Dear Earl

I think you're onto something when you say maybe the wrong windows manager (TWM) is being started.  A while back, on another flavour of Linux, I did have to change the configuration to get my normal GDE going.  At that time VNC looked at a bunch of files in ~/.vnc/ including one, xstartup, that had this line in it

/usr/bin/startkde &

If this is all right then the question is simple - where is the corresponding file now that I need to edit to point at KDE?

Thanks for your help

Dan

---

### Post by heckheck on 2007-05-19
> **danzinho said:**
> Hi everyone

I've followed the HOWTO taking note of the XFIXES issue (which got round one problem).  All seems well until I issue

$ vncviewer localhost:1

and then dappled black/white screen seen by an earlier poster.  It has a simple black diagonal cross cursor which moves but doesn't respond to mouse clicks.

Can anyone help me take the final step to getting VNC working?

Many thanks

Daniel

The HOWTO is good, but it misses a few tricks that will help to resolve your problem.  Basically I was in the same boat as you, working from a brand new Feisty installation.  All it takes is a few tweaks and you should be good to go.

First off, the window manager you see (tweed) is the twm window manager.  There is no mouse support, because this window manager isn't fully installed on your system.  Specifically, the menu package is not installed.  If you start aptitude or synaptic and properly install twm, you would have a working system.  But what you really want is GNOME, right?

Well to get that you need to get vncserver operating with the correct config files.  The HOWTO steps don't cover creating a xstartup config file for VNC to use that will allow you to choose your window manager (you're getting twm just by pure default).  The easiest way to do this is as follows (cut from my personal TWIKI, so forgive the format hack job):

   *  Installation with aptitiude 

root@heckmedia:~# aptitude install vnc4server xinetd

   * First as root, we want to first establish configuration files in the /root/.vnc directory. This requires creating a VNC password. 

root@heckmedia:~# vncpasswd 
Password: 
Verify:   

   * Next, invoke the vncserver to cause the rest of the configuration files to be created. Immediately kill the server, since we won't be using it (instead xinetd will start the vncserver on demand when we try to VNC in). 

root@heckmedia:~# vncserver

New 'heckmedia:1 (root)' desktop is heckmedia:1

Creating default startup script /root/.vnc/xstartup
Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/heckmedia:1.log

root@heckmedia:~# vncserver -kill :1
Killing Xvnc process ID 12108

   * Now change the session window manager in the /root/.vnc/xstartup file from 'twm' to 'gnome-session' 

root@heckmedia:~# cd .vnc/
[email]root@heckmedia:~/.vnc[/email]# ls
heckmedia:1.log  passwd  xstartup
[email]root@heckmedia:~/.vnc[/email]# emacs xstartup 
[email]root@heckmedia:~/.vnc[/email]# diff xstartup xstartup~
12c12
< gnome-session &
---
> twm &

   * Next we need some configuration to start Xvnc as a service under xinetd. Create the file /etc/xinetd.d/Xvnc using cat and input redirection. Close the input stream with a Control-D. 

[email]root@heckmedia:~/.vnc[/email]# cd /etc/xinetd.d/
root@heckmedia:/etc/xinetd.d# cat > Xvnc
service Xvnc
{
    type = UNLISTED
    disable = no
    socket_type = stream
    protocol = tcp
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = -inetd :1 -query localhost -geometry 1280x1024 -depth 24 -once -DisconnectClients=0 -NeverShared passwordFile=/root/.vnc/passwd -extension XFIXES
    port = 5901
}

   * Now stop and restart the xinetd daemon, killing any Xvnc processes in between. 

root@heckmedia:/etc/xinetd.d# /etc/init.d/xinetd stop
Stopping internet superserver: xinetd.
root@heckmedia:/etc/xinetd.d# killall Xvnc
root@heckmedia:/etc/xinetd.d# /etc/init.d/xinetd start
Starting internet superserver: xinetd.
   
   * A reboot seems necessary at this point. I have not been successful using VNC the first time without it.

   * Finally try to login from a remote computer to IP Address:1 using a VNC client.
      * It is also possible to test using vncviewer to localhost:1
      * Sessions will not end when you close the VNC client unless you log out! 

That should just about do it.  You should now be able to remotely login.

Good luck,

h_h

---

### Post by danzinho on 2007-05-22
Dear h h

Thanks very much for the reply.  Unfortunately, I still seem to be missing something.  I've changed the configuration files like you said, but I'm still getting the tweed window manager. 

/root/.vnc/xstartup looks like this

--------------------------------------------------------------------------------------------
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &
--------------------------------------------------------------------------------------------

and /etc/xinetd.d/Xvnc looks like this

service Xvnc
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/Xvnc
server_args = -inetd :1 -query localhost -geometry 1280x1024 -depth 24 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vnc/passwd -extension XFIXES
port = 5901
}

Some queries

-- should those lines at the top of xstartup remain commented out?  I did try uncommenting but that didn;t seem to help.  It's not clear what a 'normal desktop' means in this context.

-- -fp /usr/share/fonts/X11/misc in Xvnc seems necessary for me - I get additional errors otherwise.

-- this setup seems to imply that logging on via vnc would be as root.  That might have security issues and I'd rather just log on as me anyway.  What would need changing to allow that?

-- any idea why I'm still getting the dratted tweed manager?!

Thanks very much for your help

Daniel

---

### Post by BDNiner on 2007-05-22
Wow these instructions actually worked for me. First time i have followed instructions on linux and they have worked the first time. The instructions at the beginging of the thread did work. I am new the linux so i have no idea why, i am just happy that it works and i didn't spend all day on it.

> **Tichondrius said:**
> Ok, to resume a session you started on your physical display (display :0) all you really need is to turn on Ubuntu's remote desktop feature using the Remote Desktop Preferences dialog box accessible from System->Preferences->Remote Desktop menu item.  Just check the first two options there (allow other users to view your desktop and allow other users to control your desktop) and set the password in the bottom of the dialog box (check the REuqire password option), and you're done ! 
  The above uses the built in VNC capability that Ubuntu comes installed with, but the drawback is that it's a little slow, and you need to enable it for each user which wants to allow his desktop to be view or controlled remotely. Also this doesn't allow remote VNC clients to log in to GDM, only to view a GDM session that was started by someone actually using the physical display. So if currently no one is logged in, a remote user cannot connect to display :0 and start a new session.
  But don't worry - there is a better way which allows you to view the phyical display remotely and also log-in to a new session from GDM (using a remote VNC client) !  And it works faster (as fast as the regular VNC server), and works for all users. Here's how to do that :

1. Install x11vnc package

```
sudo apt-get install x11vnc
```

2. Add x11vnc service to xinetd:

```
sudo gedit /etc/xinetd.d/x11vnc
```

Enter this into the new file:

```

service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg
        disable         = no
}

```

3. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo killall x11vnc
sudo /etc/init.d/xinetd start
```

4. From a remote machine use your VNC client to connect to display :0

```
vncviewer  vnchost:0
```

Note that after loggging from GDM and also after logging out from the X-session back and going back to GDM, the VNC client gets disconnected for some reason. So you just need to re-connect and you will get back into the session you logged into. When logging out, the disconnect happens when gnome asks you to confirm your intention to log out, so it's best to turn off the log-out confirmation dialog box by going to System->Preferences->Sessions and un-checking the "ask on logout" option.

Please tell me how this works out for you....I plan to add this to the HOWTO

---

### Post by BDNiner on 2007-05-22
i guess i spoke too soon. After a reboot i was unable to connect using the same options as before. I had to use vnc to connect to x.x.x.x:2 instead of x.x.x.x:1 like i did the first time. when i connect to x.x.x.x:1 i get the same grey screen. Also i need to keep looking and find out how to load these option on login.

---

### Post by BDNiner on 2007-05-23
After i did what is outlined in this post i was able to connect fine. the machine even shows up on the options menu before you log in. 

> **Jose Catre-Vandis said:**
> I have just got to the bottom of this one myself.

gdm needs to be running, and xdmcp also needs to be enabled.

To start gdm use the following command on the machine you are trying to remote to ( this assumes you can either physically access it, or you have already "ssh"ed in Terminal)

sudo /etc/init.d/gdm start        (you might then need to wait a minute, depending on the speed on your machine)

Next ensure that XDMCP is enabled

sudo gedit /etc/X11/gdm/gdm.conf
or
sudo nano /etc/X11/gdm/gdm.conf (if doing this through Terminal)

and find the [xdmcp] section at the end of the file
change

Enabled=False

to

Enabled=True

Then save and then best to reboot. of course if gdm is not loaded on boot, you will have to start it again

---

### Post by sastian on 2007-05-23
> **heckheck said:**
> The HOWTO is good, but it misses a few tricks that will help to resolve your problem.  Basically I was in the same boat as you, working from a brand new Feisty installation.  All it takes is a few tweaks and you should be good to go.

First off, the window manager you see (tweed) is the twm window manager.  There is no mouse support, because this window manager isn't fully installed on your system.  Specifically, the menu package is not installed.  If you start aptitude or synaptic and properly install twm, you would have a working system.  But what you really want is GNOME, right?

Well to get that you need to get vncserver operating with the correct config files.  The HOWTO steps don't cover creating a xstartup config file for VNC to use that will allow you to choose your window manager (you're getting twm just by pure default).  The easiest way to do this is as follows (cut from my personal TWIKI, so forgive the format hack job):

   *  Installation with aptitiude 

root@heckmedia:~# aptitude install vnc4server xinetd

   * First as root, we want to first establish configuration files in the /root/.vnc directory. This requires creating a VNC password. 

root@heckmedia:~# vncpasswd 
Password: 
Verify:   

   * Next, invoke the vncserver to cause the rest of the configuration files to be created. Immediately kill the server, since we won't be using it (instead xinetd will start the vncserver on demand when we try to VNC in). 

root@heckmedia:~# vncserver

New 'heckmedia:1 (root)' desktop is heckmedia:1

Creating default startup script /root/.vnc/xstartup
Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/heckmedia:1.log

root@heckmedia:~# vncserver -kill :1
Killing Xvnc process ID 12108

   * Now change the session window manager in the /root/.vnc/xstartup file from 'twm' to 'gnome-session' 

root@heckmedia:~# cd .vnc/
[email]root@heckmedia:~/.vnc[/email]# ls
heckmedia:1.log  passwd  xstartup
[email]root@heckmedia:~/.vnc[/email]# emacs xstartup 
[email]root@heckmedia:~/.vnc[/email]# diff xstartup xstartup~
12c12
< gnome-session &
---
> twm &

   * Next we need some configuration to start Xvnc as a service under xinetd. Create the file /etc/xinetd.d/Xvnc using cat and input redirection. Close the input stream with a Control-D. 

[email]root@heckmedia:~/.vnc[/email]# cd /etc/xinetd.d/
root@heckmedia:/etc/xinetd.d# cat > Xvnc
service Xvnc
{
    type = UNLISTED
    disable = no
    socket_type = stream
    protocol = tcp
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = -inetd :1 -query localhost -geometry 1280x1024 -depth 24 -once -DisconnectClients=0 -NeverShared passwordFile=/root/.vnc/passwd -extension XFIXES
    port = 5901
}

   * Now stop and restart the xinetd daemon, killing any Xvnc processes in between. 

root@heckmedia:/etc/xinetd.d# /etc/init.d/xinetd stop
Stopping internet superserver: xinetd.
root@heckmedia:/etc/xinetd.d# killall Xvnc
root@heckmedia:/etc/xinetd.d# /etc/init.d/xinetd start
Starting internet superserver: xinetd.
   
   * A reboot seems necessary at this point. I have not been successful using VNC the first time without it.

   * Finally try to login from a remote computer to IP Address:1 using a VNC client.
      * It is also possible to test using vncviewer to localhost:1
      * Sessions will not end when you close the VNC client unless you log out! 

That should just about do it.  You should now be able to remotely login.

Good luck,

h_h

I have tried this on a new server i just set up but i didnt do it as root..
and i have no xstartup file.. should i make one or startover as root and itll make one then?

:(

---

### Post by antoniuk on 2007-05-31
Looks like I needed to update my vnc client to get it to work with vnc4server. I think there was some authentication thingies (technical term) updated that only allow for something or another... eithr way all is well again

---

### Post by Lowfront on 2007-06-09
Ok so I went through this guide and got to the point of being able to "remote" connect to the same machine I worked on


I want to be able to remote connect from my laptop to the computer while I'm away for the day.  How would I go about doing this.  

I believe I have the desktop set up properly just need to figure out what do to with the laptop.




This is what I attemped to do........no clue though


lowfront@lowfront-x60:~$ vncviewer 192.168.1.103::5901
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

---

### Post by mpadams on 2007-06-12
1. Add "flags = IPv6" to the x11vnc file.

2. Restart xinetd if needed.

3. Use the IPv6 TightVNC viewer (free) or RealVNC 4.1 (pay) to access it. Not sure what other Linux or Windows clients support IPv6 at this time.

[http://jungla.dit.upm.es/~acosta/paginas/vncIPv6.html](http://jungla.dit.upm.es/~acosta/paginas/vncIPv6.html)
[http://www.realvnc.com/products/enterprise/4.1/ipv6.html](http://www.realvnc.com/products/enterprise/4.1/ipv6.html)

Reference: "IPv6 in Practice" [http://www.benedikt-stockebrand.de/books_e.html](http://www.benedikt-stockebrand.de/books_e.html)

---

### Post by beengone on 2007-06-29
Running  Xubuntu 7

for step 4:
Add vnc service to xinetd:
Code:     sudo gedit /etc/xinetd.d/Xvnc

I get errors.  

Warning:  unknown mime-type for "/etc/xinetd.d/Xvnc" - - using "application/*"
Error: now write permission for file "/etc/xinetd.d/Xvnc"


Any idea how to fix this?

---

### Post by hobs0n on 2007-07-01
First I wanna say: Thank you for making this great newb helping guide thread :D

My problem is: when I run the test you said "vncviewer localhost:1" it says: "ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)"


I followed your guide and did all as you said but I couldnt find the "enable xdmcp" options. Im running latest Xubuntu so I guess the xdmcp options isnt where it says it is in your guide?

---

### Post by hotani on 2007-07-01
hobs0n: the "enable xdmcp" option is not there. Instead of marking a checkbox for it, go into the 'login window' prefs and under the 'remote' tab, set it to 'simple' which should do the same thing. 

Also, I had the same problem when trying to run locally. use "localhost:5900" or whatever port you are using instead of "localhost:1" which did it for me.

---

### Post by hobs0n on 2007-07-01
Ok, I started the "login window" app and the remote tab, I found no simple, my options was: same as local, plain, plain with face  browser. I guess instead of simple its called plain? I selected plain and connected to my port that was 5901, still get the same "ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)" error. What am I doing wrong?

---

### Post by hotani on 2007-07-01
right - sorry, it is 'plain' and not 'simple', i'm getting my control panels mixed up. 

As for the error, I'm not sure what is causing that. Do you have the vnc port open on the machine? And is the xinetd server awaiting connections (via the Xvnc script in the howto)?

---

### Post by hobs0n on 2007-07-02
I rechecked the howto and found nothing wrong what I have done, altho when I read deeper in the thread I found when I ran "grep xinetd /var/log/syslog" as Tichondrius said I get HEAPS of error messages : 

"Jul  2 17:30:42 vargtass-server xinetd[7572]: warning: can't get client address: Transport endpoint is not connected
Jul  2 17:30:42 vargtass-server xinetd[7573]: warning: can't get client address: Transport endpoint is not connected
Jul  2 17:30:42 vargtass-server xinetd[7191]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Jul  2 17:30:52 vargtass-server xinetd[7191]: Activating service Xvnc"

Earlier in the log file it shows: 

"Jul  2 17:28:10 vargtass-server xinetd[7191]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing chargen
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing chargen
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing daytime
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing daytime
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing discard
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing discard
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing echo
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing echo
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing time
Jul  2 17:28:10 vargtass-server xinetd[7191]: removing time
Jul  2 17:28:10 vargtass-server xinetd[7191]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Jul  2 17:28:10 vargtass-server xinetd[7191]: Started working: 1 available service
Jul  2 17:28:57 vargtass-server xinetd[7207]: warning: can't get client address: Transport endpoint is not connected"

Might this be that it isnt listening to the port??

EDIT: I add the I just restarted the  machine which didnt help, I also want to say that in the [Post](http://ubuntuforums.org/report.php?p=688683) in this page, Tichondrius said: "sudo Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd" and I tried that and it said: "Unrecognized option: -DisconnectClients=0" and I tried to remove that option and then it said that command was wrong and I tried remove more options but I gave it up.

Might this be that my VNC server is wrong or that its a different version? How can I check what version I got?

EDIT2:  Hpw do I check if my machine has that port open?

---

### Post by bouzzi on 2007-07-12
HI
 I have the french 7.04 Feisty Fawn version of Ubuntu and I cannot figure how to get to this part of your steps :

1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

When I get there, I don't see nothing about XDMCP...

Is there an other way to enable XDMCP?

In a config file ???? maybe ?

For each other steps, I worked well...  I think

But in vncviewer I get a grey screen with X cursor giving me nothing to do but moving it...

Thanx

Bouzzi

---

### Post by prostock3 on 2007-07-13
I just used this tutorial to install vnc4, and my friend gt onto a session without pass word or login

He pointed me to this demo of how to break in:

[http://hydrogen.oshean.org/vnc-exploit.htm](http://hydrogen.oshean.org/vnc-exploit.htm)

And told me to upgrade my version.  What security precautions do you guys recommend for vnc?


Thanks.:guitar:

---

### Post by hotani on 2007-07-13
> **bouzzi said:**
> HI
 I have the french 7.04 Feisty Fawn version of Ubuntu and I cannot figure how to get to this part of your steps :

1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

When I get there, I don't see nothing about XDMCP...

Is there an other way to enable XDMCP?

In a config file ???? maybe ?

Go to Administration -> Login Window -> Remote tab -> style: "plain"
> 
For each other steps, I worked well...  I think

But in vncviewer I get a grey screen with X cursor giving me nothing to do but moving it...

Thanx

Bouzzi
A reboot cleared the gray screen problem for me.

---

### Post by kurgbe on 2007-07-15
There is a detailed tutorial on the installation of vnc on Ubuntu, including info on XDMCP for 7.04

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/]("http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/")

---

### Post by henryhynd on 2007-07-17
Thanks a heaps for this how to, been wondering how i could achieve something like this for sometime... then LTSP conflicted with something and did some very dodgy things!

but yeh, all good now... cheers to the author!

Henry

---

### Post by netvampire on 2007-07-22
thanks. worked like a charm.

---

### Post by cheetah86 on 2007-08-01
Does anyone know of a program or command(s) that allow you to send windows from the real desktop (:0) to the VNC desktop (:1) or vice versa?

---

### Post by kostin on 2007-08-03
Hello

Is it possible to set up remote connection via VNC for more than one user?

I can login only as root with this manual.

How can I set up remote for 2 users (root & user1)?

(Sorry for my English)

---

### Post by Underpants on 2007-08-15
I use this to run x11vnc for my gnome based systems.


```

/etc/xinetd.d/x11vnc

service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg -localhost
        disable         = no
}

```

can anyone assist in changing this to work with a KDE/Kubuntu system?

---

### Post by asutherlandus on 2007-08-16
I worked my way through the tutorial and got vnc4 working on my EM64T box.

Now it has mysteriously stopped working. Having spent a full day trying to debug I'm stuck. Any help would be appreciated.

vncserver fails to start either manually or via xinetd when I am logged in via gdm.

However, if I switch to text login via alt-ctrl-f1 then stop gdm and restart using startx I can get vncserver to run. However in this mode I get the basic grey X screen with no login.

So there is some difference between these two ways of starting X and I'm not sure what the difference is.

Any ideas? I have tried every thing in the tutorial short of reinstall ubuntu and start over.

thanks,

Andrew

---

### Post by lns on 2007-09-10
Can you elaborate on how LTSP "conflicted with something and did some very dodgy things"? I'm about to deploy a fairly large number of VNC services using this HOWTO - all of them happen to be LTSP servers as well.

Thanks for any insight!!

> **henryhynd said:**
> Thanks a heaps for this how to, been wondering how i could achieve something like this for sometime... then LTSP conflicted with something and did some very dodgy things!

but yeh, all good now... cheers to the author!

Henry

---

### Post by krunge on 2007-09-13
> **Underpants said:**
> I use this to run x11vnc for my gnome based systems.
```

/etc/xinetd.d/x11vnc

service x11vnc
{
        ...
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg -localhost
}

```

can anyone assist in changing this to work with a KDE/Kubuntu system?

For KDM (or XDM) display manager it will be tricky because the -auth filename is random.  E.g. on a KDM running system I have, "ps wwwwwaux | grep auth" reveals the auth file:

```
/usr/X11R6/bin/X -br -nolisten tcp :0 vt7 -auth /var/lib/xdm/authdir/authfiles/A:0-ghswan
```

So the "/var/lib/xdm/authdir/authfiles/A:0-ghswan" will change each reboot, etc.

The only way I can think of handling this is via a wrapper script, say:

```

/etc/xinetd.d/x11vnc

service x11vnc
{
        ...
        server          = /usr/local/bin/x11vnc_WRAPPER
        server_args     =
}

```

where /usr/local/bin/x11vnc_WRAPPER might look like:

```
#!/bin/sh
authfile=`ps wwwwwaux | grep '/X.*-auth' | grep -v grep | sed -e 's/^.*-auth *//' -e 's/ .*$//' | head -n 1`

if [ -r "$authfile" ]; then
        exec /usr/bin/x11vnc -inetd -o /var/log/x11vnc.log -display :0 -auth "$authfile" -localhost
fi
exit 1
```
(untested)



In the x11vnc 0.9.3 dev tarball this is automated to some degree.  I believe the x11vnc cmdline would be something like:
    ```
server_args     =  -inetd -o /var/log/x11vnc.log -find -env FD_XDM=1 -localhost
```
This works from the cmdline; but I haven't tried with inetd yet.

---

### Post by krunge on 2007-09-13
I just tried /usr/local/bin/x11vnc_WRAPPER under xinetd. To have it work one needs to get rid of the -localhost and also set COLUMNS to be wide since inetd isn't connected to a terminal.

/usr/local/bin/x11vnc_WRAPPER:
```
#!/bin/sh
export COLUMNS=256
authfile=`ps wwwwwaux | grep '/X.*-auth' | grep -v grep | sed -e 's/^.*-auth *//' -e 's/ .*$//' | head -n 1`

if [ -r "$authfile" ]; then
        exec /usr/bin/x11vnc -inetd -o /var/log/x11vnc.log -display :0 -auth "$authfile"
fi
exit 1
```

---

### Post by lns on 2007-09-13
Well, I tried following this HOWTO on one of my LTSP servers.

There seems to be a conflict with xinetd and inetd - once you install xinetd, inetd is disabled, effectively shutting down all of the services in inetd (LTSP uses 'ldminfod' and 'tftpd' under inetd to function). Obviously, thin clients were unable to boot after this.

Is there any way we can provide a line in inetd for this howto, for those who require it?

Also, as a (temporary) workaround, I used a program called "XWinLogon" - which is an XServer for Windows (free) which doesn't require any modification to the Linux installation as it's transport is XDMCP.

---

### Post by Fubarovic on 2007-09-14
I solved the dreadful endpoint error I got from xinetd by changing the color depth to 24 bits  (the same as the local desktop). I tried setting it to 8 bits to save network bandwidth but that gave me the endpoint errors.

---

### Post by chaeron on 2007-09-19
> **bouzzi said:**
> HI
 
1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

When I get there, I don't see nothing about XDMCP...

Is there an other way to enable XDMCP?


Go to System->Administration->Login Screen Setup and click on the Remote tab.  Then change the style to "same as local".  Then a button will appear on the bottom of the panel to Configure XDMCP, click that, disable "Honor Indirect Requests" and you're good to go, almost (see below!)

> **bouzzi said:**
> 
But in vncviewer I get a grey screen with X cursor giving me nothing to do but moving it...
i

You also need to do the following:


```
sudo gedit /etc/gdm/gdm.conf
```

then find this rule:

```
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
# RemoteGreeter=/usr/lib/gdm/gdmlogin

```

remove the '#' in the last line so there should be:

```
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
RemoteGreeter=/usr/lib/gdm/gdmlogin
```

You also have to change another part of the gdm.conf file. 

Look for the following piece of text in /etc/gdm/gdm.conf

```
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=false
```

Change the Enable=false to Enable=true

Then do a restart, and it should fix your grey screen issue. It did for me.

---

### Post by chaeron on 2007-09-19
I've gotten both Xvnc and x11vnc to work on Feisty following the advice in this thread.

However, when I use a viewer on mymachine:0, the VNC viewer does not ask for a password.  It blasts you right into the session.

Anyone figured out a way to configure x11vnc to force the entry of a password before making the VNC viewer connection?

Thanks!

---

### Post by chaeron on 2007-09-19
Solved it....to make x11vnc force the vnc viewer to enter a password, just add the following parameter to the server args line:

```
-rfbauth /root/.vncpasswd
```

Which means that the full /etc/xinetd.d/x11vnc file should look like:
```

service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg -rfbauth /root/.vncpasswd
        disable         = no
}
```

Marvelous!

---

### Post by chaeron on 2007-09-19
For those that are interested, I've created a PDF summary of this thread, with the key steps required to set up VNC on Ubuntu with resumable sessions, including getting access to the physical display (:0).

These are the steps I've taken on three Feisty machines, one real (system76 box) and two virtual (running under VMWare).

No AMD info in the file though, you'll have to scan the thread for AMD specific fixes I'm afraid.

[http://www.chaeron.com/software/SettingUpVNCOnUbuntu.pdf](http://www.chaeron.com/software/SettingUpVNCOnUbuntu.pdf)

Many, many thanks to all those that took the time to figure all this out!

Enjoy!

---

### Post by timander2002 on 2007-09-22
I followed this howto.  still I found that I am getting the gnome prompt, however, it continues to prompt me, first for the user name, then the password.  This repeats.

What am I doing wrong??

---

### Post by mongrol on 2007-09-22
4 hours into this and I've managed to get VNC started. However, I can't get the GDM login prompt up. I've went over the gdm.conf twice, enabled it in the login window control panel. All I get is the grey root window and the wristwatch mouse cursor.

---

### Post by lns on 2007-10-07
I've posted a quick alternative to using xinetd in this HOWTO. I was running into the problem of xinetd interfering with the default inetd and therefore LTSP functionality, so I coded Xvnc to launch via inetd.conf . Hope this helps anyone else in this situation.

[http://ubuntuforums.org/showthread.php?p=3489584#post3489584](http://ubuntuforums.org/showthread.php?p=3489584#post3489584)

---

### Post by swapmon on 2007-10-11
> **timander2002 said:**
> I followed this howto.  still I found that I am getting the gnome prompt, however, it continues to prompt me, first for the user name, then the password.  This repeats.

What am I doing wrong??

I ran into the same problem until I enabled multiple logins by the same user.

To change this setting navigate to System->Administration->Login Window. In the General tab uncheck the "Disable multiple logins for a single user" field.

After doing this I was able to login on the second attempt.

---

### Post by gtswanny on 2007-10-12
Argggh, I can't even get past the first step.

when I "sudo  apt-get install vnc4server"  all I get is the:

E: Couldn't find package vnc4server

This is a new 7.04 server install.  Up until this point I've had no problems finding and installing packages.  I have verified that sources.list is setup properly according to all tutorials I can find.   I have searched everywhere and I can't find any references to this problem, and now at wits end.  Any ideas? Thanks.

---

### Post by Hubris2 on 2007-10-15
Does anyone know if it's possible to transfer running applications from a VNC session back to display:0 ?  After I remote my box from work, I have to shut down all my apps and restart them on the local system.  Can the apps be moved between desktops like they can between virtual desktops on the physical display?

---

### Post by brianmrowe on 2007-10-16
> **mongrol said:**
> 4 hours into this and I've managed to get VNC started. However, I can't get the GDM login prompt up. I've went over the gdm.conf twice, enabled it in the login window control panel. All I get is the grey root window and the wristwatch mouse cursor.

I am having this exact same experience.  I can ssh -X into the box and launch the apps I want, but that is not really ideal.  I was hoping VNC would perform a little better than this.... which is really bad.  If not maybe I am wasting my time.  I'm using 7.04.  I can see xvnc started.  I get passed the vnc authentication succeeded.  It opens the screen and waits.  no gdm login.  IT dies eventually 
error says:
ReadFromRFBServer: rdr::EndOfStream.

---

### Post by kacheng on 2007-10-16
gtswanny: Make sure if you are using vnc4server that you use the '-extension XFIXES' parameter.

brianmrowe: Are you connecting to port 5901 or 5902, which are presumably the displays you configured in xvnc.conf?  5900 will not work, as that is the display used by the console.

---

### Post by gtswanny on 2007-10-17
> **kacheng said:**
> gtswanny: Make sure if you are using vnc4server that you use the '-extension XFIXES' parameter.



Thanks!  Actually my problem was universe was not turned on even though I *swear* I checked it.  I did use your paremeters as suggested.

I now have it all working per this tutorial and even upgraded the dist to Gutsy RC.

---

### Post by Distortedgamer on 2007-10-19
Is there away to enable XDMCP from CLI??? I am remoted in from work through SSH but I want to figure out how to connect with Desktop from a winXP machine. Thanks for the tutorial though!

---

### Post by gtr225 on 2007-10-21
How do I enable XDMCP in Ubuntu 7.10?

---

### Post by chaeron on 2007-10-21
> **gtr225 said:**
> How do I enable XDMCP in Ubuntu 7.10?

Same way as in Feisty.  Use the instructions I posted earlier.

---

### Post by gtr225 on 2007-10-21
> **chaeron said:**
> Same way as in Feisty.  Use the instructions I posted earlier.
Apparently I don't have that option.

---

### Post by chaeron on 2007-10-21
> **gtr225 said:**
> Apparently I don't have that option.

What are you doing on the Security tab?

The settings you need to make are on the General and Remote tabs only.

RTFM, carefully. ;-)

---

### Post by gtr225 on 2007-10-21
Isn't this what I'm supposed to do? 1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

---

### Post by chaeron on 2007-10-21
> **gtr225 said:**
> Isn't this what I'm supposed to do? 1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

Those were not my instructions, and are misleading.  Try downloading the PDF I posted, as it will give you step by step instructions, which worked fine for me on Gutsy, installing on 3 new machines yesterday.

Try this instead:

Go to System->Administration->Login Screen Setup and click on the Remote tab. Then change the style to "same as local". Then a button will appear on the bottom of the panel to Configure XDMCP, click that, disable "Honor Indirect Requests" and you're good to go, almost (see below!)

If you read the whole thread, maybe you wouldn't be having these troubles. ;-)

Like I said, RTFM.

---

### Post by roningaijin on 2007-10-22
I had problems after upgrading to gutsy.  I was getting the problem regarding the connection being refused that is posted about on the first page of this thread.  I couldn't find a solution, so I kept experimenting until I got it to work.

I found this by trying to execute the same page the xinetd daemon is trying to execute when it starts Xvnc.  It said something about a font called "Fixed" not being found.

Try executing this to see if an error comes up:
```
 sudo Xvnc :2 -query localhost -geometry 1280x800 -depth 16 -once  -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES

```

It turns out that Gutsy moved my fonts from  /usr/share/X11/fonts/misc here to /usr/share/fonts/X11/misc.  I correct the "-fp /usr/share/X11/fonts/misc" option in the Xvnc.conf file, and it works fine now. Here is my Xvnc.conf:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1280x800 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```

---

### Post by turbotom on 2007-10-26
I had vnc4server working wonderfully in Feisty, then I upgraded to Gutsy (I can't resist upgrading) and now I get the damned gray screen with the X cursor!

The Xvnc config file has the changed font directory and xfixes arguments that Feisty needed.

I'm sure others, who are smarter than me, ran into this problem.

---

### Post by Jose Catre-Vandis on 2007-10-27
Been successfully using this howto for some time, until I upgraded to Gutsy on my host machine. Found that with Compiz enabled I could not enter a password in the authentication box. Vnc-ing without compiz and from other machines works fine.

installed xtightvncviewer from the repos and then using the command
```
xtightvncviewer myserver:1
```
gave me back a working password box

---

### Post by sefs on 2007-10-30
1) left click in the field you cannot set focus too and keep depressed
2) click on the right mouse button with left mouse button still depressed, and release right mouse button and left mouse button
3) cursor will magically appear in pesky field
4) type in password

This should work 100% of the time, and as you get nimble with it ... it would be like performing a single left click as one should

---

### Post by giruzz on 2007-11-01
> **turbotom said:**
> I had vnc4server working wonderfully in Feisty, then I upgraded to Gutsy (I can't resist upgrading) and now I get the damned gray screen with the X cursor!

The Xvnc config file has the changed font directory and xfixes arguments that Feisty needed.

I'm sure others, who are smarter than me, ran into this problem.


Same here.
Any suggestions? I tried a couple of things and didn't work...

g.

---

### Post by corvuscorax on 2007-11-07
I also had my Terminal Server Client using VNC setup under feisty, and it also broke under Gutsy with compiz enabled, making it impossible for the password box to get focus.  I found after some experimentation that if, after the password prompt is up, you open the network tools and ping the box you want to connect to, that the password field will then allow get focus to be set.

---

### Post by Linuxnz on 2007-11-11
Can someone tell me if Realvnc should work ok with Gutsy Ubuntu?  I have followed this thread and set up the standard Realvnc and I cannot get it work. xinetd is working fine, netstat has all the right stuff, go to connect (locally with vncviewer) and 10061, connection refused or reset.

Set vncpasswd etc, still no joy.  I do notice there is no Xvnc process in the ps -ef report, but assume I would only see that if I had a stable connection? 

Have set up Realvnc fine on Kubuntu (originally Feisty upgraded to Gutsy), without xinetd, just manual start ie; running vncserver command.  Have x11vnc working fine on Xubuntu (Feisty) box.

Is there any / much difference between standard Realvnc and vnc4server?  Should I just deinstall Realvnc and reinstall vnc4server?

Any other ideas on how I can trouble shoot the set up?  

Any help much appreciated  - Chris NZ

---

### Post by kingjm on 2007-11-12
I am uding dapper lts and your [directions]("http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc&page=12") worked excellent!

Is there a way to use a display model where one login will be 1024x768 and another at 800x600 and so on? I know that I can change the resolution in the xvnc configuration file. This could be useful when loging in with vnc and using display =0 or =1 or =2 and so on.

Could use brackets perhpas
```
service Xvnc
{
     type = UNLISTED
     disable = no
     socket_type = stream
     protocol = tcp
     wait = yes
     user = root
     server = /usr/bin/Xvnc
     
     if port = 5901
          {
          server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
          }
     if port = 5902
          {
          server_args = -inetd :1 -query localhost -geometry 800x600 -depth 24 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
          }
     else port = 5900
          {
          server_args = -inetd :1 -query localhost -geometry 800x600 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
          }
}
```I don't know but any thoughts

---

### Post by BassKozz on 2007-11-20
I am having trouble getting this to work, I followed these instructions and when I try and connect from my WinXP box using TightVNC I get the following error message:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/ScreenShot28.jpg[/IMG]
Any ideas?
Thanks again,
-BassKozz

---

### Post by fatmcgav on 2007-11-21
HI there, 

I managed to get this working using the following [guide]("http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/"), however i've now got a slightly weird bug.

When i connect on :1, it gives me the login screen, and i can login fine.

Once i'm logged in however, the menu at the top doesnt work - so i cant get to applications, places, power button etc...

Any ideas why???

Cheers
Gavin

---

### Post by deep75 on 2007-11-21
Hi!
I'm a Ubuntu newbie, with this guide I set up my linux box for remote VNC session :) thank's !!!

I have a little problem, occasionally I put a CD or USB key in the remote machine, but I can't mount them without log in locally. Is possible to mount device remotely? 

Because the remote pc have no monitor nor keyboard and mouse.. so it's quite difficult for me log in locally :)

I control with tightVNC on windows xp machine  (...for now...)

THNX

---

### Post by ResumeMan on 2007-11-22
Well I *think* I did everything according to the pdf instructions. All seems to go ok but when I try to connect from the server computer (localhost:1) I get a "connection refused (111)" error.

I tried revising my Xvnc.conf file per roningaijin, but that didn't seem to help.

Anything obvious I'm doing wrong? FWIW, I'm using gOS, not regular Ubuntu, but I don't think that should matter much, should it?

---

### Post by ResumeMan on 2007-11-22
Er, I don't think I ever actually RAN vncserver on the host machine before #-o

Now I'm able to access it but am getting the infamous gray screen and black X. Off to research that one...

---

### Post by Skip Da Shu on 2007-11-23
> **Tichondrius said:**
> ```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

```

For my Xubuntu Gutsy 7.10 the server arg for fonts in Xvnc needed to be```
-fp /usr/share/fonts/X11/misc
```

---

### Post by BassKozz on 2007-11-23
> **B/-\ssKozz said:**
> I am having trouble getting this to work, I followed these instructions and when I try and connect from my WinXP box using TightVNC I get the following error message:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/ScreenShot28.jpg[/IMG]
Any ideas?
Thanks again,
-BassKozz

Since I haven't heard anything I went ahead and installed UltraVNC and RealVNC to see if I might have better luck with one of those clients, here are the results...

[CENTER][SIZE="5"]**_UltraVNC_**[/SIZE]

[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/UltraVNC1.jpg[/IMG]
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/UltraVNC2.jpg[/IMG]
[SIZE="5"]**_RealVNC_**[/SIZE]

[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/RealVNC1.jpg[/IMG]
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/RealVNC2.jpg[/IMG][/CENTER]

I can't figure out for the life of me what I am doing wrong here... I am trying to connect to the box on my local LAN, but I setup port forwarding anyways and tried to connect via my WAN IP address and got the same results.  On another note, I was able to get Xming working perfectly, but I can't get an answer on [whether or not I can use Xming as a "Full Desktop Environment"/VNC replacement](http://ubuntuforums.org/showthread.php?t=619611)?

Please someone help me here... I can't even do a simple VNC connection from the actual machine I am on ```
vncviewer localhost:1
``` it gives me a ```
CConn:       connected to host localhost port 5901
 main:        read: Connection reset by peer (104)
```
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/VNC-104error.png[/IMG]:(

PLEASE SOMEONE HELP

---

### Post by Skip Da Shu on 2007-11-23
> **ResumeMan said:**
> Er, I don't think I ever actually RAN vncserver on the host machine before #-o

Now I'm able to access it but am getting the infamous gray screen and black X. Off to research that one...
Well let us know because that's where I ended up also so I went back to my kludge 2 step x11vnc setup detailed [HERE]("http://ubuntuforums.org/showthread.php?t=42941&page=10&highlight=autostarted") in post #96.

---

### Post by knoid on 2007-12-04
I'm having exactly the same problem as you guys. I followed all the instructions at [http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html) to set this up.

I can connect OK if I just run vnc4server on it's own:

```
sudo vnc4server -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
```

With the above, I can connect successfully with any VNC client.

So then I kill vnc4server (sudo vnc4server -kill :1; sudo killall Xvnc; sudo killall xinetd) and sudo /etc/init.d/xinetd start.

sudo netstat -tap | grep xinetd reveals that xinetd is listening on port 5901as expected.

On connecting I get the exact same messages as posted by Baskozz above.

Looking in syslog (which I wouldn't have thought to do without this post: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)) for xinetd events I get the following:

```
Dec  3 09:03:13 Vault xinetd[7172]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Dec  3 09:03:13 Vault xinetd[7172]: Started working: 1 available service
Dec  3 09:03:24 Vault xinetd[7173]: warning: can't get client address: Transport endpoint is not connected
```

Several hundred instances of the "transport endpoint" line follow, then:

```
Dec  3 09:03:24 Vault xinetd[7222]: warning: can't get client address: Transport endpoint is not connected
Dec  3 09:03:24 Vault xinetd[7172]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Dec  3 09:03:34 Vault xinetd[7172]: Activating service Xvnc
Dec  3 09:03:36 Vault xinetd[7223]: warning: can't get client address: Transport endpoint is not connected

```

So when I connect to 5901, xinetd is attempting to launch the Xvnc server but it all goes pear-shaped....why?

---

### Post by digitalhack on 2007-12-23
knoid,

Your problem could the same one I had.  In EDIT2 grumpymole says to append "-extensions XFIXES" to the server_args.  I had to change this to "-extension XFIXES" with no "s".

In /etc/xinetd.d/Xvnc the server_args line in my configuration is:

server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES

Note that all server_args must be on the same line and not broken like they may be in this post.

Hope this helps,

Greg D
digitalhack

---

### Post by giruzz on 2007-12-25
> **digitalhack said:**
> knoid,

Your problem could the same one I had.  In EDIT2 grumpymole says to append "-extensions XFIXES" to the server_args.  I had to change this to "-extension XFIXES" with no "s".

In /etc/xinetd.d/Xvnc the server_args line in my configuration is:

server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES

Note that all server_args must be on the same line and not broken like they may be in this post.

Hope this helps,

Greg D
digitalhack

I've just updated my parents' PC and I lot the gray screen to get the same error as knoid. Unfortunately your suggestion doesn't work.

g.

---

### Post by giruzz on 2007-12-30
> **knoid said:**
> I'm having exactly the same problem as you guys. I followed all the instructions at [http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html) to set this up.

I can connect OK if I just run vnc4server on it's own:

```
sudo vnc4server -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
```

With the above, I can connect successfully with any VNC client.

So then I kill vnc4server (sudo vnc4server -kill :1; sudo killall Xvnc; sudo killall xinetd) and sudo /etc/init.d/xinetd start.

sudo netstat -tap | grep xinetd reveals that xinetd is listening on port 5901as expected.

On connecting I get the exact same messages as posted by Baskozz above.

Looking in syslog (which I wouldn't have thought to do without this post: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)) for xinetd events I get the following:

```
Dec  3 09:03:13 Vault xinetd[7172]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Dec  3 09:03:13 Vault xinetd[7172]: Started working: 1 available service
Dec  3 09:03:24 Vault xinetd[7173]: warning: can't get client address: Transport endpoint is not connected
```

Several hundred instances of the "transport endpoint" line follow, then:

```
Dec  3 09:03:24 Vault xinetd[7222]: warning: can't get client address: Transport endpoint is not connected
Dec  3 09:03:24 Vault xinetd[7172]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Dec  3 09:03:34 Vault xinetd[7172]: Activating service Xvnc
Dec  3 09:03:36 Vault xinetd[7223]: warning: can't get client address: Transport endpoint is not connected

```

So when I connect to 5901, xinetd is attempting to launch the Xvnc server but it all goes pear-shaped....why?

got any luck?

g.

---

### Post by xxbill420xx on 2008-02-01
Well, I've read through this whole thread and I can't seem to solve the problem I'm having... I have attached a screen shot showing what my VNC- Viewer screen pulls up when I try to log in.   It is a gray box with a console stuck in it!  Strange I know :-/  If anyone has any ideas let me know please.
[URL="http://img171.imageshack.us/img171/1099/vnchelpge6.png"]
http://img171.imageshack.us/img171/1099/vnchelpge6.png[/URL]

Originally I tried a variety of methods to get this running.  On the server I am attempting to make it work it is running the latest distro of Ubuntu.  It is running the desktop version and already has a X11 window system working and in place.  However the problem lies in the fact I do not have a monitor to run on that machine, which is why I was hoping to get this working on it.

Oh something else to note, whenever I would try and connect to the VNC server on port 5900 or 5901 it would accept the connection, and then crash disabling further connections.  To get this far I ran a netstat and noticed I was listening for connections on 5900, 5901 and 5902.  Where the 5902 came from I have no idea, but that is the one I connected to where it gives me the image shown in the screenshot.  
Thanks

Console output attached below (in bold is when it crashes)
For Client:
```
nimda@nimda:~$ vncviewer 192.168.1.2:5901
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
**ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)**
nimda@nimda:~$ vncviewer 192.168.1.2:5902
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password: 
VNC authentication succeeded
Desktop name "nimda-server:2 (root)"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Using shared memory PutImage
Throughput 10000 kbit/s - changing from 8bit
Using viewer's native pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Throughput 11944 kbit/s - changing to Hextile
```

---

### Post by lns on 2008-02-01
I would recommend you follow my instructions - not sure if you can "start over" but I have set up many installs exactly like I have in my instructions and it works great (you don't even have to replace inetd with xinetd)...

[http://ubuntuforums.org/showthread.php?t=569451](http://ubuntuforums.org/showthread.php?t=569451)

HTH,
Jordan


> **xxbill420xx said:**
> Well, I've read through this whole thread and I can't seem to solve the problem I'm having... I have attached a screen shot showing what my VNC- Viewer screen pulls up when I try to log in....

...


---

### Post by xxbill420xx on 2008-02-01
Wow, thank you very much for your prompt response! 
I am trying your instructions now and will report back with the results.

Shoot, already noticed a problem... I don't have a monitor so I can't access the menus where you have 
```

1 ) Enable XDMCP
- System->Administration->Login Screen Setup
- Tab Remote -> Style = "Same as local"
- Bottom button XDMCP (still in Remote) --> You can disable "Honor Indirect Requests" if you'd like.

```
> **lns said:**
> I would recommend you follow my instructions - not sure if you can "start over" but I have set up many installs exactly like I have in my instructions and it works great (you don't even have to replace inetd with xinetd)...

[http://ubuntuforums.org/showthread.php?t=569451](http://ubuntuforums.org/showthread.php?t=569451)

HTH,
Jordan

---

### Post by Footer on 2008-02-01
Could your problem be as simple as this:

[http://www.realvnc.com/support/faq.html#grey](http://www.realvnc.com/support/faq.html#grey)

Specifically:

"Why do I just get a grey desktop in my Unix VNC Server?"

Granted, this is Linux vs. UNIX but there isn't THAT much of a difference!

Good luck!

---

### Post by lns on 2008-02-01
I'm not sure where the settings are, but with most/all things Linux, GUI tools are merely front-ends for back-end configuration files. Not sure if the the XDMCP stuff is stored in GCONF or in /etc/gdm/gdm.conf, but just poke around, you're sure to find it somewhere.

Good luck! I highly recommend using my method as I have tested it a lot and haven't run into any issues (yet..knock on wood) ;)

> **xxbill420xx said:**
> Wow, thank you very much for your prompt response! 
I am trying your instructions now and will report back with the results.

Shoot, already noticed a problem... I don't have a monitor so I can't access the menus where you have 
```

1 ) Enable XDMCP
- System->Administration->Login Screen Setup
- Tab Remote -> Style = "Same as local"
- Bottom button XDMCP (still in Remote) --> You can disable "Honor Indirect Requests" if you'd like.

```

---

### Post by Skip Da Shu on 2008-02-01
> **Linuxnz said:**
> Can someone tell me if Realvnc should work ok with Gutsy Ubuntu?  I have followed this thread and set up the standard Realvnc and I cannot get it work. xinetd is working fine, netstat has all the right stuff, go to connect (locally with vncviewer) and 10061, connection refused or reset.

Set vncpasswd etc, still no joy.  I do notice there is no Xvnc process in the ps -ef report, but assume I would only see that if I had a stable connection? 

Have set up Realvnc fine on Kubuntu (originally Feisty upgraded to Gutsy), without xinetd, just manual start ie; running vncserver command.  Have x11vnc working fine on Xubuntu (Feisty) box.

Is there any / much difference between standard Realvnc and vnc4server?  Should I just deinstall Realvnc and reinstall vnc4server?

Any other ideas on how I can trouble shoot the set up?  

Any help much appreciated  - Chris NZ

I don't know how relevant this is but when I was setting up x11vnc for remote, resumable sessions I found that some display drivers would not work.  While I no longer have the exact error message from the log it was something about the serial id, I think of the framebuffer.  It seems, guesswork now, that some of the display drivers were addressing a different framebuffer or accessing it differently.  This was resolved by running ```
dpkg-reconfigure xserver.org
```  specifying the VESA driver, instead of the hardware specific driver the install had used and selecting the kernel framebuffer option.  I have several machines now running headless under Xubuntu (Gutsy) and x11vnc.  I've used a couple different viewers to get to the 'remote' machines w/o problems.

---

### Post by webwolf_3000 on 2008-02-10
:popcorn:

overall good guide, only problem I realy have - and probably cannot figure out, when I connect the viewer - I just get a grey chequered screen with a black X cursor ( this is true on the local machine and the remote machine )

Any idea where Im going wrong here ?

---

### Post by chelrob on 2008-02-24
After working on this all weekend I finally got it up and running using this guide: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

There were two differences though.

1 . My gdm.conf was not in the specified location.  It was located  here ```
/etc/xdg/xubuntu/gdm/gdm.conf
```

2. I did have to reboot before the Remote Greeter started working.  Stopping and restarting the services didn't work for me.

[IMG]http://www.invisionweb.net/VNC.jpg[/IMG]

I can remote to the Ubuntu box with VNC from any windows Vista or XP Pro PC on my home netwrok.

---

### Post by Skip Da Shu on 2008-02-24
> **chelrob said:**
> 
1 . My gdm.conf was not in the specified location.  It was located  here /etc/xdg/xubuntu/gdm/gdm.conf


That's strange... my Xubuntu, Gutsy, 64bit install put these two here:
```
/etc/gdm/gdm.conf
/etc/gdm/gdm/conf-custom
```

They both needed the "killinitclient" under [daemon] tweaked before i got x11vnc working.

---

### Post by chelrob on 2008-02-24
The guide I followed had me looking here for gdm.conf.  But it was not found there on my system.
```
/etc/X11/gdm/gdm.conf 
```

I also had this one too. But making changes to this file had no impact.
```
/etc/gdm/gdm.conf
``` 

Only tweaking this file made a difference.
```
/etc/xdg/xubuntu/gdm/gdm.conf
```

---

### Post by BB34 on 2008-02-26
Hi guys sorry to bother but whats the command to uninstall this VNC setup(Page 1). 

Thanks,

---

### Post by chelrob on 2008-02-27
Well to uninstall the vnc server and xinetd packages you would type: 
```
sudo apt-get remove vnc4server xinetd
```

The other thing you would do is delete the file you created:
```
sudo rm /etc/xinetd.d/Xvnc
```

Just follow the procedure in reverse order from step 4 down to step 1.


Check her for instructions on how I got it to work: [http://ubuntuforums.org/showpost.php?p=4398393&postcount=390](http://ubuntuforums.org/showpost.php?p=4398393&postcount=390)

---

### Post by BB34 on 2008-02-27
Hey Thanks Alot Man I Sucessfully Remove the VNCviewer.

I will be checking your guide and see if it will work for me.For Now My brain is alittle bit fried since my last failed attempts and also im new to linux.

I Appreciate Your Help.

Adrian Lopez

---

### Post by chelrob on 2008-02-28
You're welcome.  Glad I could help.  Btw, it's not my guide, just a guide I followed that worked for me.

Take care.

---

### Post by BartInTN on 2008-02-28
Good how-to... but needs to be updated.  I'm running Gutsy 7.10 and vnc4server 4.1.1.

XDMCP can be enabled under the Login Window Prefs, Remote tab

And the Xvnc files should have this instead:
server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES

---

### Post by chelrob on 2008-02-28
@BartInTN 

```
server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
```

That's what worked for me.  This guide has the updates you mentioned: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/) :)

---

### Post by prioret on 2008-02-29
HELP!!

I've been messing with this for a while, and gave it serveral tries.

I'm running 7.10 and followed all the directions. I'm also running vnc4server, so the X bugs are fixed.

When I connect to my system, I get the VNC password prompt, enter it, and the session is closed with this error:

[INDENT]VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri Feb 29 17:42:20 2008
 CConn:       connected to host localhost port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8

Fri Feb 29 17:42:25 2008
 main:        End of stream
[/INDENT]

Any ideas? im pulling my hair out.
Tom

---

### Post by chelrob on 2008-03-04
> **prioret said:**
> HELP!!

I've been messing with this for a while, and gave it serveral tries.

I'm running 7.10 and followed all the directions. I'm also running vnc4server, so the X bugs are fixed.

When I connect to my system, I get the VNC password prompt, enter it, and the session is closed with this error:

[INDENT]VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri Feb 29 17:42:20 2008
 CConn:       connected to host localhost port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8

Fri Feb 29 17:42:25 2008
 main:        End of stream
[/INDENT]

Any ideas? im pulling my hair out.
Tom

The guide at the start of this thread does not work for Ubuntu 7.10.

Try this guide: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)
It worked for me.

Read here for my comments on following that guide: [http://ubuntuforums.org/showpost.php?p=4398393&postcount=390](http://ubuntuforums.org/showpost.php?p=4398393&postcount=390)

---

### Post by chelrob on 2008-03-06
Does anyone know how to start a second VNC session that also goes to the remote greeter instead of using my *home/username/.vnc/xstartup *preference?  Can I modify gdm.conf  or xstartup to envoke another remote greeter when I VNC to <server IP>:2?

Currently my xstarup starts gnome desktop when I VNC to <server IP>:2.
Thanks!

---

### Post by Linuxnz on 2008-03-08
Hey guys just trying to get basic vnc4server going at the mo before auto start. 

Had RealVNC loaded but could not get this to work properly.  Everything worked ok except the keyboard characters were wrong. so deinstalled and install vnc4server.

No mostly working, but get vnc client screen with xterm window only wiht a command line prompt in top left hand corner of screen.  Cannot see graphical desktop. If I exit xterm by typing "exit" at command line I get a screen with check boxes saying "Accept clipboard from viewers" "Send clipboard to viewers" and "Send primary selection to viewers". 

I guess I am not starting the correct gdm for some reason.  Log file as below. Not sure if errors are serious as I have not moved /installed fonts etc

Any ideas where to check?

Thanks

Log file output shows minor font errors;

[email]chris@maxii:~/.vnc[/email]$ cat maxii:2.log

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Sun Mar  9 10:02:29 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
/home/chris/.vnc/xstartup: 12: twm: not found

Sun Mar  9 10:02:38 2008
 Connections: accepted: 192.168.1.21::1250
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)

Sun Mar  9 10:02:41 2008
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 8 (8bpp) rgb max 3,3,3 shift 4,2,0

Sun Mar  9 10:03:09 2008
 Connections: closed: 192.168.1.21::1250 (Clean disconnection)
 SMsgWriter:  framebuffer updates 2
 SMsgWriter:    ZRLE rects 3, bytes 591
 SMsgWriter:    raw bytes equivalent 786980, compression ratio 1331.607445

---

### Post by chelrob on 2008-03-11
Sounds like you need to edit your */home/username/.vnc/xstartup* file to launch a graphical desktop.

Just google *xstarup and gnome* or *xstarup and KDE* to find examples of how to edit xstartup.

Here's a my xstartup:
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
vncconfig -iconic &
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#twm &
gnome-session &
#xfce4-session &
#startkde &

```
I have examples there for Gnome, KDE, and Xfce4.

---

### Post by Linuxnz on 2008-03-17
Yep, that did it alright.  All fixed.

Thanks Chelrob.

Much appreciated.

Ubuntu forums as always such a great community.

:)

---

### Post by keninem on 2008-03-17
Hi all..been reading this thread and have gotten pretty far..I am running Ubuntu 7.10 desktop, and am having the following problem:

I don't have the gdm.conf file at ALL where it references in the guide..the ONLY place I have it is /etc/gdm/gdm.conf  and I have modified that to be correct, but since it isn't working, I have to wonder if that's the reason..what, if anything, do I need to install to get the full path that is in the guide?

When I manually run the Xvnc command, I can VNC remotely, and get the passwd prompt..when I enter that, I get the pixelated screen with the grey "X" as the mouse curser, nothing else..

When I try and let xinetd take care of it, I get "Connection reset by Peer" for the first attempt(with no passwd prompt)
and if I try to reconnect, I get "Connection refused"

Any help with this would be greatly appreciated..I've read so many guides my head is spinning!

---

### Post by chelrob on 2008-03-18
> **Linuxnz said:**
> Yep, that did it alright.  All fixed.

Thanks Chelrob.

Much appreciated.

Ubuntu forums as always such a great community.

:)

You're welcome :)

---

### Post by chelrob on 2008-03-18
@kenimen
Are you following this guide: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

Check out my comments here: [http://ubuntuforums.org/showpost.php?p=4398393&postcount=390](http://ubuntuforums.org/showpost.php?p=4398393&postcount=390)

Try this command to find all gdm.conf files on your system...
```
sudo find / -name 'gdm.conf'
```

---

### Post by keninem on 2008-03-18
> **chelrob said:**
> @kenimen
Are you following this guide: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

Check out my comments here: [http://ubuntuforums.org/showpost.php?p=4398393&postcount=390](http://ubuntuforums.org/showpost.php?p=4398393&postcount=390)

Try this command to find all gdm.conf files on your system...
```
sudo find / -name 'gdm.conf'
```

Yes, I followed both of those actually..and the path for gdm.conf that you and the website are talking about doesn't exist on my machine..
:confused:

---

### Post by keninem on 2008-03-18
is anyone else running into this issue, or am I the lucky one?:(

---

### Post by chelrob on 2008-03-18
What OS is the client PC running?

Are you just opening the VNC client and typing *<server IP> :1*?
Example:
```
172.16.1.102:1
```

---

### Post by keninem on 2008-03-18
> **chelrob said:**
> What OS is the client PC running?

Are you just opening the VNC client and typing *<server IP> :1*?
Example:
```
172.16.1.102:1
```


I have tried it from the local ubuntu box and from the remote Vista box..

and yes, that's what I'm doing..tried :1 and :2

---

### Post by chelrob on 2008-03-18
To use :2 you first have to ssh to the server and start another vnc session before you start the vnc client.
```
vncserver :2
```

Then run the client.  If you don't get a graphical desktop check out my xstartup file a few posts back.

When you're done you have to kill the session after you close vnc client.
```
vncserver -kill :2
```

---

### Post by keninem on 2008-03-20
I set my xstartup to look like that and am still having the same problem.. :(

---

### Post by chelrob on 2008-03-20
Try backing out all the chagnges from the tutorials, delete any files it had you create, and just install the VNC server.  See if you can connect after that and see the graphical desktop.

---

### Post by keninem on 2008-03-20
Thanks, that actually worked!  I have no idea what caused it to stop/start working though unfortunately..


Now what is the easiest way to get this to start on boot? Can anyone clear that up? I tried adding it in /etc/rc.local but it didn't start properly..

---

### Post by chelrob on 2008-03-20
You're welcome.

---

### Post by anemptygun on 2008-03-21
Is this still the most efficient way to set up VNC? I am on 8.04 beta and I am trying to set up a vnc server. Anyone have an opinion on this?

---

### Post by Tu13erhead on 2008-03-22
> **anemptygun said:**
> Is this still the most efficient way to set up VNC? I am on 8.04 beta and I am trying to set up a vnc server. Anyone have an opinion on this?

+1.  I'd like to know this as well.

Thanks!

---

### Post by kindofabuzz on 2008-03-30
I'm not gonna read this whole thread to see if someone posted this fix but here's how i got mine running: 

in /etc/xinetd.d/Xvnc, the part where it mentions fonts should be:

[COLOR="Red"]/usr/share/fonts/X11/misc[/COLOR] and not /usr/share/X11/fonts/misc

at least in gutsy it is

---

### Post by chelrob on 2008-03-30
> **anemptygun said:**
> Is this still the most efficient way to set up VNC? I am on 8.04 beta and I am trying to set up a vnc server. Anyone have an opinion on this?

Go back about 4-5 pages and you will find the answer to your question.  Look for my first post in this thread.

---

### Post by kindofabuzz on 2008-03-31
> **Tu13erhead said:**
> +1.  I'd like to know this as well.

Thanks!

yes, just do exactly what the very first post says, but change 
/usr/share/X11/fonts/mic to /usr/share/fonts/X11/misc in Xvnc

---

### Post by Virtual_Ron on 2008-03-31
Hi,

I'd like to run vnc4server manually (without xinetd).    I just run "vnc4server" from the command line and it works fine.    But, it defaults to port 5901.     Anyone know how I can change that port number?

Thanks,
Ron

---

### Post by Virtual_Ron on 2008-04-01
thngs that go "**bump**" in the night

---

### Post by wareagle on 2008-04-01
I set this up and it doesn't let me connect to a display if another host is connected to the same display.

I have "disable multiple logins for a single user" unchecked in my "Login Window" options.

This is mainly a problem because if I am connected and the connection dies, I am unable to resume the session I was on.

---

### Post by anemptygun on 2008-04-01
> **chelrob said:**
> Go back about 4-5 pages and you will find the answer to your question.  Look for my first post in this thread.
thx

---

### Post by Gujs on 2008-04-02
Hello,

I have instaled Ubuntu 8.04 beta and I have a lot of problems with Xvnc on separate display :1. My xinetd config for Xvnc:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1280x1024 -depth 16 -fp /usr/share/fonts/X11/misc PasswordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```

Gnome is always changing theme from Clearlooks to Human and back. I think that my gnome settings daemon is crashing all the time. How can I disable to load it at all, or even better fix this problem. Where can I get some logs from daemon, that I would easier find the problem!

Thanks

---

### Post by popie on 2008-04-02
@Gujs:

Not sure if this will help, as I'm still on 7.10, but VNC server is working fine. My server_args line in the Xvnc file is slightly different from yours:

```
 server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES

```

---

### Post by Gujs on 2008-04-03
Sorry for not reporting that. I had these options in the server_args and I removed them with hope that it will work better, but it is actually the same thing.

Before I had also Ubuntu 7.10 and it worked great, but on 8.04 beta it doesn't work any more!

---

### Post by FoolsRun on 2008-04-14
Hi,
I have a fresh Hardy install and I've followed this guide exactly (and tried a number of tweaks elsewhere in the thread) and I continue to get the "gray screen with X cursor" issue.

Clearly VNC is working, but it's either not launching GDM/gnome-session, or not talking to it somehow.

Could it be relevant that I run my Hardy server headless without a user logged in to GNOME? Since Xvnc is looking for ~/.vnc/xstartup and I'm not logged in to GNOME, how would it know which home directory to get xstartup from? Is there a default location for xstartup (or can I redirect it?) for when Xvnc is starting before login?

---

### Post by BurakkuChi on 2008-04-25
> **Gujs said:**
> Hello,

I have instaled Ubuntu 8.04 beta and I have a lot of problems with Xvnc on separate display :1. My xinetd config for Xvnc:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1280x1024 -depth 16 -fp /usr/share/fonts/X11/misc PasswordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```

Gnome is always changing theme from Clearlooks to Human and back. I think that my gnome settings daemon is crashing all the time. How can I disable to load it at all, or even better fix this problem. Where can I get some logs from daemon, that I would easier find the problem!

Thanks

Gujs, apparently gnome-settings-daemon is having an issue with the keyboard plugin.

Run gconf-editor and go to apps->gnome_settings_daemon->plugins->keyboard. Then uncheck "active."

There's currently a bug report out for this at [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245)

---

### Post by concite on 2008-04-27
OK - I had the same problem.  Upgraded from Gutsy to Hardy, and VNC went haywire.  

Following advice:

Run gconf-editor and go to apps->gnome_settings_daemon->plugins->keyboard. Then uncheck "active."

Fixed the major problem.  Now, I still have the problem that VNC is REALLY slow. REALLY REALLY slow.  When I was using Gutsy, it was great.

Any thoughts?  Only change was to upgrade Ubuntu.

---

### Post by concite on 2008-04-27
OK - a little more research.  If I use the built in VNC server (port 5900) I can use VNC, and speed is acceptabe, but not good.  This also requires that I log in to the box locally first.  I am trying to create a headless machine, so that defeats the purpose.

I read somewhere that vnc4server was "broke" for Hardy and they suggested I use tightvncserver.  Installed that, ran it, get a grey screen with a terminal.  No Gnome session.

I could use help to either:

1) fix VNC4server so it is not so slow
or
2) help setting up tightvncserver si that I get a gnome session.

Thanks again.

---

### Post by hernejj on 2008-04-29
> **concite said:**
> OK - I had the same problem.  Upgraded from Gutsy to Hardy, and VNC went haywire.  

Following advice:

Run gconf-editor and go to apps->gnome_settings_daemon->plugins->keyboard. Then uncheck "active."

Fixed the major problem.  Now, I still have the problem that VNC is REALLY slow. REALLY REALLY slow.  When I was using Gutsy, it was great.

Any thoughts?  Only change was to upgrade Ubuntu.


I have the EXACT same problem.  I had Xvnc working perfectly under Gutsy... I could watch video in a vnc session and the framerate was 25-35 fps.  Now that I've done a fresh install of Hardy Xvnc is really slow :-/  So slow that Scrolling in Nautilus is painful!!

Can anyone suggest a solution to this?  I think, in the meantime, I may try tightvnc or something else... will post if I discover anything new.

---

### Post by hernejj on 2008-04-29
OK new info... both Xvnc and xtightvncserver exhibit the same odd slowness in Nautilus and Firefox.  In both applications scrolling within a VNC session is extremely slow and unresponsive.  Gnome menus are also slow to appear and slow to populate, window resizing is slow.  However, I find that I can play DVD ripped video files at close to perfect frame rates just like when I had Gutsy installed....  The slowness was not a problem in Gutsy.

I'm at a loss on this one. :confused:

---

### Post by Skip Da Shu on 2008-04-29
> **hernejj said:**
> OK new info... both Xvnc and xtightvncserver exhibit the same odd slowness in Nautilus and Firefox.  In both applications scrolling within a VNC session is extremely slow and unresponsive.  Gnome menus are also slow to appear and slow to populate, window resizing is slow.  However, I find that I can play DVD ripped video files at close to perfect frame rates just like when I had Gutsy installed....  The slowness was not a problem in Gutsy.

I'm at a loss on this one. :confused:

I'm using X11vnc... different port on each remote machine (59xx) and haven't noticed any slow down (yet) with v8.04 of Xubuntu.

---

### Post by concite on 2008-04-30
More information.....

vnc4server will not work at all if I remove the -extension XFIXES argument
With XFIXES, I can log into the box remotely, multi-user works, but it is still too painfully slow to use

X11vnc works, but I have to log into the physical box first, and there is no multi user support

tightvncserver - still can't get anything but a grey screen and terminal

vino (the default server software) works on display 0.  Again, I have to log into the physical box first, and there is no multiuser support.

*****
Is is possible to roll back to Gutsy Gibbon?  Everything was working fine, I just upgraded "because it was there"

---

### Post by Skip Da Shu on 2008-04-30
> **concite said:**
> More information.....
X11vnc works, but I have to log into the physical box first, and there is no multi user support


I don't have to physically log into machine first here, using X11vnc server... don't know about multi user and I certainly didn't try to set it up for that.  

If any interest I can post my config file entries for X11vnc.

However I am running Xubuntu not Ubuntu.

Skip

PS:  I **DO** have the 'slower than molasses in winter' problem when I vnc into the x11vnc server on my wife's Ubuntu v8.04, 64bit desktop.

---

### Post by hernejj on 2008-04-30
New info again :) !!

A little back ground first.  I have my main user account, we'll call him userfoo.  I also have a second account called userbar.  I log userfoo in at my computer and use that as my main desktop account.  I want to be able to bring up a vnc session and log in userbar when I need that account.  

The slowness I have been referring to is NOT there for userbar if I log him in at my normal gdm login window.  It is only present when I log him in via the gdm that gets laucnhed for the vnc 'd display.

I suspect that this slowness in VNC my sessions (and probably yours too concite) is coming from something in the Gnome session... Very likely gnome-settings-daemon..

if you edit your ~/.vnc/xstartup file (make sure it is executable) and have it JUST start an xterm and then from that xterm you launch nautilus and gnome-panel then everything works perfectly!!  No slowdowns... ultra fast.  As is SHOULD be!  As it was in Gutsy :)

I believe that gnome-settings-daemon is causing the slowness because one time I logged userbar in via vnc and gnome-settings-daemon failed to start and everything was fast, as it is supposed to be.

So... if anyone knows how to further debug this... or how to completely stop the loading of gnome-settings-daemon PLEASE TELL!!  kill -9 doesn't even work.. it just keeps coming back to life.  In the meantime I'll keep playing with it and post what I find.

---

### Post by concite on 2008-04-30
Skip da Shu - it would help if you post your config files for X11vnc.   I can live without multiuser, but I would like to avoid having to log in to the physical machine.

Hernejj - I think you are on to something with the Gnome settings demon.  I originally had a message that it kept resetting until I turned off "active" on the keyboard.  Let me know if you get any further.

---

### Post by bubba on 2008-04-30
> **hernejj said:**
> New info again :) !!
...

So... if anyone knows how to further debug this... or how to completely stop the loading of gnome-settings-daemon PLEASE TELL!!  kill -9 doesn't even work.. it just keeps coming back to life.  In the meantime I'll keep playing with it and post what I find.

There is a bug here:  [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245)

If you are having issues, you need to let folks know about it so they will fix it.

---

### Post by Cerin on 2008-05-07
> **Tichondrius said:**
> So here's the complete list of steps that are required to set the VNC server that any user can login into and start a session...

These instructions didn't work at all for me. When testing locally with vncviewer, I get that "Refuse/Allow" prompt.

---

### Post by Skip Da Shu on 2008-05-07
> **concite said:**
> Skip da Shu - it would help if you post your config files for X11vnc.   I can live without multiuser, but I would like to avoid having to log in to the physical machine.

Hernejj - I think you are on to something with the Gnome settings demon.  I originally had a message that it kept resetting until I turned off "active" on the keyboard.  Let me know if you get any further.

I will post 'em up here (or post a link), later today or tonight.  The same setup worked on the Ubuntu desktop also.

The one Ubuntu v8.04 machine is very very slow via VNC.  It was OK pre-upgrade. I will try local login first and see if either account on it behaves any differently.

And I agree.. on to something because my Xubuntu v8.04 machines don't show this extreme sluggishness under any situation.

---

### Post by yeehawjared on 2008-05-07
Skip Da Shu, could you possibly write a new, quick how-to for people who just installed a fresh copy of hardy heron xubuntu 8.04?

I wouldn't go into great detail - just what packages you need, and what files need to be modified.  The original post hasn't been edited since February 20th, 2006 and 45 pages is a lot to read :)

I'm going to do a fresh xubuntu install tonight, if I get it working (maybe with your help) I can create a new thread / guide.

---

### Post by Skip Da Shu on 2008-05-07
> **Virtual_Ron said:**
> Hi,

I'd like to run vnc4server manually (without xinetd).    I just run "vnc4server" from the command line and it works fine.    But, it defaults to port 5901.     Anyone know how I can change that port number?

Thanks,
Ron 

Not with that server, but a workaround if using (at least) RealVNC viewer is to enter a ":1" after the remote machines name or ip in the viewer.  It'll add 5900 to that to come up with the port number to go to.  On other viewers you may have to add ":5901" after the host name / ip.

This works on both the Win and Linux version of RealVNC's viewer.

Skip

---

### Post by Skip Da Shu on 2008-05-07
> **yeehawjared said:**
> Skip Da Shu, could you possibly write a new, quick how-to for people who just installed a fresh copy of hardy heron xubuntu 8.04?

I wouldn't go into great detail - just what packages you need, and what files need to be modified.  The original post hasn't been edited since February 20th, 2006 and 45 pages is a lot to read :)

I'm going to do a fresh xubuntu install tonight, if I get it working (maybe with your help) I can create a new thread / guide.

I had already started... not quite a "fresh install" because I added too much history and too much detail for that... Should have 1st cut done shortly.

PS: Toooo late, must sleep, finish tomorrow.

PPS:Still proof reading but here's '[My Ubuntu/Xubuntu X11vnc setup]("http://www.skipsjunk.net/how-to/xubuntu04.html")' or 'The idiot's guide to X11vnc'... we can work that out later.

PPPS: At least one of the links in that html write up is wrong.  Should have them fixed in a couple hours.

PPPPS: Also slightly simplified and posted to DC team forum on [Guru Mountain]("http://guru-mountain.com/dcteam/forums/viewtopic.php?t=100").

---

### Post by Skip Da Shu on 2008-05-09
> **bubba said:**
> There is a bug here:  [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245)

If you are having issues, you need to let folks know about it so they will fix it.

Thanx for the link to the bug report... I need to incorporate that link into my x11vnc setup for idiots 'how-to'.

Also added link to my prior post... will be a couple more hours before I can set up a forum thread for questions on it.  This thread is too busy / popular to be mixing my x11vnc junk into it. I'll add a link to a thread into the HTML write up also.

---

### Post by Skip Da Shu on 2008-05-09
**_*Delete Me*_**

---

### Post by DexterLB on 2008-05-14
good
but can I use port 5431 or 5996 instead of 5901

P. S. when I do "vncviewer localhost:1" it says "connection reset by peer". Is that bad?

---

### Post by Skip Da Shu on 2008-05-14
> **DexterLB said:**
> good
but can I use port 5431 or 5996 instead of 5901

P. S. when I do "vncviewer localhost:1" it says "connection reset by peer". Is that bad?

If you're talking about the x11vnc setup... Think you can if those ports aren't reserved for something else, I've used 5800 and 5900 thru around 5950 at various times for various reasons.

If you're talking about the vnc4server setup this thread is REALLY about... I dunno.  I'm gonna drop adding further confusion here with my little x11vnc stuff.  I'll follow the x11vnc thread over [HERE]("http://guru-mountain.com/dcteam/forums/viewtopic.php?t=100") if there's something about it somebody wants me to try to answer.

I'll try the localhost : x thing later tonight when I can hook up a monitor to one of the "remote" machines.

---

### Post by bhe on 2008-05-18
Everything installs fine in my VPC, but when I try to connect from a terminal, I get the following:

> VNC Viewer Free Edition ...
Copyright ...
See [http://.](http://.)..

Mon May 19 ...
 CConn:     Connected to host localhost port 5901

And that's it, nothing happens, I don't get a login window.

I tried connecting from a different host (win xp) and the same thing happens, it connects, but no login window.
Does anyone know how I can solve this?

---

### Post by tmaleshafske on 2008-05-19
I have ubuntu Hardy 8.04 and am having issues with getting this working.  First off.  I couldn't find "Enable XDMCP" in the login screen setup menu.  The other place is in the gdm.config where you can enable it correct?   

Also your location for fonts is incorrect at least for hardy it should be /usr/share/fonts/X11/misc

2.  I cannot get connected.  It shows me the password screen and then it drops as soon as I put the password in.  I can see the process via netstat.  

this is the output of the log file


```
May 18 23:37:43 male001 xinetd[17740]: warning: can't get client address: Transport endpoint is not connected
tmaleshafske@male001:/etc/xinetd.d$ 



```


Here is a copy of my /etc/xinetd.d/Xvnc
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

```

Some assistance please.  I am missing something but I don't know what it is.  Let me know if you need any other outputs.  Also I don't have anything located /usr/share/X11/fonts/misc  which I know is one of my main problems.  which package installs those.   all i have is a /usr/share/X11/locale  which appears to include font sets.  

Thanks ahead of time for the help

---

### Post by Skip Da Shu on 2008-05-19
> **tmaleshafske said:**
> 
2.  I cannot get connected.  It shows me the password screen and then it drops as soon as I put the password in.

One swag you might try:

/etc/gdm/gdm.conf-custom
```

[daemon]
#
# Added KillInitClients, changed to =false - SRG
#
KillInitClients=false

[security]

```

---

### Post by samosamo on 2008-05-19
This tutorial is great, I never had GDM showing for VNC.  I think I like it.  Now, after closing VNC and reconnecting, why don't I get the login screen again?

If I close my VNC session and then walk away from the comp, someone else can open it up without it asking for a password.  I looked through gdm.conf and "man Xvnc" but I couldn't find anything to help me.

here is my config (modified)
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = nobody
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1280x768 -depth 16 -cc 3 -once -SecurityTypes=none -extension XFIXES -DisconnectClients=0 -NeverShared
        port = 5901
}

```

---

### Post by trdc on 2008-05-21
> **samosamo said:**
> If I close my VNC session and then walk away from the comp, someone else can open it up without it asking for a password

That is exactly what it is meant to do:

> **Tichondrius said:**
> It is also persistent, meanning that even if you disconnect the VNC client your X session will not end (unless you explicitly log out) and you can reconnect to the same session again.

---

### Post by chelrob on 2008-05-21
You have to log out from Ubuntu first if you want a log in acreen next time you use VNC... otherwise your session stays open, hence *resumable sessions*.

---

### Post by birgernator on 2008-06-18
I have followed all the instructions here using a xubuntu 8.04 machine and am in much the same place as Tmaleshafske in post 450.  the server seems to be listening on port 5901 but every time i try to connect to localhost i get a: 
Wed Jun 18 10:38:27 2008
 main:        End of stream
:confused:
browsing through var/log/auth.log I found:
Jun 18 10:04:05 VPNsrv02 gdm[5697]: PAM unable to dlopen(/lib/security/pam_gnome_keyring.so)
Jun 18 10:04:05 VPNsrv02 gdm[5697]: PAM [error: /lib/security/pam_gnome_keyring.so: cannot open shared object file: No such file or directory]
Jun 18 10:04:05 VPNsrv02 gdm[5697]: PAM adding faulty module: /lib/security/pam_gnome_keyring.so
Jun 18 10:04:05 VPNsrv02 gdm[5697]: pam_nologin(gdm:auth): cannot determine username

a quick search led me to [[COLOR="Red"]this[/COLOR]]("http://lists.alioth.debian.org/pipermail/pkg-gnome-maintainers/2008-January/041787.html") thread.  so I apt-get install libpam-gnome-keyring.  now the error does not appear in the log and instead of nothing happening after entering my pass word when i try vncviewer localhost:1, i get a winodow with black and white checkers and a watch for about 5 seconds.  then ends with the same end of stream error in the terminal.  

can anybody provide some insight into a 8.04 install?

---

### Post by birgernator on 2008-06-18
inside of the Auth log i am still getting
"pam_nologin(gdm:auth): cannot determine username" each time I try to login.  and when the login screen pops up, the username box is greyed out.  is this a setting I need to change?

---

### Post by chelrob on 2008-06-18
This tutorial was written two yeas ago for Ubuntu Edgy.

---

### Post by popie on 2008-06-20
Here are the instructions I use, and they work in v8.04.

[B]VNC Server w/Resumable Sessions on Ubuntu
Works in Ubuntu 7.04, 7.10, 8.04, and Mint 4 (Daryna)
[/B]

Make these changes while logged into gnome:

[LIST]
[*]Go to System -> Administration -> Login Window (General tab) and uncheck "Disable multiple logins for a single user."
[*]Now go to the Remote tab. Change Style: to "Same as Local"
[*]Still on the Remote tab, click "Configure XDMCP," then uncheck "Honor indirect requests."
[*]Enable Universe repositories in Synaptic. (this wasn't necessary in Ubuntu 8.04)
[/LIST]

**The remaining changes can be made while SSH'd into the system, or in a terminal window:**

[LIST]
[*]Edit /etc/gdm/gdm.conf-custom
[/LIST]
```
sudo nano /etc/gdm/gdm.conf-custom

```
add the following two lines to the existing [security] and [xdmcp] sections:
```

[security]
DisallowTCP=false
[xdmcp]
Enable=true

```
[LIST]
[*]Install packages:
[/LIST]
```
sudo apt-get install vnc4server xinetd
```
[LIST]
[*]Set the VNC password
[/LIST]
```
sudo vncpasswd /root/.vncpasswd
```
[LIST]
[*]Create a new file Xvnc to add the vnc service to xinetd:
[/LIST]
```
sudo nano /etc/xinetd.d/Xvnc
```
Paste these contents into the file:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```
[LIST]
[*]Reboot
[/LIST]

That's it. I've used these exact instructions on three Ubuntu 8.04 installs without a hitch, as well as 7.04, 7.10, and Mint 4. Good luck.

---

### Post by pickarooney on 2008-06-23
Just so I'm clear on this, is there a way to set up VNC on Kubuntu so that the remote user has the option of logging in using their own session and logging into the existing session to take control of the PC? 

I could do with being able to use both options.

---

### Post by mikeduffy13 on 2008-06-25
```
vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

Why do I keep getting this when I try to change the password??

I can download that library as it says it doesn´t exist...

---

### Post by chelrob on 2008-06-25
> **mikeduffy13 said:**
> ```
vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

Why do I keep getting this when I try to change the password??

I can download that library as it says it doesn´t exist...

Search your computer for .vncpasswd
Maybe it's not in /root

---

### Post by mikeduffy13 on 2008-06-26
I don't get any results when searching for .vncpasswd.

If I search for just vncpasswd I get:
```
user@machine:~$ locate vncpasswd
/etc/alternatives/vncpasswd.1.gz
/etc/alternatives/vncpasswd
/home/rnccadmin/Desktop/vnc-4_1_2-x86_linux/vncpasswd
/home/rnccadmin/Desktop/vnc-4_1_2-x86_linux/vncpasswd.man
/usr/bin/vncpasswd
/usr/bin/realvncpasswd
/usr/bin/realvncpasswd.real
/usr/local/bin/vncpasswd
/usr/share/man/man1/vncpasswd.1.gz
/usr/share/man/man1/realvncpasswd.real.1.gz
/usr/share/man/man1/realvncpasswd.1.gz
/var/lib/dpkg/alternatives/vncpasswd

```

If I just try and start the Xvnc I get the same library error message...

---

### Post by chelrob on 2008-06-26
Maybe try creating .vncpasswd in root?

---

### Post by mikeduffy13 on 2008-06-26
Even if I create .vncpasswd in /root, still when I issue the command 
:~$sudo vncpasswd /root/.vncpasswd I get the same library error...

---

### Post by chelrob on 2008-06-26
Perhaps their's a problem with your C compiler's tool chain?

Are you able to install binaries with ```
.configure
```and ```
make
```?

---

### Post by mikeduffy13 on 2008-06-27
When I first installed unbuntu I could...I haven't tried lately.  Where can I find a .bin file to install for a test?  sourceforge?

...sorry, i'm still new to linux...

---

### Post by chelrob on 2008-06-27
Sorry, I meant source not binaries.

I found this in the Ubuntu forums... you can try to build and install nano from source:

```
If you have gcc installed you can download nano's source 
([http://www.nano-editor.org/](http://www.nano-editor.org/)) 

Then type:

tar -xzf file-name
cd new-directory
../configure
make
make install
```

---

### Post by mikeduffy13 on 2008-06-30
I already have nano installed, but ./configure seems to work ok.  When I try to do makefile I get errors like listed below:

```
nano.h:263: error: expected specifier-qualifier-list before ‘bool’
nano.h:294: error: expected specifier-qualifier-list before ‘bool’
nano.h:325: error: expected specifier-qualifier-list before ‘bool’
In file included from browser.c:24:
proto.h:32: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘jump_buf_main’
proto.h:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
proto.h:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
proto.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
proto.h:149: error: expected declaration specifiers or ‘...’ before ‘bool’
proto.h:149: error: expected declaration specifiers or ‘...’ before ‘bool’
proto.h:151: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘browser_select_filename’
proto.h:153: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘findnextfile’
```

---

### Post by chelrob on 2008-06-30
Does make finish?  If it doesn't try installing another program from source.  

If you continue to get errors it could be a problem with your compiler's toolchain.

---

### Post by acambre on 2008-07-02
> **popie said:**
> Here are the instructions I use, and they work in v8.04.

[B]VNC Server w/Resumable Sessions on Ubuntu
Works in Ubuntu 7.04, 7.10, 8.04, and Mint 4 (Daryna)
[/B]

Make these changes while logged into gnome:

[LIST]
[*]Go to System -> Administration -> Login Window (General tab) and uncheck "Disable multiple logins for a single user."
[*]Now go to the Remote tab. Change Style: to "Same as Local"
[*]Still on the Remote tab, click "Configure XDMCP," then uncheck "Honor indirect requests."
[*]Enable Universe repositories in Synaptic. (this wasn't necessary in Ubuntu 8.04)
[/LIST]


Supposed I only have SSH access and cannot get to the console. How would I do the above?

I checked the conf files in /etc/gdm, and none of the options appear to directly correlate to what's mentioned above.

---

### Post by jamesrfla on 2008-07-02
popie I am confused when we have to add the following two lines to the existing [security] and [xdmcp] sections. I put in the new lines but how do I save it and exit?

---

### Post by popie on 2008-07-02
> **jamesrfla said:**
> popie I am confused when we have to add the following two lines to the existing [security] and [xdmcp] sections. I put in the new lines but how do I save it and exit?

If you're using the nano editor, as I used in the example, press CTRL-X to exit, then press "Y" to save, then press ENTER to save using the original file name.

---

### Post by jamesrfla on 2008-07-02
Okay I tried that and did everything else and when I try connect I still get my desktop and not a new sesion. I had remote desktop enabled before so could that be the problem?

---

### Post by popie on 2008-07-02
You should see the login screen when you connect. Be sure to connect to **yourpc:1**, not yourpc:0

Not sure if having the built-in remote control still enabled matters or not, but you can try disabling it if you still see your local session.

---

### Post by avallach on 2008-07-03
I've followed these instructions and got it working on my Xubuntu (6.06) system, however...

As the HOWTO says right at the beginning, this is designed to connect you on a different display (:1) than the local console (:0).  I'd like to connect to the console session and control it remotely, which has been default behavior in all of the Ubuntu versions I've enabled it on.  Even if I type in ipaddress:0 when I connect, I get a greeter screen and when I log in, it's a new session and not the local.  I also get a warning saying I'm already logged in.  Help?

---

### Post by jamesrfla on 2008-07-03
I went ahead and tried localhost:1 and it worked. Before I was putting in my ip address. Thanks for the help!!:)

---

### Post by mikeduffy13 on 2008-07-08
> **chelrob said:**
> Does make finish?  If it doesn't try installing another program from source.  

If you continue to get errors it could be a problem with your compiler's toolchain.

I configured, and successfully completed make on another program...so now where does that leave me?

---

### Post by mikeduffy13 on 2008-07-09
ok i got the library installed via rpm from [www.rpmfind.net](www.rpmfind.net).  Used alien to install in Ubuntu and now I don't get the error anymore.

NOW - how do I actually get this vncserver to work correctly???  hrmmm

---

### Post by dansued on 2008-07-10
When I try to make a connection with tightVNC viewer, the first window that pops up has this to say,

```

Connecting to 10.0.0.3:1...

Status: Connection Established.
```
However, seconds later another window pops up with this error message,

```

ReadExact: Socket error while reading.
```
What does this mean?

---

### Post by mikeduffy13 on 2008-07-10
are you behind a firewall?  do you have the right port specified?

usually socket errors occur when ports don't match up or are being blocked.

---

### Post by dansued on 2008-07-10
> **mikeduffy13 said:**
> are you behind a firewall?  do you have the right port specified?

usually socket errors occur when ports don't match up or are being blocked.
both computers are behind the same router, so the firewall settings shouldn't matter right?

my Xvnc conf is this, ```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901

}

```

whether I connect by using :1 or :5901, I get the same socket error.

---

### Post by jamesrfla on 2008-07-10
Should be ip address:1. example 192.168.1.9:1

---

### Post by popie on 2008-07-10
> **dansued said:**
> both computers are behind the same router, so the firewall settings shouldn't matter right?

my Xvnc conf is this, ```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901

}

```

whether I connect by using :1 or :5901, I get the same socket error.

Check your fonts path. Unless you're using an old, old version of Ubuntu, it needs fixing. I also don't see the XFIXES statement... See [http://ubuntuforums.org/showpost.php?p=5229232&postcount=458](http://ubuntuforums.org/showpost.php?p=5229232&postcount=458)

---

### Post by dansued on 2008-07-11
> **popie said:**
> Check your fonts path. Unless you're using an old, old version of Ubuntu, it needs fixing. I also don't see the XFIXES statement... See [http://ubuntuforums.org/showpost.php?p=5229232&postcount=458](http://ubuntuforums.org/showpost.php?p=5229232&postcount=458)
am I able to make these changes in the console? I only have ssh access to this box.

> Make these changes while logged into gnome:

[LIST]
[*]Go to System -> Administration -> Login Window (General tab) and uncheck "Disable multiple logins for a single user."
[*]Now go to the Remote tab. Change Style: to "Same as Local"
[*]Still on the Remote tab, click "Configure XDMCP," then uncheck "Honor indirect requests."
[/LIST]

---

### Post by popie on 2008-07-11
> **dansued said:**
> am I able to make these changes in the console? I only have ssh access to this box.




I don't know of a way to make the gnome changes at the console, so that could be a problem. But I'm not a super expert at this. I have always had access to make the gnome changes.

You can make changes to the Xvnc file at the command line.

---

### Post by jcr1 on 2008-07-18
Hi, Lovely HOWTO thanks...got it working...mostly.

I seem to run into a similar problem quite often. 

I logged in yesterday (over the internet) and got the gdm login screen, logged in, great! full control on display:1. I could log out (using the button for logging out inthe remote window) and log back in later. or I could lock the screen and close the vncviewer.

But sometimes (well quite often) something seems to get upset and I can't get the viewer to open up again. I try the viewer, get prompted for a vnc password, but then get an error:

The connection closed unexpectedly.

And nothing I do now seems to let me get back...

So I tried the following:

```

jonrserv@jcrserver2:~$ vnc4server :1
A VNC server is already running as :1
jonrserv@jcrserver2:~$ sudo /etc/init.d/xinetd stop
[sudo] password for jonrserv:
 * Stopping internet superserver xinetd                                                      [ OK ]
jonrserv@jcrserver2:~$ sudo killall Xvnc
Xvnc: no process killed
jonrserv@jcrserver2:~$ sudo /etc/init.d/xinetd start
 * Starting internet superserver xinetd                                                      [ OK ]

```

thinking, this would kill the vnc session, starting afresh and I could log in...but it makes no difference. The only way I have solved this is by rebooting my server, but obviously this is not a nice option.

Question is basically, why is it doing it and how do I rectify it when it happens? How do I kill it off so its like the first time I am trying to log in?

Hope you can help!

---

### Post by xmrkite on 2008-07-18
Hello, after following the instructions to get vnc going in the beginning of this post, I was able to get it going....at least, mostly.

When i log in, all i see is a background of black and white tiny criss cross lines. I can't right click the desktop, and there is no taskbar or Apps menu of any sort.

What am I missing here?

-Thanks
-Steve

---

### Post by popie on 2008-07-18
> **xmrkite said:**
> Hello, after following the instructions to get vnc going in the beginning of this post, I was able to get it going....at least, mostly.

When i log in, all i see is a background of black and white tiny criss cross lines. I can't right click the desktop, and there is no taskbar or Apps menu of any sort.

What am I missing here?

-Thanks
-Steve


This is a common problem, but it usually is because part of the install process wasn't done properly. Please review the following post and make sure you've done **everything** in it **exactly** as described. :)

[http://ubuntuforums.org/showpost.php?p=5229232&postcount=458](http://ubuntuforums.org/showpost.php?p=5229232&postcount=458)

---

### Post by xmrkite on 2008-07-18
Hello, i did exactly as instructed in your post, then rebooted, but it's still exactly the same. What else could it be?

-Thanks for any assistance
-Steve

---

### Post by xmrkite on 2008-07-18
Also, i'm using xubuntu 8.04

-Thanks again

---

### Post by popie on 2008-07-18
> **xmrkite said:**
> Hello, i did exactly as instructed in your post, then rebooted, but it's still exactly the same. What else could it be?


Not sure... I haven't tried this process with Xubuntu, maybe there's something different needed w/that version. 

Did you manage to find all the remote settings listed at the top ("while logged into gnome")? Were there counterparts in xubuntu? Beyond that you might have to do some more searching related to xubuntu and vnc. I bet that's the issue.

---

### Post by xmrkite on 2008-07-18
I did find some other info on xubuntu and vnc, but everything i've tried just gives me the same thing i have now.

I'm wondering if there is a way to reset things and try fresh, without reinstalling, cause i have a lot of stuff setup on this computer.

---

### Post by popie on 2008-07-18
> **xmrkite said:**
> I did find some other info on xubuntu and vnc, but everything i've tried just gives me the same thing i have now.

I'm wondering if there is a way to reset things and try fresh, without reinstalling, cause i have a lot of stuff setup on this computer.

Did you verify that the fonts directory is correct for your system? Its in one of the lines in the **Xvnc **file.

It changed a few versions back, and maybe its still the old path in xubuntu...
The current: /usr/share/fonts/X11/misc USED to be: /usr/share/X11/fonts/misc
 Just a guess, but make sure this path is valid for your system.

---

### Post by xmrkite on 2008-07-18
I'm not sure exactly where i set the fonts path...any ideas?

---

### Post by popie on 2008-07-18
> **xmrkite said:**
> I'm not sure exactly where i set the fonts path...any ideas?

Its in the Xvnc file. /etc/xinetd.d/Xvnc

---

### Post by xmrkite on 2008-07-18
tons of fonts in the /usr/share/fonts/X11/misc folder that the file calls. Must be something else then i guess.

---

### Post by ttroy50 on 2008-07-30
I've set this up and can logon and view my desktop in Ubuntu 8.04, however whenever I start my first application (e.g. Firefox) after remote logon I get the following error

"There was an error starting the GNOME settings Daemon.

Some things such as themes, sounds, or backgrounds may not work correctly.

The setting Daemon restarted too many times"

This causes me to lose the Human theme and revert to the default GNOME theme.

I previously had this problem when I upgraded from Ubuntu 6 to 8 and then assumed that it was caused by the upgrade, but I've now reinstalled and it's still happening.

Everything works fine if I login directly to the PC. The issue only happens when I use vnc.

Does anyone know why this would happen?

---

### Post by p_schott on 2008-07-30
Seems to be a bug :

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/239342]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/239342")

A workaround is proposed here :

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245")

---

### Post by ttroy50 on 2008-07-30
> **p_schott said:**
> Seems to be a bug :

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/239342]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/239342")

A workaround is proposed here :

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/199245")

Thanks that seems to have done it. The workaround was to disable the keyboards plugin under /apps/gnome_settings_daemon/plugins/keyboard in gconf-editor

---

### Post by dasmith on 2008-08-05
Been following the forum on this as I set multiple session for VNC on previous Ubuntu distro's as well as Fedora and have gotten them to work.  I am receiving this error:
[I][INDENT]
root@Zues:/home/david# vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:23:14
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Tue Aug  5 00:44:53 2008
 CConn:       connected to host localhost port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8

Tue Aug  5 00:44:58 2008
 main:        No password configured for VNC Auth
root@Zues:/home/david# sudo vncpasswd /root/.vncpasswd
Password:
Verify:
root@Zues:/home/david# vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:23:14
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Tue Aug  5 00:45:30 2008
 CConn:       connected to host localhost port 5901
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8

Tue Aug  5 00:45:34 2008
 main:        No password configured for VNC Auth
root@Zues:/home/david# [/INDENT][/I]

Any ideas as I can log into localhost:0 just fine.  Actually wanting 5901 to be for a buddy of mine to log into his own desktop.  I am using Ubuntu 8.04 desktop

Thanks for any assistance.

---

### Post by jamesrfla on 2008-08-05
I think when you do localhost:1 it uses the same port which is 5900. It kinda seems like it is not posible but when you think about web servers they are sending a whole bunch of info on one port.

---

### Post by Kahran on 2008-08-08
Running Hardy, and followed the instructions in the initial post.

Here is my issue: I am trying to VNC into my Ubuntu box at home from work, which blocks a lot of ports. But that's okay, I setup OpenSSH so that I can tunnel in. SSH tunnel works fine because I used it in some other programs successfully.

VNC server is listening on port 5900 as it should but when I try to connect I get a "server closed unexpectedly" error.

Now... I am setting this all up remotely via SSH. I was never able to test of things worked locally because X11 obviously could not display. So right now I am using PuTTY+xming to open X11 applications. Of course I do not intend to run X this way but I just wanted to see if it could connect. When I try "vncviewer localhost:0" (or if I change the listen port to 5901 like the original instructions in the main post and do localhost:1) it shows me that it connected but I get a "read: Connection reset by peer (104)" error.

Am I missing a step here?

Edit: No firewall or NAT, just a direct connection.

---

### Post by jamesrfla on 2008-08-08
If you want to login to the console of the computer you have to login and then you can remote from your work place.

---

### Post by Kahran on 2008-08-08
> **jamesrfla said:**
> If you want to login to the console of the computer you have to login and then you can remote from your work place.

I have been doing that. As I said, I can tunnel no problem. I launch PuTTY on Windows with all my tunnels configured, login and leave that tunnel up. Then I launch VNC viewer and connect, and it does seem to be communicating, just quits and I am not sure why.

---

### Post by Kahran on 2008-08-08
Update: After scouring this thread some more I changed to :02/5902 and things seem to be actually working now.

---

### Post by Jose Catre-Vandis on 2008-08-12
Thanks, this works fine on **Hardy 8.04.01** after a fresh install :)

> **popie said:**
> Here are the instructions I use, and they work in v8.04.

[B]VNC Server w/Resumable Sessions on Ubuntu
Works in Ubuntu 7.04, 7.10, 8.04, and Mint 4 (Daryna)
[/B]

Make these changes while logged into gnome:

[LIST]
[*]Go to System -> Administration -> Login Window (General tab) and uncheck "Disable multiple logins for a single user."
[*]Now go to the Remote tab. Change Style: to "Same as Local"
[*]Still on the Remote tab, click "Configure XDMCP," then uncheck "Honor indirect requests."
[*]Enable Universe repositories in Synaptic. (this wasn't necessary in Ubuntu 8.04)
[/LIST]

**The remaining changes can be made while SSH'd into the system, or in a terminal window:**

[LIST]
[*]Edit /etc/gdm/gdm.conf-custom
[/LIST]
```
sudo nano /etc/gdm/gdm.conf-custom

```
add the following two lines to the existing [security] and [xdmcp] sections:
```

[security]
DisallowTCP=false
[xdmcp]
Enable=true

```
[LIST]
[*]Install packages:
[/LIST]
```
sudo apt-get install vnc4server xinetd
```
[LIST]
[*]Set the VNC password
[/LIST]
```
sudo vncpasswd /root/.vncpasswd
```
[LIST]
[*]Create a new file Xvnc to add the vnc service to xinetd:
[/LIST]
```
sudo nano /etc/xinetd.d/Xvnc
```
Paste these contents into the file:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```
[LIST]
[*]Reboot
[/LIST]

That's it. I've used these exact instructions on three Ubuntu 8.04 installs without a hitch, as well as 7.04, 7.10, and Mint 4. Good luck.

Thanks, this works fine on **Hardy 8.04.01** after a fresh install :)

---

### Post by antm88 on 2008-08-13
Two questions:

Is there anyway to make it restart the session automatically on reboot??
and why does nm-applet not load up / how can I make nm-applet load up automatically?

Thanks, Ant

---

### Post by jamesrfla on 2008-08-13
When you are done with the session click the power button on the top right corner of the desktop. Then click log out and that&#8217;s all you need to do but if you want it to do it automatically when you shut down that is a good question.

---

### Post by dasmith on 2008-08-13
If you go to System >>> Sessions >>>  Select the Session Option tab, Check the box next to Automatically remember running applicatiopn when logging out.

---

### Post by Jose Catre-Vandis on 2008-08-13
For Hardy 8.04.*

VNC Speedfix reported here

[http://ubuntuforums.org/showpost.php?p=5252422&postcount=5](http://ubuntuforums.org/showpost.php?p=5252422&postcount=5)

also if your theme keeps changing when running a vnc session, on your remote machine, run

gconf-editor

and disable  apps  >  gnome-settings-daemon  >  plugins  >  keyboard

then reboot

EDIT

Hardy is still "jaggy" with slow refresh rates compared to previous versions, even with these fixes

---

### Post by berryrag on 2008-08-19
Everytime I try to connection, I get an error connection reset by peer.

Any help please? :)

---

### Post by kamkos on 2008-08-23
hey,

I have a Xvnc running on Ubuntu server with GNOME as for GUI.

my Xvnc file started with xinetd:

service vnc2
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/Xvnc
server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
port = 5903
}
service vnc1
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/Xvnc
server_args = -inetd :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
port = 5902
}
service vnc3
{
type = UNLISTED
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = root
server = /usr/bin/Xvnc
server_args = -inetd :3 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
port = 5904
}

I have also added the following lines to /etc/services

vnc1 5902/tcp
vnc2 5903/tcp
vnc3 5904/tcp

The deal is that I can make two connections to the server but not three at the same time. For example, if vnc1 and vnc2 are on then vnc3 cannot be made with the given error:

read: Connection reset by peer (10054)

Any help will be appreciated.

kamkos

---

### Post by ziogionni on 2008-08-24
> **popie said:**
> Here are the instructions I use, and they work in v8.04.

[B]VNC Server w/Resumable Sessions on Ubuntu
Works in Ubuntu 7.04, 7.10, 8.04, and Mint 4 (Daryna)
[/B]

Hello.

I am trying to remote control an Ubuntu Desktop 8.04LTS installation.
The "standard" remote desktop that you can configure into gnome did work fine, but everytime you reboot you have to login manually, and even if you setup automatic login the X server on :0 won't start with no monitors turned on and connected into the VGA port. Basically X server won't start on an headless computer.

So I have followed this guide to run resumable sessions over :1

But I have some problems, basically the "desktop theme" (i don't know how else call the style of the windows, scroll bars, etc, hope you understood, English is not my first language) keeps changing every seconds o_O' ... and I am getting a bunch of error.

It seems like some widgets (network one?) are not authorized to run on :1 or something like that. I don't even know how to remove it from the bar now that I haven't got the monitor plugged in.

This is a sample of errors I get in .xsession-errors
> ** (nm-applet:5447): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.24" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'


** (gnome-session:5322): WARNING **: Failed to authenticate with GDM
Avviso del window manager: CurrentTime used to choose focus window; focus window may not be correct.
Avviso del window manager: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
seahorse nautilus module shutdown
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 3152 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
** Message: Got disconnected from the session message bus; retrying to reconnect every 10 seconds
DBus connection has been lost, trackerd will now shutdown


I am very frustrated. There has to be a simple way to control an Ubuntu 8.04 LTS desktop headless installation without having to keep the VGA port connected to a monitor, or having themes changing every seconds with gnome slowing down and so on the :1 display ...

---

### Post by FJA on 2008-08-26
> **ziogionni said:**
> ... There has to be a simple way to control an Ubuntu 8.04 LTS desktop headless installation without having to keep the VGA port connected to a monitor, or having themes changing every seconds with gnome slowing down and so on the :1 display ...

I have sam problem - that is settings changes. Seems to be triggered when I launch a program after logon, and continues til at get a settings-server error. Tried cure mentioned in post below - but with no result. [http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=5582731&postcount=510]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=5582731&postcount=510")

ALSO: I can't do certain changes using Xvnc - like adding new user. There is not prompt for SUDOer password... Why is that ??

---

### Post by mediajunkie on 2008-08-26
VNC on hardy has been a real pain in the neck for me.

my laptop (hardy) can perfectly do vnc to any realvnc winxp machine, 
also tsclient to xppro works, but can't get vnc (also not vinagre) to work to another Ubuntu hardy machine. 

I get either connection closed or with vnc Connection reset by peer (104) 


Note ssh works perfect. 


grrrrr at the end of my knowledge here.
Any help appreciated

---

### Post by jon.breakdesign on 2008-08-27
Hi Guys

Finally got vnc working nicely in hardy.

I also had the theme change errors.

When i looked in ~/.xsession-errors i see....

** (nm-applet:15671): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.314" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'


Now I'm not sure if I'm talking rubbish here but authorizations [system->administration->auhorizations] generally isn't set up to allow certain stuff to happen when you are not logged in on a local terminal....which you don't have when you are logged in via Xvnc....its remote...so..

anyway to cut a long story short I messed around in the authorizations tab [system->administration->auhorizations] (you are going to need to do this for stuff like HAL too otherwise you won't be able to mount usb drives in gnome over vnc) and also under the gnome tab in there..you should change the settings to change system settings to allow anyone  with admin authentication if you want the policykit unlock boxes not to be grayed out over vnc

and then i also installed the .debs for vnc4server from this url as mentioned on the previous page..

[http://www.francescosantini.com/index.php?page=linux&lang=en](http://www.francescosantini.com/index.php?page=linux&lang=en)


and that was it..everything worked from there....so for me changing authorization policies and installing those debs sorted out performance and also that theme and usb mount problems...


Notes: My /etc/xinetd.d/Xvnc file has the following lines to it:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

@mediajunkie I know this is a really n00b silly question but on hardy you are allowing the port your vnc service is to run on through your firewall?

oh lastly if you don't feel like plugging the monitor back in and logging in on the local console again, and want to change a bunch of stuff under authorizations that you are not authorized to change under your account on a non local terminal (even if you are an admin) then very briefly enable the root account log in as root over vnc change what you have to and disable the account again.

---

### Post by mediajunkie on 2008-08-28
Yep, even turned off firewall. // it does work from laptop to xp machines, running realvnc.

---

### Post by jocko_johnson on 2008-08-30
[QUOTE=Jose Catre-Vandis;5577387]Thanks, this works fine on **Hardy 8.04.01** after a fresh install :)


I'm wondering is there a way that I can resume my current "at home" session when I connect remotely?  i.e, when I VNC to home from work, can I see the session I have open at home?

I find it annoying to have to login via the main ubuntu login screen and then I have a blank desktop - while at home my screen shows the apps I have running.

does it have anything to do with the "-NeverShared" part in "service Xvnc"??
if so, what is the option to allow me to resume my current "home" session?

Thanks

---

### Post by Jose Catre-Vandis on 2008-08-30
> **jocko_johnson said:**
> [QUOTE=Jose Catre-Vandis;5577387]Thanks, this works fine on **Hardy 8.04.01** after a fresh install :)


I'm wondering is there a way that I can resume my current "at home" session when I connect remotely?  i.e, when I VNC to home from work, can I see the session I have open at home?

I find it annoying to have to login via the main ubuntu login screen and then I have a blank desktop - while at home my screen shows the apps I have running.

does it have anything to do with the "-NeverShared" part in "service Xvnc"??
if so, what is the option to allow me to resume my current "home" session?

Thanks

My experience is that you should be able to do this. If I leave my session logged in at home and then access via vnc at work I get the same session either via vnc (Linux) or putty (Windows). I can also login at work and then vnc from home to the same desktop.

---

### Post by jocko_johnson on 2008-08-30
> **Jose Catre-Vandis said:**
> [QUOTE=jocko_johnson;5692329]

My experience is that you should be able to do this. If I leave my session logged in at home and then access via vnc at work I get the same session either via vnc (Linux) or putty (Windows). I can also login at work and then vnc from home to the same desktop.

any idea how I alter my settings to allow this?
every time I "PuTTY" from my work windows machine, or my wifes laptop I get a ubuntu signin screen and then a totally new session which I dont want.

when I login using Vino server I resume the session, but I prefer xvnc server because of the existence of more options ( better password options - vino is 8 char max, I can tell xvnc to only allow connections from my user, etc... )

unless Vino offers these options too?  the GUI for vino offers very little in terms of options.

 anyway, for Jose Catre-Vandis, your post detailing the instructions to get xvnc server running were great.  thank you for that very much.

---

### Post by thenuge26 on 2008-09-01
i am trying to set up ubuntu as a headless server, and i am having trouble accessing it remotely via vnc.  i remember before i ran through the setup, vnc would work through vino, however, without a monitor plugged in, i could not change the resolution.  anyways, i ran though the guide here, and when i try to access the server from my windows box, i get this error.

```
connection failed - error reading protocol version

possible causes:

- you've forgotten to select a DSMPlugin and the server uses a DSMPlugin
- Viewer and server are not compatible (they use different RFB protocoles)
- bad connection
```

if it is indeed that my viewer (ultraVNC) is not compatible, do you guys know of a windows viewer that is compatible?

thanks in advance for any help

---

### Post by sefs on 2008-09-02
How do you enable the loopback for vnc4server?  It's needed when connecting over ssh.

Thanks.

---

### Post by sefs on 2008-09-03
Hi,

following some advice earlier to test this thing I am getting this error

```

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Wed Sep  3 00:24:12 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/X11/fonts/misc, removing from list!

Fatal server error:
could not open default font 'fixed'
pokeymon@pokeymon:~$ 

```


This is the command I run

```

 sudo /usr/bin/Xvnc :2 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

```

I am also getting lots of those errors in syslog 
```

Sep  3 00:02:23 pokeymon xinetd[12445]: warning: can't get client address: Transport endpoint is not connected
Sep  3 00:02:23 pokeymon xinetd[12446]: warning: can't get client address: Transport endpoint is not connected
Sep  3 00:02:23 pokeymon xinetd[12447]: warning: can't get client address: Transport endpoint is not connected
Sep  3 00:02:23 pokeymon xinetd[12448]: warning: can't get client address: Transport endpoint is not connected
Sep  3 00:02:23 pokeymon xinetd[12449]: warning: can't get client address: Transport endpoint is not connected

```

How can i solve this.


Edit:

following this link [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

in /etc/xinetd.d/Xvnc

I changed this line...

```

server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

```

to this

```

server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES

```

NB: the -extension XFIXES at the end... i could not get it to work without that.
As well as the font path...there is a subtle change there as well.

---

### Post by popie on 2008-09-03
Your fonts path is incorrect. See post #458 in this thread for updated setup instructions.

The font path should be: /usr/share/fonts/X11/misc

---

### Post by kacheng on 2008-09-04
@jon.breakdesign

Thanks for your post.  I had the same error messages.  I tried a series of policy changes, but could not get it working.

However, I found this easy solution:
```
sudo adduser USER netdev
sudo /etc/init.d/dbus restart
```
[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg102963.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg102963.html)

Which I think essentially has the same effect (setting the user's policies correctly).

Thanks

> **jon.breakdesign said:**
> Hi Guys

Finally got vnc working nicely in hardy.

I also had the theme change errors.

When i looked in ~/.xsession-errors i see....

** (nm-applet:15671): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.314" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'


Now I'm not sure if I'm talking rubbish here but authorizations [system->administration->auhorizations] generally isn't set up to allow certain stuff to happen when you are not logged in on a local terminal....which you don't have when you are logged in via Xvnc....its remote...so..

anyway to cut a long story short I messed around in the authorizations tab [system->administration->auhorizations] (you are going to need to do this for stuff like HAL too otherwise you won't be able to mount usb drives in gnome over vnc) and also under the gnome tab in there..you should change the settings to change system settings to allow anyone  with admin authentication if you want the policykit unlock boxes not to be grayed out over vnc

and then i also installed the .debs for vnc4server from this url as mentioned on the previous page..

[http://www.francescosantini.com/index.php?page=linux&lang=en](http://www.francescosantini.com/index.php?page=linux&lang=en)


and that was it..everything worked from there....so for me changing authorization policies and installing those debs sorted out performance and also that theme and usb mount problems...


Notes: My /etc/xinetd.d/Xvnc file has the following lines to it:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

@mediajunkie I know this is a really n00b silly question but on hardy you are allowing the port your vnc service is to run on through your firewall?

oh lastly if you don't feel like plugging the monitor back in and logging in on the local console again, and want to change a bunch of stuff under authorizations that you are not authorized to change under your account on a non local terminal (even if you are an admin) then very briefly enable the root account log in as root over vnc change what you have to and disable the account again.

---

### Post by DasNiche on 2008-09-06
I am getting the common problem, when I enter 

```
vncviewer localhost:1
```

I get the output:

"VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Sat Sep  6 03:18:07 2008
 CConn:       connected to host localhost port 5901
 main:        read: Connection reset by peer (104)"

And get a pop up error message saying "read: Connection reset by peer (104)". 

I followed the instructions exactly and I'm getting really frustrated because I can't figured this out. Also I am running 8.04 Hardy Heron if that helps. Any help is GREATLY appreciated, thanks!

---

### Post by Dethecus on 2008-09-09
Same problem as above, have followed this guide to the letter and the box is just refusing connections. I can VNC to it just fine when it's logged in but not to GDM :(

I've tried several different things from around the net with no success, I also noticed that when you enable XDMCP through the menu's it is still set as "enabled = false" in /etc/gdm/gdm.conf

Any help would be greatly appreciated, this is basically a fresh install and it's the last thing I need to get working!

---

### Post by popie on 2008-09-09
@Dethecus, If you followed the first post in this thread, it won't work. Many things have changed since this thread began. 

I listed the entire process, step by step, that works for me (every time) in the following post in this thread:

[http://ubuntuforums.org/showpost.php?p=5229232&postcount=458](http://ubuntuforums.org/showpost.php?p=5229232&postcount=458)

---

### Post by Dethecus on 2008-09-10
> **popie said:**
> @Dethecus, If you followed the first post in this thread, it won't work. Many things have changed since this thread began. 

I listed the entire process, step by step, that works for me (every time) in the following post in this thread:

[http://ubuntuforums.org/showpost.php?p=5229232&postcount=458](http://ubuntuforums.org/showpost.php?p=5229232&postcount=458)

Well I just tried those steps of yours exactly on **both** my Ubuntu computers and it didn't work on either =\

Still getting connection refused.

---

### Post by jiji2k on 2008-09-10
@popie - thank you so much for the tutorial, it works like a charm! 

however is there a way to have concurrent VNC connections? like multiple connections with the same username so people share the desktop without having to log off, right now when i try to login again with the same username it says "VNC authentication faild!"
thank you!

---

### Post by Hobgoblin on 2008-09-18
> **popie said:**
> Your fonts path is incorrect. See post #458 in this thread for updated setup instructions.


Worked for me. :KS

BTW, to save people some clicks, the post is [here](http://ubuntuforums.org/showpost.php?p=5229232&postcount=458).

---

### Post by DasNiche on 2008-09-19
The localhost:1 works now poppi! As for the remote desktop VNC... all goes well for a split second and then the windows begin to pop up infinitely. Here's a screenshot to explain.

[http://img443.imageshack.us/my.php?image=vncerrorcq8.jpg](http://img443.imageshack.us/my.php?image=vncerrorcq8.jpg)
[IMG]http://img443.imageshack.us/my.php?image=vncerrorcq8.jpg[/IMG]

What the heck is going on!?
Any help is MUCH appreciated, thanks!

---

### Post by nexxteh on 2008-10-04
> **popie said:**
> 
I listed the entire process, step by step, that works for me (every time) in the following post in this thread:

[http://ubuntuforums.org/showpost.php?p=5229232&postcount=458](http://ubuntuforums.org/showpost.php?p=5229232&postcount=458)

First of all Dethecus, thank you for this!

I do have problems though. If I do *vncviewer localhost:1* I dont get a GDM login window, just a blank screen with some checkboxes.

**EDIT: FIXED. Followed the instructions [here](http://ubuntuforums.org/showpost.php?p=4497342&postcount=403).**

---

### Post by killdeer on 2008-10-06
When I do the last command in part 2 of the tutorial "vncviewer localhost:1" I didnt have vncviewer. So I managed to figure that out and got it. After that when I type in the command I get...


> VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Mon Oct  6 17:48:14 2008
 CConn:       connected to host localhost port 5901
 main:        read: Connection reset by peer (104)

---

### Post by conorgriffin on 2008-10-12
Hi guys, I'm getting the same issue, I followed the newer guide in [post 458]("http://ubuntuforums.org/showpost.php?p=5229232&postcount=458") but I'm still getting this

```
VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Mon Oct 13 00:11:29 2008
 CConn:       connected to host localhost port 5901

Mon Oct 13 00:11:43 2008
 main:        read: Connection reset by peer (104)
conor@linux:~$ 


```

Then when I look in the syslog for messages I see the following

```
Oct 13 00:51:00 linux xinetd[9156]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[9157]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[9158]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[9159]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[9160]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[9161]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[9162]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[9163]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[9164]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[9170]: warning: can't get client address: Transport endpoint is not connected
Oct 13 00:51:00 linux xinetd[6687]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.
Oct 13 00:51:10 linux xinetd[6687]: Activating service Xvnc
Oct 13 00:55:39 linux xinetd[6687]: Exiting...

```

:confused:

---

### Post by alenis on 2008-10-14
I followed popie's instructions and it seems to work, However, when I try to connect from my laptop I get this error message from VNC viewer: "Error: couldn't find suitable pixmap format". How can I solve the problem?

---

### Post by kr3w on 2008-10-15
I followed popie's instructions, everything went well until i rebooted and nothing had changed. I still can't vnc unless i log in the physical desktop, and then it only controls the physical desktop... Am I connecting wrong?

---

### Post by johanang on 2008-10-15
I really hate this side of Ubuntu.. So far i am unsuccessful at installing a vnc server.. This definitely needs to be address by the ubuntu admins in their documentation.

---

### Post by kr3w on 2008-10-15
> **johanang said:**
> I really hate this side of Ubuntu.. So far i am unsuccessful at installing a vnc server.. This definitely needs to be address by the ubuntu admins in their documentation.

As far as getting the VNC server running, that is as simple as clicking in GNOME System>Preferences>Remote Desktop, then clicking Allow users to view your desktop, and Allow users to control your desktop under General Tab subsection Sharing.

Getting VNC to work independently of sessions on the physical display, is another issue, apparently.

---

### Post by havok1977 on 2008-11-11
Hello everyone, i am trying to get my laptop to run the vnc4server on Kubuntu 8.10; which as you may know uses KDE 4.1.3.

I followed the instructions exactly as described on post #458 of this thread and Im having the same type of problem as many other people have posted in this thread and in other forums:

```

diego@raziel:~$ vncviewer localhost:1
Connected to RFB server, using protocol version 3.8
vncviewer: read: Connection reset by peer

```

To which my /var/log/syslog says:

```

Nov 11 21:09:35 raziel xinetd[15191]: warning: can't get client address: Transport endpoint is not connected

```

I made the following configurations in /etc/kde4/kdm/kdmrc:

```

[Xdmcp]
Enable=true
Port=177
Xaccess=/etc/kde4/kdm/Xaccess
Willing=/etc/kde4/kdm/Xwilling

```

Is there anything new that i should take into account for 8.10? Did the vnc4server get any significant changes between last release and now?

Thanks in advance.


Edit: Fixed the problem, had to edit /etc/kde4/kdm/Xaccess like this:

```

*                                       #any host can get a login window
*               CHOOSER BROADCAST       #any indirect host can get a chooser

```

Now it works great! Thanks to the howto posters....

---

### Post by Eviltechie on 2008-11-11
I'm using Ubuntu 8.10 and I get...
```
ivan@ivan-ubuntu:~$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Tue Nov 11 20:07:28 2008
 CConn:       connected to host localhost port 5901
 main:        read: Connection reset by peer (104)
```
I followed the directions in 458, but it didn't work.

---

### Post by v_dragon on 2008-12-02
> **Eviltechie said:**
> I'm using Ubuntu 8.10 and I get...
```
ivan@ivan-ubuntu:~$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Tue Nov 11 20:07:28 2008
 CConn:       connected to host localhost port 5901
 main:        read: Connection reset by peer (104)
```
I followed the directions in 458, but it didn't work.

I also am having the same issue - been web searching for days, no luck!!!
its really disappointing to have such issues with my Linux boxes - i kinda wish i had not made the switch from windows. I can get VNC to work to my CentOS5 machine either!

---

### Post by karlson on 2008-12-04
Hi,

I have set up the sessions in Hardy Heron (8.04.1).  I have a problem with getting a login screen.

I am able to connect and launch Xvnc through xinetd but I cannot get the login prompt the gdmlogin to launch.  When I try to launch X with -query localhost I am able to come up with the login prompt no problem, but Xvnc seem to have an issue.

Has anyone seen the issue?  Or resolve one like this or similar?

---

### Post by chiefchief on 2008-12-04
I found a guide that enables VNC in 8.10, now it's a little more integrated.  You can find it [here]("http://www.ubuntugeek.com/how-to-use-remote-desktop-in-ubuntu-810-intrepid-ibex.html").

It'd be nice if Ubuntu could get VNCing down as nice as OpenSuse does.

---

### Post by chelrob on 2008-12-04
^^^^ Does that give you resumable sessions or does it just give you desktop control?

---

### Post by veiloctane on 2008-12-08
> **popie said:**
> Here are the instructions I use, and they work in v8.04.

[B]VNC Server w/Resumable Sessions on Ubuntu
Works in Ubuntu 7.04, 7.10, 8.04, and Mint 4 (Daryna)
[/B]

Make these changes while logged into gnome:

[LIST]
[*]Go to System -> Administration -> Login Window (General tab) and uncheck "Disable multiple logins for a single user."
[*]Now go to the Remote tab. Change Style: to "Same as Local"
[*]Still on the Remote tab, click "Configure XDMCP," then uncheck "Honor indirect requests."
[*]Enable Universe repositories in Synaptic. (this wasn't necessary in Ubuntu 8.04)
[/LIST]

**The remaining changes can be made while SSH'd into the system, or in a terminal window:**

[LIST]
[*]Edit /etc/gdm/gdm.conf-custom
[/LIST]
```
sudo nano /etc/gdm/gdm.conf-custom

```
add the following two lines to the existing [security] and [xdmcp] sections:
```

[security]
DisallowTCP=false
[xdmcp]
Enable=true

```
[LIST]
[*]Install packages:
[/LIST]
```
sudo apt-get install vnc4server xinetd
```
[LIST]
[*]Set the VNC password
[/LIST]
```
sudo vncpasswd /root/.vncpasswd
```
[LIST]
[*]Create a new file Xvnc to add the vnc service to xinetd:
[/LIST]
```
sudo nano /etc/xinetd.d/Xvnc
```
Paste these contents into the file:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```
[LIST]
[*]Reboot
[/LIST]

That's it. I've used these exact instructions on three Ubuntu 8.04 installs without a hitch, as well as 7.04, 7.10, and Mint 4. Good luck.



thankyou so much this worked for me with ubuntu studio 8.10

---

### Post by RomanIvanov on 2008-12-12
Does anybody succeed in connecting to vncserver with resolution "-geometry 1280x800 " ?

Is there any way to connect to current session(with all applications running) instead of new session?

---

### Post by chelrob on 2008-12-12
The answer to your second question is yes... don't log out of the current session.  Close VNC without logging out.  When you reconnect the session will still be open, hence resumable sessions.

---

### Post by cphan on 2008-12-13
Thanks, This updated code fixed my 104 error, I believe it was due to a bad font path.

Fixed in Xbuntu 8.04


    * Create a new file Xvnc to add the vnc service to xinetd:

Code:

```

sudo nano /etc/xinetd.d/Xvnc

```

Paste these contents into the file:

```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```

---

### Post by popie on 2008-12-13
> **cphan said:**
> Thanks, This updated code fixed my 104 error, I believe it was due to a bad font path.



Yup, the font path in the original post worked when it was posted, but the font path changed at some specific version of Ubuntu (forgot which one). Its easy to overlook.

Also, XFIXES wasn't in the original post, and wasn't previously required. But somewhere along the way, things broke, and it became necessary as a workaround.

---

### Post by RomanIvanov on 2008-12-14
Hi ,chelrob, thanks for answer, but I am interesting in the following case:

I have Desktop and Laptop, and need to connect from Laptop to Desktop:
1. Turn On Laptop and Desktop
2. Run In Desktop few UI applications (firefox, thunderbird)
3. Run VNCViewer on Laptop and connect to Desktop

Now, we have a warning that session exists, and can only connect to new session of the same user on the Desktop. Yes, for this new session - the session is resumable.

Is there way to connect to the session that I run on Desktop with few application that already exists (point 2)?

---

### Post by RomanIvanov on 2008-12-14
Also problem with 1280x800 resolution was resolved after restart. Now it works.

---

### Post by bushwakko on 2008-12-14
font path needs to be :  /usr/share/fonts/X11/misc in newer versions of X, that is why a lot of people cannot connect.

---

### Post by RomanIvanov on 2008-12-15
Good point to use x11vnc instead: [http://ubuntuforums.org/showthread.php?t=1002240](http://ubuntuforums.org/showthread.php?t=1002240)

To be brief:
On server:
```

sudo apt-get install x11vnc

/usr/bin/x11vnc -display :0 -24to32 -usepw -forever -ncache 10

```
you can add "-allow [YOUR_IP]" to make it a bit secure.

On client: 
```
vncviewer 192.168.0.100:0
```
to scroll - use right and left button click on scroller

---

### Post by cu_ on 2008-12-21
Having issues after upgrade to Intrepid.  This tutorial is great and I really was using the display:1 thru my nokia 770 for a long time.  The mistake I did is to upgrade to Intrepid and now my vnc session shows a blank X-Window.  Screen shot attached.  
I did google all kinds of stuff and tried reinstalling vnc4server, xinetd etc.,  Could it be some issue with XDMCP on Intrepid?

---

### Post by cu_ on 2008-12-21
> **cu_ said:**
> Having issues after upgrade to Intrepid.  This tutorial is great and I really was using the display:1 thru my nokia 770 for a long time.  The mistake I did is to upgrade to Intrepid and now my vnc session shows a blank X-Window.  Screen shot attached.  
I did google all kinds of stuff and tried reinstalling vnc4server, xinetd etc.,  Could it be some issue with XDMCP on Intrepid?

Just wanted to add, that I get the same results even when I run Xvnc from commandline for display :2 i.e.  even this window does not show the XDMCP login dialog, but a basic X-Window.

```
Xvnc :2 -query localhost -geometry 800x480 -depth 16 -once -fp /usr/share/fonts/X11/misc -rfbauth /root/.vncpasswd 
```

---

### Post by cu_ on 2008-12-22
> **cu_ said:**
> Just wanted to add, that I get the same results even when I run Xvnc from commandline for display :2 i.e.  even this window does not show the XDMCP login dialog, but a basic X-Window.

```
Xvnc :2 -query localhost -geometry 800x480 -depth 16 -once -fp /usr/share/fonts/X11/misc -rfbauth /root/.vncpasswd 
```

To give the gurus more information:
When I try to see if there is anything on port 177 or port 6000, nothing is listening.  Could it be a gdm issue?

---

### Post by cu_ on 2008-12-22
Here is my syslog:

Dec 22 17:06:18 server gdm[5366]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 127.0.0.1  
Dec 22 17:06:18 server gdm[5366]: DEBUG: Attempting to parse key string: debug/Enable=false 
Dec 22 17:06:18 server gdm[5366]: DEBUG: gdm_xdmcp-handle_manage: Got display=1, SessionID=1181938353 Class=MIT-unspecified from MIT-unspecified1 
Dec 22 17:06:18 server gdm[5366]: DEBUG: gdm_xdmcp_handle_manage: Failed to look up session id 1181938353 
Dec 22 17:06:18 server gdm[5366]: DEBUG: XDMCP: Sending REFUSE to 1181938353 
Dec 22 17:06:18 server gdm[5366]: DEBUG: gdm_forward_query_lookup: Host ::ffff:127.0.0.1 not found 
Dec 22 17:06:18 server gdm[5366]: DEBUG: decode_packet: GIOCondition 1 
Dec 22 17:06:18 server gdm[5366]: DEBUG: XDMCP: Received opcode QUERY from client ::ffff:127.0.1.1 : 60899 
Dec 22 17:06:18 server gdm[5366]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 127.0.1.1  
Dec 22 17:06:18 server gdm[5366]: DEBUG: XDMCP: Sending WILLING to ::ffff:127.0.1.1

---

### Post by amp88 on 2008-12-31
> **Jose Catre-Vandis said:**
> Thanks, this works fine on **Hardy 8.04.01** after a fresh install :)

...

Thanks, this works fine on **Hardy 8.04.01** after a fresh install :)

Thank you so much. This works perfectly and is very well laid out for a Linux newb, like myself :) 

I have a questions though. Is there an easy way to restrict IPs who can connect to this server? I want to run a VNC server on my file server but I only want IPs from within my network to be able to connect to it. That way I can do away with the password.

---

### Post by amp88 on 2009-01-01
> **amp88 said:**
> Thank you so much. This works perfectly and is very well laid out for a Linux newb, like myself :) 

I have a questions though. Is there an easy way to restrict IPs who can connect to this server? I want to run a VNC server on my file server but I only want IPs from within my network to be able to connect to it. That way I can do away with the password.

I found out about the firewall "gufw", so I've now been able to use that to enforce the IP to connect to the server.

---

### Post by shizow on 2009-01-09
I have the same problem like cu_.
I updated to Intrepid, and since that i only get a grey screen when i try to login.
I am using KDE, so this doesnt seem to be a Gnome problem.

---

### Post by cu_ on 2009-01-09
> **shizow said:**
> I have the same problem like cu_.
I updated to Intrepid, and since that i only get a grey screen when i try to login.
I am using KDE, so this doesnt seem to be a Gnome problem.

Hi,
My problem got resolved.  I did two things at the same time, upgrade of ubuntu and replacing my router.  The problem turned out to be with the new router.  Here is my guess at why...  for the vnc to query for an existing xdmcp, it uses port 177.  For some reason, the new router took it upon itself to block it.  
I found this accidentally... when I removed the nextwork cable and tried the vnc session, it showed the login screen instead of the the grey.  That is when I realized it is the router.  
Please try "vncviewer localhost:1"  with your network cable removed... to see if your problem is due to the same reason.

Hope this helps
cu_

---

### Post by ottotk on 2009-01-09
> **cu_ said:**
> Hi,
My problem got resolved.  I did two things at the same time, upgrade of ubuntu and replacing my router.  The problem turned out to be with the new router.  Here is my guess at why...  for the vnc to query for an existing xdmcp, it uses port 177.  For some reason, the new router took it upon itself to block it.  
I found this accidentally... when I removed the nextwork cable and tried the vnc session, it showed the login screen instead of the the grey.  That is when I realized it is the router.  
Please try "vncviewer localhost:1"  with your network cable removed... to see if your problem is due to the same reason.

Hope this helps
cu_

Hi!
I think is has something to do with ipv6 (My network is ipv4)

On file /etc/modprobe.d/aliases find the line containing 
> 
alias net-pf-10 ipv6

and replace „ipv6“ with „off“. After reboot everything should work!

---

### Post by cherry316316 on 2009-01-19
i got this link 1st and i followed the commands with ssh option
and everything worked fine.

On my remote machine, i have a primary user (which using sudo su becomes the root of the computer) and I am ordinary/desktop user.

when I followed your post,
and tried to connect vncviewer to my desktop user,

i got something like

 CConn:       connected to host localhost port 5901
 main:        End of stream


in the end, i decided to uninstall xinetd
and then as a desktop user, i run the command
vncserver :1 -extension XFIXES

and then every thing start working fine.

do u , or any one know what went wrong ?

---

### Post by dmizer on 2009-01-19
> **cherry316316 said:**
> do u , or any one know what went wrong ?

The howto was last updated on February 21st, 2006. Ubuntu has gone through several generations since then. It's a little like trying to make a Windows 95 howto work in XP. :)

---

### Post by shizow on 2009-03-02
> **shizow said:**
> I have the same problem like cu_.
I updated to Intrepid, and since that i only get a grey screen when i try to login.
I am using KDE, so this doesnt seem to be a Gnome problem.

I am still having the problem!
After i enter the password i get a grey screen
i tried to connect from the server machine itself with vncviewer localhost:1, but there i get the same grey screen.
Is it possible that vnc is not starting kdm?

please anyone can help me?

---

### Post by Cerin on 2009-03-02
It's a bit dated, but I've had some success following this howto:

[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

With this, I was ablet to VNC into my machine, and be prompted by the standard Gnome login screen, which then started a new session.

It's really surprising that this setup isn't a bit more standardized. Separate resumable sessions are standard functionality in the windows world, but few distros directly support this.

---

### Post by cherry316316 on 2009-03-04
> **shizow said:**
> I am still having the problem!
After i enter the password i get a grey screen
i tried to connect from the server machine itself with vncviewer localhost:1, but there i get the same grey screen.
Is it possible that vnc is not starting kdm?

please anyone can help me?

this may be of some help to you.
it worked for me

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

---

### Post by shizow on 2009-03-10
> **cherry316316 said:**
> this may be of some help to you.
it worked for me

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

is this surely a How-To for a RESUMABLE session?

---

### Post by shizow on 2009-03-10
> **shizow said:**
> I am still having the problem!
After i enter the password i get a grey screen
i tried to connect from the server machine itself with vncviewer localhost:1, but there i get the same grey screen.
Is it possible that vnc is not starting kdm?

please anyone can help me?

I solved with this How-To for KDE [http://kubuntuforums.net/forums/index.php?topic=12376.0](http://kubuntuforums.net/forums/index.php?topic=12376.0)

The problem was i just updated from Kde3 to Kde4, so i had to edit /etc/kde4/kdm/kdmrc and /etc/kde4/kdm/Xaccess.

---

### Post by Crixi on 2009-03-15
i have followed all the information in this thread.
i login into my server (hosting the vnc server and ssh server)

runnung Ubuntu 8.10 on both systems.

if i hav the followin setup in the Xvnc file.
service Xvnc
{       type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no      
        user = root    
        only_from = localhost
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5950
}

when i login using first
user@clieent> ssh IP -L 5900:localhost:5950
then
user@client> vinagre localhost
i get the password prompt.  then the ligin screen. i can log in to a user and start apps like utorrent and so on.

Now to the problem! I cant figure out how to close vnc and still have the session going on the server, so i can reconnect to it later on.

do i have to do something to get this functionality?

another problem.. i cant login via vnc if i have "wait = yes". any ideas ?

---

### Post by dmizer on 2009-03-15
The information in this howto is old and extremely out of date. It's extremely easy to get remote desktop working now: [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

### Post by AncientPC on 2009-03-31
I'm trying this set up on an 8.04.2 machine.

I followed the directions in the original post but it only got me so far before Xvnc crashed looking for the fixed font.  One problem was that the font path was pointing in the wrong direction.

```
-fp /usr/share/X11/fonts/misc/
```
should be
```
-fp /usr/share/fonts/X11/misc/
```

However there was a second problem:
> Fatal server error:
could not open default font 'fixed'

To solve this problem I ran:
```
cd /usr/share/fonts/X11/misc/
sudo ln -s ../100dpi
sudo ln -s ../75dpi
sudo ln -s ../Type1
sudo ln -s ../util
```

Then I ran into this problem that I can't solve:
```
root@Punk:/usr/share/fonts/X11/misc# Xvnc :2 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc/ -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpaswd -IdleTimeout 900

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Tue Mar 31 01:36:14 2009
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
root@Punk:/usr/share/fonts/X11/misc# 
```

---

### Post by NefariousPrior on 2009-04-02
This should be called "HOWTO: Set up VNC server with 1 resumable session" as in the single vnc session it allows.


Do you know of any way to allow multiple resumable sessions the way that windows terminal service does on a single port?

---

### Post by Eviltechie on 2009-04-02
XRDP sort of works like that, it is terminal services over RDP. Unfortunately, the package is broken.

---

### Post by Wolfpup on 2009-04-22
> **dmizer said:**
> The information in this howto is old and extremely out of date. It's extremely easy to get remote desktop working now: [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)
 
i have been trying eveything in this thread and i even checked out the link to the "new" way to do it but none of talks about how to set your router and i have a a new linksys wrt54g2 router and when i start the vnc viewer on my winxp system i get an error  the erro reads connection reset by perr(10054) do you wish to attempt to reconnect to <ubuntu ip> when i click yes i get unable to connect also when i try to connect in the treminal on the ubuntu system get bacily the same error and in the syslog i see the spam about the connection error and reseting if any of you can help me it would be welcomed also the system is only going to be acessable by local network only and would rather use the remote desktop feature of my winxp systems as i have to use that for loging in ay my work.

---

### Post by theDaveTheRave on 2009-05-07
Hi all.

VNC on the terminal I am attempting to remote log in to simply refuses to play ball!

I have followed the instructions for installation and set up in the OP's original post.

when I try to log onto the ubuntu box from the windows machine I get a
```

failed to connect to server (ip.address)
```

I can ssh into the box, which is how I'm doing all the set up. but now I want to be able to log into a graphical desktop also (or rather my colleagues do - I'm happy with command line!).

I have a suspicion it may be to do with the location of the fonts?

I'll change the /etc/inetd.d/Xvnc file and... back in a moment

David

yes that did the trick... I also need to ensure I am logged into the correct display!

---

### Post by theDaveTheRave on 2009-05-07
Hello again.

This has now broken again after a reboot!

I'm trying to run tightvnc (rather than just "normal" vnc. looking at the tightvnc web site I get the impression that the protocols are the same  / very similar?

any ideas or advice would be greatfully received.

Thanks in advance

David

---

### Post by cherry316316 on 2009-05-07
> **theDaveTheRave said:**
> Hello again.

This has now broken again after a reboot!

I'm trying to run tightvnc (rather than just "normal" vnc. looking at the tightvnc web site I get the impression that the protocols are the same  / very similar?

any ideas or advice would be greatfully received.

Thanks in advance

David

this may be of some help 
[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)

---

### Post by theDaveTheRave on 2009-05-09
Cherry316316

Thanks for the link, reading that sounds like it should solve my problem, but it will be a couple of weeks before I can test it out properly... Although I will set this up on my personal system so as I don't need to take my laptop to work with me all the time!

However, it hasn't cleared up one of my main queries regarding the tightvnc (what the whole teams uses for the connecting to various remote pc's and Mac's) and "normal" vncviewer?

I notice when I downloaded tightvncserver / viewer via synaptic that the dependencies were titles vncviewer / vncserver (no "tight" in the name!), hence my assumption that they are using a similar method and are cross compatible. I just want to have someone tell me that I am correct or not in this regard... or someone point me to the correct place on the net that will tell me.

thanks again for your link, as I'm more certain now that it will solve my problem.

Cheers.

David

---

### Post by piyushj on 2009-05-15
i don't know if it will help any1--i got it working in 8.04.2 ubuntu with latest updates.

install vnc4server
make .vnc/xstartup file as
---
unset SESSION_MANAGER
exec sh /etc/X11/xinit/xinitrc
---
note the additional 'sh' above
------
run this
sudo mkdir /usr/X11R6/lib/X11
sudo mkdir /usr/X11R6/lib/X11/lib
sudo ln -s /usr/share/fonts/X11 /usr/X11R6/lib/X11/fonts
-----
u are done !!
set vncpasswd first and u r done !!

---

### Post by mikhmv on 2009-07-13
Does anybody know how to add vnc-java for resumable sessions?

---

### Post by cu_ on 2009-07-13
> **mikhmv said:**
> Does anybody know how to add vnc-java for resumable sessions?
Are you talking a bout using a java client?  Should be the same process.  Let me explain.  "Resumability" of a session is a property you set on the vnc server (parameter passed to Xvnc on the server side).  It should be resumable based on this property no matter which client you use.  So, whatever page you found for setting up vnc java applet and follow this thread to set up resumable session and it should work.  This is how I am set up.  

Let me know if you are running into issues.

---

### Post by mikhmv on 2009-07-13
CU_:
No, I meant of equivalent of using next line:
vnc4server :5 -httpport 6505 -httpd /usr/share/vnc-java
this command create listener for http request on port 6505. It is allow to connect to server by command [http://xx.xx.xx.xx:6505](http://xx.xx.xx.xx:6505) 
vnc-java client will be downloaded automatically and client will connect to port 5905. 

I tried to use this code for xinetd:
```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :5 -httpport 6505 -httpd /usr/share/vnc-java -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vnc/passwd -extension XFIXES
        port = 6505
}

```
But it don't work.

---

### Post by mikhmv on 2009-07-13
Just for info. How to install it on ubuntu server without any X. 
All operation was made under root account. If you are using another account you should modify
passwordFile=/your_user_name/.vnc/passwd

```

apt-get install screen xfce4  mousepad thunar-archive-plugin vnc4server vnc-java xserver-xorg-core xdm xinetd 

vnc4server :55
inter password for vnc
vnc4server -kill :55

```
------------------------------------------

edit xdm parameters:
---------------------------------------------------------------------
xdm

These changes are only required, if your display manager is XDM. If you use GDM or KDM, see the next sections.

Open /etc/X11/xdm/xdm-config with your favorite editor.

Look at the last line : "DisplayManager.requestPort: 0"

Comment it out by inserting a ! at the beginning of the line. File: /etc/X11/xdm/xdm-config

!DisplayManager.requestPort: 0

Edit /etc/X11/xdm/Xaccess and uncomment the line " '* #any host can get a login window" by removing the single quote. You could also change it to 192.168.0.* for some security 
(from: [http://en.gentoo-wiki.com/wiki/XVNC_Server#xdm](http://en.gentoo-wiki.com/wiki/XVNC_Server#xdm) )
--------------------------------------------------------------------
 
 edit services for xinetd:
 
 nano /etc/xinetd.d/Xvnc
 
```

 service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vnc/passwd -extension XFIXES
        port = 5901
}
 
```

---

### Post by chelrob on 2009-07-14
I switched to NoMachine NX.

Install SSH, NX client, NX node and NX server on the Ubuntu box you want to remote into and install NX client on the other PCs.

I have NX client intalled on XP, Vista and Ubuntu Jaunty desktop.  They can all remote to the Ubuntu box running NX server flawlessly.

It's faster than VNC and is more secure because it uses SSH to authenticate users.

NX is free, it works out of the box with the default configuration and you also have the ability to resume sessions with NX.

---

### Post by cherry316316 on 2009-07-15
this works for me


[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop]("http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop")

---

### Post by d3ngar on 2009-07-26
Hi, my problem is that the host machine has got me logged in, so when I try to connect it shows a message asking for permission.

Any solution?

Thanks,

Chris

---

### Post by puzzler on 2009-08-02
Hi,
Has anyone managed to get this working in 9.04 jaunty?
 
I followed the guide which worked for me on previous versions, but I cant get it to run any longer, I cant connect at all.

---

### Post by dmizer on 2009-08-03
> **puzzler said:**
> Hi,
Has anyone managed to get this working in 9.04 jaunty?
 
I followed the guide which worked for me on previous versions, but I cant get it to run any longer, I cant connect at all.

The default tools that have come with Ubuntu since Feisty have allowed you to configure resumable remote desktop sessions simply by going to system > preference > remote desktop. That's why this tutorial is in the "Outdated tutorials and tips" section. :)

Have you tried to configure remote desktop via this method and failed?

---

### Post by Syntax. on 2009-08-28
> **popie said:**
> Here are the instructions I use, and they work in v8.04.

[B]VNC Server w/Resumable Sessions on Ubuntu
Works in Ubuntu 7.04, 7.10, 8.04, and Mint 4 (Daryna)
[/B]

Make these changes while logged into gnome:

[LIST]
[*]Go to System -> Administration -> Login Window (General tab) and uncheck "Disable multiple logins for a single user."
[*]Now go to the Remote tab. Change Style: to "Same as Local"
[*]Still on the Remote tab, click "Configure XDMCP," then uncheck "Honor indirect requests."
[*]Enable Universe repositories in Synaptic. (this wasn't necessary in Ubuntu 8.04)
[/LIST]

**The remaining changes can be made while SSH'd into the system, or in a terminal window:**

[LIST]
[*]Edit /etc/gdm/gdm.conf-custom
[/LIST]
```
sudo nano /etc/gdm/gdm.conf-custom

```
add the following two lines to the existing [security] and [xdmcp] sections:
```

[security]
DisallowTCP=false
[xdmcp]
Enable=true

```
[LIST]
[*]Install packages:
[/LIST]
```
sudo apt-get install vnc4server xinetd
```
[LIST]
[*]Set the VNC password
[/LIST]
```
sudo vncpasswd /root/.vncpasswd
```
[LIST]
[*]Create a new file Xvnc to add the vnc service to xinetd:
[/LIST]
```
sudo nano /etc/xinetd.d/Xvnc
```
Paste these contents into the file:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

```
[LIST]
[*]Reboot
[/LIST]

That's it. I've used these exact instructions on three Ubuntu 8.04 installs without a hitch, as well as 7.04, 7.10, and Mint 4. Good luck.

I followed those instructions, on 64 bit 9.04. Whenever I try to VNC in I get a black dotted grey screen with a black x mouse. Google didn't really help me :( Any ideas?

---

### Post by Syntax. on 2009-08-28
Strange.. I just restarted the computer. SSH'd into it and started vnc4server. It came up with still the black mouse and grey dotted background but now a little terminal box popped up and I was able to type in it. No GUI though..

Edit - And I'm doing this because It's a headless server and FTP + SSH are nice.. But I like having the GUI.

---

### Post by goffa72 on 2009-09-18
> **Syntax. said:**
> I followed those instructions, on 64 bit 9.04. Whenever I try to VNC in I get a black dotted grey screen with a black x mouse. Google didn't really help me :( Any ideas?


I'm using Mythbuntu 8.10 and had the grey screen. After following the additional info from post #563 all works well.

> **ottotk said:**
> Hi!
I think is has something to do with ipv6 (My network is ipv4)

On file /etc/modprobe.d/aliases find the line containing 

and replace „ipv6“ with „off“. After reboot everything should work!

---

### Post by Nephiel on 2009-09-18
I just got Xvnc + xdm working on 9.04, but every time I try to open a GUI app from a xterm through a VNC connection I get this on the xterm:
```

Xlib: extension "RANDR" missing on display "mymachine:1.0".
Xlib: extension "Generic Event Extension" missing on display "mymachine:1.0".
Xlib: extension "Generic Event Extension" missing on display "mymachine:1.0".
Xlib: extension "Generic Event Extension" missing on display "mymachine:1.0".

```
The apps still work but the error messages are pretty annoying. I don't get them when logged on directly on my machine. Any ideas?

---

### Post by jearenas87 on 2009-09-21
> **Tichondrius said:**
> [B]Warning!
This howto is old, unsupported, and relies on a broken package. This should be used as reference only.[/B]

So here's the complete list of steps that are required to set the VNC server that any user can login into and start a session. It is also persistent, meanning that even if you disconnect the VNC client your X session will not end (unless you explicitly log out) and you can reconnect to the same session again. The VNC server uses a separate display (:1) than your regular X server, which works with your physical display (:0). So two sessions can be active at the same time (one person sitting at the physical display and another remotely connecting using VNC).

  1. Enable XDMCP
**System->Administration->Login Screen Setup**
      Tab **Security->Enable XDMCP**
      Tab **XDMCP**--> You can disable "Honor Indirect Requests"
    
Note: Before doing the next step, you need to make sure the extra repositories (e.g. universe) are enabled:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

  2. Install required packages (vncserver and xinetd)

```
sudo apt-get install vnc4server xinetd
```Note to AMD64 users: The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:

```

wget http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb
wget http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb
sudo dpkg -i vnc4server_4.0-7.3_amd64.deb
sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb

```
  3. Set the VNC passwd
```
sudo vncpasswd /root/.vncpasswd
```  4. Add vnc service to xinetd:
```
sudo gedit /etc/xinetd.d/Xvnc
```Enter this into the new file:

```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

```  5. Restart xinetd (usually there is no need to reboot, but occasionally it might be required)

```
sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start
```  6. That's it! To test that this is working first try to connect from the same machine (the machine we just set up the VNC server on):

```
vncviewer localhost:1
```You should be prompted for the VNC password, and then see the GDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above). Remember to use the VNC server machine's domain name or IP address, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails, then this means you have a problem with a firewall which is blocking some ports. See the notes below about how to deal with that.

Note about ports: The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

Note about security: This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started.  So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300"  to change it to 5 minutes.

when i do sudo killall Xvnc it gives me the below.
> 
root@worldstream-desktop:~# sudo killall Xvnc
Xvnc: no process killed


---

### Post by jearenas87 on 2009-09-21
```
vncviewer localhost:1
```

When i put that in, it gives me this message

```

root@worldstream-desktop:~# vncviewer localhost:1

VNC viewer for X version 4.0 - built Oct 19 2005 20:19:45
Copyright (C) 2002-2004 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
vncviewer: unable to open display ""

```

What could be wrong?

---

### Post by mmoo9154 on 2009-10-02
> **dmizer said:**
> The default tools that have come with Ubuntu since Feisty have allowed you to configure resumable remote desktop sessions simply by going to system > preference > remote desktop. That's why this tutorial is in the "Outdated tutorials and tips" section. :)

Have you tried to configure remote desktop via this method and failed?

I have tried this, and it failed.  I use TightVNC client on a Windows 7 (Win7) platform, and the Ubuntu is Hardy, Ubuntu 8.04.3 LTS.

The VNC session starts and then fails.  If I uninstall vino and install vnc4server, it works fine.

I'm going to try Xvnc next to see if that works better.

-Mark

---

### Post by backtolinux on 2009-11-05
Here's a way to get it set up on Ubuntu 9.04 jaunty:

[http://saraiya.com/blog/2009/11/06/how-to-get-vnc-working-with-a-hidden-desktop-on-ubuntu-9-04-jaunty/](http://saraiya.com/blog/2009/11/06/how-to-get-vnc-working-with-a-hidden-desktop-on-ubuntu-9-04-jaunty/)

---

### Post by SBKch on 2009-11-08
After upgrade to Ubuntu 9.10 i have non-stop gdm errors, so i must "service gdm stop" it, right after server start (load). /var/log/syslog:

Nov  9 01:28:23 nexem gdm-binary[17829]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Nov  9 01:28:23 nexem kernel: [24091.516477] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:23 nexem init: gdm main process (17829) terminated with status 1
Nov  9 01:28:23 nexem init: gdm main process ended, respawning
Nov  9 01:28:23 nexem gdm-binary[17871]: WARNING: Unable to find users: no seat-id found
Nov  9 01:28:23 nexem kernel: [24091.700349] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:23 nexem gdm-binary[17871]: WARNING: GdmDisplay: display lasted 0,116247 seconds
Nov  9 01:28:23 nexem kernel: [24091.745531] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:23 nexem kernel: [24091.813181] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:23 nexem gdm-binary[17871]: WARNING: GdmDisplay: display lasted 0,110766 seconds
Nov  9 01:28:23 nexem kernel: [24091.856681] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:23 nexem kernel: [24091.924367] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:24 nexem gdm-binary[17871]: WARNING: GdmDisplay: display lasted 0,109573 seconds
Nov  9 01:28:24 nexem kernel: [24091.966587] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:24 nexem kernel: [24092.035196] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:24 nexem gdm-binary[17871]: WARNING: GdmDisplay: display lasted 0,110129 seconds
Nov  9 01:28:24 nexem kernel: [24092.077081] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:24 nexem kernel: [24092.149128] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:24 nexem gdm-binary[17871]: WARNING: GdmDisplay: display lasted 0,109363 seconds
Nov  9 01:28:24 nexem kernel: [24092.186805] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:24 nexem kernel: [24092.253891] [drm:intelfb_restore] *ERROR* Failed to restore crtc configuration: -22
Nov  9 01:28:24 nexem gdm-binary[17871]: WARNING: GdmDisplay: display lasted 0,109566 seconds
Nov  9 01:28:24 nexem gdm-binary[17871]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors 

In attachment there is log after "vncserver :1 -geometry 1440x898 -depth 32" command

I use Ubuntu server (2.6.31-14-server #48-Ubuntu SMP x86_64 GNU/Linux) on non-monitor/keyboard/mouse machine.
What the heck went wrong?

---

### Post by covert on 2009-11-23
I have got a virtual second screen running and it works great, now.. How do I enabled VNC to the normal screen at the same time ?

---

### Post by pbreddy on 2009-11-25
change this line from '/usr/share/X11/fonts/misc' to '/usr/share/fonts
/X11/misc'. 

Repeat step 5. then execute below(at terminal):

'vncserver'

It worked for me. Please, let me know comments.

---

### Post by vishnu.patel on 2009-12-02
[quote=Tichondrius;688683]From your description it seems that after the reboot xinetd is listening on port 5901 and the setup is correct.

xinetd is supposed to start Xvnc as soon as it gets an incoming connection from a VNC client.

I assume you copied /etc/xined.d/Xvnc exactly from this howto without changing anything, right ?  if so, then maybe the fact you are using the old vnc sever (version 3.x) is related because it might not support some of the arguments ?   

After you start the vncviewer, xinetd should spwan Xvnc with the arguments specified in the Xvnc file we created in step 3.  So immediately after starting vncviewer (and even before entering the vnc password), you can check the Xvnc started by issueing this command:

```
ps -ef | grep Xvnc
```This should show something like this:



If it doesn't work it means that Xvnc wasn't started. So in that case I would suggest to try starting Xvnc manually (not from within xinetd)  just to make sure it can run at all (we will use screen :2 so it doesn't overlap with the original Xvnc):

[code]sudo Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd}


I tried above command but i have 


[COLOR=Red]Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Thu Dec  3 10:04:42 2009
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/misc, removing from list!

Fatal server error:
could not open default font 'fixed'



[COLOR=Black]I could not understand what[/COLOR] [COLOR=Black] could be the problem ?[/COLOR]
[/COLOR]

---

### Post by auraithx on 2010-01-22
Okay, after trials and tribulations I think I've got it setup right.

```
root@hostname:~# sudo netstat -tap | grep xinetd
tcp        0      0 *:5901                  *:*                     LISTEN      7047/xinetd
root@hostname:~# vncserver

New 'hostname:5 (root)' desktop is hostname:5

Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/hostname:5.log

root@hostname:~# vncviewer localhost:1
Error: Can't open display:

```

I figure the last error is because I'm accessing my server via SSH? 

However, when I open up VNC viewer on windows and try to connect I get a 'Connection Refused' error

---

### Post by liquidonline on 2010-05-05
I had this working fine (with a few tweaks here and there, as noted throughout this thread) on jaunty.  I've moved to Lucid and it seems there's no hope of getting a remote desktop connection to my PC unless I've already logged in - quite useless on a headless machine.

I've been trying for some time to get this working on lucid.  I didn't upgrade to karmic for this, but I took the plunge to lucid now determined to get this to work.  I can't be the only one trying to do this.  The one that comes with ubuntu is horrible, lacks any configuration options, and doesn't work if 1: you're running headless, or 2: you're not already logged in.  To boot, my desktop has a 22inch and 19inch monitor.  A 2000(something)x1050 VNC session with the full colors is hardly responsive.

Isn't there anyone here who is doing this on ubuntu? I mean, if I wanted to have a console-only server, with all due respect, I would be using a bsd, or at least some other form of linux than ubuntu...

At this point, I don't care if I have to login to ssh first, which sucks as I need to ssh to the router before hand (running openbsd, and refreshingly, well documented btw... very frustrated with lack of documentation so far) and run a handful of commands to get a remote desktop.  Not ideal, but it would be a start.

Big fail for ubuntu if even jumping through hoops doesn't get you a useable remote desktop.

---

### Post by Crass Spektakel on 2010-05-05
[FONT="Arial Black"][SIZE="5"]Lucid Lynx: Works out of the box with very little work![/SIZE][/FONT]

I'll do a sum up of all options required to make VNC over XDMCP managed log in session displaying X11 applications on a perfectly fresh Lucid Lynx.

On Port 5920 you'll get a dynamic login session, that means, several clients can connect to this vnc port, getting a gdm login and a session running as long as the window is open. Closing the window is synonymous for logging out or killing your window manager. Very convenient to allow for "lots of normal users" to log into a computer at once.

On Port 5925 you'll get a static login session, one person can connect and works on a persistant screen which keeps its data between disconnects. Very helpful for administration purposes.

```
aptitude install vnc4server xinetd
vncpasswd /etc/vncpasswd-semipublic
```

edit /etc/services and add something like

```
vnc1024         5920/tcp
SV1024          5925/tcp
```

create /etc/xinetd.d/Xvnc containing something like:

```
root@boni:/etc/gdm# cat /etc/xinetd.d/Xvnc
service vnc1024
{
  disable = no
  socket_type = stream
  protocol = tcp
  wait = no
  user = nobody
  server = /usr/bin/Xvnc4
  server_args = -inetd -desktop boni-loginvnc-1024 -query localhost -geometry 1024x768  -once -depth 16 -fp /usr/share/fonts/X11/misc -SecurityTypes=none
}

service SV1024
{
  disable = no
  socket_type = stream
  protocol = tcp
  wait = yes
  user = root
  server = /usr/bin/Xvnc4
  server_args = -inetd :25 -desktop boni-staticvnc-1024 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc/ -DisconnectClients=0 -NeverShared passwordFile=/etc/vncpasswd-semipublic
}

```

next create or edit /etc/gdm/custom.conf:
**edit:** I insert jocko_johnson settings here, they avoid several problems.

```
[daemon]
[security]
DisallowTCP=false
[xdmcp]
Enable=true
HonorIndirect=false
#following line fixes a problem with login/logout
DisplaysPerHost=2
MaxSessions=16
[greeter]
[chooser]
[debug]
Enable=true
```

You might try creating /etc/X11/xserver/SecurityPolicy but I think it might be useless/harmful:

```
version-1 

# $Xorg: SecurityPolicy,v 1.3 2000/08/17 19:47:56 cpqbld Exp $

# The site policy fields are interpreted by the XC-QUERY-SECURITY-1
# authorization protocol.  The values are arbitrary and site-specific.
# Refer to the Security Extension Specification for the usage of the policies.
#sitepolicy A
#sitepolicy B
#sitepolicy C

# Property access rules:
# property <property> <window> <permissions>
# <window> ::= any | root | <propertyselector>
# <propertyselector> ::= <property> | <property>=<value>
# <permissions> :== [ <operation> | <action> | <space> ]*
# <operation> :== r | w | d
#	r	read
#	w	write
#	d	delete
# <action> :== a | i | e
#	a	allow
#	i	ignore
#	e	error

# Allow reading of application resources, but not writing.
property RESOURCE_MANAGER	root	ar iw
property SCREEN_RESOURCES	root	ar iw

# Ignore attempts to use cut buffers.  Giving errors causes apps to crash,
# and allowing access may give away too much information.
property CUT_BUFFER0	root	irw
property CUT_BUFFER1	root	irw
property CUT_BUFFER2	root	irw
property CUT_BUFFER3	root	irw
property CUT_BUFFER4	root	irw
property CUT_BUFFER5	root	irw
property CUT_BUFFER6	root	irw
property CUT_BUFFER7	root	irw

# If you are using Motif, you probably want these.
property _MOTIF_DEFAULT_BINDINGS	root	ar iw
property _MOTIF_DRAG_WINDOW	root	ar iw
property _MOTIF_DRAG_TARGETS	any 	ar iw
property _MOTIF_DRAG_ATOMS	any 	ar iw
property _MOTIF_DRAG_ATOM_PAIRS	any 	ar iw

# If you are running CDE you also need these
property _MOTIF_WM_INFO		root	arw
property TT_SESSION		root	irw
property WM_ICON_SIZE		root	irw
property "SDT Pixel Set"	any	irw

# The next two rules let xwininfo -tree work when untrusted.
property WM_NAME	any	ar

# Allow read of WM_CLASS, but only for windows with WM_NAME.
# This might be more restrictive than necessary, but demonstrates
# the <required property> facility, and is also an attempt to
# say "top level windows only."
property WM_CLASS	WM_NAME	ar

# These next three let xlsclients work untrusted.  Think carefully
# before including these; giving away the client machine name and command
# may be exposing too much.
property WM_STATE	WM_NAME	ar
property WM_CLIENT_MACHINE	WM_NAME	ar
property WM_COMMAND	WM_NAME	ar

# To let untrusted clients use the standard colormaps created by
# xstdcmap, include these lines.
property RGB_DEFAULT_MAP	root	ar
property RGB_BEST_MAP	root	ar
property RGB_RED_MAP	root	ar
property RGB_GREEN_MAP	root	ar
property RGB_BLUE_MAP	root	ar
property RGB_GRAY_MAP	root	ar

# To let untrusted clients use the color management database created
# by xcmsdb, include these lines.
property XDCCC_LINEAR_RGB_CORRECTION	root	ar
property XDCCC_LINEAR_RGB_MATRICES	root	ar
property XDCCC_GRAY_SCREENWHITEPOINT	root	ar
property XDCCC_GRAY_CORRECTION	root	ar

# To let untrusted clients use the overlay visuals that many vendors
# support, include this line.
property SERVER_OVERLAY_VISUALS	root	ar

```

additional infos:

-sometimes you have to add "-extension XFIXES" to /etc/xinetd.d/Xvnc at "server_args".
-if telnet <system> 5920 fails with "can't connect" then you xinetd doesn't work
-if telnet <system> 5920 closes fast or your VNC client reports "unknown Plugin/whatever" then your X "-extension XFIXES" must be changed.
-if telnet <system> 5920 hangs completely try restarting your system
-if your vnc session is showing nothing except the default X11 pattern then your gdm isn't listening, see /etc/gdm/custom.conf
-always check /var/log/syslog
-change the resolutions in /etc/xinetd.d/Xvnc with -geometry
-there you'll also find color depth, depth 16 sometimes falls back to depth 8 with a 233 mapping, ugly colors result. Try using depth 8 "flat color" or "color tables" (TODO) or depth 24 which might work better or worse. Your milage may vary.
-play around with vncconfig for copy-and-paste and other nifty stuff.

About me: I think I have been one of the very first users getting a XDM/GDM-Login over VNC, a long time ago, before Xvnc, sometimes around 1999, running SuSE 6.3. Most nowadays FAQs are more or less based on my old FAQ. So if you have a question I might be the best person to ask - though I must admit that a lot of things have changed, a lot more since Ubuntu8.04 than all the time before, lots of configs have totally changed or changed position, patches no longer working and so on. Therefore I would suggest to make this topic a new one.

---

### Post by liquidonline on 2010-05-05
Wow, thanks for the feedback.  While your point about starting a new thread is valid, I think many people still come to this thread, and it's worthwhile to update this.  Once I have a fully documented process, I'll gladly start up a new thread as a reliable Howto for lucid (and really, gdm > 2.28 ).

Your post motivated me.  Likely due to everything I had been tinkering with, and likely why nothing was working anymore when I decided to post this, I couldn't get this to work at first.  I figured, it's a 4-day old install, I hadn't even restored backups, so I decided to reinstall ubuntu-server.  My experience is summarized below.  I'm hoping you can lend a helping hand.  I'm a bsd sysadmin by trade, I never really used X for anything, so I know very little of it.  I just know enough to know doing it within the confines of what's available ported to BSD is painful ;)

==========

Post reinstall, it still didn't work at first.  My needs don't require two vnc server sessions running, I went with one based on my needs.  No matter what I did, xfixes there or not, restart gdm, it wouldn't go.  Tried matching more closely yours (the second of the two), still didn't work.

So next, I tried using your exact /etc/xinetd.d/Xvnc file (besides obvious necessary changes to reflect my system), only one service would start, the other would (quietly) fail.  Consistently, the one setup to run as nobody would not start up.  Changing the "wait" to yes and user to root did not help this. Interestingly though, the second one suddenly worked (after putting the two services, prior to any modifications)!  I have no explanation for this, but one would be nice, as it would help understand more what's going on.  Here is what the /etc/xinetd.d/Xvnc file looks like now (/etc/services reflects screen numbers used).  I can access the "service vncbig" using this.  Regardless if I used -extension XFIXES or not, the first one would time out on telnet instantly, as you'll see below the snippet from my syslog

```

service vncsmall
{
  disable = no
  socket_type = stream
  protocol = tcp
  wait = no
  user = nobody
  server = /usr/bin/Xvnc4
server_args = -inetd -desktop zeus-1024x768 -query localhost -geometry \
1100x800  -once -depth 15 -fp /usr/share/fonts/X11/misc \
-SecurityTypes=none -extension XFIXES
}

service vncbig
{
  disable = no
  socket_type = stream
  protocol = tcp
  wait = yes
  user = root
  server = /usr/bin/Xvnc4
  server_args = -inetd :5 -desktop zeus-HiQ -query localhost -geometry \
1280x1024 -depth 16 -once -fp /usr/share/fonts/X11/misc/ \
-DisconnectClients=0 -NeverShared -SecurityTypes=none
}

```

From syslog:

May  5 21:11:15 zeus xinetd[20950]: bind failed (Address already in use (errno = 98)). service = vncbig
May  5 21:11:15 zeus xinetd[20950]: Service vncbig failed to start and is deactivated.
May  5 21:11:15 zeus xinetd[20950]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
May  5 21:11:15 zeus xinetd[20950]: Started working: 1 available service
May  5 21:11:25 zeus xinetd[20953]: warning: can't get client address: Transport endpoint is not connected
May  5 21:12:59 zeus gdm-session-worker[20689]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 21:13:03 zeus gnome-session[20978]: WARNING: GSIdleMonitor: IDLETIME counter not found
May  5 21:13:03 zeus rtkit-daemon[21046]: Sucessfully called chroot.
May  5 21:13:03 zeus rtkit-daemon[21046]: Sucessfully dropped privileges.
May  5 21:13:03 zeus rtkit-daemon[21046]: Sucessfully limited resources.
May  5 21:13:03 zeus rtkit-daemon[21046]: Running.
May  5 21:13:03 zeus rtkit-daemon[21046]: Watchdog thread running.
May  5 21:13:03 zeus rtkit-daemon[21046]: Canary thread running.



Not out of the woods yet though.  Seems like the fast-user-switching (or something related to it anyway) fails when I login.  I only mention this because I wonder if it's related to the following problem:  If I log out of the session to close vnc server, I can no longer log back in, until I reboot.  restarting gdm or restarting xinetd is of no help.  If I simply "X" the window closed, then I can log back into it. Is this something that an Xstartup file would be able to help with by any chance?

Here's what I get on each login:
[IMG]http://mail.obsecured.net/fusa.png[/IMG]

So.  While there's signifcant progress made, the one thing above all that really gets to me is why I need to run two vnc servers, in order to get one to work!?!?!?

update: Upon reboot, now I noticed in syslog that it reports both of them as up and running, though ps shows only the second of the two, and I still get an instant timeout on connect to the first one (running as user nobody)

---

### Post by liquidonline on 2010-05-06
OK, regarding the whole "unable to vnc back in if I logout" thing, it's worth noting that I'm running ubuntu-server on this machine, and I simply installed gnome-desktop-environment instead of the clunkier ubuntu-desktop.  Not knowing whether or not this is responsible for that odd behaviour, I'm now in the process of installing ubuntu-deskstop and we'll see if that makes any sort of difference in the morning.


Some other stuff I've noticed:

For clarity:  In /etc/xinetd.d/Xvnc, when I went to setting up two services as was shown to us by crass, I named the first one "vncsmall" and the second "vncbig," the latter of which is the one which runs as root.  BTW, still not sure how the one running unprivileged as nobody runs exactly.  Ok, moving right along...

In syslog, the error msgs indicate the service "vncbig" (see above) couldn't bind to the requested port because it's already in use.  However, when I connected to :5, which is the one designated for "vncbig" I was able to connect:  Here's what I'm talking about:


May  5 20:58:06 zeus xinetd[20767]: Reading included configuration file: /etc/xinetd.d/Xvnc [file=/etc/xinetd.conf] [line=14]

***SNIP*** (other services)

May  5 20:58:06 zeus xinetd[20767]: bind failed (Address already in use (errno = 98.)). service = vncbig
May  5 20:58:06 zeus xinetd[20767]: Service vncbig failed to start and is deactivated.
May  5 20:58:06 zeus xinetd[20767]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
May  5 20:58:06 zeus xinetd[20767]: Started working: 1 available service
May  5 20:58:21 zeus xinetd[20767]: Exiting...


==============================================

Now, back to my observation that the two VNC's started up according to syslog on reboot.  Here's what I mean:

May  5 21:18:30 zeus xinetd[21315]: Reading included configuration file: /etc/xinetd.d/Xvnc [file=/etc/xinetd.conf] [line=14]

**SNIP** same again

May  5 21:18:30 zeus xinetd[21315]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
May  5 21:18:30 zeus xinetd[21315]: Started working: 2 available services
May  5 21:19:23 zeus xinetd[21323]: warning: can't get client address: Transport endpoint is not connected
May  5 21:19:27 zeus xinetd[21325]: warning: can't get client address: Transport endpoint is not connected


Those warning messages are what appears at the same time as I get the connection reset by peer when I try to telnet or vnc to the server.

---

### Post by muhnkee on 2010-05-13
Hey I went through and installed vnc4server, xinetd and set everything up as in this guide on an Ubuntu 10.04 Lucid Lynx machine.  Everything worked phenominally.  
 
Then I made what is apparently a huge mistake and did a sudo apt-get upgrade. Now I get the gray screen with the old style x cursor.  It even gives me the gray screen when I run the vncserver from the desktop and try to login. 
 
If I try to do it with vnc4server straight from the command line and attempt to connect, I get the additional "Could not acquire name on session bus."  
 
If I use the Xvnc4 command, I get "error opening security policy file /etc/X11/xserver/SecurityPolicy" in the terminal and get the gray screen when I try to VNC to the display.  
 
The ~/.vnc/passwd file is there and being referenced in /etc/xinetd.d/Xvnc file. 
 
Now if I login as root and run through things manually it works like a charm. 
 
I've read through a majority of the 60 pages of this posting, some other ones and still can't find a solution to my problem.   Any ideas?

---

### Post by DaleEMoore on 2010-05-23
These are great instructions and served me well on Ubuntu 8.04. But I just upgraded to 10.04 and Xvnc is not responding to vncviewer.

I would love it if someone had any guidance on how to setup Xvnc for Ubuntu 10.04.

Any suggestions are very much appreciated,
Dale E. Moore
PS: My upgrade method was:
[LIST=1]
[*]"update-manager -d" from 8.04 to 9.10
[*]"do-release-upgrade" from 9.10 to 10.04
[/LIST]

---

### Post by Wolfpup on 2010-05-25
> **DaleEMoore said:**
> These are great instructions and served me well on Ubuntu 8.04. But I just upgraded to 10.04 and Xvnc is not responding to vncviewer.

I would love it if someone had any guidance on how to setup Xvnc for Ubuntu 10.04.

Any suggestions are very much appreciated,
Dale E. Moore
PS: My upgrade method was:
[LIST=1]
[*]"update-manager -d" from 8.04 to 9.10
[*]"do-release-upgrade" from 9.10 to 10.04
[/LIST]

  Actually with the newer versions you can configure a remote desktop from System>Personal>Remote Desktop.

That is how i have done mind and i also have a good Linksys Roughter that lest me set the ip of computer on my network so that the have a static ip in the roughter, I also have a free domain form a place that prodied them and with the new roughter i even have accec to my 'server' that is at home when im at work. as well on my local network by useing VNC viewer on those windows based systems.

---

### Post by PhDLinux on 2010-05-27
Thanks to Crass Spektakel for Post #605 above! I got this working on Lucid Lynx, Ubuntu Studio edition, with some minor changes. 

Here is an exact copy of one stanza in my file /etc/xinetd.d/Xvnc. This one serves the netbook:
```

service vnc1024x600
{
  type           = UNLISTED
  disable        = no
  port           = 5911
  socket_type    = stream
  protocol       = tcp
  wait           = no
  user           = nobody
  server         = /usr/bin/Xvnc4
  server_args    = -inetd -once -SecurityTypes None -geometry 1000x600 -depth 24 -fp /usr/share/fonts/X11/misc/ -co /usr/share/X11/rgb -query localhost
  log_type       = SYSLOG daemon info
  log_on_failure = HOST
  log_on_success = PID HOST EXIT
}
```
The added logging commands helped me figure out some changes suggested below. 

I inserted one corresponding line in the lengthy file /etc/services, as follows:
```
vnc1024x600     5911/tcp			# VNC 1024x600  @ 24bpp
```
(Perhaps the "UNLISTED" directive in the Xvnc file makes this redundant, but I want to thoroughly document everything. The port number 5911 shown here must match the port number declared in the Xvnc file shown above.) 

Here is my key difference from the cited post (without this my connection attempts would flash a grey X screen for a fraction of a second and then quit). I had to add two extra lines to the end of the suggested gdm configuration file. Here is an exact copy of my complete file /etc/gdm/custom.conf:
```

[security]
DisallowTCP=false
[xdmcp]
Enable=true
MaxSessions=16
DisplaysPerHost=2
```

The cited post also mentions a file named /etc/X11/xserver/SecurityPolicy. My system does not even have a directory named /etc/X11/xserver, so I skipped the creation of this file. The setup works anyway.

Every time you change the file /etc/xinetd.d/Xvnc, it is necessary to restart the xinetd server *as root* ("sudo /etc/init.d/xinetd restart"). [When I forgot "sudo", the system supplied a user-mode xinetd server in addition to the system-wide one, and things got confusing.] Similarly, changes to /etc/gdm/custom.conf don't actually take effect until you restart the display manager ("sudo service gdm restart"). Note that restarting gdm terminates your session completely and sends you back to the login screen instantly.

As a preliminary step, I used the command line to practice giving the Xvnc command that the xinetd daemon would ultimately emit. I picked a port number different from the ones xinetd was busy listening to (my choice was 5903) and replaced the option "-inetd" with the string ":3" to get this command. No need to run as root:
```

$ Xvnc4 :3 -SecurityTypes None -geometry 1000x600 -depth 24 -fp /usr/share/fonts/X11/misc/ -co /usr/share/X11/rgb -query localhost
```
Seeing a small-sized greeter screen in response to "vncviewer localhost:3" meant it was safe to take the next step and get xinetd involved. Of course there were many failures before this point, and they came with helpful messages -- something you don't get when relying on xinetd!

---

### Post by errodrigues on 2010-05-28
Thanks a lot Crass Spektakel!!! Ihad already spent more than 1 day trying to make this thing work on my Lucid and your instructions did the trick.

I don't need 2 services running so I just created 1 and it works like a charm now. Only thing I added was including "gdm: localhost" to file /etc/hosts.allow

Thanks again!

---

### Post by vyath on 2010-06-21
I managed to set things up like Spektakel and it works great, only now if I remotely login and try to access a connected USB drive (from "places", for example) I get
"Unable to mount X filesystem, Not authorized"

How do I fix it?

---

### Post by KillerPancake on 2010-07-14
After trying a lot of different things, I was FINALLY able to get a VNC server up and working reliably (sort of!) on 10.04.  It was the sage advice of Crass Spektakel and PHDLinux that did the trick.

My goal is to setup a headless server that can live in the basement, toiling in obscurity while not taking up any space or generating heat in prime living space.  Having gotten everything set up and working well, I dragged the box downstairs and started it up.  Fired up the VNC viewer on my laptop and only got the X11 screen when connecting to the server, so I dragged the box back upstairs to investigate. Started up the box again, and this time no problems with the VNC viewer on the laptop.  So, back downstairs with the machine, and again only got the X11 screen in the VNC viewer.  What, is the machine lonely in the basement and protesting!?  Other than this issue, the machine seems fine and I can access shares without problems, no matter where the server is.

So one of two things is happening:
1) Something is happening due to the difference in location - main difference in the basement is that keyboard, monitor and mouse are not connected and a different Ethernet cable connects the server to a switch 
2) Some problem is occurring intermittently and its just coincidence that it shows up when the computer is moved to the basement

I would appreciate anyone's insight as to what might be happening here!  Below are the outputs of the VNC viewer during a good connection, followed by a failed connection with X11 screen only.

Successful connection:
Tue Jul 13 23:29:34 2010
 CConn:       connected to host 192.168.1.105 port 5920
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding

Tue Jul 13 23:29:37 2010
 CConn:       Throughput 4000 kbit/s - changing to hextile encoding
 CConn:       Throughput 4000 kbit/s - changing to full colour
 CConn:       Using pixel format depth 24 (32bpp) little-endian rgb888
 CConn:       Using hextile encoding

Failed connection (note the last 5 lines are missing compared to above):
Wed Jul 14 00:02:25 2010
 CConn:       connected to host 192.168.1.105 port 5920
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding

---

### Post by Crass Spektakel on 2010-07-17
> **Wolfpup said:**
> Actually with the newer versions you can configure a remote desktop from System>Personal>Remote Desktop.

 This is different from the objective of this topic:

 Your method allows for remote control of the local, physical screen (though i must say this has always been very edgy and unreliable within ubuntu for me).

 This topic is about creating virtual sessions, eg. if someone connects to port 5920 he will get a seperate VNC session not connected to the local, physical screen. This also means that several people can log in over VNC and work seperately. This has proven to be rockstable even with 10 or more people logging in at once.

 --- cut ---

> **PhDLinux said:**
> Thanks to Crass Spektakel for Post #605 above!

 I have to thank you too, your logging-statements are pretty helpful. About the following:

> **PhDLinux said:**
> 
```

[security]
DisallowTCP=false
[xdmcp]
Enable=true
MaxSessions=16
DisplaysPerHost=2
```

 I am pretty sure that the last two lines are NOT required - they are useful sometimes though. Try putting one or two blank lines there instead and it will work too.

 Reason: Many unix tools have a problem reading config files which don't end in a newline so basically the last line "Enable=true" gets ignored. I think this has been haunting us since before mankind visited the moon :-)

---

### Post by scaltro on 2010-08-05
This tutorial seems to be very helpful thanks to all...

But unfortunately I have some problems....
When I'm trying to connect to my vnc server, I got a grey window in which I'm able to move the cursor, but nothing else... Any idea?

My /etc/gdm/custom.conf  is as default:
```
[daemon]

[security]
DisallowTCP=false

[xdmcp]
Enable=true
```

I'm working on a fresh install of Ubuntu 10.04.

---

### Post by Crass Spektakel on 2010-08-15
Now I have run into something odd myself...

I have four nearly identically configured systems. One of them decided to display the grey screen upon vnc connect from time to time.

Restarting xinetd and gdm doesn't do the trick but rebooting does. I really have no idea where this comes from as all log file are clean and nice. It only happens rarely so I haven't investigated much. I think I did some inner works on the system though, lots of updates, configuring, changing runlevels, all that will produce the effect pretty reliable. But sometimes, once a month or less, it happens without good reason at all.

[SIZE="4"]Keep in mind: If things dont work, reboot.[/SIZE]

---

### Post by howardjacobson on 2010-09-17
As of September 17, 2010, the instructions most recently posted on pages 61 and 62 of this thread work for Lucid 10.04.  Thank you to all for the great help!

---

### Post by jmontani on 2010-09-20
what should I write in the server parameter in a home network? I only
have the computers names available (i.e pc01; pc02, etc)

---

### Post by popzero on 2010-09-24
> **KillerPancake said:**
> After trying a lot of different things, I was FINALLY able to get a VNC server up and working reliably (sort of!) on 10.04.  It was the sage advice of Crass Spektakel and PHDLinux that did the trick.

My goal is to setup a headless server that can live in the basement, toiling in obscurity while not taking up any space or generating heat in prime living space.  Having gotten everything set up and working well, I dragged the box downstairs and started it up.  Fired up the VNC viewer on my laptop and only got the X11 screen when connecting to the server, so I dragged the box back upstairs to investigate. Started up the box again, and this time no problems with the VNC viewer on the laptop.  So, back downstairs with the machine, and again only got the X11 screen in the VNC viewer.  What, is the machine lonely in the basement and protesting!?  Other than this issue, the machine seems fine and I can access shares without problems, no matter where the server is.

So one of two things is happening:
1) Something is happening due to the difference in location - main difference in the basement is that keyboard, monitor and mouse are not connected and a different Ethernet cable connects the server to a switch 
2) Some problem is occurring intermittently and its just coincidence that it shows up when the computer is moved to the basement

I would appreciate anyone's insight as to what might be happening here!  Below are the outputs of the VNC viewer during a good connection, followed by a failed connection with X11 screen only.

Successful connection:
Tue Jul 13 23:29:34 2010
 CConn:       connected to host 192.168.1.105 port 5920
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding

Tue Jul 13 23:29:37 2010
 CConn:       Throughput 4000 kbit/s - changing to hextile encoding
 CConn:       Throughput 4000 kbit/s - changing to full colour
 CConn:       Using pixel format depth 24 (32bpp) little-endian rgb888
 CConn:       Using hextile encoding

Failed connection (note the last 5 lines are missing compared to above):
Wed Jul 14 00:02:25 2010
 CConn:       connected to host 192.168.1.105 port 5920
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
 TXImage:     Using default colormap and visual, TrueColor, depth 24.
 CConn:       Using pixel format depth 6 (8bpp) rgb222
 CConn:       Using ZRLE encoding


I think I hit the same issue as you did with this one, mine was after doing an upgrade from 8.04 LTS to 10.04 LTS for my headless/mouseless/keyboardless server. :)

Took me a while to figure this one out; finally found it by forcing my system to disable kernel mode setting. There's a description of what is needed to disable it here: [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
I used the change listed for radeon cards and then it forced my X system to use the vesa setup. (Note: in my /etc/modprobe.d/ directory it didn't have any of the file names listed under "Turning it off"; the purpose of the link is to create the files using the echo command...the webpage didn't really make that clear so I like to be extra explicit :) ). This little gem of an issue drove me crazy for a day wondering WTH was going on with that dam grey X display mouse doing remote vnc access. 

Oh one other thing I've found that might be helpful is putting "DisplaysPerHost=2" in my /etc/gdm/custom.conf file under the [xdmcp] section so it looks like this: 
[security]
      DisallowTCP=false
[xdmcp]
      Enable=true
      HonorIndirect=false
      DisplaysPerHost=2

If I don't have this in my config each time I logout using the UI it won't let me log back in (gives that stupid timeout "111" error in the terminal). That might be why PhDLinux added that into the custom.conf file. 

Hope this helps some of my fellow Ubuntu users

---

### Post by jocko_johnson on 2010-10-08
I am only able to get the grey X11 screen.  can someone please look at my setup and point me in a direction to resolve this?


I am running 10.04, fresh install, all updates current.

Here are my files:

/etc/xinetd.d/Xvnc
```

service xvnc
{
	disable = no
	socket_type = stream
	protocol = tcp
	wait = no
	user = nobody
	server = /usr/bin/Xvnc4
	server_args = -inetd -desktop xvncDesk -query localhost -geometry 1024x768 -once -depth 16 -fp /usr/share/fonts/X11/misc -SecurityTypes=none
	log_type = SYSLOG daemon info
	log_on_failure = HOST
	log_on_success = PID HOST EXIT
}

service xvncResumable
{
	disable = no
	socket_type = stream
	protocol = tcp
	wait = yes
	user = me
	server = /usr/bin/Xvnc4
	server_args = -inetd :88 -desktop xvnc-resumableDesk -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc/ -DisconnectClients=0 -NeverShared passwordFile=/home/me/.vnc/passwd
	log_type = SYSLOG daemon info
	log_on_failure = HOST
	log_on_success = PID HOST EXIT
}
```

/etc/gdm/custom.conf

```


[daemon]

[security]
DisallowTCP=false

[xdmcp]
Enable=true
HonorIndirect=false
#following line fixes a problem with login/logout
DisplaysPerHost=2
MaxSessions=16

[greeter]

[chooser]

[debug]
Enable=true
```

/etc/services
I added these lines
```

#added by me 10.6.2010 for xvnc server
xvnc		5908/tcp
xvncResumable	5988/tcp

```

/etc/hosts.allow
I added this line
```
gdm: localhost
```


I am testing this locally on the server with the commands:
```
 Xvnc :4 -query localhost -geometry 1024x768 -once -depth 16 -fp /usr/share/fonts/X11/misc -SecurityTypes=none
``` 
and
```
sudo Xvnc :3 -query localhost -geometry 1024x768 -once -depth 16 -fp /usr/share/fonts/X11/misc -SecurityTypes=none passwordFile=/home/me/.vnc/passwd
```

as well as trying to connect from a different machine within my LAN and also from my work computer via ssh tunnelling/x11 forwarding ( ssh is configured to allow x11forwarding ).

no matter what the results are the same:

I get the x11 window but I only seethe grey speckled screen with the giant "X" for a cursor - no login window

would really appreciate if someone knows how to fix this.

---

### Post by r0ck3t on 2010-10-24
> **jocko_johnson said:**
> I am only able to get the grey X11 screen.  can someone please look at my setup and point me in a direction to resolve this?

 
Hi,

just registered, hope this helps: I had exactly the same setup and the same problem, some of the last updates broke it...
I disabled IPV6 and everything works as expected (saw some strange errors in the gdm logs).

Cheers

---

### Post by jocko_johnson on 2010-10-24
thanks for the suggestion.

sorry if this is a dumb question...

how do you disable IPv6?


------
edit - found my answer i think:

[http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html]("http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html")

---

### Post by eti.que on 2011-01-01
Just to mention, this is indeed a bug with GDM, listening to ipv6 only:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=563406](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=563406)

It is fixed already. For now... disabling ipv6 will do the trick !

---

### Post by sebu18 on 2011-01-03
Hi, i'm kind of new and didn't want to start a new thread so i ask here. How can i connect to my httpc running win 7 and vnc, from my desktop running ubuntu 10.04. I tried the methods i found on google. None of them worked. I don't want to turn on the tv when i want to make a change in the torrent client, or delete some movies. 

Can you also give me a  link with a tutorial on connecting to the shared windows drives from ubuntu?

Thanks!!

---

### Post by sanlinhtet on 2011-01-03
Hi;
Anybody , can help me ,plz?
I want some address , I mean host address to call in client computer from Ubuntu server.
Now I have to call like this "http://my-IP/administrator" so that I get my index files form public_html. I don't want to use that address. Let me know how to setup domain to do that
like "https://sit-name.com or others to use for only local.
please guide me
Thanks to all

---

### Post by tails_naf on 2011-02-06
I have a real head scratcher here..
pretty fresh install of 10.10, and I was trying to set up vnc with resumable sessions, and had originally used this guide:

[http://www.stuartellis.eu/articles/vnc-on-linux](http://www.stuartellis.eu/articles/vnc-on-linux)

But ran into problems - which I'll explain later.
So I assumed the guide was wrong, and instead I followed post #605 (copied exactly the setup, just to get me going)

and then when I tried it, I had the same problem.
The problem is, unless the resolution is set to  640x480, the login hangs.

I created the following screen-shots to illustrate the point - 
[http://imgur.com/a/tBaSh#QJxD4](http://imgur.com/a/tBaSh#QJxD4)

one image shows the login correctly (I edited one of the configs to use 640x480)
the second image shows the broken login (this login will not respond to keys or mouse input). The resolution chosen is the only difference between them.

My main desktop is very high res (in case that makes a difference)

could someone please offer any help or advice? using a 640x480 login is really difficult.
I installed vnc4server and xinetd today, so should have the latest versions.

---

### Post by Lommelun on 2011-03-15
This is my exact same problem. I am running 10.10 and I can't get resumable sessions to run for my life. Same problem when logging into XDMCP or VNC. 

An entry in /ETC/HOSTS.ALLOW was required, before that I could not even connect. I have also disable IPV6, but I do not know if that was necessary. Right now at least I have the exact same problem you are describing tails_naf. It works in 640x480, but not in any other resolution.

It was all running nicely in Lucid, after a few tears and lots of sweat. I have had it running since Ubuntu 6.x. But now it seems like it is no more to be.

>tail /var/log/syslog 
Mar 15 20:31:55 reoserv xinetd[10434]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Mar 15 20:31:55 reoserv xinetd[10434]: Started working: 2 available services
Mar 15 20:32:03 reoserv gnome-session[10453]: WARNING: GSIdleMonitor: IDLETIME counter not found
Mar 15 20:32:03 reoserv gdm-simple-greeter[10470]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow

This probably is a good clue... The greeter has problems. But we knew that.....

---

### Post by Lommelun on 2011-05-04
Problems are fixed in natty. 
A host of new problems introduced, but remote login is back up and working now.

---

### Post by cu_ on 2011-05-22
> **Lommelun said:**
> Problems are fixed in natty. 
A host of new problems introduced, but remote login is back up and working now.

Hi... I am trying to set this up on Natty.  I get a blank x windows screen instead of XDMCP.  Any ideas?  I mean, can you please share your set up to have this working in Natty.

---

### Post by kalyp on 2011-06-24
Just installed vnc4server this morning and I had the same problem at first, I fixed it either by disabling ipv6 (cf above) or by commenting the last 4 lines in .vnc/xstartup (cf [http://www.ehow.com/how_5089245_install-vnc-server-ubuntu.html](http://www.ehow.com/how_5089245_install-vnc-server-ubuntu.html), even if the syntax is slightly different). Not sure because I tried both at the same time.

I'm running into another problem. When I'm logged out and try to connect via VNC (I want to be able to remotely connect while someone else is logged in...) I get```
Authentication to host [myhost] has failed (No password configured for VNC Auth).
```. I simply have to ssh to the machine, not even do anything else, then it works (and I can kill the ssh terminal, doesn't matter, after I'm logged in I don't need to be logged in via ssh anymore). Somehow it looks like if I don't have one session open on the computer, the password fails.
Any way to avoid that?
Thanks.

edit - actually, that's not totally true. If I close the ssh terminal I lose the possibility to control the desktop. For instance trying to launch a terminal, it hangs and never opens it, while if I'm still sshed in it shows up in a fraction of second...

---

### Post by mök on 2011-08-11
> When I'm logged out and try to connect via VNC (I want to be able to remotely connect while someone else is logged in...) I get Authentication to host [myhost] has failed (No password configured for VNC Auth). I simply have to ssh to the machine, not even do anything else, then it works

Sounds like an encrypted home directory to me.

---

### Post by kalyp on 2011-08-11
Yep that's what I figured out in between (forgot I had posted this). It also causes my autofs to stop mounting network shares into my home directory while I'm logged out and a session is running via VNC, which is obviously a problem when running scripts. 

I need to un-encrypt my home directory, but since I'm away from the machine right now, I won't risk it until I'm back :) the ssh trick works well enough except that I can't switch off my computer...

I find it kind of annoying though, that encrypted home folders aren't accessible by remote VNC sessions if not logged in. I would have imagined that virtual sessions were just as good as "regular" ones...

---

### Post by Rogach on 2011-08-18
Hello!
I have a problem with vnc. I configured it like it was in how-to, got grey screen at first, but it solved after enabling xdmcp.
Now I do see the login prompt, and I am able to login to system - but only if I set -geometry option of Xvnc to 640x480. On higher resolutions login prompt hangs after several seconds - on 800x600 it sometimes starts to render user names, on 1024x768 it is draws only the white box with machine name.

What could cause such behavior?

---

### Post by dreamage on 2011-08-23
> **mök said:**
> > When I'm logged out and try to connect via VNC (I want to be able to remotely connect while someone else is logged in...) I get Authentication to host [myhost] has failed (No password configured for VNC Auth). I simply have to ssh to the machine, not even do anything else, then it works

Sounds like an encrypted home directory to me.

I've found a simple solution for this problem.
Login to your remote machine and create a screen session:
```
$ screen
```
The from inside the screen session run vncserver:
```
$ vnc4server 
```
and open a ssh sesion to localhost
```
$ ssh localhost
```
Next detach the screen by "CTRL+A" "d"
Done
Now the vnc accepts the connections without the ssh session

---

### Post by kalyp on 2011-08-23
oh wouah!! it works!! this is simply awesome. Not need to go through the un-encryption process anymore :)
Thank you so much!

---

### Post by mdavi on 2011-10-04
Forgive me if this there is an obvious solution to this, but I am new enough to linux that it isn't obvious to me.

First of all, thanks to everyone for all the tips here.  I got everything set up with all of the advice and some thought and perseverance.  I have a need for several folks to be able to log in to my machine with independent sessions for doing calculations that can take days to run, thus the need for resumable sessions.  Having an ssh session doesn't work when the calculation running stops on logout.

The problem I'm having is that after a number of successful repeat logins to the same session, occasionally a user is getting locked out with a message at the VNC login stage saying "the server is already in use."  He isn't logged in, so he isn't using the server.  We aren't sure what is happening.  I've searched the logs and cannot find anything unusual, other than the attempted logins.  It is very frustrating, because thus far, I cannot find a way to get him in, other than to kill the vnc session and restart the servers which also kills the calcuations he has been running for days.   

I'm running Lucid and have several vnc services set up on different ports with different users and passwords as outlined elsewhere in this thread.  A copy of my Xvnc file is below for reference.  Any thoughts on how to fix the problem will be most appreciated.  As a second best advice, if you have an idea on  how to restore my user's access without killing the session when he does get locked out, I could use that as a band-aid in the meantime while I continue to troubleshoot the root cause.

Thanks!
Mark

```

service vncshort
{
  disable = no
  socket_type = stream
  protocol = tcp
  wait = no
  user = nobody
  server = /usr/bin/Xvnc4
  server_args = -inetd -desktop mark-desktop -query localhost -geometry 1024x768  -once -depth 16 -fp /usr/share/fonts/X11/misc -SecurityTypes=none
}

service vncsticky1
{
  disable = no
  socket_type = stream
  protocol = tcp
  wait = yes
  user = root
  server = /usr/bin/Xvnc4
  server_args = -inetd :25 -desktop mark-desktop-staticvnc -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc/ -DisconnectClients=0 -NeverShared passwordFile=/etc/vncpasswd-somefile1
}

service vncsticky2
{
  disable = no
  socket_type = stream
  protocol = tcp
  wait = yes
  user = root
  server = /usr/bin/Xvnc4
  server_args = -inetd :30 -desktop mark-desktop-staticvnc -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc/ -DisconnectClients=0 -NeverShared passwordFile=/etc/vncpasswd-somefile2
}

service vncsticky3
{
  disable = no
  socket_type = stream
  protocol = tcp
  wait = yes
  user = root
  server = /usr/bin/Xvnc4
  server_args = -inetd :35 -desktop mark-desktop-staticvnc -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc/ -DisconnectClients=0 -NeverShared passwordFile=/etc/vncpasswd-somefile3
}

service vncsticky4
{
  disable = no
  socket_type = stream
  protocol = tcp
  wait = yes
  user = root
  server = /usr/bin/Xvnc4
  server_args = -inetd :40 -desktop mark-desktop-staticvnc -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc/ -DisconnectClients=0 -NeverShared passwordFile=/etc/vncpasswd-somefile4
}

```

---

