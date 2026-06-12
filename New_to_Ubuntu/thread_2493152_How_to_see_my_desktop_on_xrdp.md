---
title: "How to see my desktop on xrdp?"
date: 2023-12-05
forum: New to Ubuntu
---

### Post by polaatx on 2023-12-05
Hello, I am total newbie. I used an online tutorial to install xrdp on a remote server running [COLOR=#333333][FONT=&quot]Ubuntu 22.04 64 Bit.[/FONT][/COLOR]
 I was expecting to see a desktop. 
But when I login from my windows pc using Remote Desktop** I just see a black screen and a white terminal window. **
Can you please tell me how I can see the desktop or did I do something wrong during installation? 
I just want to open Firefox remotely and do some browsing. 
Sorry about a question that probably sounds really stupid to the experienced people.

---

### Post by TheFu on 2023-12-05
You don't need a full remote destkop just to run firefox on a different system and have it display locally.  Just use ssh.

```
$ ssh -X  deneb /usr/bin/firefox -no-remote 
```

So, 
[LIST]
[*]-X says to use X11-Forwarding. This will tunnel all X protocol in the session through the SSH tunnel.
[*]deneb is the DNS name of the remote system.  An IP address can be used instead.  My usernames on both systems match, to I don't need to specify that.
[*]-no-remote is required for firefox not to check and force a local version of firefox be started or used.  This is needed only for Mozilla programs.
[*]
[/LIST]

I need to say that snap-based firefox won't work.  That's due to how snap packages force constraints and don't allow us to override those constraints.  There are some workarounds, but if you are new, forgetaboutit.  Firefox needs to be a non-snap, non-flatpack, version.  If the remote system is Linux Mint, then the firefox there is fine.  If Ubuntu, you'll probably want to remove the snap-version of firefox and install the ESR non-snap version.

Clear enough?

I use firefox in this way constantly.  You should realize that video and audio probably won't work well enough, but displaying static pages or those with animated GIFs work fine.  Try it to see if your setup handles this well or not.  X11-Forwarding provides full integration of local and remote programs like they are all local to the system.

This same pattern can be used for nearly all programs without the massive overhead and security issues VNC/rdp include. Both VNC and RDP are not the best protocols to use for remote desktops.

Of course, this is an X/Windows thing, so you need to be running an X/Server on your local workstation, which means setting up the correct DISPLAY environment variable too.

BTW, the xrdp window you are seeing is probably just not running a window manager and a DE on top of that.  If you setup the init files for the connection to run a window manager, then a minimal desktop should be provided. **openbox** is a light WM.  Using a heaving DE will have negative impacts, since there are hundreds of objects that have to be transmitted across the wire with the added overhead of the graphics.  Using X11 directly is more efficient.  With the client/server communications going through ssh, security issues are effectively removed.  So, using ssh X11/forwarding is not just more secure, but more convenient.  That basically never happens.

---

### Post by MAFoElffen on 2023-12-05
@TheFu --

Something to consider with your 'X over ssh' answer to him...
> **polaatx said:**
> Hello, I am total newbie. 
...
But when I login from my windows pc using Remote Desktop
...

Windows does not have an XServer installed by default... Nor does it have ssh by default.

You said you followed a tutorial... What is the link to the turtorial so we know what you did, and what we can expect to help you with.

You said "on a remote server". Ubuntu Server does not have a desktop installed by default. So that begs to ask (again), what did you install on it?

This goes back to some more basic questions... starting with: "What is your Goal?

What do do need to do on this remote server? TheFu is correct... in that on a Linux Server, usually you manage it from another PC via an shh connection, via it's console based commandline. You can also run XServer from a remote server, without it actually having a desktop installed.

Being you are connecting from a Windows PC, that would require you ssh services on your Windows system. If you wanted to run GUI app's via X over shh, then you would need to enable WSL and install something XMing from the Windows store for Windows...

But going back to what "you" started, yes... to do xrdp server on the remote server, then you need to install a desktop for xrdp-server to use... configure the user to start that desktop on login...

You must also be aware that RDP protocols have a "limitation"... That only a "user" can be logged into it at one time... It can have multiple users logged in, but a user can only be logged in once. If a user is already logged in locally, it can not be logged in through an xrdp session. The connection will be refused. Does that make sense? To get around that, I would add a user named "xrdp-user" that I used just to do RDP sessions.

---

### Post by polaatx on 2023-12-06
> **MAFoElffen said:**
> @TheFu --

Something to consider with your 'X over ssh' answer to him...


Hello @MAFoElffen

Yes, you're correct. @TheFu 's answer, while I appreciate the time  put in, went right over my head. 

> 
This goes back to some more basic questions... starting with: "What is your Goal?

Glad you asked. 
My goal is to connect to the nerdrack server I just paid for from my windows machine using Remote Desktop and be able to use Ubuntu visually just like the way I use it on a local machine. I mean with a desktop, open a browser, be able to install programs, etc. 

I used this tutorial [https://www.cyberithub.com/how-to-install-xrdp-on-ubuntu-22-04-lts-jammy-jellyfish/](https://www.cyberithub.com/how-to-install-xrdp-on-ubuntu-22-04-lts-jammy-jellyfish/)  to install xrdp.

It says I should see this desktop:
 [IMG]https://i.postimg.cc/zXS9bbQQ/screenshot-www-cyberithub-com-2023-12-06-15-34-50.png[/IMG]
But, as I said, I'm just getting a black screen with white terminal.

I totally get how using the terminal is efficient. It blows my mind how quickly things happen when you know what you're doing. 
I just have too many things going on in my life so I keep relying on gui. Everytime I have to use the terminal I have spend all this time relearning the commands. And then a month later, when I need the terminal again, I've forgotten the commands.

---

### Post by TheFu on 2023-12-06
He shoots ... and misses!  Oh, well.  I missed "windows pc".  There are lots of different kinds of "windows", so I look for capitalization "Windows" or an exact name, like "MS-Windows".  Yep. No X/Server on MS-Windows, without adding it.  I've only used commercial X/Servers (Hummingbird), but I suspect only corporate users did.  Don't even know if that company is still in business.  Plus, they had to do some odd things to make X/Windows work on MS-Windows. It wasn't friendly to most users, including those with Unix Workstation background. And getting **ssh -X ** functionality out of MS-Windows back then was a real pain.

Back when I still used MS-Windows, I found that running a tiny Linux desktop virtual machine in virtualbox was a much better X/Server than any of the other options, plus it was free. But then you'd need to load virtualbox and a tiny version of Linux. That wasn't too hard, but remote desktops like rdp and VNC were terrible and buggy.  I think nothing much has changed there.  

Around 2010, I was in a regular job and had to use MS-Windows on a laptop. I found something called the NX protocol and researched the best implementations of it. There was a commercial version which allowed 3 clients to be used from No-Machine. They invented the NX protocol.  There were also a few other F/LOSS implementations - neatx, freeNX, and x2go.  Today, only x2go remains and I've been using it for full remote desktops over the internet since around 2012.  It feels 2-3x faster than any of the other options.  There's a Windows client and Linux server.  There are also clients for Linux and MacOS.  I used x2go daily for about 5 yrs and can vouch for the stability, security, performance, and the ability to drop a connection on 1 system, then reconnect later to the exact same session/place on another.  No more spending 5 minutes getting your desktop windows all setup just-so, at a new login.

BTW, while it may not see like it, my last paragraph tried to provide an answer to the initial question.  In short, you need to run a window manager, WM.  [https://en.wikipedia.org/wiki/Window_manager](https://en.wikipedia.org/wiki/Window_manager)   If you see a term that you don't know, wikipedia usually has the answer. I even provided a simple, light, window manager to be use, openbox.  You'd probabaly need to install that:
```
sudo apt install openbox
```
on the remote system.  I suspect you'd need to do that after making an ssh connection and perhaps updating the apt database.
Because the security of VNC and RDP are known to be weak/hackable, people usually setup an ssh tunnel between their clients. Some how-to guides from a few Universities:
[https://help.ece.gatech.edu/windows/remote-desk](https://help.ece.gatech.edu/windows/remote-desk)
[https://grit.ucsb.edu/tutorials/ssh-tunnel-windows-windows-or-linux-xrdp-installed](https://grit.ucsb.edu/tutorials/ssh-tunnel-windows-windows-or-linux-xrdp-installed)
[https://sas-it.rutgers.edu/how-to-guides/working-remotely/connecting-to-campus-resources/213-linux/730-remote-desktop-to-linux-machine-from-windows](https://sas-it.rutgers.edu/how-to-guides/working-remotely/connecting-to-campus-resources/213-linux/730-remote-desktop-to-linux-machine-from-windows)

I don't like to NOT provide an answer, even if it isn't the best real solution.  Linux isn't one of those things you can part-time use remotely without a significant "on-boarding" effort, I'm sorry to say and for the "corporate speak".   It is possible to use it locally with just the GUI, but remote takes more skill.

"nerdrack server" isn't a generic term everyone knows.  I made an assumption that it was a "normal VPS", available anywhere for $4/month, if you lease it for the entire month.  If it is something special, please enlighten us.  When I google the term, RackNerd came up.  That choice got me thinking you knew more about Linux, so I didn't need to be as detailed with my response.

As to which desktop you should see, that would depend on the version you installed. In Linux, a desktop GUI is just another program. There are many that are popular.  Also, the fancier desktops, also called "Desktop Environments" or "DEs", don't work well over remote connections.  I tried to steer you towards a light solution with openbox that would work well.  That tutorial seems to be showing Gnome, which is the hoggiest, hog, in the DE hog world.  Almost any DE besides that would be better.  XFCE, Mate, LXQt would all be better choices and are known to work over remote desktops.  Gnome is known to have issues.

You know, it is possible to use a remote system with just ssh as a SOCKS5 proxy and run Firefox locally, but have all traffic appear from that other system too.  Just offering that up as another option.  With Linux, there are usually 10 to 500 different solutions for the same problem.

---

### Post by MAFoElffen on 2023-12-06
Yes... Seeing that tutorial you followed, I see where you are and the missing pieces. That tutrial assumes that you started out with the remote machine starting out as Ubuntu Desktop edition being an Ubutu Desktop Edition... Where as Being a cloud instance you started out as an Ubuntu Cloud, image, where you would have to install XServer and at least a Minimal X Desktop...

If you wanted to use a Desktop, and being a self-proclaimed "Newbie", I would recommend installing some lightweight as a desktop. I would usually just go with a Minimal-X install. such as just 'lxqt-core'... 

Except, just having a desktop alone, with no other applications might not fill the bill with someone that is not comfortable with only a terminal with no applications there to use, so I would probably recommend installing a full light-weight desktop, with a lightweight suite of applications, such as the 'lxqt' suite... So let's shoot for that... 

Since a cloud instance, I might assume that you are probably logging in  as root presently, but just in case that is not the case, I added  "sudo" into all these. Does not hurt if either...
```

sudo apt update             ## refresh the apt cache
sudo apt install lxqt       ## Will pull in a lot of dependencies, including the full XServer packages

```
Since root has problems running XServer you need to create a user that can be connected via xrdp...
```

sudo adduser xrdp-user
sudo usermod -aG sudo xrdp-user
sudoedit /home/xrdp-user/.xinitrc

```
You are going to add this line at the end of that file, for it to start the lxde desktop, when zrdp logs it...
```

exec startlxqt

```
Ensure that "Port 3389" is open through any firewall that might be running on your server instance, and through your cloud console for your instance... That is what RDP protocol needs to connect via RDP.

Test it, and tell me how that goes.

---

### Post by TheFu on 2023-12-06
No need for an ssh tunnel to safely use rdp?

---

### Post by MAFoElffen on 2023-12-06
> **TheFu said:**
> No need for an ssh tunnel to safely use rdp?

LOL. He could add that for added security, once he gets xrdp working. Or an IPSEC tunnel... 

RE: [https://www.mandiant.com/resources/blog/bypassing-network-restrictions-through-rdp-tunneling](https://www.mandiant.com/resources/blog/bypassing-network-restrictions-through-rdp-tunneling)

I used to setup Win Server RDP Gateways through Cisco VPN...

Better to get things working 'correctly' before, adding more pieces to the complexity puzzle. Then you aren't wondering which piece of that is not working if it doesn't work right. (A step at a time...)

You want to talk him through that part?

---

### Post by TheFu on 2023-12-06
> **MAFoElffen said:**
>  You want to talk him through that part?

Post #5 provides 3 links to instructions from 3 different Universities, assuming MS-Windows. ;)

---

### Post by polaatx on 2023-12-06
> **TheFu said:**
> 
"nerdrack server" isn't a generic term everyone knows.  I made an assumption that it was a "normal VPS", available anywhere for $4/month, if you lease it for the entire month.  If it is something special, please enlighten us.  When I google the term, RackNerd came up.  That choice got me thinking you knew more about Linux, so I didn't need to be as detailed with my response.
 
there's so much material here I need to digest. thank you. 

Sorry. My mistake. I meant Racknerd. I thought the Black Friday deals are pretty good.   [https://www.racknerd.com/BlackFriday/](https://www.racknerd.com/BlackFriday/)

I purchased this deal

[COLOR=#666666][FONT=mpolis]4 GB KVM VPS (Black Friday 2023)[/FONT][/COLOR]
[COLOR=#666666][FONT=mpolis]2 vCPU Cores
80 GB **PURE SSD** RAID-10 Storage
4 GB RAM
8000GB **Monthly** Premium Bandwidth
1Gbps Public Network Port
Full Root Admin Access
1 Dedicated IPv4 Address
KVM / SolusVM Control Panel - Reboot, Reinstall, Manage rDNS, & much more
**[COLOR=black]Available in[/COLOR]** Multiple Locations
[B][COLOR=green]JUST $38.88/YEAR - WOW!!
[/COLOR][COLOR=#000000][/COLOR][/B][COLOR=#000000][B]
[/B]**It's cheap but the downside is that there's no support whatsoever. I mean no hand holding. **[/COLOR]**[COLOR=green][/COLOR]**[/FONT][/COLOR]

---

### Post by TheFu on 2023-12-06
That does sound good, but I'd want to know the exact performance of the provided cores.
4GB is a little light for Gnome DE. Would be smart to use LXQt as MAFoElffen (and I) suggested.

No hand-holding is common.
Good price, if the uptime meets your needs.  I pay $4/month for a small VPS - no GUI. It is just a VPN server providing a reverse proxy to some services I host at home through my ISP.  Basically, I needed a static IP for email and websites and a VPN on occasion for outbound traffic.  For inbound traffic, my IP doesn't change very often and I use a direct VPN or SSH to get back into my LANs.

In the mid-1990s, my first web hosting happened on a BSD-based shared hosting platform - NearlyFreeSpeech.net.  I put a $10 into an envelop to fund my needs for about 4 yrs.  It was $0.25/month to host a simple static website with only ssh and rsync access. Nothing else. No control panel.  No GUI.  No support phone number. No help.  They are still around and have added more complex offers, but they still use BSD and static websites are very cheap.

I'm a huge believer in using remote desktops, but not using someone else's computers.  Self-hosted instead.  Then I have complete control over the setup and all my data.  To each their own. I'm already paying monthly for a slow-by-today's standards internet connection (30/6 Mbps), so I only want to use a VPS when absolutely necessary.  Most of us have a very fast Linux computer at home - mine perform like the Cray supercomputers from 30 yrs ago and are considered mid-tier these days.  Each was less than $400.  I suspect you have something similar or better. Anyway, running virtual machines on almost any computer that is less than 10 yrs old is quite acceptable for most people.

But we are way off-topic now.  You have reasons for doing what you are doing, I'm certain. MAFoElffen and I have been around Linux/Unix a long time.  He's kept up with MS-Windows stuff, which I haven't.

---

### Post by MAFoElffen on 2023-12-06
For 4GB max head-room... Let me crunch the numbers vs packages for a min-X solution

I came up with this script for you... That would be a minimal X solution, adding just what you mentioned. 
You could either cut/paste it into a script to make executable or run the commands individually. 
```

#!/bin/bash


  ## Mike Ferreira: <MAFoElffen@ubuntu.com>, 2023.12.06
   
  ## Setup/Install Minimum X on Debian based Server (Ubuntu)
  # -- Server monitoring software needs a minimal X config for remote 
  # -- graphical admin consoles to use X enabled monitoring tools to  
  # -- display.
  # --
  # -- I amended this for min-X cloud image, for use with xrdp-server
  # -- 
  # -- This install adds a minimal X config that allows an "instance" load of X that 
  # -- server admin tools from a remote graphical X console needs to get working 
  # -- over X enabled ssh.
  # --
  # -- This X instance does not load by default (local on server) and unloads X on exit.


## Installs a Minimal X Server Core
echo "# Installing the XServer core"
echo "#"
echo " "

# Install minimal
sudo apt-get install --yes --without-recommends xserver-xorg-core xserver-xorg-input-evdev \
    xserver-xorg-input-mouse xserver-xorg-video-vesa xserver-xorg-video-fbdev xinit

# Installs a minimal window environment with a few utils to manage it 
sudo apt-get install --yes lxqt-core

# Add user xrdp-user
sudo adduser xrdp-user
sudo usermod -aG sudo xrdp-user

# Add startup of lxqt desktop for user xrdp-user's login
sudo echo "exec startlxqt" >> /home/xrdp-user/.xinitrc

# Add an .Xuthority file to user home
# If you use ssh with "-X" to enable X over shh, 
# it needs to see the .Xauthority file of the user.
rm /home/xrdp-user/.Xauthority
touch /home/xrdp-user/.Xauthority
chown xrdp-user:xrdp-user /home/xrdp-user/.Xauthority
chmod 600 /home/xrdp-user/.Xauthority

# Add firefox, leafpad and any other light-weight applications 
# you want... As needed...
sudo apt-get install --yes firefox leafpad xterm

```
Notice the last section... It doesn't install a full suite of applications. To save room, add those as needed. When you install a full suite of applications, it adds a lot of fluff. If you find you need something, then install it. If you find you don't use something, uninstall it to save room.

You'll find with cloud-images, even to do some basic things, sometimes you'll have to install would we would usually assume to be basic Linux utilities. In those cases you'll get a command-not-found... LOL. They cut those cloud-images down below the ubuntu base and ubuntu-standard to cut the base image size down. I usually just install those when I find I need them, to do what I want, or need to do to keep their size down.

This solution when you logout, it keeps the instance running, but unloads the XServer to save resources. That treats the XServer instance as on-demand (when needed). If you log out with xrdp, it closes the RDP session down. But is still running, waiting for the next time you want to connect. 

If you need to shut the instance down, then open a terminal window, and use the shutdown command to shut it down. This is what I do for Server VM's and cloud-images when I want to do Min X. And with XRDP, it needs at least XServer and a Desktop to connect to.

---

