---
title: "Run a graphical application remotely"
date: 2006-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by jonny on 2006-05-03
This is so simple that it hardly counts as a how-to.  But it took me ages to discover and I guess that many of you are just as ignorant.

Sometimes it's really useful to run a program on another computer.  Perhaps you don't have the program that you want installed on the computer that you're using.  Perhaps you don't want to spoil the kids' Supertux game just so that you can get at a spreadsheet for work.  Or perhaps you want to do some remote system administration without struggling with a command line file editor.

All this is stunningly simple in ubuntu.  Simply install SSH Server on the computer (this is a one-off task) that you want to connect to:
```
sudo apt-get install openssh-server
```
There's a much fuller discussion about SSH in the Ubuntu Wiki, [here]("https://wiki.ubuntu.com/SSHHowto"), but you don't need to follow it unless you have problems or are deeply interested in these things.

Now all you need to do is open a terminal session on the other PC (ie the one that you want to sit in front of) and type:
```
ssh -X [server ip address] [program that you want to run]
```
For example, to run OpenOffice.org writer on the first computer to be connected to a typical home network, you'd type:
```
ssh -X 192.168.1.2 oowriter2
``` (If you want to find out what a program is called, drag the appropriate menu item to your desktop, right click on it to view its properties and look at the Launcher tab.  The program name is in the Command box.)

And that's it.  It Just Works.  It doesn't even matter if someone else is logged on to the remote PC.

This really is a much more elegant solution than using VNC.  It doesn't take over your whole desktop, and the clipboard will interoperate properly between applications.  I hope that you enjoy using it as much as I do.

---

### Post by RAOF on 2006-05-05
It is worth noting that this will be **sloooooow** unless you've got a fast connection between the computer you're using and the remote machine.  That's one of the things that VNC/FreeNX are better for - they work faster over slower connections.

If you're just running stuff on another machine on your local network, ssh will work just fine.

---

### Post by george_apan on 2006-05-05
Thanks! This is great. Since the software runs on the server that means I can use an old PC as a client to run CPU and RAM hungry software on my home network. :D

---

### Post by jonny on 2006-05-05
I installed VNC before I discovered this trick.  On a wireless LAN, it's definitely faster to use ssh -X than it is to use VNC, although I've never made a comparison over the internet.  Even complex apps like OpenOffice are handled effortlessly on my network.  On ubuntu, SSH is configured to use compression by default, so I guess that helps to speed things up.

The great thing about using ssh -X is that the application looks and feels exactly like a local one - it'll even respect your Gnome notification area if appropriate.  You can also create menu shortcuts to the remote machine, so, for example, a launcher with the command ssh -X gksudo gedit will give you instant access to a root text editor on your remote machine.  It's great for administering a home server (in a corporate environment most people wouldn't install X on a server)

---

### Post by n8bounds on 2006-05-05
Awesome tip, thanks jonny

---

### Post by stalefries on 2006-05-05
Does anyone know of a way where remote applications can be run on a Windows machine? Even better, could I install a Windows port of ssh on a flash drive, and carry it with me?

---

### Post by jonny on 2006-05-05
I don't know of a way to use the solution that I've described under Windows.  You need VNC instead - that'll allow you to see a full remote Linux desktop in Windows.  There are several How Tos out there, but I can't recommend any particular one as I originally got VNC working under Warty many months ago.

If you plan to use VNC over the web, bear in mind that it's not a safe protocol.  If your connection is insecure, you need to channel it through SSH - sorry if that adds an extra layer of complexity.

---

### Post by george_apan on 2006-05-06
[QUOTE=stalefries]Does anyone know of a way where remote applications can be run on a Windows machine? Even better, could I install a Windows port of ssh on a flash drive, and carry it with me?[/QUOTE]
Maybe this could be done with cygwin using ssh and the X port. I don't know, I haven't tried it, it's just an idea...

---

### Post by dabear on 2006-05-06
Download the command line version of putty (plink.exe) and install xming. Now you can reach your ubuntu from a windows machine.

I am doing that now, although the fonts are small, it works perfectly.

evolution from ubuntu running in windows

---

### Post by chuko on 2006-05-06
dabear and jonny many thanks for your awesome and useful howto!!!

Now I can acces my kubuntu machine from uni without having to use that VNC!!!!

xD

---

### Post by GoldBuggie on 2006-05-06
this was some great stuff...thank you.

Do I understand it correctly that the app that you will run will do its computing or processing on the server?

---

### Post by GoldBuggie on 2006-05-06
from my ubuntu machine i tried doing **ssh -X <IP> "/usr/kde/3.5/bin/kwrite"**
to my gentoo machine

but it spits out:
[B]kwrite: cannot connect to X server
[/B]
You know what I missed? Any config?

---

### Post by DA_uf on 2006-05-07
I use XLiveCD to run a remote graphical application, but I learned 2 things from this thread.

1) That you can run the specific app with 1 command:
> ssh -X [server ip address] [program that you want to run]

2) How to find out the names of the application to be used from the command line:
> (If you want to find out what a program is called, drag the appropriate menu item to your desktop, right click on it to view its properties and look at the Launcher tab. The program name is in the Command box.)

I think that "Properties" menu option should be available from a right-click from the menu in the first place, but at least now I know this method.  Maybe you should put this tip under its own entry somewhere.  Thanks jonny.

---

### Post by pkbarber on 2006-05-07
Nice, way eaiser than the last time i tired to do this.  WAY EASIER.

---

### Post by jonny on 2006-05-07
[QUOTE=GoldBuggie]Do I understand it correctly that the app that you will run will do its computing or processing on the server?[/QUOTE]
You understand correctly.  It means that you can use a low spec machine as the local box.

---

### Post by jonny on 2006-05-07
[QUOTE=GoldBuggie]from my ubuntu machine i tried doing **ssh -X <IP> "/usr/kde/3.5/bin/kwrite"**
to my gentoo machine

but it spits out:
[B]kwrite: cannot connect to X server
[/B]
You know what I missed? Any config?[/QUOTE]I never use kwrite so I don't know what the problem is here.  I have found that a few apps don't work over SSH, and maybe kwrite is one of them.

You might get more luck if you make your ssh connection first (just use ssh -X [server name] ) and then try to run the app.

---

### Post by benplaut on 2006-05-08
i use this for doing things on my headless server... works like a charm :D

plus, i can run MythTV inside a window and stream stuff to the laptop... not as fast as local, but definately usable

---

### Post by TheXanaX on 2006-05-23
[QUOTE=dabear]Download the command line version of putty (plink.exe) and install xming. Now you can reach your ubuntu from a windows machine.

I am doing that now, although the fonts are small, it works perfectly.

evolution from ubuntu running in windows[/QUOTE]

Works great, thanks a lot for the tips. Only thingy is that I always have to save my configuration file or else an error will occur. 

Quick setup: 

- install SSH on your Ubuntu machine.
- Download Xming for Windows and Install in on your machine.
- Download Plink.exe (used to remote acces the ubuntu machine)

Well then start XLaunch and follow the instructions, should work like a charm.

XanaX

---

### Post by GOwin on 2006-05-26
Have you tried FreeNX?

[Here](http://www.snakeoillabs.com/2005/10/27/freenx-on-ubuntu-breezy-howto/)'s a fellow Ubuntu user who has done it. (In case it's down, here's google cache of the site.

The [Ubuntu Wiki entry](https://wiki.ubuntu.com/FreeNX).

---

