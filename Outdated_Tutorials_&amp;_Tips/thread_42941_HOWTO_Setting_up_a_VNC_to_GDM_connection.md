---
title: "HOWTO: Setting up a VNC to GDM connection"
date: 2005-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by intangible on 2005-06-20
This howto is to show how to setup VNC to show a GDM login screen when you connect to your Ubuntu box, effectively using XDMCP over VNC.  A VNC client is easier to get going on Windows than a X server for most people, so here's how to use it to connect to your linux box.

I posted the instructions in another thread already, but decided to put them here as well so it's easier to find for everyone.

First thing you'll need to do is enable the universe repositories: [https://wiki.ubuntu.com//AddingRepositoriesHowto](https://wiki.ubuntu.com//AddingRepositoriesHowto)

Then it's just five easy steps:
[list=1]
[*] **System->Administration->Login Screen Setup**
Tab **XDMCP->Enable XDMCP** You can disable "Honor Indirect Requests"
For kdm or even xdm, just look through the settings and find XDMCP, make sure it's enabled.
[*] **sudo apt-get install vnc4server** (comes from universe)
[*] Put the following line at the end of **/etc/inetd.conf**:
```
5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=Server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
```
Replace "Server" with something you want the window title to be, usually the server name.
[*] **sudo /etc/init.d/inetd restart**
[*] Log out of your desktop (to restart gdm, xdm, or kdm)
[/list] 

That's it!  Try connecting from another machine using and see how it goes.

If you need a VNC client for Windows, try out UltraVNC [http://ultravnc.sf.net](http://ultravnc.sf.net) it's the one I prefer.

For connecting from Linux vnc4viewer with tsclient work well.

---

### Post by dazzla on 2005-06-20
Excellent, i'd gone about  things slightly different and set up a different user for each WM.  This is a much simpler method.

Although i did have a problem getting it to work initially, i changed the user from nobody to my usual user account in "/etc/inetd.conf" and it all worked fine.  Will this present me any problems?

---

### Post by intangible on 2005-06-20
The problem I might be worried about is that if you're using "securitytypes=none" like I posted, and you are letting the Xvnc process run as yourself, you might have given people a way into your account without a password.  But I haven't seen your configuration so you may be safe.

---

### Post by spacemonkey on 2005-06-24
I tried this with my server install of ubuntu that has XDM on it, and it didn't seem to work.  I assume that I didn't set up XDMCP properly on it.  In Xaccess I uncommented the '*' line so it would allow any host, then I commented out the "DisplayManager.requestPort:   0" line in xdm-config to allow connections.  Then I followed your howto.  When I try to connect using vncviewer I get this:

ReadFromRFBServer: rdr::EndOfStream

Any suggestions would be greatly appreciated...I would love to be able to manage my server from my desktop using more than just the terminal via SSH.

---

### Post by slimsam1 on 2005-06-24
I just wanted to say thank you. It worked great for me. I am using this method to administer a headless/keyboardless/mouseless backup server.

---

### Post by intangible on 2005-06-24
Ok, sorry, there are two things to do if you use XDM:
I installed xdm just to get to the right settings for ya :D.

1. Put a # before the last line in /etc/X11/xdm/xdm-config so it looks like this:
**#DisplayManager.requestPort:     0**

2. Only localhost is connecting back to XDM through VNC, so you only have to do is add "localhost" to /etc/X11/xdm/Xaccess.  Only the VNC client connects to the remote host.

Restart XDM and there ya go!

---

### Post by intangible on 2005-06-24
Glad I helped.

Since you are running it headless, you made sure to disable the local X server to save yourself some memory, right?
If not, just comment out the **0=Standard** line in the **[servers]** section in **/etc/X11/gdm/gdm.conf**.

---

### Post by Blackie_Chan on 2005-06-25
I am using gdm which doesn't have Xaccess so how do I change who has access to VNC?

Thanks in advance.

BTW, at the moment I can 'vncviewer localhost' and the vnc window will open, but if I type 'vncviewer **my WAN IP**' the window doesn't open, seems like nothing happens.

---

### Post by zaguar on 2005-06-25
Is this secure?  ie. is it possible for a hacker to enter the system with VNC enabled?

---

### Post by oofnik on 2005-06-26
[QUOTE=Blackie_Chan]I am using gdm which doesn't have Xaccess so how do I change who has access to VNC?

Thanks in advance.

BTW, at the moment I can 'vncviewer localhost' and the vnc window will open, but if I type 'vncviewer **my WAN IP**' the window doesn't open, seems like nothing happens.[/QUOTE]
 You probably just need to forward port 5900 to your LAN IP in your router settings.

---

### Post by spacemonkey on 2005-06-26
I appreciate the help, but I'm still getting the same error when I try to connect:

ReadFromRFBServer: rdr::EndOfStream

I've got Xaccess set to localhost, and I've commented out DisplayManager.requestPort: 0.

---

### Post by intangible on 2005-06-26
I know you probably already did, but did you make sure to restart xdm after those changes?  **sudo /etc/init.d/xdm restart**

Those two are the only changes I had to make to make sure it all worked properly in xdm.

What vnc viewer are you using? ([http://ultravnc.sf.net](http://ultravnc.sf.net) is a great one for windows)  Have you tried connecting to yourself on the same machine with a vncviewer?

---

### Post by intangible on 2005-06-26
Right, or if you're using a firewall such as firestarter, you'll have to open up port 5900.

---

### Post by intangible on 2005-06-26
This setup gives them direct access to your gdm login screen so they could sit there retrying passwords all day, but AFAIK, there are no known problems with this method yet.

Other than the fact that VNC is not encrypted, so if someone intercepted your connection, they could watch the traffic for passwords, etc.  If you need to use this outside of a LAN, it wouldn't hurt to look into SSH tunneling, it's pretty easy to do.  If you need some pointers for that, just let me know.

---

### Post by spacemonkey on 2005-06-27
I had been using the vncviewer that came already installed on ubuntu, but I decided to try xvnc4viewer, same thing, End of Stream.  I tried installing a xvnc4viewer on my server and connecting to localhost....same thing, End of Stream.  There is no firewall set up on my server (I use a hardware firewall, and I'm connecting from inside the lan).  I have restarted xdm, x, and the entire computer...still nothing.  

This is a server install of Ubuntu I'm trying to set this up for, so it's only got the base system, plus some daemons like ftp servers, apache, gnump3d, and a few others.  It also has only xdm and fluxbox installed, as well as a few other programs for admin purposes (xterm, browser, text file editor...).  Not sure if any of that matters, but perhaps vnc, or xdmcp requires something that isn't installed in the base system or xdm.

Again, thanks so much for the help.  If I get this running I can finally run my server headless.

---

### Post by intangible on 2005-06-27
If you run nmap on the machine, what do you see?  You did add the lines to inetd.conf as well?

---

### Post by spacemonkey on 2005-06-27
ok, I ran "nmap localhost" to scan for open ports and it returned this:

(only the relevant ones are listed)
5900/tcp open vnc
6000/tcp open X11:1

And yes, I did add the inetd.conf lines and restarted inetd.

---

### Post by spacemonkey on 2005-06-27
Oh wow.....I feel incredibly stupid....I found a typo in the line in inetd.config.  I swear I looked at that line 25 times, character for character, and didn't notice it until now.  Well it works great now.  Thanks a ton for the help, and the great howto.  I really appreciate it.

---

### Post by intangible on 2005-06-27
Heh, glad you found the problem, we all do that sometimes :D.

---

### Post by Blackie_Chan on 2005-06-28
[QUOTE=Blackie_Chan]I am using gdm which doesn't have Xaccess so how do I change who has access to VNC?

Thanks in advance.

BTW, at the moment I can 'vncviewer localhost' and the vnc window will open, but if I type 'vncviewer **my WAN IP**' the window doesn't open, seems like nothing happens.[/QUOTE]

I have checked to see that port 5900 is open by running 'nmap -sT -P0 -p 5900 **my WAN IP** and I get ```
PORT     STATE    SERVICE
5900/tcp filtered vnc

``` 

I also checked my internal IP, running 'nmap -sT -P0 -p 5900 **my internal IP**
and I got ```
PORT     STATE SERVICE
5900/tcp open  vnc
```

I uninstalled firestarter, and with all these efforts.  I still can't 'vncviewer **my WAN IP**'

Anymore suggestions?

---

### Post by intangible on 2005-06-28
If you're going through a router or even some cable modems, you have NAT setup and you may have to configure port-forwarding.

I'm not sure how much you know about networking, so I'm gonna break it down a little for you.

Here's an setup of someone with a router:

62.45.23.20 (Internet Ip)->Router Outside->Router Internal/Gateway (192.168.0.1)->Desktop External (192.168.0.101) aka NAT.
Your desktop also has the loopback address 127.0.0.1

Try running nmap on all your different IPs (except the gateway), It makes a big difference if it's your Internet IP that's filtering, or if it's your Desktop's NAT that is.

---

### Post by Blackie_Chan on 2005-06-29
[QUOTE=intangible]If you're going through a router or even some cable modems, you have NAT setup and you may have to configure port-forwarding.

I'm not sure how much you know about networking, so I'm gonna break it down a little for you.

Here's an setup of someone with a router:

62.45.23.20 (Internet Ip)->Router Outside->Router Internal/Gateway (192.168.0.1)->Desktop External (192.168.0.101) aka NAT.
Your desktop also has the loopback address 127.0.0.1

Try running nmap on all your different IPs (except the gateway), It makes a big difference if it's your Internet IP that's filtering, or if it's your Desktop's NAT that is.[/QUOTE]

I'm connected to the net using a router (there are 2 computers connected to it). I have setup port forwarding, everything on port 5800-5905 is forwarded to my computer.  Should running `nmap **My-Internet-IP**` tell me that port 5900 is open?  because as I wrote earlier, it says that the port is filtered.

---

### Post by intangible on 2005-06-29
We need to see where it's getting blocked... Open a terminal, paste this, and then send me scanlog.txt through private message.  This will scan just about everything that could be causing the problem.

*This assumes you have nmap and w3m installed and the interface you want to scan is eth0.*
```

echo "Looking up addresses...";IN=127.0.0.1;ON=`ifconfig eth0|grep -Eo \
"inet addr:[0-9.]{7,15}"|grep -Eo "[0-9.]{7,15}"`;IG=`route|grep -Eo "^\
default[ ]{1,}[0-9a-z]{1,}"|grep -Eo "[0-9a-z]{1,}\$"`;IA=`w3m -dump -n\
o-cookie "http://www.showmyip.com/simple/"|grep -Eo "[0-9.]{7,15}"`;ech\
o -en "Starting scan on the following:\n\nInternal\t$IN\nOutter  \t$ON\\
nGateway \t$IG\nInternet\t$IA\n\nResults will be in scanlog.txt\n\nPlea\
se Wait...\n";echo -ne "\nScans started at ">>scanlog.txt; date>>scanlo\
g.txt; echo -e "\nInternal: $IN\nOutter: $ON\nGateway: $IG\nInternet: $\
IA">>scanlog.txt;nmap $IN $ON $IG $IA>>scanlog.txt;echo Done.

```

Or you could manually scan everything yourself, but this does all the IP address lookups for you :D.

Anybody else having similar problems, feel free to PM me for help.

---

### Post by intangible on 2005-06-29
Just as a side-note: this is the thing I love most about Unix-like systems, you can combine all these commands, and have them pasted by someone into a terminal instead of having to ask them 100 questions or explain a bunch of different things.

---

### Post by Blackie_Chan on 2005-06-29
> **intangible]We need to see where it's getting blocked... Open a terminal, paste this, and then send me scanlog.txt through private message.  This will scan just about everything that could be causing the problem.

*This assumes you have nmap and w3m installed and the interface you want to scan is eth0.*
```

echo "Looking up addresses..." said:**
> {7,15}"|grep -Eo "[0-9.]{7,15}"`;IG=`route|grep -Eo "^\
default[ ]{1,}[0-9a-z]{1,}"|grep -Eo "[0-9a-z]{1,}\$"`;IA=`w3m -dump -n\
o-cookie "http://www.showmyip.com/simple/"|grep -Eo "[0-9.]{7,15}"`;ech\
o -en "Starting scan on the following:\n\nInternal\t$IN\nOutter  \t$ON\\
nGateway \t$IG\nInternet\t$IA\n\nResults will be in scanlog.txt\n\nPlea\
se Wait...\n";echo -ne "\nScans started at ">>scanlog.txt; date>>scanlo\
g.txt; echo -e "\nInternal: $IN\nOutter: $ON\nGateway: $IG\nInternet: $\
IA">>scanlog.txt;nmap $IN $ON $IG $IA>>scanlog.txt;echo Done.

```

Or you could manually scan everything yourself, but this does all the IP address lookups for you :D.

Anybody else having similar problems, feel free to PM me for help.

Thanks for the script, I ran it and was able to find the problem with my setup.

It was actually a stupid mistake on my part. In my router settings, I didn't check a checkbox (which would enable the corresponding virtual server'). I've actually never noticed the checkbox until today.

Now when I run 'nmap **My-Internet-IP**' I'm told port 5900 is open instead of filtered.

---

### Post by spacemonkey on 2005-06-29
> Since you are running it headless, you made sure to disable the local X server to save yourself some memory, right?
If not, just comment out the 0=Standard line in the [servers] section in /etc/X11/gdm/gdm.conf. 

How would I do this for xdm?

EDIT:
Bah, nevermind....A little fiddling and I figured it out.  I just had to comment out the line at the bottom of the /etc/X11/xdm/Xservers file.

---

### Post by intangible on 2005-06-29
Glad you got it; I figured it was either that or a firewall on the computer itself.  It's easy to overlook stuff like that, I do it all the time. :lol:

---

### Post by Devi0s on 2005-06-30
I actually ended up using x11vnc to do it.  Here's how:

First of all, disable Desktop Sharing with Vino under System -> Preferences -> Remote Desktop.

Use synaptic to install x11vnc.

Once x11vnc is installed, you will need to create a password file that x11vnc will use.  Do this:

```
sudo x11vnc -storepassword yourpasswordhere /etc/x11vnc.pass
```

Now, we need to configure GDM to run x11vnc when it loads:

```
sudo nano -w /etc/X11/gdm/Init/Default
```

Add this line to the file:

```
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
```

Now, we need to make a change to another file:

```
sudo nano -w /etc/X11/gdm/gdm.conf
```

In the [Debug] section, find the line:

```
#KillInitClients=true
```

And change it to

```
KillInitClients=false
```

Restart gdm (you can just reboot), and you are good to go.

---

### Post by intangible on 2005-06-30
That looks like the newest x11vnc from Breezy, the one from Hoary doesn't have the same options.

---

### Post by _Pete_ on 2005-06-30
[QUOTE=Blackie_Chan]I'm connected to the net using a router (there are 2 computers connected to it). I have setup port forwarding, everything on port 5800-5905 is forwarded to my computer.  Should running `nmap **My-Internet-IP**` tell me that port 5900 is open?  because as I wrote earlier, it says that the port is filtered.[/QUOTE]

Have you tried to scan you WAN-IP outside of your LAN? I'm have similar setup, Telewell EA400 which is doing to firewalling & NAT for all 4 computers in the LAN. I since the WAN IP is assigned to the telewell itself I can't nmap directly it from inside the LAN. Instead I do that from some other machine out in the WAN to check what is the port status really.

---

### Post by intangible on 2005-07-01
That is a good thing to remember, I have the same situation here.  Luckily the parent poster got his setup going now :D.

---

### Post by kingzasz on 2005-07-02
How do I Enable XDMCP in Kubuntu (running KDE)?

---

### Post by intangible on 2005-07-02
I don't use kdm, but I believe the following will get it working:

**sudo gedit /etc/kde3/kdm/kdmrc**

look for **[xdmcp]** and set the option **Enable=false** to **Enable=true**

**sudo gedit /etc/kde3/kdm/Xaccess**

add **localhost** to the bottom of the file

**sudo /etc/init.d/kdm restart** (this might kick you out of X)

There might be a gui for it already though, does **kdm_config** show anything?

---

### Post by traherom on 2005-07-02
I've been trying to get Cygwin to work completely without its registry entries so I can stick it on my thumbdrive for a while. This just saved me time and a lot of space!

Thanks! Works great here.

---

### Post by ions on 2005-07-05
I have a client that managed to delete one of the panels in Gnome.  Thus he is left with no menu to start his applications and has no clue how to re-create the gnome panel.  So I would like to go into his computer and recreate the panel.

First, is vncviewer what I need to do this?

Second, how do I enable desktop sharing by ssh?  Since he deleted the menu I can't have him go into System, Admin, etc.  I need to do it via ssh.

Currently when I try to run vncviewer I get this of course: Unable to connect to VNC server

---

### Post by intangible on 2005-07-05
Tell him to right-click on his background and select **Open Terminal**
Then, have him type **vino-preferences**.  There he can check **Allow other users to view your desktop** and he can set a password.  Then you just connect to him through VNC.  If he doesn't know is ip address, he can type **ifconfig eth0** in the terminal window after enabling the remote desktop.

---

### Post by ions on 2005-07-05
The problem is this user is not at the level to do that sort of VERY simple thing.  And it's MY job.  So, I need to change these things.  I got it going through ssh.  Now I just gotta figure out vncviewer... :)  Thanks!

Edit: Just as a rant if I had been using Gnome 2.8's menu I could have right-clicked on the 'Remote Desktop' menu item looked at the Properties and seen the command to start it...Gnome Devs, PLEASE bring back some menu functionality!!

---

### Post by shizow on 2005-07-05
[QUOTE=intangible]I don't use kdm, but I believe the following will get it working:

**sudo gedit /etc/kde3/kdm/kdm.options**

look for **[xdmcp]** and set the option **Enable=false** to **Enable=true**

**sudo gedit /etc/kde3/kdm/Xaccess**

add **localhost** to the bottom of the file

**sudo /etc/init.d/kdm restart** (this might kick you out of X)

There might be a gui for it already though, does **kdm_config** show anything?[/QUOTE]


in the file kdm.options there is no [xdmcp]
```

# /etc/kde3/kdm/kdm.options
#
# configuration options for kdm
# See kdm.options(5) for an explanation of the available options.

no-ignore-nologin
no-restart-on-upgrade
use-sessreg

```

---

### Post by ions on 2005-07-05
After doing this Evolution will not start: [http://www.ubuntuforums.org/showthread.php?t=42803&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=42803&page=2&pp=10)

The only thing different from the last time I ran Evolution succesfully is getting VNC setup as set out in the first post of this topic.  I can't fathom why they'd be related but here we are.

---

### Post by intangible on 2005-07-05
Actually, I think the file is /etc/kde3/kdm/kdmrc.

I'm sorry, I don't actually use kdm, so I was recalling from memory.  I had a 50/50 chance of getting it right :D.

---

### Post by shizow on 2005-07-06
[QUOTE=intangible]Actually, I think the file is /etc/kde3/kdm/kdmrc.

I'm sorry, I don't actually use kdm, so I was recalling from memory.  I had a 50/50 chance of getting it right :D.[/QUOTE]

thanks really, that was the right file and it works!

but i need something else,
can i connect in to a running x session without getting a new x session

the thing is that i want to run my desktop without monitor, and on the desktop some x applications like emule need to be controlled but then i need to log into the running x session

---

### Post by intangible on 2005-07-06
Look under **System->Preferences->Remote Desktop**  Enable that to have a VNC session for the current desktop.  If you use this HOWTO and that one together, the remote desktop will start on 5901 instead of 5900.

The built-in remote desktop doesn't support copy and paste between the two hosts and is pretty slow, so I made another howto on how to use x11vnc instead.  It performs better and supports clipboard between hosts.  You can find it here: [thread]45565[/thread]

---

### Post by sinky on 2005-07-06
Thanks for the howto.  I managed to get it working, but is there any way of keeping all the apps running after vnc is closed so they'll still be there when the user logs in again?

---

### Post by intangible on 2005-07-06
Look into "freenx" it does what you ask, and it has encryption and compression to boot! :D

---

### Post by sinky on 2005-07-06
Thanks, freenx works great.  Found out how to install it [here](http://oakley.bioinformaticsonline.co.uk/?q=node/18).

---

### Post by stefanoaguiar on 2005-07-11
Hey, intangible, great HOWTO. Got it working in minutes, and tested it with a friend on another town. But it didn´t solve my initial problem, that is connecting from my Windows 2000 box at work. 

The point is, at work I´m under a firewall that let´s only port 8080 open. By marking the "Honor indirect requests" on the XDMCP screen would this be solved?

Thx in advance.

---

### Post by intangible on 2005-07-12
The easiest fix is to tell inetd to listen on 8080 for VNC as well as the standard VNC port.

Leave your setup as it is, add this to your **/etc/inetd.conf** in addition to the normal line:
```
8080    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=Server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
```

There's also a fix where you can use SSH and tunnel your connection encrypted, but it's a little more complex, it's what I do.

---

### Post by toastedd on 2005-07-15
[QUOTE=intangible]Look into "freenx" it does what you ask, and it has encryption and compression to boot! :D[/QUOTE]

Hi intangible,

Is "FreeNX" the *only* way to have apps remain running after closing a VNC session? To me it seems a fairly basic feature, it's in Microsoft's RDP, you just press "disconnect" instead of "log off". I was just wondering if I'm able to do this with XDMPC without having to install FreeNX.

FreeNX looks good so I will probably install it anyway, I'm actually just curious :-)

Thanks for the guide,
-ToAsTeDd.

---

### Post by stefanoaguiar on 2005-07-15
[QUOTE=intangible]The easiest fix is to tell inetd to listen on 8080 for VNC as well as the standard VNC port.

Leave your setup as it is, add this to your **/etc/inetd.conf** in addition to the normal line:
```
8080    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=Server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
```

There's also a fix where you can use SSH and tunnel your connection encrypted, but it's a little more complex, it's what I do.[/QUOTE]
 Hey there! Unfortunately all the good help was useless. A friend of mine was able to connect, access and control my computer in both ways: SSH tunnel and direct VNC through XDMCP - all from his Ubuntu box. But myself, from the Win2000 work box couldn´t connect. The company firewall isn´t blocking 8080, ´cause my friend installed Apache2 on my computer and on the same time I was able to connect to it. 
I don´t know, but it seems to me that the clients I´m using for VNC are not connecting to the port I tell them to. 
I tried RealVNC, TightVNC and Putty. None of them has options for selecting the port. UltraVNC I couldn´t manage to install here.

Think I´ll move on to finding another solution, like creating my own webproy, like [www.anonymizer.com](www.anonymizer.com) and alikes.

Anyway, thank you a lot for your help and attention, intangible. Now I really know how to make things work, on systems not blocked by this bloody firewall.

---

### Post by toastedd on 2005-07-16
Well I tried FreeNX server and client.

Works... most of the time. My Suspended sessions tend to stop working after a while and it will then decide to create a new session, leaving unable to resume my old session, having to restart X and lose my work. I'm having trouble finding info/help for FreeNX. It is definitely very fast though.

Are you sure that FreeNX is the only way to have resumable sessions ?

---

### Post by toastedd on 2005-07-18
Actually, nevermind.

I've read up on just plain normal VNC.

Normal VNC (vncserver) works fine and does exactly what I want it to do (resume sessions reliably).

I may look into FreeNX later on when I understand it more or when I need the speed, but for now it's too much trouble.

Thanks

---

### Post by Jade Robbins on 2005-08-06
[QUOTE=intangible]The easiest fix is to tell inetd to listen on 8080 for VNC as well as the standard VNC port.

Leave your setup as it is, add this to your **/etc/inetd.conf** in addition to the normal line:
```
8080    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=Server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
```

There's also a fix where you can use SSH and tunnel your connection encrypted, but it's a little more complex, it's what I do.[/QUOTE]
 intangible, could you give us instructions for disabling X for that headless/mouseless server? my server is running on an older machine and could use any extra juice it can get!

---

### Post by intangible on 2005-08-09
Sure thing, are you running GDM, XDM, or KDM?

---

### Post by Jade Robbins on 2005-08-09
[QUOTE=intangible]Sure thing, are you running GDM, XDM, or KDM?[/QUOTE]
 GDM! Thanks!

---

### Post by intangible on 2005-08-12
sorry about the delay in replying, here ya go:

open a terminal and:
**sudo nano /etc/gdm/gdm.conf**

look for the **[servers]** section
replace : **0=Standard**
with this: **#0=Standard**

press **ctrl X** to close nano and save changes when it asks, then
**sudo /etc/init.d/gdm restart**

There ya go.

---

### Post by Jade Robbins on 2005-08-16
[QUOTE=intangible]sorry about the delay in replying, here ya go:

open a terminal and:
**sudo nano /etc/gdm/gdm.conf**

look for the **[servers]** section
replace : **0=Standard**
with this: **#0=Standard**

press **ctrl X** to close nano and save changes when it asks, then
**sudo /etc/init.d/gdm restart**

There ya go.[/QUOTE]
 thank you for the help!

Did anyone find a good solution to resumable sessions using what we did in this guide?

---

### Post by SlimDady on 2005-08-18
[QUOTE=Jade Robbins]thank you for the help!

Did anyone find a good solution to resumable sessions using what we did in this guide?[/QUOTE]

I am also looking for a solution to this.

With remote desktop client and my old windows server i could start a session.. do somthing then close the remote desktop client. WIthought closing the session.

Then the next itme i open it it will resume. I totally would love this with vnc

---

### Post by intangible on 2005-08-22
If you're looking for a more robust solution for something like that, you may want to look into "freenx".  It handles encryption, compression, and resumeable sessions.  

Here's the way to do it with standard vnc server, straight from the Xvnc4 man page :D
```

       In the wait mode, when the first connection comes in, inetd  gives  the
       listening  socket to Xvnc.  This means that for a given TCP port, there
       is only ever one Xvnc at a time.  Further  viewer  connections  to  the
       same  port  are accepted by the same Xvnc in the normal way.  Even when
       the original connection is broken, the Xvnc will continue to  run.   If
       this  is  used  with  the  XDMCP options -query and -once, the Xvnc and
       associated X clients will die when the user logs out of the  X  session
       in the normal way.  It is important to use a VNC password in this case.
       A typical entry in inetd.conf might be:

       5951   stream   tcp wait   james      /usr/local/bin/Xvnc  Xvnc  -inetd
       -query localhost -once passwordFile=/home/james/.vnc/passwd

       In  fact typically, you would have one entry for each user who uses VNC
       regularly, each of whom has their own dedicated  TCP  port  which  they
       use.  In this example, when user "james" connects to :51, he enters his
       VNC password, then gets the XDM login screen where he logs  in  in  the
       normal  way.   However, unlike the previous example, if he disconnects,
       the session remains persistent, and when he reconnects he will get  the
       same  session  back again.  When he logs out of the X session, the Xvnc
       will die, but of course a new one will  be  created  automatically  the
       next time he connects.

``` 

You can create the passwd file it specifies using **vncpasswd**

---

### Post by MemoryDump on 2005-08-26
is it at all possible to get FreeNX to resume an already "locally" logged on session? Display :0 for example. Again, similiar to M$'s Remote Desktop where I can login at home.. go to work and resume that same active session.. you know what I mean? I know I can resume FreeNX session initiated using FreeNX however I can't go home and resume that session locally.. or can I?

thxs
-MD

---

### Post by Jade Robbins on 2005-08-26
[QUOTE=MemoryDump]is it at all possible to get FreeNX to resume an already "locally" logged on session? Display :0 for example. Again, similiar to M$'s Remote Desktop where I can login at home.. go to work and resume that same active session.. you know what I mean? I know I can resume FreeNX session initiated using FreeNX however I can't go home and resume that session locally.. or can I?

thxs
-MD[/QUOTE]
 i actually believe there would be the same problem with the VNC fix intangable setup earlier as well, which is what i need unfortunatly.

---

### Post by intangible on 2005-08-26
Well, there's the built-in remote desktop, (**System->Preferences->Remote Desktop**) which uses vino. If you use this VNC->GDM HOWTO here, it'll probably run on the next port up (5901) instead of the default.  The thing is, it's slow... very slow... and it doesn't do clipboard copy and paste.

There's a solution using another program as a replacement called **x11vnc** that's quite usable (though not as fast as one using the pure VNC->GDM, which is faster because it never has a physical screen to update). 
I put a howto use x11vnc **automagically** here: [thread]45565[/thread]

I use this solution daily to connect from work to home without having to log out of my computer before I leave the house (because logging in the same account twice on the same computer acts a little wonky with Gnome).

---

### Post by master_b on 2005-08-27
How about Screen?

Haven't tried it myself as I've only just got my File/Print Server running and haven't got that far yet.

Here's a link to a HowTo:-

[http://learn.clemsonlinux.org/wiki/Screen](http://learn.clemsonlinux.org/wiki/Screen)

I understand tht it keeps your programs running between remote sessions.

Some time ago there was an article in a Linux Mag about this, but I can't remember which.

Whenh I find it I'll post again.

Bill

---

### Post by master_b on 2005-08-29
Here's the link for the  article on Screen - It was not a Mag but Linux.com posting.

[http://applications.linux.com/article.pl?sid=04/11/29/1651257](http://applications.linux.com/article.pl?sid=04/11/29/1651257)

Bill

---

### Post by er4z0r on 2005-09-19
Could it be that the vnc4server package is broken on breezy?

I did everything according to your HOWTO and I could not get it working:

nmap shows port 5900 and 5901 (vino) as open.

also does netstat -ntlp show it as running
 tcp6       0      0 :::5900                 :::*                    LISTEN     5685/inetutils-inet

But still I can not connect to the system from my windows box (both tightvnc and RealVNC fail)

What am I doing wrong?

---

### Post by intangible on 2005-09-21
will you post your inetd.conf? (or xinetd.conf if that's what you use)

Also, you are sure XDMCP is enabled for GDM?

---

### Post by Concord Dawn on 2005-09-29
[QUOTE=zaguar]Is this secure?  ie. is it possible for a hacker to enter the system with VNC enabled?[/QUOTE]

If you have the computer on the internet, it's possible for a hacker to get it :rolleyes: But a properly secured VNC shouldn't present any security risks. If you're really concerned, you can make sure that only certain IPs can connect to the VNC server (port 5900)

---

### Post by taewon on 2005-10-03
Same problem with breezy here (updated from working conf of hoary, i.e. XDMCP was working via vnc)...

XDMCP was turned off after the upgrade and thus I turned it on manually.

Here's the inetd.conf
# /etc/inetd.conf:  see inetd(8) for further informations.
#
# Internet server configuration database
#
#
# Lines starting with "#:LABEL:" or "#<off>#" should not
# be changed unless you know what you are doing!
#
# If you want to disable an entry so it isn't touched during
# package updates just comment it out with a single '#' character.
#
# Packages should modify this file by using update-inetd(8)
#
# <service_name> <sock_type> <proto> <flags> <user> <server_path> <args>
#
#:INTERNAL: Internal services
#echo           stream  tcp     nowait  root    internal
#echo           dgram   udp     wait    root    internal
#chargen        stream  tcp     nowait  root    internal
#chargen        dgram   udp     wait    root    internal
#discard        stream  tcp     nowait  root    internal
#discard        dgram   udp     wait    root    internal
#daytime        stream  tcp     nowait  root    internal
#daytime        dgram   udp     wait    root    internal
#time           stream  tcp     nowait  root    internal
#time           dgram   udp     wait    root    internal

#:STANDARD: These are standard services.
#<off># ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/proftpd

#:BSD: Shell, login, exec and talk are BSD protocols.

#:MAIL: Mail, news and uucp services.

#:INFO: Info services

#:BOOT: Tftp service is provided primarily for booting.  Most sites
# run this only on machines acting as "boot servers."

#:RPC: RPC based services

#:HAM-RADIO: amateur-radio services

#:OTHER: Other services
5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=Server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd

---

### Post by intangible on 2005-10-04
Looks like breezy has a broken Xvnc right now (try running Xvnc :1 from a terminal, you'll see that it looks for a 'fixed' font that it cannot find).

---

### Post by taewon on 2005-10-05
[QUOTE=intangible]Glad I helped.
Since you are running it headless, you made sure to disable the local X server to save yourself some memory, right?
If not, just comment out the **0=Standard** line in the **[servers]** section in **/etc/X11/gdm/gdm.conf**.[/QUOTE]
How can I disable the local x server if I'm using xdm?

Thanks in advance!

---

### Post by intangible on 2005-10-06
After mucking around a bit, found a switch to make it work in breezy.
First, run **gdmsetup** and then goto the **Security Tab** and make sure the last option **Deny TCP** is unchecked.  Restart gdm: **/etc/init.d/gdm restart**
Second, add this to the end of the line in **/etc/inetd.conf**:
```
-fp /usr/share/X11/fonts/misc/
```
Also, just restarting inetd doesn't seem to be enough to make things work on my test machine (could be because of multiple network interfaces?) So try a full system restart if that doesnt make it work.

---

### Post by btdown on 2005-10-09
Anyone up for creating this how-to for Breezy? I tried it, thinking it may be the same, and I dont even have an /etc/inetd.conf file...

Could anyone recreate this how-to with a breezy focus?

Thanks,
BT

---

### Post by T-One on 2005-10-13
[QUOTE=intangible]After mucking around a bit, found a switch to make it work in breezy.
First, run **gdmsetup** and then goto the **Security Tab** and make sure the last option **Deny TCP** is unchecked.  Restart gdm: **/etc/init.d/gdm restart**
Second, add this to the end of the line in **/etc/inetd.conf**:
```
-fp /usr/share/X11/fonts/misc/
```
Also, just restarting inetd doesn't seem to be enough to make things work on my test machine (could be because of multiple network interfaces?) So try a full system restart if that doesnt make it work.[/QUOTE]

This worked for me. Thanks!

---

### Post by thnogueira on 2005-10-14
Didn't worked on my Kubuntu Breezy Box :confused: 

My added inetd.conf line:

```

5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=Server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none -fp /usr/share/X11/fonts/misc/

```

Yes, I have retarted the system...

```

thnogueira@amdsp:~$ Xvnc :1

Xvnc version 4.0 - built Apr 19 2005 04:26:49
Underlying X server release 40200000, The XFree86 Project, Inc


Fri Oct 14 23:43:42 2005
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!

Fatal server error:
could not open default font 'fixed'


```

---

### Post by T-One on 2005-10-15
okay, this is weird. This worked on ONE of my boxes with breezy, but I upgraded a different box, and this doesn't work...

---

### Post by Raj on 2005-10-19
EDIT - I sorted out the problem...firestarter was tricking me...thanks for all the help everyone
--------------------------------------
Hi intagible,

Okay, I have a day off work [tore a muscle in my back] so I thought I would try and set this up. Now [after a couple of hours of trying] I not only have a [more] sore back, but very patchy chuncks of hair :(

I have tried everything you have said, from the begining. I have the result of the scanlog.txt from the below commands, could I send them to you via PM?

Cheers

Raj

> **intangible]We need to see where it's getting blocked... Open a terminal, paste this, and then send me scanlog.txt through private message.  This will scan just about everything that could be causing the problem.

*This assumes you have nmap and w3m installed and the interface you want to scan is eth0.*
```

echo "Looking up addresses..." said:**
> {7,15}"|grep -Eo "[0-9.]{7,15}"`;IG=`route|grep -Eo "^\
default[ ]{1,}[0-9a-z]{1,}"|grep -Eo "[0-9a-z]{1,}\$"`;IA=`w3m -dump -n\
o-cookie "http://www.showmyip.com/simple/"|grep -Eo "[0-9.]{7,15}"`;ech\
o -en "Starting scan on the following:\n\nInternal\t$IN\nOutter  \t$ON\\
nGateway \t$IG\nInternet\t$IA\n\nResults will be in scanlog.txt\n\nPlea\
se Wait...\n";echo -ne "\nScans started at ">>scanlog.txt; date>>scanlo\
g.txt; echo -e "\nInternal: $IN\nOutter: $ON\nGateway: $IG\nInternet: $\
IA">>scanlog.txt;nmap $IN $ON $IG $IA>>scanlog.txt;echo Done.

```

Or you could manually scan everything yourself, but this does all the IP address lookups for you :D.

Anybody else having similar problems, feel free to PM me for help.

---

### Post by zorzeta on 2005-11-04
The same problems. None of VNC to GDM HowTo's posted in this forum by now work with CLEAN Ubuntu Breezy install. Tried all of them. 

Server seemed to work, but no connections from clients, even from localhost. The same time Remote Desktop (vivo) works just fine.

It would be nice to have guaranted to work on Breezy VNC to GDM HowTo finaly.

---

### Post by isaac_golding on 2005-11-06
Have you looked at  XDMCP?

This is super simple and works  "OUT OF THE BOX" for a local lan.
I'm making a few assumptions:

#1 no firewall on the boxes (hopefully behind a router)

#2 you havent hacked up your box trying all of this other stuff.

#3 Thes boxes are all on a Local lan  not  work to home or vica versa

**On the pc you want to access**
Go to System -> Administration -> New Login setup

Amongst the tabs (security tab) you will find the option to ENABLE XDMCP

I also unchecked the last option (deny TCP connections)  But im not sure that matters and am too lazy to test it out.

Once you've checked those options close the panel.

Go to client pc  (one you are accessing from)

go to System Tools -> New Login,   (screen will change but not log you out of  current user totally (like fast user switching in XP)

On the login screen that appears goto Actions -> Run XDMCP chooser

The XDMCP chooser will appear and scan your network for XDMCP enabled X sessions.  (on port 177 udp)   If its not listed then something is blocking the port.   If its listed choose it and hit connect it should take you to the login screen for that box.


Logout when done and you will return to your local login on your current box.
This is all I know on this as this is day one of using this feature for me.

I do know that its not the most secure system in the world but if your needs are like mine and you have several linux boxes with Gnome installed its an easy way to get around a local network.

:)

---

### Post by shizow on 2005-11-08
[QUOTE=intangible]After mucking around a bit, found a switch to make it work in breezy.
First, run **gdmsetup** and then goto the **Security Tab** and make sure the last option **Deny TCP** is unchecked.  Restart gdm: **/etc/init.d/gdm restart**
Second, add this to the end of the line in **/etc/inetd.conf**:
```
-fp /usr/share/X11/fonts/misc/
```
Also, just restarting inetd doesn't seem to be enough to make things work on my test machine (could be because of multiple network interfaces?) So try a full system restart if that doesnt make it work.[/QUOTE]

what shall i do to get this to work in kdm with breezy?

---

### Post by LxP on 2006-02-18
I would like to politely second/third/X the request to have this thread updated for the Breezy distribution.

I understand that [another thread is available]("http://ubuntuforums.org/showthread.php?t=45565") which discusses the use of x11vnc, however I see this proposed approach as a generally tidier one (the other seems to involve adjusting settings on a per-user basis; please do correct me if I'm wrong).

---

### Post by Abdi110 on 2006-03-17
Hi, can't seem to get this to work with Breezy. Here are the steps I took (sorry for the crap formatting).

1) sudo nano /etc/X11/gdm/gdm.conf
2) Under [security], set DisallowTCP to false
3) Under [xdmcp], set Enable to true, set HonorIndirect to false
4) Save and exit
3) sudo apt-get install vnc4server
4) sudo nano /etc/inetd.conf
5) Added in, saved, exit:

# VNC
5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none -fp /usr/share/X11/fonts/misc/

6) sudo reboot

Tried to connect to both port 5900 and 5901 from a Windows machine, both come back with failed connections. I had the "HOWTO: Set up VNC server with resumable sessions" setup running, which was fine and all but I would like to give my roommate access too. I went through and undid all of the changes I made with that HOWTO before messing around with this one.

Any help with this would rock, thanks in advance.

Edit: I should also note that this machine was a full install, not server.

---

### Post by intangible on 2006-03-22
You don't have a firewall enabled by chance do you?

---

### Post by Abdi110 on 2006-03-23
On said machine no, I do have a firewall setup on the network for internet access, but right now I'm just trying to connect locally.

---

### Post by intangible on 2006-03-24
Install nmap (**sudo apt-get install nmap**)and do **nmap 127.0.0.1** and then **nmap 10.0.0.1**(replace 10.0.0.1 with your box's ip address **sudo ifconfig** should show you it) just to make sure it is indeed listening;  once we find that out, we can go from there.

---

### Post by Abdi110 on 2006-04-04
[QUOTE=intangible]Install nmap (**sudo apt-get install nmap**)and do **nmap 127.0.0.1** and then **nmap 10.0.0.1**(replace 10.0.0.1 with your box's ip address **sudo ifconfig** should show you it) just to make sure it is indeed listening;  once we find that out, we can go from there.[/QUOTE]
Hi, sorry for taking so long, I got a new job. :D I went ahead and did the nmap, nothing shows up for both localhost and the ip of the machine on port 5900. Any ideas?

---

### Post by intangible on 2006-04-05
[QUOTE=Abdi110]Hi, sorry for taking so long, I got a new job. :D I went ahead and did the nmap, nothing shows up for both localhost and the ip of the machine on port 5900. Any ideas?[/QUOTE]

This would definately be easier to trouble-shoot in real-time, feel free to contact me through any of the IM names on my profile on here.

---

### Post by Omegatron on 2007-01-03
This would allow you to login from a remote computer through VNC, right?  Like you'd be able to see the GDM login window from a remote VNC viewer and then log in through that?  How would you get this enabled in Ubuntu 6.10?  

I already installed **vnc4server**.

Unlike the instructions, there's only a **System --> Administration --> Login Window** and then inside that under the **Remote** tab there's a single option **Style**:
[LIST]
[*]Remote login disabled
[*]Same as Local
[*]Plain
[*]Plain with face browser
[/LIST]
No mention of XDCMP explicitly, though in the Security tab it says *Disables X forwarding, but does not affect XDMCP* under **Deny TCP connections to Xserver**.

I already tried [this]("http://www.odrakir.com/blog/?p=201") but it didn't work.  I'm sick of hacking around with text files and command line options I found online from dubious sources and screwing up my installations with crap when I don't know too much about Linux yet.  I want to do this the (simple) orthodox (graphical) Ubuntu way.

---

### Post by Kreychek on 2007-07-13
First off, thanks for continually responding to replies on this thread. I believe I am experiencing a problem that no other users have posted on. I have narrowed it down to your memory-saving step of commenting out "0=Standard" in gdm.conf.

-----

I tried connecting using 2 different VNC Clients...

Using RealVNC:
After commenting that out, stopping/starting gdm and then restarting my VNC connection I find myself viewing a black and white dotted window with the mouse cursor stuck as the "working" or "loading" animation (the circle with the dots moving clockwise). On a minor note, the VNC client window is normally sized to the resolution I have set for X11 to run at, and it is now sized to some other, larger, resolution.

Using your recommended client, UltraVNC:
The following message is displayed upon attempting to connect...

"Connection failed - Error reading Protocol Version

Possible causes:

-You've forgotten to select a DSMPlugin and the Server uses a DSMPlugin
-Viewer and Server are not compatible (they use different RFB protocols)
-Bad connection"

------

The problem goes away and everything seems to work as it should if I uncomment the line in question.

For all intents and purposes you can consider me a complete novice to linux :) but I do notice when commenting out the 0=Standard line, I do save a buttload of resources and would very much like to keep it off since I'll only be accessing the machine remotely.

Thanks in advance!

Apologies if I am referring to a problem that has previously been solved in this thread, or elsewhere.

Also, is there anyway to setup the service such that, after logging in, the VNC connection doesn't cut out and have to be restarted after the remote desktop is all done loading? (without setting up an auto-login)

PS. I am running a fully updated Ubuntu 7.04. (As of the date of posting)

---

### Post by Akula on 2007-08-21
Hello.

I tried this way introduced in the first post of this thread but I can't find file /etc/inetd.conf . Anyone have idea what is the problem here?

I tried creating this file with required line in it but I get "the connection closed unexpectedly" error on VNC (which I'm using in WinXP computer).
I opened necessary ports in firestarter on my server. 

I'm using Ubuntu 7.04 (server install, in which I installed ubuntu-desktop). I need this server to be available from elsewhere (lan and wan) since after I finish installing it, it won't have any input/output devices on it. I need gui for start to familiarize myself with the whole system.

---

### Post by Akula on 2007-08-23
No one reading this anymore?

---

### Post by Dark Star on 2007-08-23
Very nice guide :D Thanks :D

---

### Post by hebetude on 2007-09-02
> **intangible said:**
> Glad I helped.

Since you are running it headless, you made sure to disable the local X server to save yourself some memory, right?
If not, just comment out the **0=Standard** line in the **[servers]** section in **/etc/X11/gdm/gdm.conf**.

Still loads the desktop on the local display with this setting

---

### Post by ErKaX on 2007-09-27
> **intangible said:**
> This howto is to show how to setup VNC to show a GDM login screen when you connect to your Ubuntu box, effectively using XDMCP over VNC.  A VNC client is easier to get going on Windows than a X server for most people, so here's how to use it to connect to your linux box.

I posted the instructions in another thread already, but decided to put them here as well so it's easier to find for everyone.

First thing you'll need to do is enable the universe repositories: [https://wiki.ubuntu.com//AddingRepositoriesHowto](https://wiki.ubuntu.com//AddingRepositoriesHowto)

Then it's just five easy steps:
[list=1]
[*] **System->Administration->Login Screen Setup**
Tab **XDMCP->Enable XDMCP** You can disable "Honor Indirect Requests"
For kdm or even xdm, just look through the settings and find XDMCP, make sure it's enabled.
[*] **sudo apt-get install vnc4server** (comes from universe)
[*] Put the following line at the end of **/etc/inetd.conf**:
```
5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=Server -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
```
Replace "Server" with something you want the window title to be, usually the server name.
[*] **sudo /etc/init.d/inetd restart**
[*] Log out of your desktop (to restart gdm, xdm, or kdm)
[/list] 

That's it!  Try connecting from another machine using and see how it goes.

If you need a VNC client for Windows, try out UltraVNC [http://ultravnc.sf.net](http://ultravnc.sf.net) it's the one I prefer.

For connecting from Linux vnc4viewer with tsclient work well.

intangible,
Thank you so much !!!! I was searching for this easy how-to for a couple of days but finnaly found. Thank you. Now I can remotely take over my physical screen by vnc.

I have some questions:
1. Is it possible to take over the initial login screen? Cause with this solution I have to login with root before i can take over the screen.
But is somehow my remote xubuntu machine is rebooted i can not take over the screen anymore ( without login first ).

2. Is it possible to login with user and password in vnc before connecting?

---

### Post by Skip Da Shu on 2007-11-21
> **stefanoaguiar said:**
> I tried RealVNC, TightVNC and Putty. None of them has options for selecting the port. UltraVNC I couldn´t manage to install here.

Using RealVNC viewer on winXP I just just fire up the viewer and enter the IP of the machine on my LAN 192.xxx.xxx.xxx:yy where yy is the number to add to 5900 so if enter 192.168.222.111:8 it will connect to that machine on port 5908... you can also just type in ip:5908.

---

### Post by Skip Da Shu on 2007-11-21
> **Devi0s said:**
> First of all, disable Desktop Sharing with Vino under System -> Preferences -> Remote Desktop.

I don't have this on Xubuntu Gutsy.  Not sure what the substitute is.

> Use synaptic to install x11vnc.  Did sudo apt-get and got it installed a couple weeks ago.

> Once x11vnc is installed, you will need to create a password file that x11vnc will use.  Do this:

```
sudo x11vnc -storepassword yourpasswordhere /etc/x11vnc.pass
```  I had also already done this in an earlier attempt but I actually didn't specify the file so it's up under /home/skip but x11vnc can find it.  

The following works when executed from a terminal command line and I can use RealVNC viewer to get to my already logged on Xubuntu desktop on 5908 from a winXP machine.
```
sudo x11vnc -forever -usepw -rfbport 5908 -allow 192.168.xxx. -sb 30 -o /var/log/vnclog
```

> Now, we need to configure GDM to run x11vnc when it loads:

```
sudo nano -w /etc/X11/gdm/Init/Default
```
***This is where the trouble starts! *** 
In Xubuntu Gutsy this path doesn't exist.  After way too many days I did find /etc/gdm/Init/Default.  This is what the top of it looks like: 

```
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH=/usr/bin:$PATH
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

sysresources=/etc/X11/Xresources

# merge in defaults
if [ -f "$sysresources" ]; then
    xrdb -merge "$sysresources"
```
And it goes on for another 50 or so lines of nested if statements.  So...
[LIST=1]
[*]Is this the right file?
[*]Does the x11vnc line get inserted right before the 'exit 0' command? (I hope)
[/LIST]

> Add this line to the file: ... 
I'll add my x11vnc line (above)** if** I'm in the right file and ya'll agree it's OK as is except for replacing "sudo" with the path to x11vnc.

> Now, we need to make a change to another file:

```
sudo nano -w /etc/X11/gdm/gdm.conf
```

In the [Debug] section, find the line:

```
#KillInitClients=true
```

And change it to

```
KillInitClients=false
```

What I have is a /etc/gdm/dgm.conf.  I have uncommented it and set it to false.

> Restart gdm (you can just reboot), and you are good to go.
Pending above.

Ya'll have NO idea how much getting this to work means to me.  This is my LAST major obstacle to replacing winXP on 8 other headless machines with Xubuntu.  Thanx so much for any help, Skip

PS:  In case you haven't figured it out yet... I'm a complete noob to Linux. So anything that's not DOS look alike or can't be done with sudo gedit you'll probably have to give me the command.

---

### Post by Skip Da Shu on 2007-11-22
> [Quote] First of all, disable Desktop Sharing with Vino under System -> Preferences -> Remote Desktop.
I don't have this on Xubuntu Gutsy. Not sure what the substitute is.[/quote]

I something that MIGHT be the equiv to this one.  **Settings>Login Window Preferences**, It has a Remote tab.  On this, from a pull down I can set "remote login disabled" or "same as local" or "plain with face browser".  This same panel has a button in the lower right labeled "Configure XDMCP" that shows up if you take it off of "remote login disabled".

I later figured out that this is in fact an execution of "sudo gdmsetup".

This is the closest thing I've found to disabling remote desktop.

Well all else in the previous post is now set... so time for a little test.

---

### Post by Skip Da Shu on 2007-11-22
I have this working now under Xubuntu 7.10 with some help from my "Gentoo geek" youngest son... it's a bit of a kludge but it's working.  

The problem encountered, once we had the x11vnc server started and running from the /etc/gdm/Init/Defalut script, was losing the session as soon as the login to the Xubuntu machine was completed.  This was from a RealVNC viewer on a winXP machine (local LAN).  Like the x11vnc server was stopped.   'Gentoo geek son' mumbled something about x11vnc ending when the gdm script ended...???  and then had to go to work.

I know, in the course of the last couple weeks trying to get this to work, I've read of this problem someplace... off to find that now but if you can help that'd be great.

The command in the /etc/gdm/Init/Default is:```
/usr/bin/x11vnc -bg -forever -rfbauth /home/skip/.vnc/passwd -usepw -rfbport 5908 -allow 192.168.xxx. -sb 15 -o /var/log/vnclog
```
The above gets x11vnc running and from the remote viewer allows me to login to the Xubuntu machine at the Xfce login screen.  

To resolve the 'drop' after login 'Gentoo geek son' had me select menu item Applications>Settings>Autostarted Applications and add the following as the command:```
/usr/bin/x11vnc -bg -forever -rfbauth /home/skip/.vnc/passwd -usepw -rfbport 5908 -allow 192.168.xxx. -sb 22 -o /home/skip/vnclog
``` This one was picky because it seems at this point there may be no session to prompt for the user password so 'sudo' wasn't used.  This required the password and log files to be accessible by me, the user.  I had to chmod the password file so it was readable by all as it shows being owned by root.  This may be due to how I created it (via sudo x11-vnc -storepasswd).  I realize this is not ideal but at this point it's accessible by  both the x11vnc started by gdm and the one autostarted in the desktop session.  If this is how this is just gonna have to be I'll go back and create two password files one for root (I assume) running the gdm Default script and another for the user running the autostarted x11vnc.

I was hoping that having two log files might actually help figure this out.

The log file out of the x11vnc started by gdm ends with with: ```
caught XIO error:
22/11/2007 15:01:31 deleted 36 tile_row polling images.
```

The log file out of x11vnc autostarted looks more normal and shows my remote winXP machine connecting and then being "gone" when I closed the remote RealVNC viewer.

This: ```
ps aux | grep x11
``` 
Returns: ```

skip      4770  0.0  1.1  14916  5764 ?        Ss   02:35   0:00 /usr/bin/x11vnc -bg -forever -rfbauth /home/skip/.vnc/passwd -usepw -rfbport 5908 -allow 192.168.xxx. -sb 22 -o /home/skip/vnclog
```
Showing me that the one running is the autostarted one.


What I don't understand and would **really** like to is **why does the initial x11vnc server lose the connection after I login** (requiring me reconnect or restart the viewer again and connect to the autostarted x11vnc).  Can anyone explain this in terms a noob would understand?  Is there a solution that would eliminate me having to start the second x11vnc server?

Thanx much for any answers, Skip

PS:  In Applications>Settings>Login Window (remote tab) I have "Remote Login Disabled".  Turning it to "Same as Local" doesn't seem to have any effect on this situation.  With it set to "Same as Local" I can configure XDMCP... but it's all off now.

PPS: entry changed in /etc/gdm/gdm.conf```

# To try to kill all clients started at greeter time or in the Init script.
# does not always work, only if those clients have a window of their own.
**KillInitClients=false**
LogDir=/var/log/gdm
```

---

### Post by Skip Da Shu on 2007-11-22
The more I read the stupider I feel...

Some things I read today on krunge's site and in the formums (now that x11vnc is mostly working) lead me to believe I am trying to implement the WRONG solution to my problem.

Let me restate my situation and maybe somebody could give me some input.

Today I have several machines that are just dedicated number crunchers.  They run winXP and they have RealVNC running as a service on them.   From a winXP machine from within my LAN (very, very rarely from outside the network on my laptop so I do have the router configured for port forwarding and dyndns set up).  I occasionally access them to check something or maybe to reconfigure their application.  Generally they just sit and run (dedicated number crunchers).  Rarely they have a crt, keyboard & mouse hooked to them but not often (changing BIOS, debugging or hardware changes only).  

When they convert to Xubunut (this one is the experiment) I'd like to leave them sitting "logged out" at the desktop login screen as they do in windows (open to better ideas here if there's a simple way to not even start the desktop till I need it).

When I do login to them via the RealVNC viewer I rarely spend more than 10 minutes on them and then logout and close the viewer.  I guess if I needed to run something longer running I would close the viewer and come back to check on it later (a resumable session?).

Todays reading has me thinking that x11vnc is the wrong solution and perhaps all I really need is vncserver as described [**HERE**]("http://ubuntuforums.org/showthread.php?t=122402")?

Thanx for the input, Skip

---

### Post by Skip Da Shu on 2007-11-23
Well disregard the above.  I backed out my x11vnc changes and tried to use vnc4server and inetd but only get to a gray screen with the X pointer.  So I'm back to my two step x11vnc setup of post #96.

---

### Post by krunge on 2007-11-24
> KillInitClients=false

Well, since you are setting the KillInitClients to false the is the right thing to do to solve the problem of x11vnc being killed by gdm right after you log in.  This is described in detail here: [http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager")

only thing I can think of is the system is strange in that it has multiple or another GDM config file; i.e. you are editing the wrong one.  Sorry, but I don't use any of the linux distros you use and so I can't tell what is up.  Look around for other gdm config files (hint use "locate" command or "find" matching gdm).  Also try making simple changes to the gdm.conf you are editing and see if they are picked up (i.e. change something else besides KillInitClients)

---

### Post by krunge on 2007-11-24
> **Skip Da Shu said:**
> Well disregard the above.  I backed out my x11vnc changes and tried to use vnc4server and inetd but only get to a gray screen with the X pointer.  So I'm back to my two step x11vnc setup of post #96.

Try jabbing one of the following into ~/.vnc/xstartup:

> startkde

gnome-session

startxfce

also removing the "twm" (or whatever) line in xstartup too.

You can use this to start any window-manager/desktop for vncserver you like.  You just have to figure out the command that starts the one you want.

---

### Post by Skip Da Shu on 2007-11-25
> **krunge said:**
> Well, since you are setting the KillInitClients to false the is the right thing to do to solve the problem of x11vnc being killed by gdm right after you log in.  This is described in detail here: [http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

only thing I can think of is the system is strange in that it has multiple or another GDM config file; i.e. you are editing the wrong one.  Sorry, but I don't use any of the linux distros you use and so I can't tell what is up.  Look around for other gdm config files (hint use "locate" command or "find" matching gdm).  Also try making simple changes to the gdm.conf you are editing and see if they are picked up (i.e. change something else besides KillInitClients)

NOTE: for this testing I have the 2nd, post login 'autostarted' interation x11vnc server disabled.

You were quite right... I don't pretend to understand it, especially since the comments in the top of the 2nd file say gdm.conf will override it but... I now have KillInitClients=false in two places.

In /etc/gdm/gdm.conf:
```
# User and group used for running GDM GUI applications.  By default this is set
# to user "gdm" and group "gdm".  This user/group should have very limited
# permissions and access to only the gdm directories and files.
User=gdm
Group=gdm

# To try to kill all clients started at greeter time or in the Init script.
# does not always work, only if those clients have a window of their own.
**KillInitClients=false**
LogDir=/var/log/gdm

# Note that a post login script is run before a PreSession script.  It is run
# after the login is successful and before any setup is run on behalf of the
# user.
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
DisplayInitDir=/etc/gdm/Init

# This runs Ubuntu's BulletProof-X failsafe mode.
FailsafeXServer=/etc/gdm/failsafeXServer
```
and in /etc/gdm/gdm.conf-custom:
```
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# Older versions of GDM used the "gdm.conf" file for configuration.  If your
# system has an old gdm.conf file on the system, it will be used instead of
# this file - so changes made to this file will not take effect.  Consider
# migrating your configuration to this file and removing the gdm.conf file.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# e.g, the "Enable" key in the "[debug]" section would be "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#

[daemon]
**KillInitClients=false**

[security]

DisallowTCP=false

[xdmcp]

MaxSessions=1

MaxPendingIndirect=1

HonorIndirect=false


[gui]

[greeter]

SoundOnLoginFile=

DefaultWelcome=false

GlobalFaceDir=//

SoundOnLogin=false

DefaultRemoteWelcome=false

Browser=false

DefaultFace=

[chooser]

[debug]

[servers]
```
While adding the KillInitClients to this 2nd file didn't solve the problem I think I got further and have a new error message. Here's the tail end of /var/log/vnclog:
```
24/11/2007 23:27:55 Got connection from client 192.168.218.21
24/11/2007 23:27:55   other clients:
24/11/2007 23:27:55 check_access: client 192.168.218.21 matches pattern 192.168.218.
24/11/2007 23:28:00 Disabled X server key autorepeat.
24/11/2007 23:28:00   to force back on run: 'xset r on' (3 times)
24/11/2007 23:28:00 created xdamage object: 0x400028
24/11/2007 23:28:01 Client Protocol Version 3.8
24/11/2007 23:28:01 Protocol version sent 3.8, using 3.8
24/11/2007 23:28:01 rfbProcessClientSecurityType: executing handler for type 2
24/11/2007 23:28:05 Pixel format for client 192.168.218.21:
24/11/2007 23:28:05   8 bpp, depth 8
24/11/2007 23:28:05   uses a colour map (not true colour).
24/11/2007 23:28:05 Enabling full-color cursor updates for client 192.168.218.21
24/11/2007 23:28:05 Enabling NewFBSize protocol extension for client 192.168.218.21
24/11/2007 23:28:05 Using ZRLE encoding for client 192.168.218.21
24/11/2007 23:28:05 Pixel format for client 192.168.218.21:
24/11/2007 23:28:05   32 bpp, depth 24, little endian
24/11/2007 23:28:05   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
24/11/2007 23:28:05 no translation needed
24/11/2007 23:28:05 Enabling full-color cursor updates for client 192.168.218.21
24/11/2007 23:28:05 Enabling NewFBSize protocol extension for client 192.168.218.21
24/11/2007 23:28:05 Switching from ZRLE to hextile Encoding for client 192.168.218.21
24/11/2007 23:28:05 client 1 network rate 2269.2 KB/sec (58575.9 eff KB/sec)
24/11/2007 23:28:05 client 1 latency:  0.5 ms
24/11/2007 23:28:05 dt1: 0.0660, dt2: 0.0022 dt3: 0.0005 bytes: 154326
24/11/2007 23:28:05 link_rate: LR_LAN - 1 ms, 2269 KB/s
caught X11 error:
24/11/2007 23:28:14 deleted 36 tile_row polling images.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  145 (MIT-SHM)
  Minor opcode of failed request:  4 (X_ShmGetImage)
  Serial number of failed request:  2749
  Current serial number in output stream:  2750 
```

How can I go about looking this error up?  Is it now telling me I have some sort of authority or shared memory error? 
```
/usr/bin/x11vnc -forever -bg -sb 15 -usepw -rfbauth /home/skip/.vnc/passwd -rfbport 5908 -allow 192.168.218. -o /var/log/vnclog
```

Thanx again, Skip

---

### Post by Skip Da Shu on 2007-11-28
I temporarily gave up on resolving this and moved this machine back to it's headless location.  After powering it back up I went to my winXP machine and used RealVNC viewer to access it expecting to have to use the started x11vnc server to login and then the desktop started server to work from... MUCH to my surprise the initial X11vnc server (started from /etc/gdm/Init/Default took me all the way to the desktop!  When I checked the log for the one that attempted to start with the desktop it had errored out for not being able to get the port.  I disabled the autostarted x11vnc, logged out and back in... it works.  The display comes up as 800x600 instead of 1024x768 but it's running off of the gdm started server!  The only change made that I hadn't tried before was there is now NO monitor, keyboard or mouse plugged into the machine.  Actually /etc/gdm/Init/Default entry:

```
/usr/bin/x11vnc -forever -bg -nofilexfer -sb 15 -usepw -rfbauth /home/skip/.vnc/passwd -rfbport 5908 -allow 192.168.218. -o /var/log/vnclog -auth /var/lib/gdm/:0.Xauth
```
Can someone explain this to me?  

Is there away to force it to use 1024x768 (not a desktop option shown now)?

I am going to plug a monitor back into it and see if it reverts to the error in the above post just to be sure.

UPDATE:  With monitor/keyboard plugged in and a reboot it's back to issue in prior post but the login screen is 1024x768.

Thanx, Skip

---

### Post by xp_newbie on 2007-12-03
> **intangible said:**
> [*] Put the following line at the end of **/etc/inetd.conf**:
Why inetd and not xinetd, as instructed in the following link?

[http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc%20login](http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc%20login)

Please note that in Ubuntu Dapper (6.06 LTS) there is no inetd...

---

### Post by Skip Da Shu on 2007-12-04
Well I'm gonna start over from OS install (wanna change it to 64bit anyway) on that machine because I set another one up last weekend and literally copied and pasted from this machine and it works fine.  Connects to the X11vnc server started in gdm and doesn't disconnect after login.  So I must have something else messed up on that machine in my various attempts.

---

### Post by Skip Da Shu on 2007-12-06
> **Skip Da Shu said:**
> Well I'm gonna start over from OS install (wanna change it to 64bit anyway) on that machine because I set another one up last weekend and literally copied and pasted from this machine and it works fine.  Connects to the X11vnc server started in gdm and doesn't disconnect after login.  So I must have something else messed up on that machine in my various attempts.

SOLVED - The after the install of the 64bit Gutsy I copied and pasted the  x11vnc changes into the appropriate files and all is well.  What was actually wrong I guess I'll never know but I suspect it may have something to do with my earlier attempts using just vnc4server and/or the XDMCP stuff.  

The casting of the magic stones into the goat entrails and reciting of ancient words probably had a lot to do with fixin' it also 
;)

---

### Post by GTSBaka on 2007-12-18
Hello,

Before I explain my problem, please forgive me for my approximative english and for not reading all the previous 11 pages.

I've got a linux box, where there is a xinetd VNC service running.
Some people are connected to it with thin clients terminals.

Since a few days ago, it seems the VNC service reject some connections.
In a term, it just says "**End of stream**" and close itself without starting gdm.

In /etc/gdm/gdm.conf there's
**MaxSessions=70**
in the [xdmcp] section

In /etc/xinetd.conf there's
**instances = 60**

... and when the crash appends, there are only about 10 people connected.

When I start vncviewer with **-log *:stderr:100** param, it says :
**Timer:       handleTimeout(0x542ea8 )**

I didn't find any other log on server-side. 

I've many open ports for Vnc, each pointing on a different depth/resolution.
When VNC start rejecting connections, other ports keep working. 
It seems there is a session limitation per vnc service, but I haven't specified it anywhere.

How can you explain that ?

PS : I hope i'm understable, it's kind of hard for me to write in english, but this thread seems to be the best for this topic.

---

### Post by gfunkdave on 2008-06-16
I cannot get this to work on Hardy. When I connect via my tunnelled SSH connection, my VNC client says "Please Wait, Initial Screen Loading" or I get the X-style wristwatch mouse pointer for a second (and a tan Ubuntu login screen background), and then disconnects with a "Connection Closed" message.

Any ideas? Here's what I've got:

Under System --> Administration --> Login Window:
-Remote style is "Same As Local"
-The Honor Indirect Requests box is unchecked
-In the Security tab, I have unchecked the "Deny TCP connections..." and "Never place cookies on NFS" boxes. (not sure what the last one does, really...)

In an effort to remove all unnecessary additions, I have this line in my /etc/inetd.conf:

```

5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -query localhost -once securitytypes=none

```

I also have the KillInitClients=false line in both /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom.


I don't know where Xvnc is putting its log, so I don't know where to look next. There is no /var/log/vnc*, but my auth.log seems to say that GDM is killing the connection because it can't determine the username:

```

Jun 16 16:29:25 meadows-server gdm[5965]: pam_nologin(gdm:auth): cannot determine username

```

Any ideas?

Thanks!

---

### Post by Skip Da Shu on 2008-06-17
> **gfunkdave said:**
> 
I don't know where Xvnc is putting its log, so I don't know where to look next. There is no /var/log/vnc*, but my auth.log seems to say that GDM is killing the connection because it can't determine the username:

```

Jun 16 16:29:25 meadows-server gdm[5965]: pam_nologin(gdm:auth): cannot determine username

```

Any ideas?

Thanks!

An idea only, no direct answer... the following two parms are on my x11vnc server startup (Default).  Maybe there are similar parms for what you are running.  Your problem sounds a bit like one I had at one point that I know the last parm resolved but I don't know now how I came up with it.

```
-o /var/log/xvnclog -auth /var/lib/gdm/:0.Xauth
```

---

### Post by gfunkdave on 2008-06-18
OK, some progress...

First, I figured out how to get Xvnc to make a log when run through inetd:

1. Make the directory /usr/adm
2. Make it writable by "nobody" (I just did a chmod 777 on it)
3. Now Xvnc will output logs to it when it's invoked from inetd.

Second, here's the log that appears:

> 

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Tue Jun 17 22:58:39 2008
 vncext:      VNC extension running!
 vncext:      created VNC server for screen 0
 Connections: accepted: 192.168.0.250::32858
 vncext:      added inetd sock
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
 SConnection: Client needs protocol version 3.4
 SConnection: Client uses unofficial protocol version 3.4
 SConnection: Assuming compatibility with version 3.3
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 8 (8bpp) bgr233

Tue Jun 17 22:58:40 2008
 VNCSConnST:  Client pixel format depth 16 (16bpp) little-endian rgb565
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixin
g.



This is what's in my inetd.conf:

```

5950    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -query localhost -once securitytypes=none

```

I just can't figure out for the life of me why things are not working. To recap, my VNC clients connect, show the brown Ubuntu desktop background with a wristwatch mouse cursor icon, then close. There is no error given.

I'm trying this with TightVNC viewer and UltraVNC viewer.

update: I am now getting this error in my /usr/adm log file:

> 
 XserverDesktop: XserverDesktop::wakeupHandler: unable to accept new
              connection: Invalid argument (22)


Any ideas?

---

### Post by gfunkdave on 2008-06-18
Some more interesting info. Removing "-query localhost" makes the X window at least persistent - but it just stays blank and gray with an X mouse cursor. Someone elsewhere had suggested "-query ::1" as working for him. It doesn't seem to make a difference for me.

I also replaces /usr/lib/gdm/gdmlogin with a script that just echoes some stuff to a file. gdmlogin IS being called.

Any ideas??? Anyone?

---

### Post by gfunkdave on 2008-06-18
GOT IT!!! After two solid days, I got it.

I started a vncserver manually with the vncserver command. Then I did a ps aux | grep Xvnc to find the command options vncserver sets things up with. I noticed it was appending "-extension XFIXES" to the command line options. I put that in to my xinetd command line, and things work now! 

Woohoo!

---

### Post by krizze on 2008-07-28
Thanks an awful lot gfunkdave! This totally saved my day :D
Edit: Also, thanks a lot for the nice howto :D

---

### Post by gfunkdave on 2008-07-28
Glad my struggles have helped others avoid ones of their own. :)

---

### Post by caue.rego on 2009-07-06
> **xp_newbie said:**
> Why inetd and not xinetd, as instructed in the following link?

[http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc%20login](http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc%20login)

Please note that in Ubuntu Dapper (6.06 LTS) there is no inetd...

Thanks for this link! Even if I still can't make it work anyway (in a zero'ed Jaunty), at least it seems like a better path. :)

---

### Post by diablothe2nd on 2009-07-15
> **gfunkdave said:**
> GOT IT!!! After two solid days, I got it.

I started a vncserver manually with the vncserver command. Then I did a ps aux | grep Xvnc to find the command options vncserver sets things up with. I noticed it was appending "-extension XFIXES" to the command line options. I put that in to my xinetd command line, and things work now! 

Woohoo!

i've been banging my head against the monitor for 4 hours now trying to get this to work - after much googling in frustration I saw your post

IT WORKED!

THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU

:lolflag:

---

