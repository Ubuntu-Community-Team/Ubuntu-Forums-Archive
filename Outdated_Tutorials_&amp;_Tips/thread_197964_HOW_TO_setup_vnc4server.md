---
title: "HOW TO: setup vnc4server"
date: 2006-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Cirrocco on 2006-06-16
(a bunch of this was taken from [L4mp's guide]("http://ubuntuforums.org/showthread.php?t=191564"), with sirspiddy's input, all of which appears to be adapted from [Tichondrius' guide]("http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc+resumable").  I've just defragged and recompiled them to form this:)

The HOW TO: setup vnc4server guide

this is for those of you who agree that 'remote desktop' is too slow, and freenx is too complicated.

############ Begin ############

1) setup XDMCP:
click System -> Administration -> Login Window
click Remote tab
  select "Same as Local"
  click Configure XDMCP
    remove check from Honour indirect requests

2) configure remote greeter:
```
sudo gedit /etc/gdm/gdm.conf
```
find this line:
```
# RemoteGreeter=/usr/lib/gdm/gdmlogin
```
replace with:
```
RemoteGreeter=/usr/lib/gdm/gdmlogin
```

Note: Before doing the next step, you need to make sure the extra repositories (e.g. universe) are enabled:
[http://easylinux.info/wiki/Ubuntu#Ho...a_repositories]("http://easylinux.info/wiki/Ubuntu#Ho...a_repositories")

3) Install required packages:
```
sudo apt-get install vnc4server xinetd
```

Note to AMD64 users: The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:
```
wget http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb wget http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb sudo dpkg -i vnc4server_4.0-7.3_amd64.deb sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb
```

4) Set the VNC passwd:
```
sudo vncpasswd /root/.vncpasswd
```

5) Define the VNC service criteria:
```
sudo gedit /etc/xinetd.d/Xvnc
```
and copy this into it:
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
save and exit

6) Reinitialize the service with new criteria:
```

sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start

```

7) Test the connection:
```
vncviewer localhost:1
```

############ you're done ############

what this whole thing accomplishes is that you can connect to the desktop using a different session than the local desktop.  IE someone can be sitting there working on that computer, and you can also login and work on that computer at the same time without interference. (even under the same user ID)

NOTE: 
If you change the port in step 5) to something else, it changes what you use to connect to the server.  I personally chose port 5959 - so when I connect to my Ubunutu box using RealVNC on Windows XP I type: 192.168.0.101:5959

---

### Post by Scaramanga19 on 2006-06-19
I am a Linux noob, although I have successfully installed Dapper server.  I have installed KDE for the gui, and the server is connected to the network (printing and internet are fine).  I can also remote from a Windows XP desktop to the Ubuntu server (Kubuntu?  since it is KDE?) using Putty for the command line, but I am having trouble configuring vnc4server.

Using the Adept package manager, I have installed the vnc4server package, but when I attempt to follow your instructions, I can't get past step 1.

-----
1) setup XDMCP:
click System -> Administration -> Login Window
click Remote tab
select "Same as Local"
click Configure XDMCP
remove check from Honour indirect requests
------

Under System, I do not see anything named Administration, and when I go to 
System Settings > System Administration > Login Manager
I do not see either a remote or security (as mentioned by Tichondrius) tab.

Did I do something wrong on my install?  Are these tabs not showing because of KDE?  

Thank you in advance for your help.

Scaramanga19

---

### Post by dbott67 on 2006-12-29
Please read this important security vulnerability about vnc4server: 

[http://www.ubuntuforums.org/showthread.php?t=327275](http://www.ubuntuforums.org/showthread.php?t=327275)

-Dave

---

### Post by UncleB on 2007-03-09
Following these steps I still can't get it to work.

When I ran the command on the local machine in Terminal I get the following error:

*[I]ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)*[/I]


Anyone know what that means?

I've tried connecting over the LAN with UltraVNC and RealVNC and get the same text in the error but the code is 10054 instead.

---

### Post by dbott67 on 2007-03-09
> **UncleB said:**
> Following these steps I still can't get it to work.

When I ran the command on the local machine in Terminal I get the following error:

*[I]ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)*[/I]


Anyone know what that means?

I've tried connecting over the LAN with UltraVNC and RealVNC and get the same text in the error but the code is 10054 instead.

Are you running Beryl on your computer?  If so, try setting your session back to Gnome instead of XGL.

-Dave

---

### Post by UncleB on 2007-03-09
I presume not. I've not done anything to choose Beryl. I should be on hte default. Actually
checking on the login session options I am on Gnome.

It's an oldish Compaq M300 with a 4MB graphics card. Isn't Beryl for those with fancier graphics?

I'm new by the way. Could you tell?

---

### Post by dbott67 on 2007-03-09
> **UncleB said:**
> I presume not. I've not done anything to choose Beryl. I should be on hte default. Actually
checking on the login session options I am on Gnome.

It's an oldish Compaq M300 with a 4MB graphics card. Isn't Beryl for those with fancier graphics?

I'm new by the way. Could you tell?

Definitely not Beryl in your case.  Can you post the output of the following command:

```
**netstat -a | grep 5900**
```This is the output from my computer:

```
dbott@thedrake:~/Desktop$ **netstat -a | grep 5900**
tcp        0      0 *:5900                  *:*                     LISTEN

```You can see that my computer is LISTENing on port 5900.  You should see the same.  If you don't, then VNC server is not running.  You could also type the command:
```
netstat -l
```to display all listening ports:
```
dbott@thedrake:~/Desktop$ netstat -l
netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:36483         *:*                     LISTEN
tcp        0      0 *:netbios-ssn           *:*                     LISTEN
tcp        0      0 *:5900                  *:*                     LISTEN
tcp        0      0 localhost:32878         *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
tcp        0      0 *:microsoft-ds          *:*                     LISTEN
udp        0      0 192.168.1.10:netbios-ns *:*
udp        0      0 *:netbios-ns            *:*
udp        0      0 192.168.1.1:netbios-dgm *:*
udp        0      0 *:netbios-dgm           *:*
udp        0      0 *:bootpc                *:*
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     18720    @/tmp/dbus-j3ImguWDBu
unix  2      [ ACC ]     STREAM     LISTENING     10309    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     10106    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     70523    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     10332    @/tmp/hald-local/dbus-kLl8rXGBiW
unix  2      [ ACC ]     STREAM     LISTENING     11521    /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     18089    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18715    /tmp/ssh-PwxRMR7351/agent.7351
unix  2      [ ACC ]     STREAM     LISTENING     14582    /tmp/orbit-dbott/linc-1769-0-444ecf0b2d074
unix  2      [ ACC ]     STREAM     LISTENING     18734    /tmp/orbit-dbott/linc-1cb7-0-24f72eed1a12f
unix  2      [ ACC ]     STREAM     LISTENING     10333    @/tmp/hald-runner/dbus-w61xwI0mwJ
unix  2      [ ACC ]     STREAM     LISTENING     18751    /tmp/.ICE-unix/7351
unix  2      [ ACC ]     STREAM     LISTENING     18760    /tmp/keyring-6bRQyW/socket
unix  2      [ ACC ]     STREAM     LISTENING     18773    /tmp/orbit-dbott/linc-1ceb-0-2fe88cbd43bf9
unix  2      [ ACC ]     STREAM     LISTENING     18789    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     19391    /tmp/orbit-dbott/linc-1d5c-0-5704060d21853
unix  2      [ ACC ]     STREAM     LISTENING     18812    /tmp/orbit-dbott/linc-1cf1-0-379a39fac12d3
unix  2      [ ACC ]     STREAM     LISTENING     11963    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     18830    /tmp/orbit-dbott/linc-1cf5-0-2de97d3d79d3
unix  2      [ ACC ]     STREAM     LISTENING     18943    /tmp/orbit-dbott/linc-1cfe-0-25620bef79615
unix  2      [ ACC ]     STREAM     LISTENING     18987    /tmp/orbit-dbott/linc-1d02-0-25620befbede9
unix  2      [ ACC ]     STREAM     LISTENING     19018    /tmp/orbit-dbott/linc-1d06-0-bcac6262e89d
unix  2      [ ACC ]     STREAM     LISTENING     19044    /tmp/orbit-dbott/linc-1d08-0-bcac626600d5
unix  2      [ ACC ]     STREAM     LISTENING     19137    /tmp/mapping-dbott
unix  2      [ ACC ]     STREAM     LISTENING     19070    /tmp/orbit-dbott/linc-1d12-0-652fb0f97a2d6
unix  2      [ ACC ]     STREAM     LISTENING     19119    /tmp/orbit-dbott/linc-1d0a-0-79b3a65bd0042
unix  2      [ ACC ]     STREAM     LISTENING     19176    /tmp/orbit-dbott/linc-1d29-0-2fa3f7f5d3776
unix  2      [ ACC ]     STREAM     LISTENING     19232    /tmp/orbit-dbott/linc-1d31-0-1d906a667bffd
unix  2      [ ACC ]     STREAM     LISTENING     19267    /tmp/orbit-dbott/linc-1d33-0-40d3a7c028a0d
unix  2      [ ACC ]     STREAM     LISTENING     63960    /tmp/xmms_dbott.0
unix  2      [ ACC ]     STREAM     LISTENING     19307    /tmp/orbit-dbott/linc-1d39-0-ae924744a342
unix  2      [ ACC ]     STREAM     LISTENING     63393    /tmp/orbit-dbott/linc-2ac9-0-7683ffad52a
unix  2      [ ACC ]     STREAM     LISTENING     39077    /tmp/orbit-dbott/linc-d3f-0-6301cb7040c60
unix  2      [ ACC ]     STREAM     LISTENING     54392    /tmp/orbit-dbott/linc-6fbe-0-6d169ab9da712

```A little background to help you with some of these terms.  The **netstat** command prints network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.  The **-a** indicates "show all" connections (the **-l** is "listening" ports).  We then 'pipe' the first commands output over to the **grep** command (General Regular Expression Print) which searches for a particular term (in this case, the port number that VNC is supposed to listen on --- 5900).  If you just type '**netstat**' by itself, you'll see pages and pages of stuff go scrolling on by.

You'll see the **<command> | grep <term>** used a lot in the forums as it allows you to quickly search for information in a long file.

-Dave

---

### Post by UncleB on 2007-03-09
Hi,

Thanks for taking the time.

I have been trying to get it going on 5901 so I edited your command. Here are the results:

tcp        0      0 *:5901                  *:*                     LISTEN

---

### Post by dbott67 on 2007-03-09
Okay, so this means that you have to instruct vncviewer to connect on port 5901 (if you don't specify the port, it defaults to 5900).

The command would be:
```
vncviewer ip.address.of.server:5901
```

-Dave

---

### Post by UncleB on 2007-03-09
That's what I thought but it still comes up with that same error only with a different code when it's a different machine on my LAN.

I've tried with 5901, 1 (for session 1) and nothing hoping it would default but none of those three work...

---

### Post by dbott67 on 2007-03-10
Let's just verify that you're not running a firewall on your Ubuntu computer.  Type the following command:
```
dbott@thedrake:~$ **sudo iptables -L**
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

-Dave

---

### Post by jgpaiva on 2007-03-13
I'm having the exact same problem mentioned in the reply (*error: ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)*).

The vncviewer establishes connection, waits about 1 minute and then exits with that error.

I get the same output mentioned for the *iptables -L* command (all ACCEPT).

---

### Post by d0rr on 2007-03-16
Hi guys, been picking up Ubuntu again after a year since I played around with it for my uni coursework.

I tried to set up vnc4server, and after much hassles and references, I managed to get it up ( many thanks to the helpful post: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/) )

No changes had been made then.

However, when I started up my Ubuntu desktop today, and tried to connect it from my laptop (exact same way / method), I couldnt get connected anymore.

Back to my Ubuntu desktop, I started off my investigation. xinetd is listening to correct port that I'm connecting to. No firewalls are up.

> Mar 17 02:09:59 xxx xinetd[5177]: Reading included configuration file: /etc/xinetd.d/Xvnc [file=/etc/xinetd.conf] [line=14]
Mar 17 02:09:59 xxx xinetd[5177]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.d/chargen] [line=12]
Mar 17 02:09:59 xxx xinetd[5177]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Mar 17 02:09:59 xxx xinetd[5177]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Mar 17 02:09:59 xxx xinetd[5177]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Mar 17 02:09:59 xxx xinetd[5177]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Mar 17 02:09:59 xxx xinetd[5177]: removing chargen
Mar 17 02:09:59 xxx xinetd[5177]: removing chargen
Mar 17 02:09:59 xxx xinetd[5177]: removing daytime
Mar 17 02:09:59 xxx xinetd[5177]: removing daytime
Mar 17 02:09:59 xxx xinetd[5177]: removing discard
Mar 17 02:09:59 xxx xinetd[5177]: removing discard
Mar 17 02:09:59 xxx xinetd[5177]: removing echo
Mar 17 02:09:59 xxx xinetd[5177]: removing echo
Mar 17 02:09:59 xxx xinetd[5177]: removing time
Mar 17 02:09:59 xxx xinetd[5177]: removing time
Mar 17 02:09:59 xxx xinetd[5177]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
Mar 17 02:09:59 xxx xinetd[5177]: Started working: 1 available service


Result above seems fine to me ( grep xinetd /var/log/syslog ).

However, when I tried to connect using my vncviewer, it results as following:

> VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server


and when i tried to access from my laptop remotely, I found the following error in log..

> 
.........
Mar 17 01:39:22 xxx xinetd[7161]: warning: can't get client address: Transport endpoint is not connected
.........


HELP!! Could anyone brigthen me up? Appreciate lots!!

---

### Post by grumpymole on 2007-03-18
Currently, there is [still an open bug]("https://launchpad.net/ubuntu/+source/vnc4/+bug/78282") that for vnc4server that causes a sudden "end of stream" after connection and authentication.

If you are running Feisty or Edgy with the latest updates, you will probably be affected.  There is a [workaround for Edgy]("http://grumpymole.blogspot.com/2007/02/edgy-and-feisty-vnc4server-still-not.html") by downgrading to the previous version.

Regards

---

### Post by Ek0nomik on 2007-03-26
I am having the same problems.  Thanks for the link GrumpMole, I will try out x11vnc.

---

### Post by UncleB on 2007-03-27
@dbott67: Apologies for asking for help and then absconding. I was away from this for a while but came back to it today and got it fixed for my setup. There were 2 main problems:

1: The font path in the **Xvnc **service was wrong on my version (6.10) of Ubuntu. The correct path is: ***/usr/share/fonts/X11/misc***.

2: The bug in **vnc4server**. You can either downgrade to a working version or, if you're doing this from fresh, just install the still working one first time with the following command:
```

sudo apt-get install vnc4server/edgy
```

Obviously, you still have to install xinetd so you should run it as one line:

```
sudo apt-get install vnc4server/edgy xinetd
```

---

### Post by eagle63 on 2007-04-07
Hey guys, I'm a bit of a Linux novice and I've got a question regarding VNC:  I see all this talk/hype regarding "setting up VNC with resumable sessions."   I've got 2 boxes running Ubuntu - one is Edgy the other is Dapper - and I'm using Xtightvncserver on both of them.  

I connect to both boxes from my Windows laptop using a VNC client, and it works fine.  If I close the VNC client, I can always reconnect later and my "session" is just how I left it.  (If I had 4 programs open, they're still there when I reconnect later)  

**Is this all that's meant by "resumable sessions"?? ** Surely there must be something more that I'm missing, because otherwise I can't figure out why anyone would go to the hassle of using vnc4server, xinetd, and all the extra setup stuff.  Does "resumable" mean that you could go so far as to reboot the box, and have it save your session state?  

Thanks for any help!

---

### Post by UncleB on 2007-04-10
I'm not sure of your setup but that sounds kind of like all it is.

What this thread and others similar are about though is a Terminal session-type VNC connection. 

What that means, in case you don't know- apologies if you do, is that you can log on with VNC and hit the login window, log in there and work normally without any visible effect on the actual computer. So you could be using your computer while someone with VNC is doing the same thing on the same computer.

If that's what you have working then yes, that's all the fuss is about.

People here were trying to work out this method because the Remote Desktop that comes installed by default only connects to the session that is logged in. So you have to physically or automatically log the machine in to use it. With the Terminal sessions type connection you can control it pre-login as well as having more than one person logged in.

Excuse my rambling style. I've not finished my morning coffee yet.

---

### Post by eagle63 on 2007-04-10
Thanks UncleB - no apologies necessary - I do understand that VNC sessions are independant of one another as well as the ":0" session.  (the one hooked up to the monitor)  However, I just assumed that's how all VNC servers worked.  I've never even used the built-in "remote desktop" on Ubuntu.  

At this point (again, assuming there isn't something additional that vnc4server + xinetd gives you), I would respecfully recommend that y'all just install Xtightvncserver.  It's already in the repository.  (I don't think you even need universe or multiverse)  It's simple.  I had it up and running in 2 minutes.  Nothing additional to install, no files to mess with (well, you might want to tweak xstartup but that applies for any vncserver you use), and "resumable sessions."

---

### Post by gurgle on 2007-04-10
I see a "tightvncserver" but not a "Xtightvncserver" 

I am running edgy server install. I tried to install the one I found, but it wouldnt let me connect up.

---

### Post by eagle63 on 2007-04-10
> **gurgle said:**
> I see a "tightvncserver" but not a "Xtightvncserver" 

I am running edgy server install. I tried to install the one I found, but it wouldnt let me connect up.

Yep, my bad it's "tightvncserver."  Not sure why it's not letting you connect...  Is it running?  As I recall, when I installed it on my Edgy box it just fired right up after I typed "vncserver".  (I think it even prompted me to set a password)

---

### Post by gurgle on 2007-04-10
OK, progress made. I get a terminal window when i sign in, now how can i start up my gui?

---

### Post by eagle63 on 2007-04-10
> **gurgle said:**
> OK, progress made. I get a terminal window when i sign in, now how can i start up my gui?

You need to make a few changes to /.vnc/xstartup file.  (again, I think this file is common to any VNC installation) 

Here's what mine looks like:
```

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
vncconfig -iconic &
eval `dbus-launch --sh-syntax --exit-with-session`
gnome-session &

```

I think the main thing is to comment-out the "x-window-manager &" line, and replace it with the "gnome-session &" line.  This will launch Gnome.  I also added the eval `dbus-launch --sh-syntax --exit-with-session` line which prevents a strange "dbus power manager" error message that I would get upon connecting.  That was from a tip I found elsewhere on this forum.

---

### Post by gurgle on 2007-04-12
^^ I did this, and I still just get a terminal. Any other ideas?

---

### Post by eagle63 on 2007-04-13
> **gurgle said:**
> ^^ I did this, and I still just get a terminal. Any other ideas?

You could post your xstartup to make sure there aren't any typos...  Otherwise I have no idea.

---

### Post by yg17 on 2007-04-13
I just installed vncserver using this howto, and I'm able to connect from another computer, but this is all I get. No Gnome login window or anything. Im using Feisty. Anything I'm doing wrong? Thanks

---

### Post by UncleB on 2007-04-24
I had to make edits to /etc/vnc.conf to get it to work with the GUI: depth 16, geometry 800x600 but with the formatting from the file.

While it works it isn't quite what I want as I want to hit the login window when I start and this will take me directly to the logged in desktop of whatever user started the vncserver.

I prefer the flexibility of logging in as whomever I choose.

However, that doesn't seem to be working in Feisty yet. I had that problem with Edgy where I had to downgrade the version of vnc4server. The fix I had there doesn't seem to work here.

That said I'm trying it with the edgy repositories added manually and then installing vnc4server/edgy... And it worked! I had to revisit the gdm.conf and xinetd.d/Xvnc files but after that it and a nervous reboot all was well and back how I wanted it! 

If anyone wants to do it these are the repositories I added to /etc/apt/sources.list...

```
##My addon attempts
deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
deb http://gb.archive.ubuntu.com/ubuntu/ edgy multiverse

```

---

### Post by mpadams on 2007-06-12
1. Add "flags = IPv6" to the x11vnc file.

2. Restart xinetd if needed.

3. Use the IPv6 TightVNC viewer (free) or RealVNC 4.1 (pay) to access it. Not sure what other Linux or Windows clients support IPv6 at this time.

[http://jungla.dit.upm.es/~acosta/paginas/vncIPv6.html](http://jungla.dit.upm.es/~acosta/paginas/vncIPv6.html)
[http://www.realvnc.com/products/enterprise/4.1/ipv6.html](http://www.realvnc.com/products/enterprise/4.1/ipv6.html)

Reference: "IPv6 in Practice" [http://www.benedikt-stockebrand.de/books_e.html](http://www.benedikt-stockebrand.de/books_e.html)

---

### Post by vampyrebytes on 2007-08-13
OK, I'm totally lost somewhere.

My computer: Ubuntu 7.04 i386 with all the repositories in this thread added/turned on. All upgrades made.

I've followed the steps in the initial post.
I tried to log in. I succeed in connecting to the vncserver, but all I get is a gray X windows screen with the X cursor.

I really want terminal-style VNC.  The "normal/default" VNC (vino) locks up my systems after 5 seconds to 1 minute every time I log into it, requiring a hard boot. And besides that, I'd rather not leave my computer just logged in.

I've tried vnc4server, tightvncserver, vino, the vnc4server/edgy, and even FreeNX and NoMachine. (I'd love to get them working well personally, but that would be threadjacking.) Even if I end up getting FreeNX working, I'd still like to know why my system logs into a "broken" X11 window instead of the gdmlogin.



ETA:
FIXED - helps to reboot. I'm using teh downgraded vnc4server/edgy it seems to be working now.

---

### Post by vampyrebytes on 2007-08-14
OK, so after getting VNC working in a terminal style, I still have my computer locking up, after issuing only one or two commands. Doesn't matter what I try to do, one to three mouse clicks later, the server is locked up tighter than a max security prison. Only a hard reset works.
I can ssh as much as I want to, no problems. I can sit at the computer and use it directly no problems. But when I log in through vnc, it locks up hard with only a few mouse clicks. Any suggestions?

---

### Post by simonsmith06 on 2008-03-20
brilliant guide - thank you

---

### Post by milasch on 2008-09-05
> **yg17 said:**
> I just installed vncserver using this howto, and I'm able to connect from another computer, but this is all I get. No Gnome login window or anything. Im using Feisty. Anything I'm doing wrong? Thanks

Have you ever found a solution? I'm using Hardy LTS and have the same issue.

---

### Post by kklier on 2008-09-05
> **milasch said:**
> Have you ever found a solution? I'm using Hardy LTS and have the same issue.

I found this in log file:
/root/.vnc/xstartup: 12: twm: not found


I then ran 'apt-get install twm' to verify that was the only problem.

Since I have kde  installed I changed the line in xstartup

from:
twm &
to:
startkde &

---

### Post by milasch on 2008-09-06
> **kklier said:**
> I found this in log file:
/root/.vnc/xstartup: 12: twm: not found


I then ran 'apt-get install twm' to verify that was the only problem.

Since I have kde  installed I changed the line in xstartup

from:
twm &
to:
startkde &

This is not the problem... I actually have twm installed, and it actually starts a gnome section, but with nothing but what's shown in this image:
[ATTACH]84344[/ATTACH]

I started Xvnc from the command line since I couldn't find its log file.

This is what I get:

```

milasch@milasch-desktop:~/.vnc$ Xvnc :1 -geometry 1024x768 passwordFile=/home/milasch/.vnc/passwd 

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Sat Sep  6 20:09:53 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```

and then when I connect using:
```

vncviewer localhost:1

```

The server displays:
```

Sat Sep  6 20:09:56 2008
 Connections: accepted: 127.0.0.1::42595
 SConnection: Client needs protocol version 3.3

Sat Sep  6 20:09:59 2008
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 24 (32bpp) little-endian rgb888

```

the client:
```

VNC server supports protocol version 3.8 (viewer 3.3)
Password: 
VNC authentication succeeded
Desktop name "x11"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Using default colormap which is TrueColor.  Pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Same machine: preferring raw encoding

```

And i don't believe it's a client issue because I try using realvnc in my wife's windows laptop and I get the same thing.

This is frustrating! I'm trying to solve this for a while now, and when I was using opensuse back 1 year, it was really easy to setup this server.

Some help here?

---

### Post by yinglcs2 on 2008-11-02
hi, 

I need help with setting up vnc4server,

I try running the Xvnc command:
```

 sudo Xvnc -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

```

But then I do a 'ps -ef |grep Xvnc'

there is nothing come up.

Can you please tell me how to run Xvnc?

Thank you.

ps -ef |grep Xvnc
ying  22105 21859  0 13:25 pts/3    00:00:00 grep Xvnc

---

### Post by graysky on 2008-11-21
Might be the wrong place to ask but here goes: how does one enable clipboard sharing through vncserver?  Mine is all setup to my liking, but I can't get it to read/write to a shared clipboard.

---

### Post by syborfical on 2009-06-04
Anyone know if this guide works for 9.04

---

### Post by H_a_D_3_z on 2009-06-10
Yeah really, I have been busting my head trying to figure out how to connect and control my windows machine from my jaunty laptop.  Would these instructions work if for example;

  laptop (192.168.1.2) connected wirelessly to router #1 (192.168.1.1),
  router #2 (192.168.1.4) connects to router #1 (192.168.1.1) wirelessly,
  pc (193.168.1.2 {i have router#2 assigning 193.168.1.2 to pc}) connected to a different router #2 (192.168.1.4),
  router #2 (192.168.1.4) gives pc (193.168.1.2)a different IP address.

I've done it before, but I just can't remember how.  Last time I used Terminal Server Client

---

### Post by maledikt on 2009-08-18
Confirming it doesn't work.

---

### Post by Damanther on 2009-11-02
Any advice on getting the 64bit vnc4server to work on the new karmic distribution? the downgrade to vnc4server4.0-7.3 depends on libstdc++5 which isn't supported(that I know of) on karmic.

---

### Post by Diubidone on 2009-11-13
I Tried to install vnc4server on ubuntu karmic koala server and I have this issue: [http://ubuntuforums.org/showthread.php?p=8307521#post8307521](http://ubuntuforums.org/showthread.php?p=8307521#post8307521)

Anyone can help me ?

---

### Post by sdhip on 2010-12-18
Hi
Got this working on Karmic by doing something similar to the above thread.  Have now just upgraded to lucid 10.04 LTS, and got this going by altering the parameters for Xvnc in the xinetd "script".
To summarise what I now have:
/etc/gdm/custom.conf contains
```

# GDM configuration storage

[xdmcp]
Enable=true
DisplaysPerHost=2

[daemon]
RemoteGreeter=/usr/lib/gdm/gdm-simple-greeter 

[security]
DisallowTCP=false

```
and /etc/xinetd.d/Xvnc contains
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
        # server_args = -inetd -query 127.0.0.1 -geometry 1600x980 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        server_args = -inetd -query 127.0.0.1 -geometry 1024x768 -depth 16 -once -fp /usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb-DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd 
        port = 5901
}

```
I got the server_args by starting vnc4server, doing a ps -ef and seeing how vnc4server brought Xvnc4 up.  I then merged it with the appropriate ones from the original parameters.
There may be a neater way to do the fonts.  I'm just glad to get it going, as I use this a lot!

---

