---
title: "HOWTO: tunnel GNOME/KDE/etc. through SSH"
date: 2007-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by maybeway36 on 2007-07-20
Besides offering the user a remote shell, SSH can also run X11 applications on a remote computer. This extends even to desktop environments such as GNOME and KDE, as they consist of a collection of separate applications.
I have used this method with two computers running Kubuntu 7.04. However, the computers do not necessarily need to run the same environment or even the same distribution.
WARNING: I offer NO support for this guide; i.e. if your computer a splode, it's not my fault.

1. On the server, install a desktop environment and OpenSSH server, if they are not already present. An X server is not required.
```
sudo aptitude install openssh-server
```
2. On the client, install an X server, the xterm terminal emulator, and the OpenSSH client. These should already be present on most distributions.
3. On the client, press Ctrl+Alt+F2 to show a terminal. Log in and type
```
xinit /usr/bin/xterm -- :1
```
to open a new X session (on "display 1") with only a terminal on the screen.
Note: In distributions besides Ubuntu and Debian, the xterm executable may be in a different place. Use the command ```
whereis xterm
``` to find it.
4. The screen should switch to a graphical screen with a terminal in the upper-left corner. If it does not, try pressing Ctrl+Alt+F8 or Ctrl+Alt+F9.
In the new terminal, open an SSH connection to the server. Type:
```
ssh -Y username@hostname
```
replacing "username" with your login name on the server and "hostname" with the server's host name (or IP address.)
5. The SSH client will ask you for your server password. Enter it. :)
6. Now that you have a shell prompt, all you need to do is launch the desktop enviroment.
For GNOME: ```
gnome-session
```
For KDE: ```
startkde
```
For XFCE: ```
startxfce4
```
7. Now enjoy! Don't close the xterm window until you are done, and if the server doesn't close after you log out of GNOME/KDE, press Ctrl+Alt+Backspace to kill it.

EDIT: roger56 mentioned Ubuntu 7.04 switches to TTY9 rather than TTY8. It turns out TTY8 is used for startup messages.

---

### Post by rainbowed_man on 2007-07-30
Review:
This guide is rated 4.5/5. There is a minor glaring detail which this guide fails to mention: In Step 3, "the new terminal" means the xterm started by the xinit command which you typed. You must switch to the new display by doing either:
> chvt 8 in the terminal, or typing CTRL+ALT+F8 (all three keys to be pressed at the same time)

---

### Post by praveenmarkandu on 2007-07-31
how do i see a GUI if i use windows to log into my ubuntu using PuTTY?

---

### Post by ynef on 2007-07-31
> **praveenmarkandu said:**
> how do i see a GUI if i use windows to log into my ubuntu using PuTTY?

Then you need to run an X server and have Putty forward X11 commands to it. Google for Cygwin, it's free.

---

### Post by DDM on 2007-07-31
Very handy. Much less cranky than FreeNX. 2 questions though:

1) Is there a way to make the sessions persist?
2) Is there a way to automate the whole process?  (As in automatically switch to VT 1, start xterm and pass the ssh -Y command to it)

I'm asking because I'm constantly accessing my headless MythTV/Torrent/Music box. In fact, I'm using it to post right now thanks to your HOWTO :)

---

### Post by maybeway36 on 2007-08-01
To rainbowed_man:
Typing xinit usually switches to F8 automatically, I think. I'll add it anyway, plus I'm changing Ctrl+Alt+F1 to Ctrl+Alt+F2 so it works with Knoppix.

To DDM:
As for automating it, you might want to look into [xserver-xephyr.]("http://packages.ubuntu.com/dapper/x11/xserver-xephyr") You can use these commands:
```
Xephyr :1 -ac -screen 800x600 &
set DISPLAY=:1
xterm -e ssh -Y username@hostname
```
I haven't tested it yet, so I can't be sure. (I took it from the Kubuntu site's instructions about starting a new server for KDE4.)
And unfournately, you can't make sessions persist. For that I'd recommend x11vnc or something similar.

To praveenmarkandu:
If Cygwin doesn't work, you can also try [Xming]("http://sourceforge.net/projects/xming"). It includes SSH capability. You might have to manually close it with Alt+F4 when you're done, though.

---

### Post by roger56 on 2007-08-06
Thank you maybeway36 for this short straight forward howto. Worked for me as promised.
I use Debian Etch on my server, and Ubuntu 7.04 on my Laptop. the only thing, that differs with my installation is, that after starting the xterm, it switches to TTY9 instead of the mentioned TTY8, but I think that's the way with Ubuntu 7.04.

---

### Post by scrooge_74 on 2007-08-09
nice how to

---

### Post by johannes_h on 2009-04-20
xinit /usr/bin/xterm -- :1

this gives me a gray screen.. also when I use VNC I only get gray screens.. hehe what can be wrong?

---

### Post by Nodaki on 2010-12-13
Excellent post.  I had to install No Machine NX on a RedHat Server because my organization absolutely does not allow VNC on anything.

Worked like it was supposed to other than failing with my MS Curve keyboard.

---

### Post by marke9 on 2011-02-10
Perhaps a minor variation for those who want to run a gnome session from a Windows machine via ssh:

[LIST=1]
[*]Install cygwin on the Windows machine (select Net>openssh and X11>xinit in the packages)
[*]Launch cygwin and in the cygwin shell window type xinit to start an X11 server.
[*]In the X11 shell window, establish a connection to the host:
[LIST=1]
[*]ssh -Y <username>@<hostname>
[*](accept the certificate if necessary)
[*]enter your password
[/LIST]
[*]Having established a connection to the host, type gnome-session to get the gnome view on the host.
[*]Minimize the terminal window leaving a full-screen gui on the host.
[/LIST]
If the host is a server, and you have sudo access, you can add gnome (etc.) by:

#apt-get install --no-install-recommends ubuntu-desktop

---

