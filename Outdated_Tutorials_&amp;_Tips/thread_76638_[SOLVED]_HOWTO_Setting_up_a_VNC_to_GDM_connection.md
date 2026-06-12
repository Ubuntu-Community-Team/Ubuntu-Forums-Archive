---
title: "[SOLVED] HOWTO: Setting up a VNC to GDM connection"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-15
[B][COLOR="DarkOrchid"]This thread is now defunct! Please refer to the following thread for a more updated Howto:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
[/COLOR][/B]



This howto is to show how to setup VNC to show a GDM login screen when you connect to your Ubuntu box, effectively using XDMCP over VNC. A VNC client is easier to get going on Windows than a X server for most people, so here's how to use it to connect to your linux box.

First thing you'll need to do is enable the universe repositories: [https://wiki.ubuntu.com//AddingRepositoriesHowto](https://wiki.ubuntu.com//AddingRepositoriesHowto)

Then it's just six easy steps:

   1. **System->Administration->Login Screen Setup**
      Tab **Security->Enable XDMCP**
      Tab **XDMCP**--> You can disable "Honor Indirect Requests"
      For kdm or even xdm, just look through the settings and find XDMCP, make sure it's enabled.
      **_For Intel chipsets_**
   2. ```
sudo apt-get install vnc4server xinetd
``` (comes from universe)
       **_For AMD64 chipsets_**
   2. ```
sudo apt-get install vncserver xinetd
``` (comes from universe)

   3. ```
sudo gedit /etc/services
```
Put the following line at the end :
> vnc1024 5901/tcp                                     # VNC & GDM

   4. ```
sudo gedit /etc/xinetd.conf
```
Make it look like the following (**please do not put the opening and closing braces of defaults in the same line**). It wont work!:
> 
defaults
{
}
service vnc1024      {
        disable     = no
        socket_type = stream
        protocol    = tcp
        wait        = no
        user        = nobody
        server      = /usr/bin/Xvnc
        server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
      }

  5. ```
sudo /etc/init.d/xinetd restart
```
  6. Restart your computer.

That's it! Try connecting from another machine using and see how it goes.

If you need a VNC client for Windows, try out UltraVNC [http://ultravnc.sf.net](http://ultravnc.sf.net) it's the one I prefer.

> for 1024x768 -> vncviewer localhost:1

For connecting from Linux vnc4viewer with tsclient work well.

Credits: **Random Juju** and of course
**Intangible**

---

### Post by traherom on 2005-10-16
I had this working on Hoary, but the upgrade has stopped it. I'm not sure why, so if anyone gets it working...

Also, the enable XDMCP option has been moved to the "Security" tab.

---

### Post by Louisvdw on 2005-10-19
I'm also having trouble making it work. 

It seems that the package vnc4server does not exist in the universe. I found vncserver and installed that instead. Xvnc is running, but UltraVNC give a Invalid Connection Failed - Invalid Protocol error.


My enable XDMCP option is still under the XDMCP Tab...

---

### Post by arnieboy on 2005-10-19
[QUOTE=Louisvdw]I'm also having trouble making it work. 

It seems that the package vnc4server does not exist in the universe. I found vncserver and installed that instead. Xvnc is running, but UltraVNC give a Invalid Connection Failed - Invalid Protocol error.


My enable XDMCP option is still under the XDMCP Tab...[/QUOTE]
vnc4server does indeed exist in breezy universe under x11 section:
[http://packages.ubuntu.com/breezy/x11/vnc4server](http://packages.ubuntu.com/breezy/x11/vnc4server)

---

### Post by traherom on 2005-10-19
It exists, but doesn't seem to work.

---

### Post by Louisvdw on 2005-10-19
Is there a diff repository I can use to get it? Cause mine does not show it. I searched as well for it. Nothing? 

My current Universe is: deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) breezy universe

---

### Post by arnieboy on 2005-10-19
[QUOTE=traherom]It exists, but doesn't seem to work.[/QUOTE]
u mean u cant install it from synaptic or it doesnt work when u try to run it?

---

### Post by arnieboy on 2005-10-19
[QUOTE=Louisvdw]Is there a diff repository I can use to get it? Cause mine does not show it. I searched as well for it. Nothing? 

My current Universe is: deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) breezy universe[/QUOTE]
do a 
```
sudo gedit /etc/apt/sources.list
```
delete all contents, and copy the following into that:
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
```
save and exit and then do a
```
sudo apt-get update
```
now install vnc4server as outlined in the howto.

---

### Post by Louisvdw on 2005-10-19
Could it be that because I have the 64bit Ubuntu that vnc4server does not show. I copied your sources.list file and still can't find it (sudo apt-cache search vnc4). It returns nothing?

---

### Post by arnieboy on 2005-10-19
[QUOTE=Louisvdw]Could it be that because I have the 64bit Ubuntu that vnc4server does not show. I copied your sources.list file and still can't find it (sudo apt-cache search vnc4). It returns nothing?[/QUOTE]
thats correct. there is no vnc4server package for AMD64. thats why it doesnt show.

---

### Post by Louisvdw on 2005-10-19
Anything I can substitute it with? (Like vncserver -> what is the diffs?)

---

### Post by arnieboy on 2005-10-19
[QUOTE=Louisvdw]Anything I can substitute it with? (Like vncserver -> what is the diffs?)[/QUOTE]
the package was called vncserver till version 3.x
from version 4.x onwards its called vnc4server.
U can try with vncserver because it does have an AMD64 package. but am not sure of the results.

---

### Post by traherom on 2005-10-19
[QUOTE=arnieboy]u mean u cant install it from synaptic or it doesnt work when u try to run it?[/QUOTE]It installs fine, but doesn't seem to be running. I had this setup and working under Hoary, so I'm not sure what has changed.

---

### Post by arnieboy on 2005-10-19
[QUOTE=traherom]It installs fine, but doesn't seem to be running. I had this setup and working under Hoary, so I'm not sure what has changed.[/QUOTE]
it would be a good idea to mail **intangible** directly cuz hez the one who wrote this howto. he might be able to help u.

---

### Post by chaumurky on 2005-10-20
This is odd:

> ~$ sudo /etc/init.d/inetd restart
sudo: /etc/init.d/inetd: command not found

What'd I miss?

---

### Post by arnieboy on 2005-10-20
[QUOTE=chaumurky]This is odd:



What'd I miss?[/QUOTE]
try doing the same as **su** and not sudo.

---

### Post by chaumurky on 2005-10-20
nope, same thing.

> # locate inetd
/home//.kde/share/config/kinetdrc
/etc/inetd.conf
/etc/webmin/inetd
/etc/webmin/inetd/config
/etc/webmin/inetd/admin.acl
/var/lib/dpkg/info/webmin-inetd.postinst
/var/lib/dpkg/info/webmin-inetd.list
/var/lib/dpkg/info/webmin-inetd.prerm
/var/lib/dpkg/info/webmin-inetd.postrm
/var/lib/dpkg/info/webmin-inetd.conffiles
/var/lib/dpkg/info/webmin-inetd.md5sums
/usr/share/doc/libnet-ssleay-perl/examples/ssl-inetd-serv.pl
/usr/share/doc/webmin-inetd
/usr/share/doc/webmin-inetd/changelog.Debian.gz
/usr/share/doc/webmin-inetd/copyright
/usr/share/doc/webmin-inetd/README.Debian
/usr/share/man/man8/update-inetd.8.gz
/usr/share/apps/kinetd
/usr/share/apps/kinetd/eventsrc
/usr/share/servicetypes/kinetdmodule.desktop
/usr/share/services/kded/kinetd.desktop
/usr/share/services/kinetd_krfb.desktop
/usr/share/services/kinetd_krfb_httpd.desktop
/usr/share/webmin/mscstyle3/inetd
/usr/share/webmin/mscstyle3/inetd/images
/usr/share/webmin/mscstyle3/inetd/images/icon.gif
/usr/share/webmin/mscstyle3/xinetd
/usr/share/webmin/mscstyle3/xinetd/images
/usr/share/webmin/mscstyle3/xinetd/images/icon.gif
/usr/share/webmin/inetd
/usr/share/webmin/inetd/config.info.zh_TW.Big5
/usr/share/webmin/inetd/backup_config.pl
/usr/share/webmin/inetd/config.info
/usr/share/webmin/inetd/config.info.ca
/usr/share/webmin/inetd/config.info.de
/usr/share/webmin/inetd/config.info.es
/usr/share/webmin/inetd/config.info.fr
/usr/share/webmin/inetd/config.info.hu
/usr/share/webmin/inetd/config.info.pl
/usr/share/webmin/inetd/config.info.ru_RU
/usr/share/webmin/inetd/config.info.ru_SU
/usr/share/webmin/inetd/config.info.sv
/usr/share/webmin/inetd/config.info.tr
/usr/share/webmin/inetd/config.info.zh_CN
/usr/share/webmin/inetd/inetd-generic-lib.pl
/usr/share/webmin/inetd/delete_rpc.cgi
/usr/share/webmin/inetd/delete_serv.cgi
/usr/share/webmin/inetd/edit_rpc.cgi
/usr/share/webmin/inetd/edit_serv.cgi
/usr/share/webmin/inetd/index.cgi
/usr/share/webmin/inetd/inetd-solaris-10-lib.pl
/usr/share/webmin/inetd/inetd-lib.pl
/usr/share/webmin/inetd/restart_inetd.cgi
/usr/share/webmin/inetd/log_parser.pl
/usr/share/webmin/inetd/module.info
/usr/share/webmin/inetd/save_rpc.cgi
/usr/share/webmin/inetd/save_serv.cgi
/usr/share/webmin/inetd/help
/usr/share/webmin/inetd/help/help.zh_TW.Big5.html
/usr/share/webmin/inetd/help/help.sv.html
/usr/share/webmin/inetd/help/help.es.html
/usr/share/webmin/inetd/help/help.html
/usr/share/webmin/inetd/help/help.ca.html
/usr/share/webmin/inetd/images
/usr/share/webmin/inetd/images/smallicon.gif
/usr/share/webmin/inetd/images/icon.gif
/usr/share/webmin/inetd/lang
/usr/share/webmin/inetd/lang/ja_JP.euc
/usr/share/webmin/inetd/lang/zh_CN
/usr/share/webmin/inetd/lang/en
/usr/share/webmin/inetd/lang/es
/usr/share/webmin/inetd/lang/sv
/usr/share/webmin/inetd/lang/hu
/usr/share/webmin/inetd/lang/pl
/usr/share/webmin/inetd/lang/tr
/usr/share/webmin/inetd/lang/fr
/usr/share/webmin/inetd/lang/ko_KR.euc
/usr/share/webmin/inetd/lang/ca
/usr/share/webmin/inetd/lang/cz
/usr/share/webmin/inetd/lang/de
/usr/share/webmin/inetd/lang/it
/usr/share/webmin/inetd/lang/zh_TW.Big5
/usr/include/linux/inetdevice.h
/usr/lib/python2.4/site-packages/twisted/runner/inetdconf.py
/usr/lib/python2.4/site-packages/twisted/runner/inetd.py
/usr/lib/python2.4/site-packages/twisted/runner/inetdtap.py
/usr/lib/python2.4/site-packages/twisted/runner/inetd.pyo
/usr/lib/python2.4/site-packages/twisted/runner/inetdconf.pyo
/usr/lib/python2.4/site-packages/twisted/runner/inetdtap.pyo
/usr/lib/python2.4/site-packages/twisted/runner/inetd.pyc
/usr/lib/python2.4/site-packages/twisted/runner/inetdconf.pyc
/usr/lib/python2.4/site-packages/twisted/runner/inetdtap.pyc
/usr/lib/kde3/kded_kinetd.la
/usr/lib/kde3/kded_kinetd.so
/usr/sbin/update-inetd
/usr/src/linux-source-2.6.12/include/linux/inetdevice.h
/usr/src/linux-headers-2.6.12-8-686/include/linux/inetdevice.h
/usr/src/linux-headers-2.6.12-8/include/linux/inetdevice.h


Would having webmin installed change anything?

---

### Post by arnieboy on 2005-10-20
[QUOTE=chaumurky]nope, same thing.



Would having webmin installed change anything?[/QUOTE]
dont think so.. let me look into this when I get back home tonight. Its unfortunate that we dont have **intangible** to comment on this.

---

### Post by chaumurky on 2005-10-20
No rush, thanks for your help.

---

### Post by Blackie_Chan on 2005-10-21
I installed Breezy and don't have the two files: /etc/inetd.conf and /etc/init.d/inetd
have they been moved into a different location?

---

### Post by arnieboy on 2005-10-21
ok I have rewritten intangible's HowTO (**First post**). please check and see if this works for u or not.

---

### Post by MattyBoy on 2005-10-24
In the instructions it looks like you give the inetd format, but you say to install xinetd.   Which should I use?

---

### Post by arnieboy on 2005-10-24
[QUOTE=MattyBoy]In the instructions it looks like you give the inetd format, but you say to install xinetd.   Which should I use?[/QUOTE]
xinetd is an extension of inetd (which has been phased out in breezy).. it shd work. try and let me know.

---

### Post by Glow on 2005-10-25
[QUOTE=arnieboy]xinetd is an extension of inetd (which has been phased out in breezy).. it shd work. try and let me know.[/QUOTE]

MattyBoy is right. The format of xinetd.conf is different.
To make this work with xinetd, put the following in xinetd.conf:

```

service vnc
{
type = unlisted
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd -desktop=Ubuntu -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
port = 5950
}

```

Hope this helps!
Erik.

---

### Post by ubuntuede on 2005-10-28
Hi

I had problems with the X11 fontpath and vnc4server. Pleas see my posting: [http://www.ubuntuforums.org/showthread.php?p=450077](http://www.ubuntuforums.org/showthread.php?p=450077)

Is this a bug in breezy ? Can someone confirm ...

---

### Post by adnan on 2005-10-31
Installed fine on AMD64, but remote clients can't connect...connection refused.  I got rid of the xinetd entry and just tried to run "Xvnc -query localhost" and I get "segmentation fault".  Am I missing something?

---

### Post by tenshiKur0 on 2005-10-31
ah... this seems to work for me now.
Service is running fine.
But clients are still not connecting.

Anyone have any luck?

[QUOTE=Glow]MattyBoy is right. The format of xinetd.conf is different.
To make this work with xinetd, put the following in xinetd.conf:

```

service vnc
{
type = unlisted
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd -desktop=Ubuntu -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
port = 5950
}

```

Hope this helps!
Erik.[/QUOTE]

---

### Post by zorzeta on 2005-11-04
The same problems. None of VNC to GDM HowTo's posted in this forum by now work with CLEAN Ubuntu Breezy install. Tried all of them. 

Server seemed to work, but no connections from clients, even from localhost. The same time Remote Desktop (vivo) works just fine.

It would be nice to have guaranted to work on Breezy VNC to GDM HowTo finaly.

---

### Post by arnieboy on 2005-11-04
I have completely rewritten the howto. Please test this and let me know how it goes.

---

### Post by zorzeta on 2005-11-05
Thank you! I'll test it as soon as I get to the box.

Just details: shouldn't the 2nd from the bottom line of step 4 listing's be:

service vnc1024 {
...
server_args = -inetd -broadcast -geometry **1024x768** -depth 16 -once -fp unix/:7100 -securitytypes=none
}

---

### Post by chaumurky on 2005-11-05
Should 'service vnc1024' be:
 
 ```
 service vnc1024      {
          disable     = no
          socket_type = stream
          protocol    = tcp
          wait        = no
          user        = nobody
          server      = /usr/bin/Xvnc
          server_args = -inetd -broadcast -geometry **[COLOR=Red]1024x768[/COLOR]** -depth 16 -once -fp unix/:7100 -securitytypes=none
        }
```

?

---

### Post by chaumurky on 2005-11-05
Beat me while I was making the change all pretty and red... :)

EDIT: Actually that was 4 hour ago! I hadn't hit refresh after I was doing other stuff...

---

### Post by tenshiKur0 on 2005-11-05
Still no juice though.
I've spent a little bit of time on it.
plus: man pages for xinetd.conf, just to make sure we're doing everything ok.

I've turned on logging. and refined the service.
Still no go.
Service starts properly... chk: ```
netstat -tap | grep vnc
```

The relevant portion of my xinetd.conf now looks like:

```

service vnc800
{
type            = unlisted
disable         = no
socket_type     = stream
protocol        = tcp
wait            = no
user            = nobody
server          = /usr/bin/Xvnc
bind            = [MY_bind_address]
log_type        = FILE /var/log/vnc800.log
log_on_success  = PID HOST USERID EXIT DURATION
log_on_failure  = HOST USERID ATTEMPT                  
only_from       = [MY_acceptable_client_addresses] 
server_args     = -inetd -broadcast -desktop=[MY_machine_name] -geometry 800x600 -depth 16 -once -fp unix/:7100 -securitytypes=none
port            = 5900
}

```

The log, returns:
```

05/11/5@18:02:37: START: vnc800 pid=8064
05/11/5@18:03:53: START: vnc800 pid=8064 from=[MY_connecting_client]
05/11/5@18:04:29: EXIT: vnc800 status=1 pid=8064 duration=36(sec) 

```

... No other info, and my vnc client, remote client from a mac, just disconnects with: "Server closed the connection".

... I wonder if maybe it's the server_args prop, maybe we're passing incorrect params.

Will check into it.
Hope this can help someone else, try to resolve the ish.

---

### Post by DarkManX4lf on 2005-11-06
ok im having some trouble with this, i use xfce/xubuntu with gdm, and the login manager i use is gdm, i have a dlink router and i forwarded ports 5900 and 5901 both tcp, and i followed the howto and nothing went wrong...but i cant connect from my windows machine which is in the lan.  i used the program ultra vnc in windows and in the VNC server box i typed 192.168.0.100:1 and it just tells me that it failed to connect to server i did the same for 192.168.0.100:0 and it said the same....what did i do wrong?



EDIT --

ok i can only connect to the linux box (with my winxp machine which is in my lan) when the linux box is in gnome, and nothing else...how would i get it to work when the linux box is in xfce? and also how would i get it to work if i were to be outside my lan?

EDIT #2 -----
i got remote desktop to work out side my lan but again it only works if my linux machine is in gnome, it wont work if its in xfce...

---

### Post by zorzeta on 2005-11-07
The same result as for **tenshiKur0** with new HowTo.

Service seem to run ok
```
mokytojas@salys:~$ sudo netstat -tap | grep vnc
tcp        0      0 *:vnc800                *:*                     LISTEN     6826/xinetd
```

Client run...

```
mokytojas@salys:~$ vncviewer localhost:5901
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)
```

...and log...

```

05/11/7@19:25:30: START: vnc800 pid=7125 from=127.0.0.1
05/11/7@19:25:35: EXIT: vnc800 status=1 pid=7125 duration=5(sec)
```

Still no luck. :(

---

### Post by XDevHald on 2005-11-08
Worked like a charm arnieboy!

Sorry I didn't test this 3 weeks ago :-/ Good work :)

---

### Post by Random Juju on 2005-11-08
I've isolated two problems.  The first is that a clean Breezy installation does NOT have a running font server.  Instead, you need to specify a path on the filesystem.  By default, try /usr/share/X11/misc.

The OTHER problem is that this may collide with an X session already on an existing display.  I resolved the problem by changing the port (in /etc/services) to 5901, which moves everything to X display 1.  You would also pass ":1" as an option to Xvnc in the xinetd config (e.g. "-inetd :1 -geometry...").

Hope this helps!

---

### Post by Random Juju on 2005-11-08
To clarify, this is what I have as /etc/xinetd.d/vnc:

```
service vnc
{
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = nobody
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}
```

Thanks, and good luck!

---

### Post by arnieboy on 2005-11-08
yes but does it work for u?

---

### Post by tenshiKur0 on 2005-11-09
Nice.
This now works for me.
--
Only change made, was the

```
 :1 
``` to ```
 -inetd 
```
and
```
 -fp /usr/share/X11/fonts/misc 
```

--community love.

[QUOTE=Random Juju]To clarify, this is what I have as /etc/xinetd.d/vnc:

```
service vnc
{
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = nobody
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}
```

Thanks, and good luck![/QUOTE]

---

### Post by arnieboy on 2005-11-09
awesome and thanks Random Juju! First post updated! Now it shd work for everyone. as soon as this is confirmed by a few more people, I will move this to the wiki. :)

---

### Post by zorzeta on 2005-11-09
WOW! Now it's work for me too! Thank you very much, Random Juju!

---

### Post by Louisvdw on 2005-11-09
I'm sorry that I had to reinstall, (Screen problems) so I can't test the AMD64bit part. 

I reinstalled with Kubuntu which have another problem. Where Do I find all the settings? Kubuntu does not have a "Login Screen Setup" to set XDMCP in it's Kcontrol.

Any pointers?

---

### Post by arnieboy on 2005-11-09
[QUOTE=Louisvdw]I'm sorry that I had to reinstall, (Screen problems) so I can't test the AMD64bit part. 

I reinstalled with Kubuntu which have another problem. Where Do I find all the settings? Kubuntu does not have a "Login Screen Setup" to set XDMCP in it's Kcontrol.

Any pointers?[/QUOTE]
look for kdm settings in kcontrol.

---

### Post by Louisvdw on 2005-11-09
found kdm settings (Login Manager), but it only has stuff for users, backgrounds, font, etc.

No Security, no XDMCP???

---

### Post by arnieboy on 2005-11-09
[QUOTE=Louisvdw]found kdm settings (Login Manager), but it only has stuff for users, backgrounds, font, etc.

No Security, no XDMCP???[/QUOTE]
u might find this useful:
[http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP-KDM](http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP-KDM)

---

### Post by traherom on 2005-11-09
Well, the server now runs (meaning I can connect and don't get disconnected), but now I just get the "xwindows running, but nothing else is" grey checkered background. I'm wondering if XDMCP isn't working correctly, because I can't connect to it through a normal connect.

Ideas?

---

### Post by arnieboy on 2005-11-09
[QUOTE=traherom]Well, the server now runs (meaning I can connect and don't get disconnected), but now I just get the "xwindows running, but nothing else is" grey checkered background. I'm wondering if XDMCP isn't working correctly, because I can't connect to it through a normal connect.

Ideas?[/QUOTE]
the server was running before as well for most people. are u sure u updated ur config files with the updated stuff on the first post?

---

### Post by traherom on 2005-11-09
Well, ok, it ran well enough to tell me that it disconnected me. Now I stay connected and get at least... something.

---

### Post by Louisvdw on 2005-11-09
OK. Got XDMCP running.
> sudo vi /etc/kde3/kdm/kdmrc
And searching for and setting Enable = true
> [Xdmcp]
Enable = false

But get this error :
> vncviewer localhost:1

VNC viewer for X version 4.0 - built Apr 19 2005 04:20:29
Copyright (C) 2002-2004 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed Nov  9 22:51:39 2005
 main:        unable to connect to host: Connection refused (111)

---

### Post by arnieboy on 2005-11-09
[QUOTE=Louisvdw]OK. Got XDMCP running.

And searching for and setting Enable = true


But get this error :[/QUOTE]
are u sure u dont have firestarter running on ur host machine? Its highly possible that firestarter is blocking your vnc ports. if it is, please make sure that port 5901 is open for vnc requests. also please ignore the 800x600 vnc config. just use the 1024x768 thing. one good thing wud be to make sure that the host is also running at 1024x768 and not at a higher or lower resolution

---

### Post by ConnyBK on 2005-11-10
Hi,

I've done everything like described in the HOWTO. Finally the vncserver is running on my ubuntu machine and nmap [ipaddress] shows that the server listens on port 5901. But when I try to connect to the server with UltraVNC I've got the following error message:

> 
Connection failed - Error reading Protocol Version

Possible causes:

-You've forgotten to select a DSMPlugin and the Server uses a DSMPlugin
-Viewer and Server are not compatible (they use different RFB protocols)
-Bad Connection


In my syslog I've got the following line when xinetd starts up:
> 
Nov 10 18:27:04 localhost xinetd[6751]: warning: can't get client address: Connection reset by peer


Has anyone got an idea what could cause that problem?

Thanks,
ConnyBK

---

### Post by ConnyBK on 2005-11-10
Ok. Solved the problem. It was the depth setting which I initially had set to 24 instead of 16. Changed this, rebooted and it works.

---

### Post by ryanodabees on 2005-11-10
Hi desperate to get this working and have followed recent instructions to the letter
I can get the gnome remote desktop to work but I dont seem to get vncserver running at all is there anything else i have to get it working and is there any commands i can use to check which services are running and diagnose what the problem is
thanks

---

### Post by ryanodabees on 2005-11-11
ok so now my vncserver is running but when i run vnce viewer on linux or winXP i only get the grey screen with the oldstyle cross and nothing else i want to be able to log into ubuntu with the gnome login interface any help would be great
thanks

---

### Post by ConnyBK on 2005-11-11
Did you do this? 
> 
1. System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"
For kdm or even xdm, just look through the settings and find XDMCP, make sure it's enabled.

I got the same problem when I first forgot to enable XDMCP...

---

### Post by LCID Fire on 2005-11-12
When trying to connect to the vnc server with tsclient I get the following error:
ReadFromRFBServer: rdr::EndOfStream

Anybody any idea why?

---

### Post by landtuna on 2005-11-16
For those people who are getting a segmentation fault when trying to run Xvnc on AMD64 Breezy, see the following post:

[http://lists.debian.org/debian-amd64/2004/11/msg00073.html](http://lists.debian.org/debian-amd64/2004/11/msg00073.html)

I think this is the same issue we're having.  Running strace, I get the same crash output as the person who posted in the above thread.  I guess vncserver isn't going to work in Breezy without rebuilding from sources using the patches mentioned.

---

### Post by intangible on 2005-11-18
Wow, just came back to the forums for the first time in weeks, found this thread, looks awful familiar :D  Actually, I saw the credit arnieboy :)  Wish I had read this sooner so I could've set everyone on the right path; yes, with Breezy, the -fp switch is required.  So if you had this working with Hoary before, you just need to add "-fp /usr/share/X11/fonts/misc" to the end of your service line in inetd.conf and re-enable XDMCP in gdmsetup.  This problem is caused by the hard-coded paths in Xvnc4 pointing to the old font locations after the upgrade.  I've submitted a bug report, but as of yet, it hasn't been fixed. [https://launchpad.net/distros/ubuntu/+source/vnc4/+bug/3593](https://launchpad.net/distros/ubuntu/+source/vnc4/+bug/3593)

---

### Post by arnieboy on 2005-11-18
> **intangible]Wow, just came back to the forums for the first time in weeks, found this thread, looks awful familiar :D  Actually, I saw the credit arnieboy :)  Wish I had read this sooner so I could've set everyone on the right path said:**
> https://launchpad.net/distros/ubuntu/+source/vnc4/+bug/3593[/url]
it wud have looked even more familiar a month back.. lol.. when i had just ported it to the breezy forums with ur name in bold on the top.. but since then, I have had to rewrite it completely... still lots of users have problems. it wud be great if u cud take over this thread from here. and yeah welcome back to the forums :)

---

### Post by intangible on 2005-11-18
Sure thing, I'll keep an eye on this thread from now on. :)

---

### Post by arnieboy on 2005-11-18
[QUOTE=intangible]Sure thing, I'll keep an eye on this thread from now on. :)[/QUOTE]
thanks a lot. really appreciate it :)

---

### Post by features on 2005-11-20
Hi all,

I have a Breezy machine that is running twin head (at 2048 X 768 - but I have 1024x768 meta modes in my xorg.conf).  I cannot connect unless I am logged in already.  All connection attempts result in:
```
mark@gumbot:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

```

I can connect, once I am logged in, if I select "Allow other users to control your desktop" option in System --> Preferences --> Remote Desktop.  But that's a bit pointless...

Here is my entire Xinetd.conf.

```
# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{}

service vnc1024{
type = unlisted
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd :1 -broadcast -desktop=gumboot -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
port = 5901
}


includedir /etc/xinetd.d
```

and the appropriate bit of /etc/services...

```
vnc1024     5901/tcp            # VNC & GDM
```

My syslog tells an interesting story, of how I have no clue how xinetd.conf is structured.:D 

```
Nov 21 13:14:56 localhost xinetd[9876]: Exiting...
Nov 21 13:14:56 localhost xinetd[10017]: Service (null): missing '{' [file=/etc/xinetd.conf] [line=6]
Nov 21 13:14:56 localhost xinetd[10017]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=21]
Nov 21 13:14:56 localhost xinetd[10017]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Nov 21 13:14:56 localhost xinetd[10017]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=26]
Nov 21 13:14:56 localhost xinetd[10017]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Nov 21 13:14:56 localhost xinetd[10017]: removing chargen
Nov 21 13:14:56 localhost xinetd[10017]: removing chargen
Nov 21 13:14:56 localhost xinetd[10017]: removing daytime
Nov 21 13:14:56 localhost xinetd[10017]: removing daytime
Nov 21 13:14:56 localhost xinetd[10017]: removing echo
Nov 21 13:14:56 localhost xinetd[10017]: removing echo
Nov 21 13:14:56 localhost xinetd[10017]: removing time
Nov 21 13:14:56 localhost xinetd[10017]: removing time
Nov 21 13:14:56 localhost xinetd[10017]: xinetd Version 2.3.13 started with libwrap loadavg options compiled in.
Nov 21 13:14:56 localhost xinetd[10017]: Started working: 0 available services
```


Can someone please point me in the right direction?

Chear,

Mark

---

### Post by intangible on 2005-11-21
It looks like xinetd.conf is a little picky; where you have: ```
defaults
{}
``` Move down the closing bracket one line, like this: ```
defaults
{
}
```  It looks like it will not work if the opening and closing brackets are on the same line.

---

### Post by features on 2005-11-21
Thanks intangible, that sorted it. \\:D/ 

To racap, items in xinetd.conf must have the braces on the next line, eg:

```
defaults
{
}

service vnc1024
{
...
}
```

Otherwise your service will not start, and your connection will be refused!

Chear,

Mark

---

### Post by arnieboy on 2005-11-21
Thanks Intangible! First post updated :)

---

### Post by dashersey on 2005-11-25
I've followed these instructions, found the vnc4package, set up Xinted as described, etc...  but there's no process listening on any of the 590x ports when I reboot.

I added the port = 5901 statement into the xinetd script, and now it works!

BUT there is still nobody listening on 5901, according to netstat -a | grep 5901. 
How is this possible? Can somebody explain how this bit of magic is occuring?

---

### Post by Joshua Hesketh on 2005-11-26
Hi,

I followed the turorial and it works fine as described. However I need to be able to log into the machine remotely then close VNC (view) to be able to open it again at a latter time and still be logged in and all the windows to stay open.

vino (the gnome remote desktop program) would be ok, but without the monitor connected my the computer it sets the vnc size to 600x480 and makes it unusable.

If you have any ideas or tips that would be great. 

Thanks,
Josh

---

### Post by traherom on 2005-11-26
Ok, I finally got this (re-)working. For some reason, the broadcast search for the X server wasn't working, so it would just show me the "X starting" black and white checker pattern. To fix it, I just changed "-broadcast" to "-query localhost."

---

### Post by fm1234 on 2005-11-26
Hi,

I've the same problem as dashersey. Xinetd reports one service running. There is also no Xvnc process running.  the logfile vnc1024.log is empty. If Xvnc is dying is there another log to look at?

TIA,
Fernando

---

### Post by curtis on 2005-11-26
The problem I have is with connecting to the VNC server...
It connects fine, except it crashes with 'Wrong DSP plugin' or something like that in UltraVNC, and with RealVNC says 'Incompatible VNC version'.
Sorry if those messages are not accurate, do not have access to the box running VNC.

---

### Post by Joshua Hesketh on 2005-11-28
Hi,

I followed the turorial and it works fine as described. However I need to be able to log into the machine remotely then close VNC (viewer) to be able to open it again at a latter time and still be logged in and all the windows to stay open (things like nautilus and evolution).

vino (the gnome remote desktop program) would be ok, but without the monitor connected my the computer it sets the vnc size to 600x480 and makes it unusable. Is there a way to get vino to start with a higher res? or change Xorg not to bring down the resolution if a monitor is connected?

If you have any ideas or tips that would be great. 

Thanks,
Josh

---

### Post by ditikos on 2005-11-29
I've put the listing that arnieboy posted (the updated one), on 5.10 server-expert, xubuntu-desktop / gdm.

First of all, if anyone is installing xubuntu then he/she should use gdmsetup for the XDMCP setup.

Secondly, a problem that has something to do with the fonts (I hope it is about them) and the -fp option; I am a Greek User, therefore I use el.UTF-8 encoding. When I try to read greek from within the RealVNC 4.1 client (my client for communicating with the linux box), the Greek fonts of XFCE4 (translations) and X.Org are being shown, but when I try to write with Greek I am having a garbage result. 

At the box itself it has:
- Better fonts (probably comes from the same error)
- Greek Read/Write support

I thought that there were not enough fonts to show/write properly, so I took each font directory I had in /etc/X11/xorg.conf and put them to the -fp argument seperated by commas. Restarted xinetd, restarted gdm but nothing happened. 

Any Suggestions?
Regards,
Panagiotis

---

### Post by arnieboy on 2005-11-29
[QUOTE=dashersey]I've followed these instructions, found the vnc4package, set up Xinted as described, etc...  but there's no process listening on any of the 590x ports when I reboot.

I added the port = 5901 statement into the xinetd script, and now it works!

BUT there is still nobody listening on 5901, according to netstat -a | grep 5901. 
How is this possible? Can somebody explain how this bit of magic is occuring?[/QUOTE]
It might be a problem with your firewall settings. try and install firestarter and make sure port 5901 is open.

---

### Post by arnieboy on 2005-11-29
[QUOTE=Joshua Hesketh]Hi,

I followed the turorial and it works fine as described. However I need to be able to log into the machine remotely then close VNC (viewer) to be able to open it again at a latter time and still be logged in and all the windows to stay open (things like nautilus and evolution).

vino (the gnome remote desktop program) would be ok, but without the monitor connected my the computer it sets the vnc size to 600x480 and makes it unusable. Is there a way to get vino to start with a higher res? or change Xorg not to bring down the resolution if a monitor is connected?

If you have any ideas or tips that would be great. 

Thanks,
Josh[/QUOTE]
AFAIK, u can try playing around with **/etc/X11/xorg.conf** and make sure u dont have 640x480 as the lowest resolution in that. u can try and set that to 800x600 or whatever suits u best. that way vino will not fallback to 640x480 as the lowest resolution

---

### Post by psusi on 2005-12-02
By specifying the display number ( :1 ) you limit yourself to a single session because further connections will try to use the same display number and fail.  

Is there a way to configure it to automatically choose the next availible display number?

---

### Post by psusi on 2005-12-02
Hrm... it seems that Xvnc does not accept the display number parameter with the -inetd parameter.  Once I left the :1 out, it works, but the fonts and icons are kind of messed up.  What's up with that?

---

### Post by intangible on 2005-12-02
Can you post a screenshot?

---

### Post by rklauco on 2005-12-03
Hello everyone.
I have been playing with the setup and I got the vnc server working (thanks to all of you).
But, my problem is, that I need shared screen with my monitor.
I need to work with the on-screen programs and let it work when I disconnect.
And, additionaly, I need the protocol version to be lowered to 3.3 to be able to connect from my PDA device.
Any help what to set in xinetd.conf / vnc.conf file?

(I have read the manual, the AlwaysShared option is somehow not working from xinetd.conf...)

---

### Post by Joshua Hesketh on 2005-12-04
[quote=arnieboy]AFAIK, u can try playing around with **/etc/X11/xorg.conf** and make sure u dont have 640x480 as the lowest resolution in that. u can try and set that to 800x600 or whatever suits u best. that way vino will not fallback to 640x480 as the lowest resolution[/quote]

Thanks for the tip, and I would've thought it to work too from logic, but it doesn't. It seems with no monitor my computer still reverts back to 600x480 even when that is not an option in the xorg configuration. Is there any other solution to my problem?

---

### Post by psusi on 2005-12-05
[QUOTE=intangible]Can you post a screenshot?[/QUOTE]

Strange... it seems to have something to do with being logged on twice.  If I log on the console, then vnc into the machine from over the network, things get seriously messed up.  As long as I don't log in on the console, things are mostly fine.  I still have some kind of issue with fonts though because when I fire up emacs all the characters are empty blocks, and it prints this to the console:

Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct

What the heck does that mean?  I have this in xinetd.conf:

server_args = -inetd -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc,/usr/share/X11/fonts/cyrillic,/usr/share/X11/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi

Also I found some documentation on the web that mentions a utility program called vncconfig that lets you change some parameters of the Xvnc server at runtime, only it does not seem to be in the ubuntu package.  Does anyone know anything about this?

---

### Post by LinuxWiz83 on 2005-12-06
I hate such a simple question but i have looked every where and i can not seem to find out how to set the password for vnc so i was wondering what is the command?

---

### Post by traherom on 2005-12-06
[QUOTE=LinuxWiz83]I hate such a simple question but i have looked every where and i can not seem to find out how to set the password for vnc so i was wondering what is the command?[/QUOTE]If you're using the VNC to GDM setup from this guide, there is none. You get a screen where you login using your normal account.

---

### Post by LinuxWiz83 on 2005-12-06
oh ok, thank you. Also i had another question. Is anyone having a problem with connecting to there vnc server? I even disable my linux firewall and using my internel IP and i can not connect.

---

### Post by intangible on 2005-12-06
If your computer is behind a router, or even some cable modems, you'll have to set up forwarding in your router to connect to it from anywhere else on the Internet.

Is your network like this:
1. Internet->ISP->Modem/Cable Modem->Your PC
this:
2. Internet->ISP->Modem/Cable Modem->Router(Wireless or not)->Your PC
Or something different?

If it's like #2, then you'll have to set up port forwarding in your router to point to your PC.

OR

Are you unable to connect to your computer from yourself? (127.0.0.1:5900) or from any other computer in your house (if you have multiple computers?)

If you want, you can IM me at intangible81 and I'll try to give you a hand.

---

### Post by LinuxWiz83 on 2005-12-06
It is like #2 but it is not a firewall or router problem because when i had vino setup i could connect but not with this vncserver setup, the ports are forward though. I can't not use vino though because it does not have a web java plugin for it.

---

### Post by ShiftyPowers on 2005-12-06
worked like a charm once i switched out of bloody TightVNC viewer.  Now I'm using UltraVNC and it works great.  Thank you so much.

---

### Post by psusi on 2005-12-06
Hrm... the emacs font problems went away when I switched to tightvncserver.

---

### Post by traherom on 2005-12-06
[QUOTE=LinuxWiz83]It is like #2 but it is not a firewall or router problem because when i had vino setup i could connect but not with this vncserver setup, the ports are forward though. I can't not use vino though because it does not have a web java plugin for it.[/QUOTE]The server setup in this guide only opens a port on 590**1**, so you'll have to specify that. (In most, do something like "server.address.com:1" That works in UltraVNC and the default client.)

If you want it to work on the default port, then change that in the xinetd.conf file.

---

### Post by LinuxWiz83 on 2005-12-06
The ports are forward is something to do with the server is why i can not connect because when i had veno installed it connected just fine.

---

### Post by traherom on 2005-12-06
[QUOTE=LinuxWiz83]The ports are forward is something to do with the server is why i can not connect because when i had veno installed it connected just fine.[/QUOTE]You have to forward port 5901. The setup given in the guide uses display 1 instead of display 0. You then have to specify display 1 (typically using :1) or port 5901 (typically ::5901) when connecting.

---

### Post by ShiftyPowers on 2005-12-07
how would one go about uninstalling this method?  I really need to be able to leave a session and log back into the same session to have the same programs and windows open.  Something a la Remote Desktop for Windows would be ideal.  I think the closest to that really is to leave the session logged in and auto login to a certain account if there system restarts.

Any ideas on how to remove this and have just plain old VNC?

---

### Post by nolodude on 2005-12-08
[QUOTE=ShiftyPowers]how would one go about uninstalling this method?  I really need to be able to leave a session and log back into the same session to have the same programs and windows open.  Something a la Remote Desktop for Windows would be ideal.  I think the closest to that really is to leave the session logged in and auto login to a certain account if there system restarts.

Any ideas on how to remove this and have just plain old VNC?[/QUOTE]
You can always try the built-in Remote Desktop: System -> Preferences -> Remote Desktop.

Or, this might suit you better: [HOWTO: Share desktops with x11vnc instead of built-in Remote Desktop]("http://ubuntuforums.org/showthread.php?t=45565"). Works for me anyways. I wanted to connect to current session but had graphics problems with built-in Remote Desktop.

I uninstalled this "vnc to gdm" config by undoing the steps described in the first post of this thread.

---

### Post by vedder on 2005-12-12
I'm newbie in ubuntu, the system appears to be very good, but a little bit confusing. I've read some of the replys to this thread and i still have a big doubt: what's the difference between remote desktop on ubuntu and configuring vnc to gdm connection? :confused:

---

### Post by traherom on 2005-12-12
[QUOTE=vedder]I'm newbie in ubuntu, the system appears to be very good, but a little bit confusing. I've read some of the replys to this thread and i still have a big doubt: what's the difference between remote desktop on ubuntu and configuring vnc to gdm connection? :confused:[/QUOTE]The remote desktop setup allows to to use an existing session (IE, you've already logged in). The setup described here allows you to login to a new session. (So no one necessarially has to be logged in.)

---

### Post by pjstadig on 2005-12-13
Please change the original post to say
>  defaults
{
}
service vnc1024
{
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}

instead of 
>  defaults
{
}
service vnc1024 {
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}

I was getting the following error from xinetd in my syslog

> Dec 13 19:13:56 localhost xinetd[9234]: Service vnc1024: missing '{' [file=/etc/xinetd.conf] [line=10]


xinetd will not start the service when the open brace is on the same line as the service name. It must be on a separate line.


Paul

---

### Post by arnobeck on 2005-12-18
Is there any way to activate Xdmcp on GDM through command line ?
because I don't have access to my Ubuntu, it's a server (without a screen).
And I'd like to install x11vnc to be able to access it from a distant computer.

---

### Post by pjstadig on 2005-12-19
[QUOTE=arnobeck]Is there any way to activate Xdmcp on GDM through command line ?
because I don't have access to my Ubuntu, it's a server (without a screen).
And I'd like to install x11vnc to be able to access it from a distant computer.[/QUOTE]
arnobeck,
I believe that the GUI config (System->Administration->Login Screen Setup) tool just provides a GUI editor for the /etc/gdm/gdm.conf file. So try making your changes there.

Paul

---

### Post by encompass on 2005-12-27
Please update the Post to include that return after the service name in xinet.d
In addition to these posts I would like to say, that if you start your viewer and see just an X that moves with your mouse and no login screen.  Turn off your firewall for a moment and see if that fixes it.  If so, you have got to forward some ports to get it working.  I have just figured that out.  If I get the time, I will right what I did.  If you don't see a post in a while.  IM me and remind me. ;)

---

### Post by luminoso on 2005-12-27
[QUOTE=pjstadig]Please change the original post to say

instead of 


I was getting the following error from xinetd in my syslog



xinetd will not start the service when the open brace is on the same line as the service name. It must be on a separate line.


Paul[/QUOTE]


Perfect! Now is connecting... buttttttttttttttt.... Pseudo-black screen and the mouse is an X...

> 
luminoso@khona4:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
No authentication needed
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

Sugestions?

---

### Post by pjstadig on 2005-12-27
I believe I got it to work with vnc4server *and* vnc4viewer.

---

### Post by jorns on 2005-12-30
Could someone help med with this. I have managed VNC to work with XDMCP and KDM.
But the problem is when i am logging out from the remote computer it shut down all application i have running in the remote computer. 

Example:  On my remote computer i will like to have Azureus open. But when i am logging out, or shutting down my client computer all the X application on the remote computer (server) also shuts down, how do prevent that. 
I will like to have them going until i manually shuts them down.

thx in advance

---

### Post by encompass on 2006-01-21
This didn't work for me....
> defaults
{
}
service vnc1024 {
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}
But this did...
> defaults
{
}
service vnc1024
{
disable = no
socket_type = stream
protocol = tcp
wait = no
user = nobody
server = /usr/bin/Xvnc
server_args = -inetd :1 -broadcast -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -securitytypes=none
}
But what would happen when lets sya the computer I am on suddenly gets disconected... do I lose what ever data I was working with... or is there a way to restore that session again?
In addition... is there a way to set up an acount that can access all my files as if it were the original user... but it is special in the fact it has lower detail, less colors, and no background or sounds?  So that I can havea special account just to remote in and control my system?

In addition... how do I set up a firewall to allow these connections?

---

### Post by Tichondrius on 2006-01-24
^^^  I completely understadnd what you need because that's what I also need. To be able to use a VNC client to log in to GDM and keep the session going even after disconnecting the VNC client. The session should only end if you explicitly log out.

Fortunately I know exactly how to do this, and in fact I've done it with my machine and it works great. The setup is a little different than what is stated in this thread, or for that matter any other thread I saw here.  

I will post a detailed howto shorty, so stay tuned......

---

### Post by Tichondrius on 2006-01-24
oops double post

---

### Post by gatorbrit on 2006-01-24
Can a VNC connection be set up when the server box is on a wireless network?  My ubuntu box is on the wireless network at work and I have gotten its IP from email headers (I know that this changes each time I log in to the network).  But assuming I log in, know my IP - should I be able to access the VNC server box from my winxp box which is connected to the network. 

I have followed the howto here and not had any luck - I just get "Failed to connect to server".  So I am wondering whether this is pointless.

Thanks

---

### Post by gatorbrit on 2006-01-24
ignore that last post - I managed to get it going - I thought that firestarter firewall was not running but in fact it was - once I shut it down the connection worked just great.  It is actually really awesome that I can control the linux box from home.

---

### Post by encompass on 2006-01-25
[QUOTE=arnieboy]It might be a problem with your firewall settings. try and install firestarter and make sure port 5901 is open.[/QUOTE]
I have done so... opened the port and still can't connect... I have to take the firewall totally down then it will connect.  Even with a loopback to the same computer.  Weird huh?

---

### Post by encompass on 2006-01-25
[QUOTE=gatorbrit]ignore that last post - I managed to get it going - I thought that firestarter firewall was not running but in fact it was - once I shut it down the connection worked just great.  It is actually really awesome that I can control the linux box from home.[/QUOTE]
BUT that is VERY insecure... I would recommend seting up your firewall... I am trying to do that here... but to no avail.

---

### Post by mssm on 2006-01-26
Hi,

I am a bit confused. Probably this has been discussed but I can not find it in the original how-to. Suppose machine A is a home laptop behind a router with firewall, running breezy with gdm. There is another machine B outside this network. I would like to access machine A from machine B using vncviewer. The ISP provides a dynamic IP address to machine A. I have already got a name for machine A from dyndns.org and ddclient keeps it updating for IP address change, if any.

So, what should I do? Should I open a port in the router's firewall and forward those ports to LAN Ip of machine A? If so, shouldn't it be mentioned in xinetd.conf? What command should I issue from machine B? Is it : vncviewer myservername:1?

---

### Post by Technoviking on 2006-01-26
Same here :(.

Mike

[QUOTE=luminoso]Perfect! Now is connecting... buttttttttttttttt.... Pseudo-black screen and the mouse is an X...


Sugestions?[/QUOTE]

---

### Post by Tichondrius on 2006-01-26
[QUOTE=mssm]Hi,

I am a bit confused. Probably this has been discussed but I can not find it in the original how-to. Suppose machine A is a home laptop behind a router with firewall, running breezy with gdm. There is another machine B outside this network. I would like to access machine A from machine B using vncviewer. The ISP provides a dynamic IP address to machine A. I have already got a name for machine A from dyndns.org and ddclient keeps it updating for IP address change, if any.

So, what should I do? Should I open a port in the router's firewall and forward those ports to LAN Ip of machine A? If so, shouldn't it be mentioned in xinetd.conf? What command should I issue from machine B? Is it : vncviewer myservername:1?[/QUOTE]


> So, what should I do? 

Just set up Xvnc like this HOWTO shows

> Should I open a port in the router's firewall and forward those ports to LAN Ip of machine A? 

YES. Also if you have a software firewall (e.g. firestarter) on machine A you may need to open port 5901.

> If so, shouldn't it be mentioned in xinetd.conf?

NO, port forwarding doesn't affect xinetd. Just add Xvnc to xinetd.conf like this howto shows.

> What command should I issue from machine B? Is it : vncviewer myservername:1?

YES

---

### Post by gatorbrit on 2006-01-26
[QUOTE=gatorbrit]ignore that last post - I managed to get it going - I thought that firestarter firewall was not running but in fact it was - once I shut it down the connection worked just great.  It is actually really awesome that I can control the linux box from home.[/QUOTE]

I should elaborate a bit more - I couldn't connect when the firewall was running - but firestarter recorded my other machines attempt to connect - I then just selected the option to allow that machine to connect and it worked fine.

---

### Post by mssm on 2006-01-27
[QUOTE=Tichondrius]> So, what should I do? 

Just set up Xvnc like this HOWTO shows

> Should I open a port in the router's firewall and forward those ports to LAN Ip of machine A? 

YES. Also if you have a software firewall (e.g. firestarter) on machine A you may need to open port 5901.

> If so, shouldn't it be mentioned in xinetd.conf?

NO, port forwarding doesn't affect xinetd. Just add Xvnc to xinetd.conf like this howto shows.

> What command should I issue from machine B? Is it : vncviewer myservername:1?

YES[/QUOTE]

Thanks Trinchondrius. In the first how-to of arnieboy, I guess I have to add a line like port=5901 right? In firewall setting I have to specify the protocol? Is it TCP?

In server_args, should I add a value -desktop=myserver? Some user did so. Finally, the 4th line of the howto - should it be: service vnc1024{  or, the bracket should go to the 5th line?

---

### Post by Tichondrius on 2006-01-27
Ok, let me clarify because this howto is a little messed up and there were a lot of changes after the initial post. So here's the complete list of steps that are required to set the VNC server that any user can login into and start a session. It is also persistent, meanning that even if you disconnect the VNC client your X session will not end (unless you explicitly log out) and you can reconnect to the same session again. The VNC server uses a separate display (:1) than your regular X server, which works with your physical display (:0). So two sessions can be active at the same time (one person sitting at the physical display and another remotely connecting using VNC).

  1. Enable XDMCP
**System->Administration->Login Screen Setup**
      Tab **Security->Enable XDMCP**
      Tab **XDMCP**--> You can disable "Honor Indirect Requests"
    
  2. Install required packages (vncserver and xinetd)
```
sudo apt-get install vnc4server xinetd
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
sudo /etc/init.d/xinetd/start
```

That's it! To test that this is working first try to connect from the same machine:

```
vncviewer localhost:1
```

You should be prompted for the VNC password, and then see the GDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client.  Remeber to use the machines domain name or IP addreess, followed by :1 (e.g. 192.168.0.100:1). If connecting locally as shown above works, but connecting remotely fails this means you have a problem with firewall or routing configuration. See the note below about how to deal with that.

Note about ports: The VNC server set up as shown uses TCP port 5901. If you are using firewall software (e.g. firestarter) on that machine, you need to allow incoming connections on this port. If you are using a router which assigns your machine a private address (e.g. 192.168.0.100) which is not accessible from the internet, then you need to forward TCP port 5901 from the router to this machine.

Note about security: This setup allows any user to start an X-session remotely by logging in using his regular password (after starting the VNC connection using the VNC password), so if the user disconnects without logging out, any other user which knows the VNC password can connect afterwards and resume the same session that the first user started.  So if you do not want to log out before disconnecting, it's advisable to at least lock your VNC X-session screen. Also note that while a remote user is connected thru VNC, no other connection will be accepted. An idle VNC client will be disconnected after one hour, but this can be changed by using the "-IdleTimeout" option in the server_args line in /etc/xinetd.d/Xvnc. For example, you can add "-IdleTimeout 300"  to change it to 5 minutes.

---

### Post by andlinux21 on 2006-01-27
Tichondrius thanks I will try this as soon as i get home I havent been able to get this or FreeNX installed correctly it's pissing me off seems like I am missing something simple.](*,)

---

### Post by Tichondrius on 2006-01-27
Cool, let me know if it works out for you. I'm in fact using the same setup and it works great.   If people want I can post this in a new HOWTO thread because it's quite different than the original HOWTO in this thread and works a lot better (simpler too).

---

### Post by arnieboy on 2006-01-27
[QUOTE=Tichondrius]Cool, let me know if it works out for you. I'm in fact using the same setup and it works great.   If people want I can post this in a new HOWTO thread because it's quite different than the original HOWTO in this thread and works a lot better (simpler too).[/QUOTE]
it would be great if u rewrite and maintain this howto since neither the original author nor the tweaker team maintains this one. The keyword is **maintaining** (answering questions when people have problems).. if u are ready to do both, let me know before u submit the new one so that it doesnt get dumped as a duplicate.

---

### Post by gatorbrit on 2006-01-27
I am having trouble keeping track of IP addresses.

In Firestarter I wanted to add my home PC's IP address to the "Allow connections from host" tab - but my home PC's IP seems to be changing.  In addition, because my ubuntu box (the VNC server) is wireless, it's IP changes as well.  So when I try to connect from home, I am never sure what IP my ubuntu box has, unless I sent myself an email right before I leave the office.

Is there a way of somehow assigning a virtual IP or something along these lines so that I don't have to keep track of these IPs each time I log in?:confused:

---

### Post by Tichondrius on 2006-01-27
[QUOTE=arnieboy]it would be great if u rewrite and maintain this howto since neither the original author nor the tweaker team maintains this one. The keyword is **maintaining** (answering questions when people have problems).. if u are ready to do both, let me know before u submit the new one so that it doesnt get dumped as a duplicate.[/QUOTE]

Yeah I submitted a new HOWTO thread but it's not showing up yet

---

### Post by arnieboy on 2006-01-27
[QUOTE=Tichondrius]Yeah I submitted a new HOWTO thread but it's not showing up yet[/QUOTE]
alright I will look into it.

---

### Post by mssm on 2006-01-27
Tichondrius, Thanks a lot for the update. As I understand, I should remove the old /etc/xinted.conf file, rught? I also found that XDMCP uses port 177 with UDP protocol. So this port should be taken in the router's config.(i.e. firewall and port forwarding)?

Can it be used to let a specific user login via vnc?

[COLOR="Red"]Update[/COLOR] : This is the output I got after I borught back /etc/xinited.conf to its original form and then following Tichondrius how-to. I have an AMD chipset, so I installed vncserver(instead of vnc4server). Moreover, I have opened port 177 in my router's firewall with UDP protocol and forwarded this port to my machine's internal LAN IP address.

$ vncviewer myserver.org:1
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)

Is it natural? What should I get?

---

### Post by arnieboy on 2006-01-27
alright this thread is now defunct and a new howto on VNC to GDM connection has been released at the following location:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by zasf on 2006-04-29
[QUOTE=ditikos]First of all, if anyone is installing xubuntu then he/she should use gdmsetup for the XDMCP setup.[/QUOTE]

Thanks for the info

---

### Post by peripatetic on 2006-05-06
[QUOTE=arnieboy]alright this thread is now defunct and a new howto on VNC to GDM connection has been released at the following location:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)[/QUOTE]

Dammit. I just read 13 pages of thread! :-)

Well I just wanted to add that I was trying to get this working on my box, where I'm using XFCE instead of Gnome. The vncserver started, and I could connect to it, but I was only seeing a grey screen. 

Turns out you have to edit ~/.vnc/xstartup 
Replace the last line (xwindow-manager &) with
/usr/bin/xfce4-session &

Hope this helps someone else. It took some time to find it.

---

### Post by shahin on 2008-04-28
I really do not want to install anything on my client.  Is there a client that comes with XP, that would work with VNC for remote desktop access?

---

### Post by krunge on 2008-04-28
> **shahin said:**
> I really do not want to install anything on my client.  Is there a client that comes with XP, that would work with VNC for remote desktop access?

There are java applet VNC viewers (the VNC server provides them via http).

So on the client all you need is a java enabled web browser.

---

### Post by freezerburn666 on 2008-08-05
> **peripatetic said:**
> Dammit. I just read 13 pages of thread! :-)

Well I just wanted to add that I was trying to get this working on my box, where I'm using XFCE instead of Gnome. The vncserver started, and I could connect to it, but I was only seeing a grey screen. 

Turns out you have to edit ~/.vnc/xstartup 
Replace the last line (xwindow-manager &) with
/usr/bin/xfce4-session &

Hope this helps someone else. It took some time to find it.

THANKS! i'll have to give this a try later. i saw your other post and it's exactly the same problem i'm having; remote desktop works with gnome but not xfce. thanks again!

---

### Post by Dethecus on 2008-09-09
Having major problems with XDMCP here :(

I am able to remote desktop to my Ubuntu box from Windows (with TightVNC) and another Ubuntu box just fine when the machine is logged in however I get "Connection Refused" if it's sitting at the login screen. IE. XDMCP just plain isn't working, I've enabled it through the GUI, tried using plain instead of same as local, have scoured the gdm.conf (where I discovered that XDMCP wasn't actually enabled even though the GUI login manager said it was????). I've googled and searched for days now with no resolution in sight. I'm not running a firewall, it's pretty much a fresh install and I'm at a loss for solutions.

---

