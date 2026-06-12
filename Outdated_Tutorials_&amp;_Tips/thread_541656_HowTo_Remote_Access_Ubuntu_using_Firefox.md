---
title: "HowTo: Remote Access Ubuntu using Firefox"
date: 2007-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2007-09-03
[size=6][center]HowTo: Remote Access Ubuntu using Firefox[/center][/size]

[center][img]http://computerworld.name/wp-content/uploads/2007/07/firefox1-resize.jpg[/img][/center]

[Size=4]**Introduction**[/size]

This how-to will show you how to make a vnc connection over the internet using firefox on the client. This how-to should work with any java capable browser, including (personal success with) internet explorer.

You can skip the rest of this introduction if you know how to configure your router/firewall.


[color=red]_Warning_: The how to installs a (vnc) server and java and is a potential security risk as your Ubuntu box will be potentially accessible to anyone on the internet.[/color]


[size=4]**Access over the Internet**[/size]

First you should strongly consider both a router and firewall.

The most difficult part of allowing internet access to your Ubuntu server may be configuring your router and firewall ... and is the most difficult part of this how-to. Unfortunately this is sometimes difficult to enable and since each situation is unique I can only give some general pointers.

If you do not understand IP addresses and ports you can think of your IP address as a physical address of say an apartment complex.

IP address = your computer = street address
Port = your server = apartment number

:rolleyes:


[size=2]_Server IP_[/size]

The IP address of your VNC server is different on a LAN vs an internet connection. Your internet IP address is assigned by your internet provider.
[list][*]You can check your IP address [here](http://whatismyip.com/) (or elsewhere).[/list]

The problem can occur if you use DHCP (rather then a static IP address) the internet IP address can change from time to time, most often when you reboot. *Most internet service providers use DHCP.*

A potential solution is to register at [dyndns](https://www.dyndns.com/services/dns/dyndns/), or similar service. ***dyndns will provide free service.***

[color=blue]You can then determine your vnc server IP address (from your client) via ping. ie ping <name_of_dyndns_server>[/color]


[size=2]_Router_[/size]

**You can skip this step if you connect directly to the internet**.

Assuming you use a router, you must configure your router to forward the correct port(s). The gory details of how to do this vary by router, you will need to refer to your routers manual (if you lost your manual, start with a google search).

You will need to forward ports 5801 and 5901 (from your router to your /ubuntu server). Ports 5801 and 5901 are the default ports for this how-to, although you can use others.
[list][*]5801 to allow the java applet to establish a connection[*]5901 for connection to the VNC server.[/list]

Basically you will start the server with a :X The default port is 5800 + X , so with this how to we will be using :1 and a default ports of 5801 and 5901. You will need to specify the 5801 port you are connecting to at the time of connection (in your browser address box). You can start more then one server (ie :2 , :3, etc corresponding to ports 5802 + 5902 , 5803 + 5903, etc).

See man vncserver for more information.


[size=2]_Firewall_[/size]

This is very easy to do via [Firestarter Ubuntu Wiki](https://help.ubuntu.com/community/Firestarter), a gui front end to IP Tables.
[list][*]Be sure to configure firestarter to allow pings.[/list]

Open the firestarter gui (Applications -> Internet -> Firestarter)

In the "Policy" tab, under the "Allow service" section, right click anywhere in the white space.

Select "Add rule"
[list][*]Under "Port" enter the ports you want to enable (5801 and 5901). "Allow Anyone" unless you know the IP you are connecting from and want to restrict access.[/list]


[size=4]**Repositories[/size]**

You will need to enable the commercial repositories on **both** Ubuntu server and client.

I do this by adding these lines to /etc/apt/sources.list

```
gksu gedit /etc/apt/sources.list
```

> ## Uncomment the following two lines to add software from Canonical's
## 'commercial' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial

_Note_: The above repos are for gutsy, you will need to use the commercial repos for your version (ie Dapper, Edgy, Feisty).

[Ubuntu Wiki Repositories Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


[size=4]**Server setup**[/size]

1. Enable the commercial repos as above.

 
2. Install by any means **vnc-common, tightvncserver, and tightvnc-java**

```
sudo apt-get install vnc-common tightvncserver tightvnc-java
```


3. Post-install configuration of the tight vnc server.

[list=number][*]Edit the fonts path in /etc/vnc.conf

```
gksu gedit /etc/vnc.conf
```

[list][*]For Feisty/Gutsy (7.04 and 7.10) add these lines jus after all the commented out font lines :
> $fontPath .= "/usr/share/fonts/X11/misc,";
$fontPath .= "/usr/share/fonts/X11/100dpi/:unscaled,";
$fontPath .= "/usr/share/fonts/X11/75dpi/:unscaled,";
$fontPath .= "/usr/share/fonts/X11/Type1,";
$fontPath .= "/usr/share/fonts/X11/100dpi,";
$fontPath .= "/usr/share/fonts/X11/75dpi,";
[*]For earlier versions of Ubuntu, see this link : [uwiki]VNCOverSSH[/uwiki] Ubuntu Wiki[/list]
[*]Setup the server.
[list][*]Open a terminal and enter: ```
vncserver :1
```
[*]The first time you run a server you will be asked a password:> ubuntu@ubuntu:~$ vncserver :1 

 You will require a password to access your desktops.
 
 Password: #Enter your desired password here
 Verify:   #Confirm Password

 New 'X' desktop is ubuntu:1

 Starting applications specified in /etc/X11/Xsession
 Log file is /home/ubuntu/.vnc/ubuntu:1.log
 
 ubuntu@ubuntu:~$
[indent]**[color=red]This password is our only security so choose well**[/color][/indent]
[*]_Note_: The name of your server is your hostname:1
[*]This creates a new directory in your home directory ~/.vnc
[indent][color=blue]The vnc server will give access to your ubuntu server *as the user who started the server*.[/color][/indent]
[*]Your password is encrypted in *~/.vnc/passwd*
[*]You can change your password with:```
vncpasswd ~/.vnc/passwd
```
[*]The vncserver uses *~/.vnc/xstartup* to start/configure your session. These are the start scripts I find most helpful :
[list=A][*]Gnome> ##!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid navy # Choose your color
x-window-manager &
{
 (gnome-panel 2> /dev/null &)
}
xterm &[*]XFCE> ##!/bin/sh

xrdb $HOME/.Xresources

xfwm4 2> /dev/null &
xfce4-panel 2> /dev/null &
xfce4-terminal &[*]KDE> ##!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid navy # Choose your color
x-terminal-emulator -geometry 80x24+10+1- -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
kicker 2> /dev/null &
[/list]
[indent][color=blue]Of the 3, IMO, XFCE gives the best results[/color][/indent]
[*]Restart the server (to re-load the configuration/xstartup)```
vncserver -kill :1
vncserver -geometry 800x600 -depth 24 :1
```[/list]

[color=blue]See man vncserver for additional options[/color][/list]


4. Start the server (later if needed).

You will likely want to reduce the resolution as the java applet will run in a firefox window :

```
vncserver -geometry 800x600 -depth 24 :1
```

If you have a large monitor you may be able to increase the server resolution (-geometry 1280x1024).

_Note_: 1024x768 is nice (client resolution @ 1280x1024)


5. You can stop the server at any time with vncserver -kill

```
vncserver -kill :1
```

[color=blue]6. _Note_: Additional servers ~ You can start additional servers with other defaults, for example :[/color]```
vncserver -geometry 1024x768 -depth 24 :2
```[color=blue]THESE ADDITIONAL SERVERS WILL ALL USE THE SAME PASSWORD (unless you start them under an alternate user name).[/color]

[size=4]**Client setup[/size]**

1. Enable the commercial repos as above.

 
2. Install by any means **sun-java6-jre and sun-java-6-plugin**

```
sudo apt-get install sun-java6-jre and sun-java-6-plugin
```

_Note_: You *do not* need a vnc (client) viewer for this how-to.


3. Allow java : In Firefox Edit -> Preferences Select the "Content" tab, tic off the "Load images automatically" "Enable JavaScript" and "Enable Java" boxes.


[size=4]**Connect**[/size]

Open Firefox, in the address bar type <vnc_server_ip> : 5801
[indent]If needed, you can obtain the IP address of the server with a ping (see "Server" section above)[/indent]

For example: 

> 192.168.1.25:5801
> <name_of_dyndns_server>:5801

The java applet will start automatically.

**If you use NoScript (or other java blockers) you will need to allow 192.168.1.25:5801 once the connection is established.**

Click the connect button.

_Note_: If you reload the firefox window you will need to log in again.

Screen shots :

[[IMG]http://img114.imageshack.us/img114/7346/sxdesktopvirtualxubuntuhe5.th.png[/IMG]](http://img114.imageshack.us/my.php?image=sxdesktopvirtualxubuntuhe5.png)     [[IMG]http://img401.imageshack.us/img401/4287/screenshotbodhisxdesktojh3.th.png[/IMG]](http://img401.imageshack.us/my.php?image=screenshotbodhisxdesktojh3.png)

References :

[uwiki]VNC[/uwiki] Ubuntu wiki

---

### Post by Jose Catre-Vandis on 2007-09-05
nice work bodhi.zazen :)

---

### Post by KCPokes on 2007-09-05
Nice How-To.  

It got me thinking though that another HOW-TO that may be nice, using much of your HOW-TO as a base, is to explain to people how they can use VNC tunneled over SSH.  Its a very basic change to your How-To, requiring only Putty instead of Firefox with some basic loopbacks.  Even most corporate firewalls allow port 22 out, thus control over SSH is rather easy.  

I may still have the writeup of how to do it if you'd like me to send it to you.

---

### Post by bodhi.zazen on 2007-09-05
> **Jose Catre-Vandis said:**
> nice work bodhi.zazen :)

Hey, thanks Jose Catre-Vandis :)

I wrote this mainly because although it is described as a feature in tightvnc, I could not find a how-to anywhere.

> **KCPokes said:**
> Nice How-To.  

It got me thinking though that another HOW-TO that may be nice, using much of your HOW-TO as a base, is to explain to people how they can use VNC tunneled over SSH.  Its a very basic change to your How-To, requiring only Putty instead of Firefox with some basic loopbacks.  Even most corporate firewalls allow port 22 out, thus control over SSH is rather easy.  

I may still have the writeup of how to do it if you'd like me to send it to you.

KCPokes : There is such a document here :

[uwiki]VNCOverSSH[/uwiki]

I have been adding to this document, and actually took some screen shots of cygwin, putty, and winscp I was going to add into this document.

---

### Post by KCPokes on 2007-09-05
> **bodhi.zazen said:**
> KCPokes : There is such a document here :

[uwiki]VNCOverSSH[/uwiki]

I have been adding to this document, and actually took some screen shots of cygwin, putty, and winscp I was going to add into this document.

Excellent.  Definitely a useful HOW-TO for a lot of people.

---

### Post by Yes on 2007-09-05
If I were to screw something up in Ubuntu so that I couldn't boot/log on, would this allow me to access Ubuntu from Windows?

I haven't tried this yet, but it looks like a great guide.  I'll definitely be trying this.

---

### Post by bodhi.zazen on 2007-09-05
> **Yes said:**
> If I were to screw something up in Ubuntu so that I couldn't boot/log on, would this allow me to access Ubuntu from Windows?

Well, if you can not boot Ubuntu, no you will not be able to gain access via this how-to.

If you can boot, gut the gui fails, you may be able to log in this way (or with ssh). To use this how-to the vncserver would need to be active and they system must be in good enough shape to be running/accepting commands.

I think though that you will need to fix your boot/log in porblem.

> I haven't tried this yet, but it looks like a great guide.  I'll definitely be trying this.

Enjoy :twisted:

---

### Post by SnakeSkin on 2007-09-20
First, great How-to! This is EXACTLY what I wanted to do and worked great!
Maybe this can help someone. I changed 2 things in my setup.
1.	The fonts section supplied did not work for me. I’m running Feisty (7.04). I added the following at the end of /etc/vnc.conf:

$fontPath "unix/:7100" # local font server
 # if the local font server has problems, we can fall back on these
 $fontPath .= "/usr/share/X11/fonts/misc,";
 $fontPath .= "/usr/share/X11/fonts/cyrillic,";
 $fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
 $fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
 $fontPath .= "/usr/share/X11/fonts/Type1,";
 $fontPath .= "/usr/share/X11/fonts/CID,";
 $fontPath .= "/usr/share/X11/fonts/100dpi,";
 $fontPath .= "/usr/share/X11/fonts/75dpi,";
 # paths to defoma fonts
 $fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType?,";
 $fontPath .= "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID";

2.	For my KDE desktop I use the following ~/.vnc/xstartup
##!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid navy # Choose your color
x-terminal-emulator -geometry 80x24+10+1- -ls -title "$VNCDESKTOP Desktop" &
startkde &
kicker 2> /dev/null &

---

### Post by Warpedflash on 2007-09-24
This tutorial is great and has worked in part for me.
I can access the my box from on my own network from firefox but i cant get at it from the internet i get to the java appet loading but then i get a connection error...

> network error: could not connect to server: myserver:5901
any ideas?

---

### Post by bodhi.zazen on 2007-09-24
> **Warpedflash said:**
> This tutorial is great and has worked in part for me.
I can access the my box from on my own network from firefox but i cant get at it from the internet i get to the java appet loading but then i get a connection error...


any ideas?

You need to forward 5901 (as well as 5801)

---

### Post by Warpedflash on 2007-09-24
as far as i can tell the ports are open... but it could be my router...
i hate teh bthomehub so much...

---

### Post by abhi.datt on 2007-10-02
Is there any way we can use https instead of http.

Also for security ereasons I use the following command to start my vncserver,
 vncserver :6 -name <somename> -geometry 1000x700 **-localhost**

This ensures that the client can only use 
vncviewer -via <my_server_ip> localhost:6

In this scenario I cannot connect using Firefox. 
Please suggest what can be done to allow browser login without compromising on security

---

### Post by bodhi.zazen on 2007-10-02
> **abhi.datt said:**
> Is there any way we can use https instead of http.

Also for security ereasons I use the following command to start my vncserver,
 vncserver :6 -name <somename> -geometry 1000x700 **-localhost**

This ensures that the client can only use 
vncviewer -via <my_server_ip> localhost:6

In this scenario I cannot connect using Firefox. 
Please suggest what can be done to allow browser login without compromising on security

All vaid points/concerns.

The short answer to your question is no. If I want a secure connection I tunnel over ssh.

Using a browser is a trade off between security and convenience, the convenience being :

1. No need to download or install a vnc client.

2. No need for a ssh server or ssh client (putty on windows).

In this case, your security is your vnc password and that is pretty much it ...

---

### Post by masingerz on 2007-11-21
I did the steps until the step that mentions to setup the server with command "vncviewer :1" I ran into this error message.

carlos@masingerz:~$ vncviewer :1

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed Nov 21 01:34:10 2007
 main:        unable to connect to host: Connection refused (111)
carlos@masingerz:~$

---

### Post by bodhi.zazen on 2007-11-21
> **masingerz said:**
> I did the steps until the step that mentions to setup the server with command "vncviewer :1" I ran into this error message.

carlos@masingerz:~$ vncviewer :1

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed Nov 21 01:34:10 2007
 main:        unable to connect to host: Connection refused (111)
carlos@masingerz:~$

oic, looks like I made a typo, sorry :redface:

Should be vnc**server** :1

I'll fix the original post ....

---

### Post by masingerz on 2007-11-21
I ran the command you mentioned and I see output:

carlos@masingerz:~$ vncserver :1

You will require a password to access your desktops.

Password: 
Verify:   
Found /usr/share/tightvnc-java for http connections.
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.

New 'X' desktop is masingerz:1

Creating default startup script /home/carlos/.vnc/xstartup
Starting applications specified in /home/carlos/.vnc/xstartup
Log file is /home/carlos/.vnc/masingerz:1.log

---o---

Please let me know if this "Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script."

---

### Post by bodhi.zazen on 2007-11-21
I am not an expert re those messages, but by the looks of it your are up and running :

> New 'X' desktop is masingerz:1

Try connecting ...

Otherwise you will need to manually correct the font path (see the original post). This is the biggest hassle with tightvnc server.

---

### Post by pinion on 2007-12-19
> **bodhi.zazen said:**
> You need to forward 5901 (as well as 5801)

I was not having a problem when I first went through the how to today connecting over the internet but now I get a connection error.  Connecting locally on my network works fine though.  I do have all the ports forwarded.  Using DD-WRT I have two different port ranges 5800-5805 and 5900-5905.   The only things I've edited are the two files mentioned in the how to. 
~/.vnc/xstartup
and
/etc/vnc.conf

The actual error is "network Error: Could Not Connect to server: 'my.ip.address':5901"

I notice it says 5901 even though I pointed to 5801.  I'm sure that's because the java redirects to the 5901 or something like that however I do have 5901 opened to this machine the same way I have 5801 open.  Any ideas?

---

### Post by pinion on 2007-12-19
> **pinion said:**
> I was not having a problem when I first went through the how to today connecting over the internet but now I get a connection error.  Connecting locally on my network works fine though.  I do have all the ports forwarded.  Using DD-WRT I have two different port ranges 5800-5805 and 5900-5905.   The only things I've edited are the two files mentioned in the how to. 
~/.vnc/xstartup
and
/etc/vnc.conf

The actual error is "network Error: Could Not Connect to server: 'my.ip.address':5901"

I notice it says 5901 even though I pointed to 5801.  I'm sure that's because the java redirects to the 5901 or something like that however I do have 5901 opened to this machine the same way I have 5801 open.  Any ideas?

Rebooted the router and now it's working.  I'm certain the router didn't think the right ports were forwarded now.  It's odd that DD-WRT would behave that way.

---

### Post by nagual on 2007-12-20
Has anybody got this to work in 64 bit ubuntu?

---

### Post by Skylive on 2008-03-29
Could someone also add in a part on how to auto start on boot ,the tightvncserver, instead of me doing it myself?

---

### Post by kait992004 on 2008-04-08
Found /usr/share/tightvnc-java for http connections.
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.


i get a problem while i included the fontpaths given ,,,,i also used other fontpaths as given above but it doesnt work ...i m using 7.10 gutsy

---

### Post by bodhi.zazen on 2008-04-08
> **Skylive said:**
> Could someone also add in a part on how to auto start on boot ,the tightvncserver, instead of me doing it myself?

Add the command to start the vncserver /etc/rc.local

/etc/rc.local is run as root as the final part of the boot process. Use the full path to vncserver and use sudo to run as a user :

> /usr/bin/sudo -u user /usr/bin/vncserver :1 &

where "user" in "-u user" = the user you want to run the vncserver.

---

### Post by bodhi.zazen on 2008-04-09
> **kait992004 said:**
> Found /usr/share/tightvnc-java for http connections.
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.


i get a problem while i included the fontpaths given ,,,,i also used other fontpaths as given above but it doesnt work ...i m using 7.10 gutsy

vncserver is not working for me in 7.10

There are a few bug reports in Launchpad, a few web pages, but I could find no solution.

I have tried editing /etc/vnc.conf and /usr/bin/vncserver
I have tried making links ...

I have reverted to vnc4server for Ubuntu 7.10 (does not work with this how-to :( )

---

### Post by yeehawjared on 2008-05-08
has anyone got this working for hardy heron 8.04?


[COLOR="Red"]edit: nevermind, I got it to work just fine.[/COLOR]

---

### Post by bodhi.zazen on 2008-05-08
> **yeehawjared said:**
> [COLOR=Red]edit: nevermind, I got it to work just fine.[/COLOR]

Thanks for the feedback yeehawjared, glad it is working for you.

I have not attempted this with 8.04, any updates you suggest to the how-to ?

---

### Post by yeehawjared on 2008-05-08
well for one, /etc/vnc.conf never exists, so I never add anything about custom fontpaths.

I'm going to do a fresh install of Xubuntu 8.04 this weekend and post back with any updates.  One thing I'd REALLY like to do is tunnel this over HTTPS for a more secure connection.  I'd like to fire up a browser from anywhere and https to the vnc-java applet.  Any info about this would be greatly appreciated.  thanks!

---

### Post by bodhi.zazen on 2008-05-08
Thanks, I will add an update then.

Another option is to tunnel your vnc connection over ssh.

You can use putty as an ssh client (runs native on Linux and Windows) and vncviewer.

Both apps are available as an .exe and can be placed on a usb (along with ssh keys). The applications do not need to be installed or run as an administrator ...

Putty : [http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe]("http://the.earth.li/%7Esgtatham/putty/latest/x86/putty.exe")

VNC : [http://downloads.sourceforge.net/vnc-tight/tightvnc-1.3.9_x86.zip](http://downloads.sourceforge.net/vnc-tight/tightvnc-1.3.9_x86.zip)

> Viewer executable, does not require installationSo IMO firefox is a novelty, ssh tunneling is for security.

[uwiki]SSHHowto[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

---

### Post by glistam on 2008-05-22
I have an strange problem occurring.  The process works, in that I can connect to my machine (Linux Mint 4.0, based on 7.10/Gutsy) just fine through a browser (FirefoxPortable on windows xp) but it looks odd.  I have a task bar with a "clear desktop" button, but nothing else, no menu or anything.  Also, my background is just a blue space, with no icons, and usually there is a terminal session running.  I can run apps fine using the terminal, which appear in their normal form as long as they were not running on the true desktop already.

Is this normal or did I mess up somewhere?  I was hoping for a true representation of my desktop, like when I use LogMeIn.

Thanks,

---

### Post by bodhi.zazen on 2008-05-22
> **glistam said:**
> I have an strange problem occurring.  The process works, in that I can connect to my machine (Linux Mint 4.0, based on 7.10/Gutsy) just fine through a browser (FirefoxPortable on windows xp) but it looks odd.  I have a task bar with a "clear desktop" button, but nothing else, no menu or anything.  Also, my background is just a blue space, with no icons, and usually there is a terminal session running.  I can run apps fine using the terminal, which appear in their normal form as long as they were not running on the true desktop already.

Is this normal or did I mess up somewhere?  I was hoping for a true representation of my desktop, like when I use LogMeIn.

Thanks,

Yes, that looks correct. Your potions depend on your desktop environment ...

Personally I think xfce is best for this :

[https://help.ubuntu.com/community/VNCOverSSH#head-162c37f4fd53ef6c06727cd57196e4a0cc57743c](https://help.ubuntu.com/community/VNCOverSSH#head-162c37f4fd53ef6c06727cd57196e4a0cc57743c)

---

### Post by glistam on 2008-06-06
> **bodhi.zazen said:**
> Yes, that looks correct. Your potions depend on your desktop environment ...

Personally I think xfce is best for this :

[https://help.ubuntu.com/community/VNCOverSSH#head-162c37f4fd53ef6c06727cd57196e4a0cc57743c](https://help.ubuntu.com/community/VNCOverSSH#head-162c37f4fd53ef6c06727cd57196e4a0cc57743c)

Is there anyway to make the lower left menu appear?  the "start menu" (to use the windows term)?

Also, my installation uses gnome.  Would I have to install XFCE separately to use that for the VNC desktop?

---

### Post by bodhi.zazen on 2008-06-06
> **glistam said:**
> Is there anyway to make the lower left menu appear?  the "start menu" (to use the windows term)?

Left click on the menu and add in the applet ...

> Also, my installation uses gnome.  Would I have to install XFCE separately to use that for the VNC desktop?

Yes, you would have to add in XFCE (you can install either xubuntu-desktop or just xfce + goodies).

---

### Post by Lucho77 on 2009-05-27
Thank you so much bodhi.zazen,
Just wanted to let you know that I got it working from the first try with Internet Explorer 7, on WinXP. the Linux Machine is Dell GX270 with Ubuntu 8.04.2 with a server install running 'icewm', see attached picture.

---

### Post by bodhi.zazen on 2009-05-27
You are most welcome, glad it is working for you.

---

### Post by suniyo on 2009-09-27
Great tutorial. It really helped me a lot. Thanks for this. :P

---

### Post by bodhi.zazen on 2009-09-27
> **suniyo said:**
> Great tutorial. It really helped me a lot. Thanks for this. :P

You are most welcome =)

---

### Post by teguh.umar on 2009-10-05
Hi, i have this worked at 904, but recently i have this problem.
Any idea? I'm using GNOME, ubuntu 904.
Please Help me..
Thanks.
And this error from log file
[SIZE="1"]05/10/09 18:32:25 Xvnc version TightVNC-1.3.9
05/10/09 18:32:25 Copyright (C) 2000-2007 TightVNC Group
05/10/09 18:32:25 Copyright (C) 1999 AT&T Laboratories Cambridge
05/10/09 18:32:25 All Rights Reserved.
05/10/09 18:32:25 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
05/10/09 18:32:25 Desktop name 'X' (sisti-09:1)
05/10/09 18:32:25 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
05/10/09 18:32:25 Listening for VNC connections on TCP port 5901
05/10/09 18:32:25 Listening for HTTP connections on TCP port 5801
05/10/09 18:32:25   URL [http://sisti-09:5801](http://sisti-09:5801)
failed to set default font path '/usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,'
Fatal server error:
could not open default font 'fixed'
05/10/09 18:32:26 Xvnc version TightVNC-1.3.9
05/10/09 18:32:26 Copyright (C) 2000-2007 TightVNC Group
05/10/09 18:32:26 Copyright (C) 1999 AT&T Laboratories Cambridge
05/10/09 18:32:26 All Rights Reserved.
05/10/09 18:32:26 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
05/10/09 18:32:26 Desktop name 'X' (sisti-09:1)
05/10/09 18:32:26 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
05/10/09 18:32:26 Listening for VNC connections on TCP port 5901
05/10/09 18:32:26 Listening for HTTP connections on TCP port 5801
05/10/09 18:32:26   URL [http://sisti-09:5801](http://sisti-09:5801)
Font directory '/usr/share/fonts/X11/Speedo/' not found - ignoring
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "Generic Event Extension" missing on display ":1.0".
Xlib:  extension "Generic Event Extension" missing on display ":1.0".
Xlib:  extension "Generic Event Extension" missing on display ":1.0".
Window manager warning: Log level 32: could not find XKB extension.[/SIZE]

---

