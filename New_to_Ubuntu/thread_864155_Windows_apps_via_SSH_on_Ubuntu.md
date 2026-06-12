---
title: "Windows apps via SSH on Ubuntu"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by TBev0 on 2008-07-19
Is it possible to run windows applications via SSH on an ubuntu machine and vice versa?

---

### Post by scorp123 on 2008-07-19
> **TBev0 said:**
> Is it possible to run windows applications via SSH on an ubuntu machine and vice versa? Not directly, no. Windows doesn't support SSH out of the box to begin with, so using SSH towards a Windows machine is pointless.

If you want to remotely access Windows apps from your Ubuntu machine you can ... 

- use VNC
- or use "Remote Desktop" (requires that this feature is enabled on the Windows side and that the firewall lets the RDP protocol through)


If you want to remotely access Ubuntu apps from your Windows machine you can ...

- enable "vino" and then use VNC
- or install and configure FreeNX and then use a NX client


Executing applications remotely via SSH and then have graphical applications displayed remotely necessitates ...

- a working SSH server
- a working SSH client capable of redirecting X11 connections (the Linux "ssh" shell command can do that without trouble)
- a working X11 server on the receiving side (or else the app cannot be displayed!)
- the SSH connection must be initiated with the "-X" parameter, e.g. "ssh -X youruser@remotehost" or "X11 redirection" enabled if you use any other client (e.g. Putty)

Usually such connections are only used between UNIX-like operating systems, as any non-UNIX-like OS such as Windows usually lacks these packages, e.g. I don't know of any free SSH server for Windows. Free X11 servers are available but hardly anyone uses them (I mean in productive environments) as with RDP and VNC there simply is hardly any need to do so.

---

### Post by TBev0 on 2008-07-19
Thanks for your reply, sorry i guess i should have been more specific in my original post although you do seem to have covered some points and answered some of my questions quite nicely. 

Currently i have: 

1) a powerful dual processor Windows Desktop Server 
2) a powerful dual processor Ubuntu Desktop Server
3) a not so powerful ubuntu laptop

What i would like to achieve is to use my low spec'd ubuntu laptop as a type of 'dumb terminal' eg: i would like to be able to run programs on my ubuntu laptop via ssh so the apps are really actually running on my servers that have the physical resources to run the programs instead of consuming the resources of my laptop that struggles as it is. Also i'd like to do this in a 'seamless' mode so i just get the app i am working on, rather than working through a vnc session where the entire machines desktop is viewable.

I have been able to achieve this via SSH between the Ubuntu Server and the Ubuntu laptop relatively easily using the ssh user@remotehost -x -f &  command.

I am now trying to implement a similar setup between my Windows server and ubuntu laptop. I have manged to get as far as installing OpenSSH server on the windows machine and establishing a SSH connection between the two. However i cant seem to run a simple command such as:
SSH user@windowsserver -x -f notepad &
When i do, if i check the windows task manager i notice that the notepad.exe process is being executed, however the app just isnt being displayed on either the windows server or on the ubuntu laptop. So it would seem the process is working to some degree. 

Is there something additional i need to setup or am i trying to do something that isnt really possible? If so is there a solution for what i am trying to achieve? I have read about a program called 2X application server, but have had limited success with this program.

---

### Post by JagDragon on 2008-07-19
If you are wanting a remote GUI, Linux has beat you to it. XDMCP is the protocol which allows X applications to be run on one computer, but displayed on another "dumb terminal". What you have to do to enable this is (on the server) go to System -> Admin -> Login window, and configure the remote login. If you set it to "Plain face browser" then you will be allowed to configure options like how many clients are allowed to run, how long for, and other things like that.

Once that is set up, to access your Powerful Ubuntu Server from your laptop, go to the login screen, find the option that says "Remote login via XDMCP", and click on that. Then enter the name of your Server and you should be in. Easy as that.

To access it from windows, you need something a bit tricky. Cygwin is a linux emulator that runs under Windoze, and you can install the X11 binaries as well. Navigate to [http://www.cygwin.com/](http://www.cygwin.com/) and download the Setup.exe which will guide you though installing Cygwin. You need to make sure you select the X11 core system, though! After cygwin is installed, open a Cygwin terminal and type```
xwin -query [name of server]
```

Well, that should about do it. About running apps the other way around (Windoze -> Ubuntu), I've no idea.

I hope I've been of some help!

PS to SSH from Windoze to Linux, Putty is your friend. Google it.

---

### Post by txcrackers on 2008-07-19
The only thing I'm aware of that allows this is to use *rdesktop*, which is the Linux client-side of Windows Remote Desktop. It actually works surprisingly well, but will be a bit more of a network hog since it's the entire desktop. Either that or set up VNC.

---

### Post by linfidel on 2008-07-19
> **TBev0 said:**
>    ...
I am now trying to implement a similar setup between my Windows server and ubuntu laptop. I have manged to get as far as installing OpenSSH server on the windows machine and establishing a SSH connection between the two. However i cant seem to run a simple command such as:
SSH user@windowsserver -x -f notepad &
When i do, if i check the windows task manager i notice that the notepad.exe process is being executed, however the app just isnt being displayed on either the windows server or on the ubuntu laptop. So it would seem the process is working to some degree. 

Is there something additional i need to setup or am i trying to do something that isnt really possible? If so is there a solution for what i am trying to achieve? I have read about a program called 2X application server, but have had limited success with this program.You can only run X-windows programs, which windows doesn't use.  I run cygwin on my windows system at work, which supports x-windows, and use ssh a lot to connect to various linux systems.  cygwin supports ssh and openssh, so I have an ssh demon running as a service on windows.  I can run the cygwin graphical apps remotely, but only things like gvim, the editor I use, or xclock, xeyes, etc.  Basically, you can run apps that normally run on linux, but not Windows apps.  To do that, you need to use a remote desktop program, and enable remote desktop on the windows box.

---

### Post by linfidel on 2008-07-19
> **JagDragon said:**
> http://www.cygwin.com/[/url] and download the Setup.exe which will guide you though installing Cygwin. You need to make sure you select the X11 core system, though! After cygwin is installed, open a Cygwin terminal and type```
xwin -query [name of server]
```Well, that should about do it. About running apps the other way around (Windoze -> Ubuntu), I've no idea.

I hope I've been of some help!

PS to SSH from Windoze to Linux, Putty is your friend. Google it.
If you have cygwin, there is no need to use putty - it is not your friend.  Especially not if you want to use x-windows.  You use ssh on cygwin just like on linux, from the command line

By the way, using the "xwin -query" is not the only way, or even the best way to use cygwin.  That's essentially a remote desktop.  I type "startx", which starts a local x-windows session, then treat it like it's any other linux box, using ssh to connect to other systems.

---

### Post by maybeway36 on 2008-07-19
To run Linux apps on Windows, I always used PuTTY+Xming, which doesn't need Cygwin.

---

### Post by linfidel on 2008-07-19
> **maybeway36 said:**
> To run Linux apps on Windows, I always used PuTTY+Xming, which doesn't need Cygwin.
Cygwin is much more than that, though. If you know the unix/linux environment, cygwin gives you that on windows.  You have a bash shell with all the utilities running on your windows system, with all the power of regular expressions, sed, grep, etc.  Cygwin even mounts the registry into the filesystem.  x-windows is a small part of cygwin.

But if all you want is Windows, with remote access to linux, then I'm sure Xming is fine.

---

### Post by The Cog on 2008-07-19
Windows has a proprietary (of course) protocol used for remote management. Ubuntu has a client for this called rdesktop.

If you can't get the rdesktop server working on Windows, you can find a VNC server to install (there are several VNC servers for windows, I can't remember the names at the moment). Both rdesktop and VNC clients can be found in Ubuntu under Internet -> Terminal Server Client.

---

### Post by AndyCooll on 2008-07-19
The bottom line is ...no it isn't possible to run Windows apps via SSH.

Running apps using SSH is using the X11 server graphics protocol, something that the Windows environment (and hence its programs) don't use.

PuTTY gives you access to Linux machines if you're sat at a Windows box. And Cygwin recreates a Unix environment on a Windows machine. However neither are giving you access to the Windows environment (though as has been pointed out Cygwin can load the Windows registry).

As has been pointed out, the nearest you are going to get to accessing programs on the Windows server is by using something like VNC, rdesktop or FreeNX.

:cool:

---

### Post by The Cog on 2008-07-20
It occurs to me that the poster mught be asking for two different reasons.

1) He is not aware of the existence of VNC and rdesktop protocols, or that Linux has clients for these, and

2) He wants the security and encryption that come with SSH.

If 2) was the reason, it is possible to tunnel VNC and rdesktop through SSH
First, configure VNC to listen only on the loopback address 127.0.0.1, which makes it unreachable from across the network. 
Second, connect to the server using SSH with a command like this:
**ssh -L 127.0.0.1:5900:127.0.0.1:5900 user@server** 
Third, try to VNC his local workstation and let SSH relay it to the server:
**vncviewer 127.0.0.1**

The ssh command above tells SSH to listen on 127.0.0.1:5900 and relay any connections to that port through the tunnel to the remote 127.0.0.1:5900.

---

### Post by sampowers on 2008-09-07
I do a lot of work with Windows Server for my day job, and I think I've tried just about every conceivable way of accessing those servers from my workstation, which has always been Debian or Ubuntu.

One option is rdesktop (or rdesktop launched via tsclient, which is my current favorite way of doing this.)

If you get rdesktop version 1.5 or newer, and install an application called seamlessrdp on your windows server, the rdesktop program can be told to trim away the backgrounds and so on, but in my experience this would only be good for running one single application.  For instance, if you had an important business app that needed to run on your windows server, but you still wanted to connect from inside of an X sesison, seamlessrdp may be the trick there.  [More information about SeamlessRDP]("http://www.google.com/search?q=seamlessrdp+howto")

Another option if you really needed to do this and had some money to spend would be to use Citrix ICA.  It's been since 2003 that i've tried this.  It worked OK with their Linux client, but the client was ugly and hard to use.  I'm sure they've made some improvements since.

---

### Post by sampowers on 2008-09-07
Oh, I almost forgot.

You can access a windows command line app via a program called WinExec, which apparently comes from Samba4 sources as a "tech preview" of all of the cool stuff they're doing with the windows RPC server.

[http://eol.ovh.org/winexe/](http://eol.ovh.org/winexe/)

---

