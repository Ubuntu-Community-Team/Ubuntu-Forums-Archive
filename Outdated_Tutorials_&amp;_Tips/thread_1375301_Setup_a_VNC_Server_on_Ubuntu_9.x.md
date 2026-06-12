---
title: "Setup a VNC Server on Ubuntu 9.x"
date: 2010-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by howardjacobson on 2010-01-07
I spent quite a few hours trying to get a VNC server functioning on 9.04 (Jaunty).  I read through many posts here and on other sites.  I thought I'd try distilling all I read down to a few key things.

There is a [**post**]("http://ubuntuforums.org/showthread.php?t=122402") on the forums that goes for 60 pages that began in 2006.  It is outdated in some respects, but has good information.  Make note of this URL only as a reference since the many replies in the thread could help you solve a particular problem you have once you follow the instructions below.

Start by following the instructions given [**here**]("http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/").
[LIST]
[*]Follow All of Step 1 in the instructions.  In this Step you tell Gnome that you want to enable remote access, and you configure a bit of how remote access will appear.
** Note that this step refers to a file /etc/X11/gdm/gdm.conf, but on Jaunty (9.04), the file is /etc/gdm/gdm.conf-custom.  You probably won't find a directory called /etc/X11/gdm.
** Note also that the RemoteGreeter config line in gdm.conf-custom probably is in the [daemon] section, not the [xdmcp] section.
** You do not need to read the commentary about software repositories and freedom to be successful setting up VNC.  If you are particularly concerned about having possibly proprietary or license-restricted software on your system, then the commentary is informative.

[*]Follow Step 2, which simply requires that you do the following:
```
sudo apt-get install vnc4server xinetd
```
The remainder of the information in Step 2 is not relevant for Jaunty (9.04).
[*]Follow Step 3.
[*]Follow Step 4, BUT in the line that begins with server_args, you will change "localhost" to "127.0.0.1" as follows:
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
server_args = -inetd :1 -query 127.0.0.1 -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
port = 5901
}

```

[*]Here's where you depart from the post cited above and must do a few things differently to succeed.  I found these remaining steps in this [**post**]("http://saraiya.com/blog/2009/11/06/how-to-get-vnc-working-with-a-hidden-desktop-on-ubuntu-9-04-jaunty/").
** You must now create an xserver directory under /etc/X11 if one does not already exist, so:
```
sudo mkdir -p /etc/X11/xserver
```
** Then, you must create a SecurityPolicy file in that new directory, but there is no such file in the 9.04 distribution.  You can find one that you can start with [**here**]("http://ubuntuforums.org/showthread.php?t=186035"). (Be sure to read through it and ensure that the policies fit your needs.)
** You then need an rgb.txt file in the /etc/X11 directory. The only one I found on my system came from the Emacs editor, and I just copied it into /etc/X11:
```
sudo cp /usr/share/emacs/22.2/etc/rgb.txt /etc/X11
```
Note that I installed Emacs previously, and I do not believe Emacs is installed by default with 9.04.
[*]Reboot, and you should be able to access your system through VNC.  I installed the free UltraVNC viewer on my Windows 7 machine, which I downloaded [**here**]("http://www.uvnc.com/download/1082/") and which was the current version at the time I downloaded it.
[/LIST]
I hope this summary helps someone get a VNC server up and running faster than I did.

---

### Post by gogobambi on 2010-01-12
I have followed your instructions and am able to get to the login screen and access VNC fine; just as long as I have a display connected to the box. If I don't have a display connected, GDM doesn't start and all I can see is a gray screen.

You can get around this by adding '/usr/bin/gnome-session &' to '~/.vnc/xstartup' and running vncserver from ssh. However, I don't have the same privileges when I access the box from anything other than Vino when the box is connected to a display.

I don't even really need to use vnc4server; in fact I'd prefer to use Vino and log into the same screen rather than a separate one. I followed **[these instructions on how to fake a connected display]("http://ubuntuforums.org/showthread.php?t=1297815")**, and have been able to log into Vino with all privilages. Doing this has the added benefit of getting past the gray screen issue, but still doesn't solve the problems with privilages.

---

### Post by frog-master on 2010-01-25
Well, all this should not be nessesary. I have full control just dowloading and installing VNC with the usage off Synaptic and then selectig **Allowing others to controll the desktop** from the upper right side off the screen.

---

