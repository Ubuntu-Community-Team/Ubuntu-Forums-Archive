---
title: "new private server runs Hardy, root shell only; how to access via XDMCP?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by hoink on 2008-05-14
Hi.

I have a new Hardy VPS at a linux host and I need to set up remote access -- desktop style, not just bash/SSH.

I've got an XDMCP client (X-Win32, i'll get Cygwin's later) ready to connect to my Hardy VPS, but my Hardy VPS is only responding to SSH and gives me a nice bash prompt.

I'm lost and need some way-pointing.  What command line incantations and gruntwork do I need to do so I can, for example, use a Qt application over XDMCP?  (laggy, but necessary)

ALL the tutorials I could find on setting up remote desktop access presuppose that a window manager is already running on my machine.  That is NOT the case for me.  I've got Hardy, but in shell-only mode.  

My hosting company pre-installed some strain of Hardy, but it didn't include any X-server doodads.  I pulled a bunch of "raw material" from the repository, but now I need some sweet, tender cluesticking to actually achieve remote-desktop-ubuntu-radness.

TIA.

---

### Post by bodhi.zazen on 2008-05-14
ssh -X or vnc server.

ssh -x = forwarding X over ssh. You launch your X server on windows and froward the desktop.

vnc server -> Install vnc server on the server, ssh in forwarding VNC ports, connect with vnc viewer.

[uwiki]VNCOverSSH[/uwiki]

[uwiki]SSHHow[/uwiki]

---

### Post by mlentink on 2008-05-14
> **hoink said:**
> 
ALL the tutorials I could find on setting up remote desktop access presuppose that a window manager is already running on my machine.  That is NOT the case for me.  I've got Hardy, but in shell-only mode.  

My hosting company pre-installed some strain of Hardy, but it didn't include any X-server doodads.  I pulled a bunch of "raw material" from the repository, but now I need some sweet, tender cluesticking to actually achieve remote-desktop-ubuntu-radness.

TIA.

Frankly, imho, you don't need xdmcp. ssh is fine. You've got a server box, not a desktop.

If you would really want to install a desktop (although it really beats me why you would want to, I run my server on cli only, much less bloat and overhead), you could do 
```
sudo apt-get install ubuntu-desktop
```
or 
```
sudo apt-get install kubuntu-desktop
```
or, if you want to stay as lean as possible and have a desktop:
```
sudo apt-get xubuntu-desktop
```

I guess you've already searched for what to do next..

---

### Post by hoink on 2008-05-15
Thanks for the names and links.

I haven't successfully connected yet, but vncserver does open port 5901.

I type vncserver and get...

```

Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.

```

...and inside the log (attached) is a corresponding complaint...

```

Fatal server error:
could not open default font 'fixed'

```

Here's my vnc.conf file taken from the wiki...

```

$fontPath .= "/usr/share/fonts/X11/misc,";
$fontPath .= "/usr/share/fonts/X11/100dpi/:unscaled,";
$fontPath .= "/usr/share/fonts/X11/75dpi/:unscaled,";
$fontPath .= "/usr/share/fonts/X11/Type1,";
$fontPath .= "/usr/share/fonts/X11/100dpi,";
$fontPath .= "/usr/share/fonts/X11/75dpi,";

```

I've attached my log file.  It seems pretty problem-encrusted...  

```
xrdb: No such file or directory
xrdb: can't open file '/root/.Xresources'
```

... and there are a slew of warnings, saying that the following extensions a) aren't supported or b) are missing: XRender, XRandr, XComposite, XDamage, Xfixes, XFree86-VidModeExtension, XFree86-Misc, Xkb, XINPUT.

I'm continuing to try to connect, but wanted the server side part checked over.

--) What do I need to enter into vnc.conf so vncserver doesn't complain with FATAL?

--) All those missing extensions... is that normal for vncserver?

---

### Post by hoink on 2008-05-15
Rad.

I connected to my server with TightVNC, but only by using the actual server address and port.  The whole "forward thru putty/ssh" thing was a big fail.  

So I guess connecting straight to the vncserver is a massive security hole?

---

### Post by bodhi.zazen on 2008-05-15
NICE !!!

No, just take things one step at a time.

Next you need to install a ssh server, learn to connect with that, forward port 5900

Then you connect with 

localhost:5900

[uwiki]VNXOverSSH[/uwiki]

---

